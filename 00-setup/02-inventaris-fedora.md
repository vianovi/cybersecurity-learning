# SET-02 — Kenali lingkungan Fedora

**Tujuan:** membaca keadaan perangkat tanpa mengubah konfigurasi.  
**Prasyarat:** SET-01 dan akses laptop. **Estimasi:** 15–20 menit.  
**Validasi:** sintaks ditinjau; belum dijalankan pada Fedora pengguna. Output di bawah ilustrasi.

## Teori singkat

Saat mengetik perintah, kamu memakai terminal (Konsole) dan shell (Bash/Fish) untuk berinteraksi dengan Fedora.

**Pegangan bab ini:** periksa lingkungan tempat perintah dijalankan. PHP di laptop bisa berbeda dengan PHP di container SPMB.

Untuk folder, cukup bedakan: `/` adalah akar filesystem, `/home` tempat home pengguna biasa, dan `/root` home pengguna root.

## Contoh

Laravel berjalan dalam container, sedangkan perintah `php --version` di host menunjukkan PHP host. Versinya boleh berbeda. Hasil host tidak membuktikan versi dalam container.

## Persiapan

Buka Konsole di Fedora, sebagai pengguna biasa. Perintah berikut tidak membutuhkan sudo. Sebagian besar kompatibel Bash/Fish; pemeriksaan PID shell memiliki dua versi. Jalankan satu blok, baca hasil, baru lanjut.

## Langkah 1 — OS dan shell

```bash
cat /etc/os-release
echo "$SHELL"
```

Dua perintah di atas membaca identitas OS dan shell login yang tercatat. Untuk memeriksa shell aktif, pilih salah satu blok berikut.

**Bash:** `$$` adalah PID shell Bash saat ini.

```bash
ps -p "$$" -o comm=
```

**Fish:** gunakan variabel fish_pid.

```fish
ps -p $fish_pid -o comm=
```

`$SHELL` tidak selalu sama dengan shell aktif bila kamu membuka Bash dari Fish atau sebaliknya.

## Langkah 2 — RAM, ruang kosong, dan mount point

```bash
free -h
df -h / /home
findmnt /
findmnt /home
```

`free -h` menampilkan RAM dalam satuan mudah dibaca. Perhatikan **available**, bukan hanya free. `df` menunjukkan kapasitas filesystem; `findmnt` menunjukkan mount point spesifik.

**Ilustrasi ringkas:**

```text
TARGET SOURCE         FSTYPE
/      /dev/nvme0n1p8  ext4
/home  /dev/nvme0n1p9  ext4
```

Nama device mungkin berbeda. Jika `findmnt /home` tidak menghasilkan baris, belum tentu rusak: /home mungkin direktori pada filesystem /. Gunakan `findmnt --target /home` untuk mencari filesystem yang menampungnya.

## Langkah 3 — Versi tools host

```bash
git --version
docker --version
php --version
node --version
curl --version
python3 --version
```

Perintah ini membaca versi executable, tidak menjalankan container. Versi Laravel tidak perlu diperiksa sekarang karena terkait project tertentu. Jangan memasang ulang tools hanya karena ada satu perintah tidak ditemukan.

## Langkah 4 — Ringkas hasil

Catat versi OS, shell aktif, RAM available, ruang kosong, dan tools yang ditemukan di jurnal. Jangan menyalin seluruh informasi perangkat bila tidak diperlukan.

## Troubleshooting

| Gejala | Tindakan |
|---|---|
| Fish menolak `$$` | Gunakan contoh khusus Fish |
| Command not found | Catat tool yang belum tersedia; tunda instalasi sampai dibutuhkan |
| Nama partisi berbeda | Gunakan hasil aktual, bukan menyalin contoh |
| Output terlalu panjang | Ringkas nilai relevan; hapus nama pengguna/hostname bila membagikan screenshot |

Tidak ada perubahan konfigurasi, sehingga tidak ada cleanup.

## Mini challenge

Jika PHP host berbeda dengan PHP container, versi mana yang relevan saat men-debug SPMB? Jelaskan alasannya.

## Checklist

- [ ] Bisa menjelaskan di mana perintah dijalankan: host atau container.
- [ ] Mengetahui perbedaan / dan /root.
- [ ] Mencatat hasil aktual; tidak menganggap ilustrasi sebagai hasil sendiri.
- [ ] Memahami bahwa versi host dan container bisa berbeda.

## Referensi

- Manual lokal: `man findmnt`, `man df`, `man free`, `man ps`.
- [Bash — Special Parameters](https://www.gnu.org/software/bash/manual/html_node/Special-Parameters.html)
- [Fish — Special variables](https://fishshell.com/docs/current/language.html#special-variables)

---

[Sebelumnya: SET-01](01-cara-belajar.md) · [Roadmap](../ROADMAP.md) · [Progres](../PROGRESS.md) · [Berikutnya: SET-03](03-git-dan-serah-terima.md)
