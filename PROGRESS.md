# Progres Pembelajaran

[README](README.md) · [Roadmap](ROADMAP.md) · [Jurnal](LEARNING_LOG.md)

## Posisi terkini

| Bidang | Status |
|---|---|
| Pembaruan konteks | 3 November 2026, Asia/Jakarta |
| Tahap proyek | Fase 0 dan NET-01 tersedia; siap mulai belajar |
| Fase belajar aktif | Fase 0 — orientasi, siap dimulai |
| Modul aktif | SET-01 ditetapkan sebagai titik mulai; belum dikonfirmasi dipelajari |
| Modul berikutnya | NET-01 setelah orientasi; SET-02/03 bisa menyusul di laptop |
| Status pembelajaran | Belum mulai |
| Bab selesai | 0 |
| Branch tujuan dokumentasi inti | main |
| Commit acuan sesi penulisan modul | 6825356521a8039d14574d9ed872673cb49a9a4a |
| Sumber verifikasi sinkronisasi | Riwayat commit GitHub; jangan menganggap perubahan lokal sudah ter-push |

## Konteks yang telah dikonfirmasi pengguna

- Junior web developer, ingin mengulang dasar web hacking dan network hacking.
- Mengutamakan fundamental sebelum membahas setup lab lanjutan.
- Penjelasan dalam percakapan harus pendek dan bertahap.
- Repository dokumentasi terpisah dari SPMB.
- Laptop: i3-1315U, RAM 16 GB, Fedora 44 KDE, Bash/Fish, dual boot Windows.
- Docker, cloudflared, Laravel, Node.js, PHP sudah terpasang menurut pengguna.
- SPMB adalah proyek eksperimen milik sendiri; seluruh data dummy, belum production, tersedia publik melalui tunnel.
- Tidak membuat AGENTS.md pada tahap awal.

Detail lingkungan ada di README. Informasi yang dilaporkan belum sama dengan hasil pemeriksaan perangkat.

## Materi yang sudah dipahami

Belum ada konsep cybersecurity yang telah diverifikasi. Pengalaman web development adalah konteks awal, bukan checklist penguasaan keamanan.

## Praktik yang sudah dilakukan

Belum ada praktik cybersecurity yang dilaporkan atau dibuktikan dalam sesi ini.

Aktivitas dokumentasi: Fase 0 dan NET-01 telah ditulis. AI menguji skenario HTTP lokal pada runtime Linux: 200, 404, kegagalan koneksi setelah stop, dan 200 setelah restart. Ini bukan praktik pengguna, bukan validasi pada Fedora pengguna, dan tidak mengubah checklist penguasaan.

## Kendala dan ketidakpastian

Tidak ada error praktik aktif karena pembelajaran belum dimulai.

Hal yang diperiksa nanti ketika relevan:

- Kapasitas penyimpanan kosong dan mount point Linux aktual.
- Versi Docker, PHP, Laravel, Node.js.
- Konfigurasi jaringan/container/tunnel SPMB sebelum dipakai untuk pengujian.
- Akses repository dari masing-masing AI; satu koneksi berhasil tidak membuktikan semua AI memiliki akses.

Tidak perlu menyelesaikan seluruh inventaris untuk mulai belajar teori.

## Langkah berikutnya

1. Baca [SET-01](00-setup/01-cara-belajar.md) sebagai orientasi singkat.
2. Mulai teori [NET-01](01-fundamentals/01-browser-ke-server.md); praktik terminal boleh menyusul.
3. Minta pengguna menjelaskan peran browser, DNS, dan server; catat bagian yang belum jelas.
4. Saat di laptop, lanjutkan inventaris/Git dan latihan HTTP lokal sesuai kebutuhan.

Jangan langsung menjalankan scan atau mengubah SPMB.

## Aturan pembaruan

Status yang digunakan: **belum mulai**, **sedang dipelajari**, **menunggu verifikasi**, **terhambat**, **selesai**.

Saat memperbarui, catat:

- Fase/ID bab aktif dan langkah terakhir.
- Pemahaman yang dikonfirmasi pengguna.
- Praktik aktual, siapa yang menjalankan, lingkungan, dan tautan bukti.
- Kendala, percobaan yang sudah dilakukan, serta hasilnya.
- Satu langkah berikutnya yang konkret.
- Tautan entri jurnal, branch, dan commit acuan bila diketahui.

Commit acuan adalah commit sebelum perubahan sesi, bukan SHA commit yang sedang ditulis. Gunakan riwayat GitHub untuk memeriksa commit hasil sinkronisasi.

## Riwayat terkait

- [Jurnal perencanaan awal](LEARNING_LOG.md#2026-11-03--perencanaan-awal)
