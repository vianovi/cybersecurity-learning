# NET-01 — Apa yang terjadi ketika kamu membuka website?

**Tujuan:** membedakan URL, DNS, koneksi, request, response, dan tampilan browser.  
**Prasyarat:** SET-01; tidak perlu pernah belajar hacking. **Estimasi:** teori 15 menit, praktik 20 menit.  
**Validasi:** teori merujuk dokumentasi resmi; contoh terminal diuji pada runtime Linux AI, bukan Fedora pengguna. Praktik pengguna belum dilakukan.

## 1. Teori singkat

Saat membuka website, browser bertindak sebagai **client** yang meminta resource. **Server** menerima permintaan dan mengirim response; browser menyusun hasilnya menjadi tampilan.

Alur sederhana untuk kunjungan baru ke website HTTPS:

1. Browser membaca URL: protokol, nama host, port, dan path.
2. Nama host diubah menjadi alamat melalui resolusi nama; hasil DNS mungkin sudah ada di cache.
3. Browser membuat atau memakai kembali koneksi. HTTPS memakai TLS; HTTP/1.1 dan HTTP/2 umumnya melalui TCP, sedangkan HTTP/3 menggunakan QUIC di atas UDP.
4. Browser mengirim HTTP request; server mengirim HTTP response.
5. Browser memproses HTML dan resource tambahan seperti CSS, JavaScript, atau gambar.

Tidak semua kunjungan membuat DNS lookup/koneksi baru; cache dan koneksi yang dipakai ulang dapat mempersingkat alurnya. IP tujuan juga bisa milik CDN/reverse proxy, bukan server aplikasi secara langsung.

## 2. Contoh sederhana

URL ilustrasi berikut tidak perlu dibuka:

```text
https://pendaftaran.example:443/login
```

| Bagian | Fungsi |
|---|---|
| https | Skema yang meminta HTTP melalui koneksi terlindungi TLS |
| pendaftaran.example | Nama host |
| 443 | Port eksplisit; lazimnya bisa dihilangkan untuk HTTPS |
| /login | Path yang diminta ke aplikasi |

DNS membantu mencari alamat host, bukan membaca tabel pengguna atau menentukan password. Server aplikasi memproses route dan bisa mengakses database jika diperlukan. Browser menerima response, bukan otomatis kode PHP server.

## 3. Titik yang penting untuk keamanan

| Bagian | Pertanyaan awal |
|---|---|
| Identitas server | Apakah kita tersambung ke server yang dimaksud? |
| Koneksi | Apakah data dilindungi saat transit? |
| Request | Input mana yang bisa diubah client? |
| Aplikasi | Siapa yang boleh membaca/mengubah resource? |
| Response | Adakah informasi yang tidak semestinya dikirim? |

HTTPS melindungi koneksi; bukan jaminan aplikasi bebas SQLi atau access-control flaw. Detail serangan belum diperlukan pada bab ini.

## 4. Persiapan latihan lokal

Jika di HP, baca teori dan jawab challenge konsep dahulu. Praktik terminal dapat menyusul.

Di laptop gunakan browser, dua tab terminal, Python 3, dan curl. Periksa:

```bash
python3 --version
curl --version
```

Jika belum tersedia, catat kendalanya sebelum instalasi. Kita menggunakan server file bawaan Python agar bisa melihat HTTP tanpa mengatur Laravel/Docker. Ini server demonstrasi, bukan server production.

Latihan memakai port 8765 dan direktori baru di dalam repository. Pastikan tidak ada tunnel/proxy yang memetakan port latihan ini. Jangan menjalankan server dari folder berisi .env atau data proyek.

Semua perintah latihan berikut kompatibel Bash/Fish. Jalankan dari root repository.

## 5. Practice — Buat halaman kecil

```bash
mkdir -p .local-labs/net01
printf '%s\n' '<!doctype html><html lang="id"><meta charset="utf-8"><title>NET-01</title><h1>Halo dari server lokal</h1></html>' > .local-labs/net01/index.html
python3 -m http.server 8765 --bind 127.0.0.1 --directory .local-labs/net01
```

- `mkdir -p` membuat direktori lokal latihan bila belum ada.
- `printf` menulis halaman HTML sederhana. Perintah ini **mengganti index.html latihan** jika sudah ada; simpan perubahanmu dulu bila perlu.
- `--bind 127.0.0.1` membatasi listener ke loopback IPv4.
- `--directory` menentukan direktori yang dilayani.
- Proses server berjalan di foreground. Biarkan terminal ini terbuka.

Direktori .local-labs diabaikan Git melalui .gitignore. Isi server tidak mengakses database SPMB.

**Ilustrasi output:**

```text
Serving HTTP on 127.0.0.1 port 8765 ...
```

## 6. Practice — Amati request dan response

Buka browser laptop ke **http://127.0.0.1:8765/**. Pastikan http, bukan https. Buka Developer Tools → Network, lalu reload.

Pilih request dokumen utama. Catat URL, method, status, dan response body. Nama tab bisa sedikit berbeda antar-browser.

Di tab terminal kedua:

```bash
curl --noproxy '*' -i http://127.0.0.1:8765/
```

`--noproxy '*'` melewati konfigurasi proxy curl untuk permintaan ini; `-i` menampilkan header response bersama body.

**Ilustrasi output dipersingkat:**

```http
HTTP/1.0 200 OK
Server: SimpleHTTP/0.6 Python/3.x
Content-type: text/html

<!doctype html><html lang="id">...
```

Header versi/tanggal bisa berbeda. `200` menyatakan request berhasil ditangani. Body berisi HTML; browser merendernya, curl menampilkannya sebagai teks.

Jika perlu melihat request yang dikirim:

```bash
curl --noproxy '*' -v http://127.0.0.1:8765/
```

Pada verbose output, baris berawalan `>` menunjukkan request dan `<` menunjukkan response headers. Ini hanya untuk lab dummy; verbose output aplikasi nyata dapat memuat informasi sensitif.

## 7. Analyze — Bandingkan kegagalan

Minta path yang tidak ada:

```bash
curl --noproxy '*' -i http://127.0.0.1:8765/tidak-ada
```

Harapannya **404**. Artinya server berhasil dihubungi tetapi resource tidak ditemukan. Secara default curl bisa tetap exit sukses pada HTTP 404; exit code curl dan status HTTP adalah hal berbeda.

Lalu di terminal server tekan **Ctrl+C**. Ulangi request ke root:

```bash
curl --noproxy '*' --max-time 3 -i http://127.0.0.1:8765/
```

Harapannya kegagalan koneksi, sering `curl: (7)`, bukan HTTP 404. `--max-time 3` membatasi waktu permintaan maksimal tiga detik.

| Hasil | Kesimpulan yang didukung |
|---|---|
| 200 + HTML | Ada layanan yang menjawab request ini dengan sukses |
| 404 | Layanan HTTP menjawab, tetapi path tersebut tidak ditemukan |
| Koneksi gagal setelah server dihentikan | Tidak ada jawaban HTTP dari server latihan pada percobaan tersebut |

Latihan memakai IP langsung sehingga **tidak mendemonstrasikan DNS**, memakai HTTP sehingga **tidak mendemonstrasikan TLS**, dan seluruh trafik berada di loopback. Jangan menyimpulkan koneksi internet rusak dari kegagalan localhost.

## 8. Fix dan retest

Jalankan kembali perintah server di langkah 5, tanpa perlu menulis ulang HTML. Ulangi request ke root; harapannya kembali 200.

Perbaikan di sini adalah memulihkan layanan yang dihentikan, bukan memperbaiki vulnerability. Catat hasil aktual bila berbeda dari harapan.

## 9. Troubleshooting

| Gejala | Kemungkinan dan tindakan |
|---|---|
| Address already in use | Port terpakai. Jangan hentikan proses yang belum dikenal; pilih 8766 dan sesuaikan semua URL |
| Root menampilkan directory listing | index.html tidak berada pada direktori yang dilayani; periksa lokasi dan path --directory |
| Browser mencoba HTTPS | Ketik URL lengkap http://127.0.0.1:8765/; gunakan curl bila browser memaksa HTTPS |
| Browser 304 atau tampilan lama | Cache dapat memengaruhi hasil; reload dengan cache dinonaktifkan saat DevTools terbuka |
| 404 favicon.ico | Browser mungkin meminta ikon yang tidak dibuat; fokus pada request dokumen |
| Tidak bisa dibuka dari HP | 127.0.0.1 di HP menunjuk HP; lakukan latihan di browser laptop |
| Command not found | Catat tool yang hilang; jangan menganggap langkah sudah berhasil |

## 10. Cleanup

Tekan Ctrl+C di terminal server. Pastikan request ulang tidak lagi mendapat halaman server latihan. Folder .local-labs/net01 boleh disimpan untuk mengulang; bila ingin menghapus, hapus hanya folder latihan tersebut lewat file manager.

Jangan mengubah firewall, Docker, atau tunnel SPMB untuk latihan ini.

## 11. Mini challenge

1. Tanpa terminal: mengapa DNS tidak sama dengan server aplikasi?
2. Saat mendapat 404, apakah koneksi ke server pasti gagal? Jelaskan.
3. Ubah judul h1 di HTML latihan, reload, lalu bandingkan body di curl.
4. Mengapa HTTPS saja tidak cukup untuk melindungi data pendaftar dari pengguna yang tidak berhak?

<details>
<summary>Petunjuk setelah mencoba sendiri</summary>

DNS membantu resolusi nama, sedangkan server aplikasi memproses request. 404 adalah response HTTP sehingga server telah memberikan jawaban. Perubahan file seharusnya terlihat pada body setelah reload. Pemeriksaan hak akses tetap harus dilakukan aplikasi walaupun koneksi dienkripsi.

</details>

## 12. Checklist dan catatan

- [ ] Menjelaskan URL → resolusi nama → koneksi → request → response → render dengan bahasa sendiri.
- [ ] Bisa membedakan DNS, server aplikasi, dan database.
- [ ] Mengamati 200, 404, dan koneksi gagal pada latihan.
- [ ] Menjalankan retest dan menghentikan server setelah selesai.
- [ ] Mencatat hasil aktual, error, dan satu pertanyaan di jurnal.

**Jika baru membaca di HP:** catat teori saja; checklist praktik tetap kosong.

## Referensi

- [MDN — How the web works](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Web_standards/How_the_web_works)
- [MDN — HTTP overview](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview)
- [Python — http.server](https://docs.python.org/3/library/http.server.html)
- [curl — Manual](https://curl.se/docs/manpage.html)

---

[Sebelumnya: SET-04](../00-setup/04-konsep-lab.md) · [Indeks fundamental](README.md) · [Progres](../PROGRESS.md)

Berikutnya: NET-02 — IP dan interface (belum tersedia).
