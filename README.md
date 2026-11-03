# Cybersecurity Learning

Dokumentasi belajar cybersecurity secara bertahap, berbahasa Indonesia, dengan fokus Web Hacking, Network Security, dan pengenalan Reverse Engineering.

Tujuan akhirnya: memahami cara kerja sistem, menemukan celah pada lingkungan berizin, memperbaikinya, lalu memverifikasi hasil perbaikan.

## Mulai di sini

1. Baca [progres terkini](PROGRESS.md) untuk mengetahui posisi belajar.
2. Pilih bab berikutnya di [roadmap](ROADMAP.md).
3. Pelajari satu konsep, lakukan latihan kecil, lalu analisis hasilnya.
4. Catat hasil aktual di [jurnal belajar](LEARNING_LOG.md).

**Mulai belajar:** [SET-01 — Cara belajar](00-setup/01-cara-belajar.md), lalu [NET-01 — Perjalanan browser ke server](01-fundamentals/01-browser-ke-server.md).

**Status dokumentasi:** Fase 0 (SET-01–04) dan NET-01 tersedia. Bab lain masih direncanakan. Jika di HP, praktik terminal boleh menyusul.

## Pendekatan belajar

- Mulai dari fundamental dan anggap pengetahuan keamanan perlu dipelajari ulang.
- Pengalaman web development membantu memberikan contoh, bukan bukti penguasaan keamanan.
- Gunakan alur **Learn → Practice → Analyze → Fix → Retest**. Pada bab fundamental, tahap Fix dapat berupa memperbaiki kesalahan pemahaman atau konfigurasi.
- Ritme fleksibel: lanjut setelah tujuan bab tercapai, bukan berdasarkan tenggat mingguan.
- Penjelasan percakapan singkat dan satu langkah setiap kali. Detail teknis disimpan dalam bab.
- Instalasi tools dan lab khusus dilakukan saat materinya membutuhkan.

## Konteks pembelajar

Junior web developer dengan pengalaman Laravel/PHP, Node.js, GitHub, VS Code, terminal, Codex CLI, dan Agy CLI. Fokus saat ini adalah mengulang fundamental jaringan dan web security.

Lingkungan yang **dilaporkan pengguna**, belum diverifikasi melalui terminal:

| Komponen | Kondisi |
|---|---|
| Laptop | ASUS Vivobook A1404VA, Intel Core i3-1315U |
| RAM | DDR4 dual-channel 16 GB, 3200 MHz |
| Penyimpanan | NVMe M.2 PCIe Gen4; kapasitas kosong belum diketahui |
| OS | Dual boot Windows dan Fedora 44 KDE Plasma Edition |
| Shell | Bash atau Fish |
| Partisi Linux | Dua partisi ext4, disebut pengguna sebagai /root dan /home; mount point perlu diperiksa saat diperlukan |
| Software tersedia | Docker, cloudflared, Laravel, Node.js, PHP |

Catatan: mount point sistem Linux umumnya `/`; `/root` adalah direktori home pengguna root. Jangan mengasumsikan konfigurasi partisi atau mengubahnya tanpa hasil pemeriksaan.

## Proyek praktik nanti

SPMB adalah proyek eksperimen milik pengguna, berbasis Laravel dalam Docker, dengan authentication, database, dan cookies/session. Pengguna menyatakan seluruh datanya dummy dan belum production. Aplikasi dapat diakses publik melalui Cloudflare Tunnel dengan custom domain.

SPMB akan digunakan setelah fundamental siap. Repository dokumentasi ini tetap terpisah dari repository aplikasi. Saat pengujian aktif nanti, pastikan target lab lokal dan tunnel ke instance yang diuji tidak aktif; konfigurasi ini belum dilakukan atau diverifikasi. Tidak perlu mengubah proyek sekarang.

## Struktur repository

| Lokasi | Fungsi | Ketersediaan |
|---|---|---|
| [README.md](README.md) | Konteks proyek, navigasi, workflow bersama | Tersedia |
| [ROADMAP.md](ROADMAP.md) | Kurikulum, urutan bab, kriteria fase | Tersedia |
| [PROGRESS.md](PROGRESS.md) | Posisi terkini dan langkah berikutnya | Tersedia |
| [LEARNING_LOG.md](LEARNING_LOG.md) | Riwayat belajar dan eksperimen | Tersedia |
| [00-setup/](00-setup/README.md) | Persiapan dan inventaris lingkungan | SET-01–04 tersedia |
| [01-fundamentals/](01-fundamentals/README.md) | Networking, Linux tools, dan dasar web security | NET-01 tersedia |
| `02-web-hacking/` | Kerentanan dan metode pentest web | Direncanakan |
| `03-network-hacking/` | Analisis dan keamanan jaringan | Direncanakan |
| `04-reverse-engineering/` | Analisis JavaScript, API, program sederhana | Direncanakan |
| `05-practical-labs/` | Praktik terpadu dan final project | Direncanakan |
| `06-secure-development/` | Mitigasi, hardening, security testing | Direncanakan |

Urutan belajar ditentukan roadmap, bukan hanya nomor folder. Folder akan dibuat saat memiliki isi yang berguna. Tidak membuat AGENTS.md pada tahap awal.

## Standar setiap bab

Setiap bab memiliki ID stabil, tujuan, prasyarat, status validasi, dan navigasi. Contoh nama: `01-fundamentals/01-browser-ke-server.md`, ID `NET-01`.

Isi bab:

1. Judul dan tujuan pembelajaran.
2. Prasyarat.
3. Teori singkat.
4. Contoh sederhana.
5. Persiapan lingkungan praktik.
6. Tutorial langkah demi langkah.
7. Perintah atau kode dengan penjelasan fungsi.
8. Contoh output berlabel ilustrasi dan cara menganalisisnya.
9. Troubleshooting.
10. Mini challenge.
11. Checklist penyelesaian dan bukti yang perlu dicatat.
12. Referensi pendalaman.

Tambahkan cleanup/reset untuk latihan yang mengubah keadaan sistem. Catat versi Fedora/tools dan tanggal validasi. Label **belum diuji** digunakan bila belum dijalankan pada lingkungan yang relevan.

Contoh pembedaan istilah: `ss -tln` menampilkan socket TCP yang listening pada komputer lokal; ini bukan port scanning. Port scanning melakukan probe ke target untuk menilai keterjangkauan port.

## Workflow lintas perangkat dan AI

GitHub menjadi sumber konteks bersama. Riwayat percakapan AI lain bukan prasyarat melanjutkan belajar.

### Memulai sesi

1. Baca versi terkini README, PROGRESS, entri terbaru LEARNING_LOG, kemudian bab aktif bila sudah tersedia.
2. Periksa branch dan commit yang sedang dibaca. Catat kendala akses jika repository tidak tersedia.
3. Gunakan langkah berikutnya dari PROGRESS; jangan mengulang materi atau melompat ke lab tanpa alasan.
4. Minta bukti yang benar-benar diperlukan, misalnya output perintah dengan rahasia dihapus.

### Menutup sesi

1. Tambahkan hasil aktual dan kendala ke LEARNING_LOG.
2. Perbarui PROGRESS dan checklist roadmap bila kriteria selesai terpenuhi.
3. Periksa diff, commit, lalu push perubahan. Klaim tersinkron hanya setelah push atau penulisan GitHub berhasil.
4. Perangkat lain mengambil versi baru sebelum melanjutkan. Jika ada perubahan lokal, selesaikan terlebih dahulu; jangan menimpa dengan force push atau reset.

AI yang tidak memiliki akses tulis menyediakan patch/teks perubahan untuk diterapkan. AI yang tidak memiliki akses baca meminta file konteks terkini. Jangan mengklaim telah membaca atau memperbarui repository tanpa akses yang berhasil.

### Aturan bukti dan status

- Materi dibuat tidak berarti materi sudah dipelajari.
- Penjelasan AI tidak membuktikan pengguna sudah memahami.
- Perintah yang disarankan tidak berarti telah dijalankan.
- Contoh output tidak boleh dicatat sebagai hasil aktual.
- Praktik selesai hanya berdasarkan konfirmasi eksplisit pengguna atau bukti hasil.
- Hasil otomatis dari AI harus dibedakan dari praktik yang dilakukan pengguna.
- Catat batas validasi, misalnya hanya membaca dokumen atau hanya menguji pada OS lain.

## Batas pengujian dan data

Pengujian hanya pada sistem milik sendiri atau dengan izin eksplisit dan scope jelas. Akses publik tidak otomatis memberikan izin untuk menguji layanan pihak lain.

Repository ini public. Jangan commit password, token, tunnel credentials, cookies/session aktif, data pribadi, atau capture trafik yang belum disanitasi. Gunakan data dummy dan bukti minimum yang diperlukan.
