# Jurnal Belajar

[README](README.md) · [Roadmap](ROADMAP.md) · [Progres](PROGRESS.md)

Catatan kronologis; entri baru ditambahkan di bawah entri sebelumnya. Gunakan tanggal Asia/Jakarta. Jangan menghapus percobaan gagal; tambahkan koreksi bila kesimpulan berubah.

Pisahkan konfirmasi pengguna, hasil tools AI, hipotesis, dan contoh output. Simpan hanya data yang aman untuk repository public.

## 2026-11-03 — Perencanaan awal

**Jenis:** perencanaan dokumentasi, bukan praktik cybersecurity.  
**Bab:** belum ada.  
**Tujuan:** menyusun pusat dokumentasi dan konteks bersama lintas perangkat/AI.

### Konteks dan keputusan

- Fokus: Web Hacking, Network Security, pengenalan Reverse Engineering, dan Secure Development.
- Mulai dari fundamental karena pengetahuan keamanan perlu dipelajari ulang.
- Pengguna meminta percakapan singkat; pembahasan dilakukan satu langkah setiap kali.
- GitHub menjadi sumber konteks bersama, dengan README, ROADMAP, PROGRESS, dan LEARNING_LOG sebagai dokumen inti.
- Repository dokumentasi terpisah dari SPMB; AGENTS.md tidak diperlukan saat ini.
- Docker sudah tersedia menurut pengguna, sehingga tidak perlu menambah Podman untuk rencana awal.
- SPMB memiliki data dummy dan merupakan proyek eksperimen pengguna. Pengguna meminta pembahasan lab ditunda sampai fundamental siap.
- Usulan ritme belajar fleksibel dan materi modular dicatat sebagai arah awal yang dapat direvisi.

### Aktivitas aktual

- Pengguna membuat repository vianovi/cybersecurity-learning.
- AI berhasil membaca metadata repository dan koleksi pull request melalui koneksi GitHub.
- Metadata menunjukkan repository public dan izin push tersedia pada koneksi yang digunakan.
- Saat pemeriksaan awal, daftar PR kosong. Saat mulai penulisan, endpoint contents menyatakan repository kosong.
- Pengguna meminta hasil dokumentasi/roadmap disimpan langsung ke repository.

### Hasil dan batas verifikasi

Belum ada bab dipelajari, perintah lab dijalankan, atau kemampuan cybersecurity diuji. Spesifikasi dan software laptop berasal dari keterangan pengguna, bukan pemeriksaan terminal.

Penulisan dokumen inti dicatat oleh commit Git. Keberhasilan membaca repository tidak otomatis membuktikan semua koneksi AI lain memiliki akses yang sama.

### Langkah berikutnya

Review singkat dokumen inti, kemudian susun orientasi SET-01 dan bab NET-01 tentang alur browser ke server.

## Cara mencatat sesi berikutnya

AI menambahkan tanggal, topik, temuan/percobaan aktual, kendala, dan langkah berikutnya secara singkat. Silvia tidak perlu menulis draft atau mengisi template. Entri lama di bawah merekam pendekatan saat itu; keputusan terbaru berlaku untuk sesi selanjutnya.

## 2026-11-03 — Penyusunan Fase 0 dan bab fundamental pertama

- **Jenis:** dokumentasi dan validasi contoh oleh AI.
- **Bab:** SET-01–04, NET-01.
- **Permintaan pengguna:** membangun fase awal agar bisa segera mulai belajar fundamental.
- **Commit acuan:** 6825356521a8039d14574d9ed872673cb49a9a4a.
- **Hasil:** empat bab orientasi, indeks fase, dan NET-01 tentang perjalanan browser ke server. README/roadmap/progres diperbarui; .gitignore mengecualikan hasil latihan lokal dan environment secrets.
- **Validasi AI:** tutorial HTTP dicoba pada runtime Linux dengan Python 3 dan curl. Root menghasilkan 200, path tidak ada menghasilkan 404 (curl exit 0), server berhenti menghasilkan curl exit 7, restart kembali 200. Proses dihentikan dan direktori uji sementara dibersihkan.
- **Batas validasi:** bukan Fedora pengguna; UI browser, Fish, Docker, clone/push laptop pengguna belum diuji. Perintah inventaris bersifat baca saja. Referensi resmi ditinjau; dokumentasi Bash daring gagal dimuat pada pemeriksaan, sintaks PID Bash merupakan sintaks standar.
- **Progres pengguna:** belum ada bab selesai atau praktik terkonfirmasi; checklist tetap kosong.
- **Langkah berikutnya:** baca SET-01 lalu teori NET-01; diskusikan alur browser, DNS, dan server dalam satu langkah pendek.

## 2026-11-03 — Mulai membaca Fase 0 dan penyesuaian teori

- **Konfirmasi pengguna:** sudah membaca sebagian Fase 0, belum masuk Fase 1. Bab spesifik dan praktik belum dikonfirmasi.
- **Preferensi:** teori lebih singkat, istilah seperlunya, fokus memahami fundamental dan alasan; bukan tuntutan menghafal.
- **Perubahan:** teori SET-01–04 diringkas dan prinsip penulisan diperbarui di README. Checklist terkait diselaraskan. Salah ketik PID Bash pada SET-02 diperbaiki menjadi dua tanda dolar.
- **Progres:** sedang dipelajari; belum ada bab ditandai selesai.
- **Berikutnya:** lanjutkan Fase 0 dari bagian terakhir yang dibaca; gunakan satu contoh dan pertanyaan sebab-akibat sebelum berpindah fase.

## 2026-11-04 — Beralih ke eksplorasi singkat

Silvia meminta pembelajaran yang membuat penasaran: pengantar, tujuan, analogi/teori singkat, praktik/pengamatan, lalu pertanyaan percakapan tentang penerapan nyata. Tidak ada tugas membuat draft/rangkuman dan tidak perlu banyak modul atau README per modul.

Materi lama dalam 00-setup dan 01-fundamentals dihapus dari versi aktif, termasuk kedua README folder. Empat dokumen inti dan AGENTS dipertahankan serta diselaraskan; .gitignore tetap ada. Versi sebelum perubahan tersedia pada commit d4fbb4f98a9178d0f4ea01e99db302fca47a5f19. Entri sebelumnya adalah catatan historis, bukan instruksi melanjutkan modul yang telah dihapus.

Belum ada eksperimen baru atau penguasaan yang dikonfirmasi. Langkah berikutnya adalah satu topik menarik dengan format baru, tanpa langsung membuat kumpulan file.
