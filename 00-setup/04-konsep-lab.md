# SET-04 — Localhost, container, dan VM

**Tujuan:** mengenali batas lingkungan praktik tanpa membangun lab besar.  
**Prasyarat:** SET-01. **Estimasi:** 10–15 menit.  
**Validasi:** teori ditinjau 3 November 2026; konfigurasi Docker pengguna belum diperiksa.

## Teori singkat

**Localhost berarti lingkungan tempat program itu berjalan.** Jadi, localhost di HP menunjuk HP, bukan laptop.

Laptopmu adalah **host**. Container menjadi lingkungan proses aplikasi di host; VM menjalankan OS tersendiri.

**Pegangan bab ini:** selalu tanyakan “program ini berjalan di mana?” sebelum menentukan alamat yang diakses. Localhost di container biasanya menunjuk container itu sendiri; mode host networking menjadi pengecualian.

## Contoh

Dua pemetaan Docker berikut memiliki maksud berbeda:

```text
127.0.0.1:8080:80  → port 8080 pada loopback host menuju port 80 container
8080:80            → publikasi port tanpa pembatasan IP host secara eksplisit
```

Contoh ini hanya untuk dibaca, bukan perintah yang perlu dijalankan. Tanpa pembatasan IP, Docker umumnya memublikasikan ke semua alamat host. Keterjangkauan aktual juga dipengaruhi konfigurasi jaringan/firewall dan versi Docker.

Binding localhost bukan penghalang tunnel: proses tunnel yang berjalan di host dapat meneruskan layanan lokal ke internet. Saat lab khusus dibuat nanti, pastikan tidak ada tunnel/proxy yang memublikasikannya.

## Persiapan

Untuk teori cukup HP. Untuk pengamatan opsional, buka terminal Fedora. Tidak perlu menjalankan atau menghentikan container apa pun.

## Latihan langkah demi langkah

1. Prediksi: apakah membuka `http://127.0.0.1:8080` di HP pasti menampilkan aplikasi di laptop?
2. Jelaskan siapa host dan siapa container dalam proyek SPMB.
3. Jika di laptop, lihat publikasi port container yang sedang berjalan:

```bash
docker ps --format 'table {{.Names}}\t{{.Ports}}'
```

Perintah ini hanya membaca daftar. Nama container mungkin mengungkap nama project; bagikan hanya bagian yang diperlukan.

4. Cari apakah mapping menampilkan loopback, seluruh interface, atau hanya port container.
5. Catat hasil sebagai observasi konfigurasi, bukan klaim layanan pasti aman.

## Contoh output dan analisis

**Ilustrasi, bukan hasil perangkatmu:**

```text
NAMES     PORTS
web-lab   127.0.0.1:8080->80/tcp
```

Docker memublikasikan port 80 container melalui loopback host port 8080. Output ini tidak membuktikan tunnel sedang mati. Baris `80/tcp` tanpa mapping juga bukan bukti port host dipublikasikan.

## Troubleshooting

- **Cannot connect to Docker daemon / permission denied:** catat error; jangan mengubah permission socket atau menambah akses administrator hanya untuk bab teori.
- **Daftar kosong:** tidak ada container berjalan pada daemon/context tersebut.
- **HP tidak bisa akses localhost laptop:** sesuai konsep; jangan membuka tunnel hanya untuk menyelesaikan bab ini.
- **Port dan IP belum jelas:** lanjutkan NET-01; rincian dibahas pada NET-02/05.

Tidak ada perubahan atau cleanup dalam bab ini.

## Mini challenge

Mengapa layanan yang bind ke localhost tetap bisa diakses publik melalui tunnel? Jelaskan peran proses perantaranya.

## Checklist

- [ ] Bisa menjelaskan localhost dari sudut HP, host, dan container.
- [ ] Bisa membedakan container dan VM.
- [ ] Memahami publish port tidak sama dengan permission aplikasi.
- [ ] Memahami tunnel dapat menjadi jalur publik ke layanan lokal.

## Referensi

- [Docker — Port publishing](https://docs.docker.com/engine/network/port-publishing/)
- [Docker — Networking overview](https://docs.docker.com/engine/network/)

---

[Sebelumnya: SET-03](03-git-dan-serah-terima.md) · [Roadmap](../ROADMAP.md) · [Progres](../PROGRESS.md) · [Mulai fundamental: NET-01](../01-fundamentals/01-browser-ke-server.md)
