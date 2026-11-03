# SET-03 — Git dan serah-terima antar-AI

**Tujuan:** semua perangkat membaca konteks yang sama.  
**Prasyarat:** SET-01, Git tersedia, koneksi internet. **Estimasi:** 15 menit.  
**Validasi:** alur ditinjau dengan dokumentasi Git; clone/push pada laptop pengguna belum diuji.

## Teori singkat

Repository lokal adalah salinan di laptop. Commit menyimpan perubahan dalam riwayat lokal. Push mengirim commit ke remote; pull mengambil dan mengintegrasikan perubahan remote.

Commit tanpa push belum terlihat oleh AI yang hanya membaca GitHub. ChatGPT/Claude/Codex CLI juga tidak otomatis berbagi riwayat chat.

## Contoh

Belajar teori di HP menghasilkan catatan baru di GitHub. Sebelum praktik di laptop, ambil perubahan tersebut. Setelah praktik, simpan hasil aktual dan push agar sesi HP berikutnya tahu posisi terakhir.

## Persiapan

Gunakan folder kerja pilihanmu di luar SPMB. Jangan clone ulang bila repository sudah ada. Perintah berikut kompatibel Bash/Fish.

## Langkah 1 — Ambil repository

Hanya bila belum memiliki salinan:

```bash
git clone https://github.com/vianovi/cybersecurity-learning.git
cd cybersecurity-learning
```

`clone` membuat direktori baru dan mengambil riwayat. Bila sudah ada, cukup pindah ke direktori repository yang benar.

## Langkah 2 — Periksa sebelum mengambil perubahan

```bash
git status
git branch --show-current
git remote -v
```

Pastikan repository benar. Jangan membagikan remote URL jika mengandung kredensial. Jika ada perubahan lokal, review dan simpan terlebih dahulu sebelum pull.

Untuk salinan bersih pada main yang mengikuti origin/main:

```bash
git pull --ff-only
git log -1 --oneline
```

`--ff-only` menolak integrasi jika riwayat bercabang; tidak membuat merge otomatis.

**Ilustrasi:**

```text
Already up to date.
abc1234 docs: add initial learning modules
```

Itu berarti branch sudah mengikuti remote pada saat pemeriksaan, bukan jaminan tidak ada update setelahnya.

## Langkah 3 — Baca konteks dan catat hasil

Baca README → PROGRESS → jurnal terbaru → bab aktif. Setelah benar-benar belajar, tambahkan hasil ke jurnal dan perbarui posisi di PROGRESS.

Contoh instruksi untuk AI:

```text
Baca README.md, PROGRESS.md, entri terakhir LEARNING_LOG.md,
dan bab aktif. Lanjutkan satu langkah saja.
Jangan tandai praktik selesai tanpa konfirmasi atau bukti saya.
```

## Langkah 4 — Simpan perubahan yang sudah direview

Jika memang ada perubahan pada kedua file ini:

```bash
git diff -- PROGRESS.md LEARNING_LOG.md
git add PROGRESS.md LEARNING_LOG.md
git diff --cached
git commit -m "docs: catat hasil sesi belajar"
git push origin main
git status
```

`add` memilih file untuk commit; `diff --cached` memeriksa isi yang akan dikirim. Gunakan branch aktif sesuai workflow aktual; jangan mengganti branch hanya untuk meniru contoh. HTTPS clone repo public tidak memerlukan login, tetapi push membutuhkan autentikasi yang berwenang. Jangan menaruh token dalam perintah/dokumen.

## Troubleshooting

- **Nothing to commit:** tidak ada perubahan baru; tidak perlu commit kosong.
- **Push rejected / fast-forward gagal:** ada perubahan remote atau riwayat berbeda. Berhenti, periksa `git status` dan `git log --oneline --graph --all -10`; minta bantuan menyelaraskan tanpa force push.
- **Authentication failed:** gunakan mekanisme autentikasi GitHub yang sudah dimiliki; jangan kirim token ke chat.
- **AI tidak dapat akses repo:** berikan isi dokumen konteks; AI harus mengakui belum menyinkronkan.
- **Merge conflict:** jangan hapus salah satu versi tanpa membandingkan catatan belajar.

Tidak ada cleanup wajib; jangan menghapus repository sesudah latihan.

## Mini challenge

Kamu sudah commit catatan di laptop, tetapi belum push. Mengapa AI di HP masih membaca progres lama?

## Checklist

- [ ] Menemukan repository dan branch yang benar.
- [ ] Bisa membedakan commit, push, dan pull.
- [ ] Bisa menunjukkan commit acuan sesi.
- [ ] Jika memperbarui catatan, sudah memeriksa hasil push; jika belum, tandai belum sinkron.

## Referensi

- [Git pull](https://git-scm.com/docs/git-pull)
- [Git diff](https://git-scm.com/docs/git-diff)
- [GitHub — Authentication](https://docs.github.com/en/authentication)

---

[Sebelumnya: SET-02](02-inventaris-fedora.md) · [Roadmap](../ROADMAP.md) · [Progres](../PROGRESS.md) · [Berikutnya: SET-04](04-konsep-lab.md)
