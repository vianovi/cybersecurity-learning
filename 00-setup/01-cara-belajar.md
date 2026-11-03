# SET-01 — Cara belajar dan scope

**Tujuan:** memahami alur belajar dan memilih target latihan yang tepat.  
**Prasyarat:** tidak ada. **Estimasi:** 10 menit, fleksibel.  
**Validasi:** materi konseptual ditinjau 3 November 2026; pemahaman pengguna belum diuji.

## Teori singkat

Cybersecurity membantu memastikan data hanya diakses atau diubah oleh orang yang berhak, dan sistem tetap bisa dipakai.

Sebelum menguji, tentukan **scope**: sistem mana yang boleh diuji dan tindakan apa yang diizinkan. Bisa membuka suatu website bukan berarti boleh mengujinya.

**Pegangan bab ini:** pahami tujuan pengujian dan batas izinnya; istilah teknis bisa dipelajari saat dibutuhkan.

## Contoh

SPMB dummy milikmu bisa menjadi target nanti. Website sekolah lain yang bisa dibuka publik belum tentu boleh diuji. Komputer di jaringan yang sama juga tidak otomatis menjadi bagian scope.

## Persiapan

Cukup HP/browser atau VS Code untuk membaca dokumen. Belum ada kebutuhan terminal atau instalasi.

## Latihan langkah demi langkah

1. Buka [PROGRESS](../PROGRESS.md). Temukan modul berikutnya.
2. Tulis satu tujuan sederhana: “Saya ingin memahami perjalanan request sebelum belajar celah.”
3. Kelompokkan tiga tindakan ini:
   - Membaca source code aplikasi sendiri.
   - Mencoba login sebagai pengguna dummy pada instance lab sendiri.
   - Menjalankan scanner ke domain pihak lain tanpa izin.
4. Tulis hasil pengelompokan dan alasan singkat.
5. Gunakan format berikut sebagai draft catatan, bukan klaim praktik telah selesai:

```text
Bab: SET-01
Yang saya pahami: ...
Yang masih membingungkan: ...
Latihan yang benar-benar saya lakukan: ...
Langkah berikutnya: ...
```

## Contoh hasil dan analisis

**Ilustrasi:** dua tindakan pertama dapat masuk scope milik sendiri; tindakan ketiga tidak boleh dilakukan tanpa izin. Bahkan di lab sendiri, tentukan data yang boleh berubah dan cara memulihkannya sebelum pengujian aktif.

Belajar mengikuti Learn → Practice → Analyze → Fix → Retest. Misalnya salah mengira “bisa diakses” berarti “boleh diuji”: perbaiki kesimpulan, lalu coba klasifikasikan target baru.

## Troubleshooting

- **Istilah terlalu banyak:** cukup pahami tujuan dan batas izin pengujian; istilah lain datang bertahap.
- **Ingin langsung scanning:** tulis pertanyaan yang hendak dijawab dulu. Tools dipilih untuk menjawabnya.
- **Belum di laptop:** latihan bab ini memang bisa diselesaikan lewat HP.

## Mini challenge

Mengapa data dummy saja belum menjamin eksperimen aman bila aplikasi masih dapat diakses publik? Jelaskan dalam dua kalimat.

<details>
<summary>Petunjuk setelah mencoba</summary>

Data dummy mengurangi risiko kebocoran data nyata, tetapi perubahan aplikasi masih dapat mengganggu layanan atau membuka kemampuan yang tidak diinginkan. Scope dan keterjangkauan lingkungan tetap perlu ditentukan.

</details>

## Checklist

- [ ] Bisa memberi satu contoh data atau layanan yang perlu dilindungi.
- [ ] Bisa membedakan akses publik dan izin pengujian.
- [ ] Bisa menyebutkan cara AI mengetahui progres terakhir.
- [ ] Sudah mencatat satu hal yang dipahami dan satu pertanyaan.

## Referensi

- [OWASP WSTG — Testing Framework](https://owasp.org/www-project-web-security-testing-guide/v42/3-The_OWASP_Testing_Framework/)
- [Workflow repository](../README.md#workflow-lintas-perangkat-dan-ai)

---

[Indeks fase](README.md) · [Roadmap](../ROADMAP.md) · [Progres](../PROGRESS.md) · [Berikutnya: SET-02](02-inventaris-fedora.md)
