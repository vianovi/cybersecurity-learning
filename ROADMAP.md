# Roadmap Cybersecurity Learning

[Kembali ke README](README.md) · [Progres](PROGRESS.md) · [Jurnal](LEARNING_LOG.md)

**Kedalaman:** mulai dari dasar cybersecurity, kemudian bertahap teknis.  
**Ritme:** fleksibel berdasarkan pemahaman.  
**Status:** seluruh bab berikut masih direncanakan. Checklist menandai penyelesaian belajar, bukan penyelesaian penulisan.

Setiap fase berisi beberapa bab tersendiri. Referensi dan tools ditinjau kembali ketika bab ditulis. Tidak perlu memasang seluruh tools di awal.

## Fase 0 — Orientasi dan persiapan minimum

Lokasi rencana: `00-setup/`. Prasyarat: tidak ada.

- [ ] SET-01 — Tujuan, scope berizin, cara belajar, dan penggunaan progres.
- [ ] SET-02 — Inventaris Fedora, Bash/Fish, versi tools, dan sumber daya perangkat.
- [ ] SET-03 — Workflow Git: membaca versi terkini, diff, commit, sinkronisasi, serah-terima AI.
- [ ] SET-04 — Konsep localhost, container, VM, isolasi, serta reset lab; pengenalan saja.

**Target:** mengetahui cara memakai dokumentasi dan batas lingkungan praktik. Setup lab khusus ditunda sampai diperlukan.

## Fase 1 — Fundamental Networking

Lokasi rencana: `01-fundamentals/`. Prasyarat: SET-01; inventaris rinci dapat menyusul saat praktik.

- [ ] NET-01 — Gambaran perjalanan browser → DNS → koneksi → server → response.
- [ ] NET-02 — Interface, IP address, IPv4/IPv6, loopback, private/public address.
- [ ] NET-03 — Subnet mask, CIDR, dan cara menentukan perangkat dalam satu subnet.
- [ ] NET-04 — MAC address, ARP, dan komunikasi di jaringan lokal; pengenalan IPv6 Neighbor Discovery.
- [ ] NET-05 — TCP versus UDP, port, socket, client, dan server.
- [ ] NET-06 — DNS: resolver, cache, record A/AAAA/CNAME, dan alur resolusi.
- [ ] NET-07 — Routing, default gateway, NAT, serta gambaran firewall.
- [ ] NET-08 — Mengurai gangguan: DNS gagal, connection refused, timeout, dan respons aplikasi.

**Target:** bisa menceritakan alur akses website serta membedakan alamat, nama domain, port, dan layanan.

**Bukti selesai:** menjelaskan alur dengan bahasa sendiri dan menyelesaikan latihan subnet serta diagnosis sederhana. Tidak memerlukan scanning jaringan.

## Fase 2 — Linux dan Network Tools

Lokasi rencana: `01-fundamentals/`. Prasyarat: Fase 1.

- [ ] LIN-01 — Proses, permission, service, log, serta kapan membutuhkan privilege.
- [ ] LIN-02 — `ip`: membaca interface, address, dan route.
- [ ] LIN-03 — `ss`: membaca listening socket dan koneksi lokal.
- [ ] LIN-04 — `curl` dan `dig`: membedakan pemeriksaan HTTP dan DNS.
- [ ] LIN-05 — Wireshark/tcpdump: capture trafik lab, filter, dan batas visibilitas TLS.
- [ ] LIN-06 — Nmap dasar: perbedaan discovery, port scan, dan service detection pada target lab.

**Target:** memilih tools sesuai pertanyaan dan membaca hasilnya, bukan menghafal perintah.

**Bukti selesai:** catatan perintah, hasil aktual, arti hasil, serta batas kesimpulannya. Praktik Nmap dilakukan setelah target dan scope ditentukan.

## Fase 3 — Web Security Fundamentals

Lokasi rencana: `01-fundamentals/`. Prasyarat: Fase 1; LIN-04 membantu praktik.

- [ ] WEB-01 — HTTP: method, URL, header, body, status code, request/response.
- [ ] WEB-02 — HTTPS/TLS: tujuan enkripsi, sertifikat, dan trust.
- [ ] WEB-03 — Browser origin, Same-Origin Policy, dan CORS.
- [ ] WEB-04 — Cookies, sessions, serta Secure/HttpOnly/SameSite.
- [ ] WEB-05 — Authentication versus authorization, password hashing, dan account recovery.
- [ ] WEB-06 — API, JWT, serta perbedaan encoding, signature, dan encryption.
- [ ] WEB-07 — Trust boundary, attacker-controlled input, dan attack surface.
- [ ] WEB-08 — DevTools dan pengenalan Burp Proxy/Repeater pada aplikasi lab.

**Target:** menjelaskan bagaimana server mengenali pengguna dan menentukan hak akses.

**Bukti selesai:** anotasi satu request/response lab dan penjelasan posisi autentikasi, session, serta pemeriksaan otorisasi.

## Fase 4 — Web Vulnerabilities

Lokasi rencana: `02-web-hacking/`. Prasyarat: Fase 3 dan target lab siap.

- [ ] VUL-01 — Broken access control: IDOR/BOLA dan akses fungsi antar-role.
- [ ] VUL-02 — SQL Injection dan parameterized queries.
- [ ] VUL-03 — Reflected, stored, dan DOM XSS; contextual output encoding.
- [ ] VUL-04 — CSRF, token, dan batas perlindungan SameSite.
- [ ] VUL-05 — Authentication, session, serta JWT validation flaws.
- [ ] VUL-06 — Path traversal dan file upload vulnerabilities.
- [ ] VUL-07 — Command injection dan pengenalan server-side template injection.
- [ ] VUL-08 — SSRF dan pembatasan akses keluar aplikasi.
- [ ] VUL-09 — Security misconfiguration, CORS, dan information disclosure.
- [ ] VUL-10 — Business logic, race conditions, serta API resource limits.

**Target:** memahami akar penyebab, bukan hanya payload yang berhasil.

**Bukti per bab:** reproduksi pada lab, analisis dampak, mitigasi, lalu retest. Bila platform latihan tidak bisa diedit, terapkan pola perbaikannya pada kode latihan sendiri.

## Fase 5 — Web Penetration Testing

Lokasi rencana: `02-web-hacking/` dan `05-practical-labs/`. Prasyarat: Fase 4 untuk kerentanan yang diuji.

- [ ] PEN-01 — Scope, inventaris endpoint, roles, dan rencana pengujian.
- [ ] PEN-02 — Menjalankan dan mereset OWASP Juice Shop lokal di Docker.
- [ ] PEN-03 — Burp Community: Proxy, Repeater, dan pengujian manual.
- [ ] PEN-04 — ZAP: passive scanning, scope, lalu active scanning pada lab.
- [ ] PEN-05 — Test case berbasis WSTG dan validasi false positive.
- [ ] PEN-06 — Laporan: bukti, dampak, prioritas, rekomendasi, dan retest.

**Target:** melakukan assessment kecil yang dapat diulang. Hasil scanner adalah kandidat temuan, bukan bukti final.

**Bukti selesai:** laporan satu assessment lab beserta batas cakupan dan hasil retest.

## Fase 6 — Network Security

Lokasi rencana: `03-network-hacking/`. Prasyarat: Fase 1–2; dapat dipelajari sebelum Fase 4–5 jika dasar sudah selesai.

- [ ] SEC-01 — Menyiapkan topologi lab terisolasi, scope, dan baseline layanan.
- [ ] SEC-02 — Network discovery dan interpretasi host yang tidak merespons.
- [ ] SEC-03 — Service enumeration dan batas keandalan banner/version.
- [ ] SEC-04 — Analisis trafik DNS, TCP, HTTP, serta metadata TLS.
- [ ] SEC-05 — Firewall, segmentasi, dan verifikasi keterjangkauan layanan.
- [ ] SEC-06 — Hardening SSH/service, least privilege, patching, dan log.
- [ ] SEC-07 — Membandingkan kondisi sebelum dan sesudah hardening.

**Target:** menemukan layanan yang terekspos dalam scope dan memverifikasi pembatasannya.

**Bukti selesai:** topologi lab, inventaris layanan, capture tersanitasi bila diperlukan, perubahan konfigurasi, dan retest.

## Fase 7 — Reverse Engineering Dasar

Lokasi rencana: `04-reverse-engineering/`. Prasyarat: dasar Linux dan web; dasar C dipelajari dalam fase ini.

- [ ] REV-01 — Static versus dynamic analysis dan perbedaan fakta/hipotesis.
- [ ] REV-02 — Analisis JavaScript bundle, source map, dan alur data.
- [ ] REV-03 — Menginferensikan perilaku API dari input/output.
- [ ] REV-04 — Dasar C, kompilasi, ELF, register, dan assembly sederhana.
- [ ] REV-05 — `file`, `strings`, `readelf`, dan `objdump` pada program latihan.
- [ ] REV-06 — GDB dan pengenalan Ghidra untuk menelusuri program buatan sendiri.

**Target:** menghubungkan input, alur kontrol, dan output program sederhana.

**Bukti selesai:** catatan hipotesis, pengamatan, dan kesimpulan yang didukung bukti. Malware analysis bukan cakupan awal.

## Fase 8 — Secure Development

Lokasi rencana: `06-secure-development/`. Prasyarat: dasar web serta bab kerentanan terkait. Mitigasi tetap dipraktikkan sejak Fase 4.

- [ ] DEV-01 — Threat modeling, trust boundary, dan insecure design.
- [ ] DEV-02 — Validation, parameterized queries, output encoding, dan upload handling.
- [ ] DEV-03 — Access control server-side, Laravel policies/gates, serta tes antar-role.
- [ ] DEV-04 — Session, password, secrets, dan cryptographic controls.
- [ ] DEV-05 — Dependency/supply chain, integritas software/data, dan konfigurasi deployment.
- [ ] DEV-06 — Logging, alerting, exception handling, dan perilaku fail-closed.
- [ ] DEV-07 — Security regression tests, dependency checks, dan pengenalan CI.

**Target:** membuktikan kontrol keamanan tetap bekerja saat aplikasi berubah.

**Bukti selesai:** perubahan kode/konfigurasi serta tes yang gagal pada versi rentan dan lulus setelah perbaikan.

## Fase 9 — Final Project

Lokasi rencana: `05-practical-labs/`. Prasyarat: kompetensi fase terkait; RE bukan syarat wajib assessment web/network.

- [ ] FIN-01 — Tetapkan scope aplikasi SPMB dan jaringan lab milik sendiri.
- [ ] FIN-02 — Siapkan data dummy, baseline, backup/reset, dan akses lokal.
- [ ] FIN-03 — Uji aplikasi serta layanan jaringan dalam scope.
- [ ] FIN-04 — Dokumentasikan temuan dan tentukan prioritas berdasarkan bukti.
- [ ] FIN-05 — Terapkan perbaikan, retest, dan regression tests.
- [ ] FIN-06 — Susun laporan akhir, batas pengujian, dan rencana tindak lanjut.

**Target:** menghasilkan assessment yang bisa direproduksi, patch, dan laporan.

SPMB adalah kandidat proyek akhir, bukan materi pertama. Tidak ada pengujian SPMB yang telah dilakukan dalam sesi perencanaan ini.

## Jalur lanjutan

Setelah dasar: OAuth/OIDC, GraphQL, request smuggling, deserialization, prototype pollution, dan topik lain sesuai kebutuhan. Wi-Fi hacking dan Active Directory belum masuk cakupan awal.

## Acuan dan pemeliharaan

Acuan diperiksa pada perencanaan 3 November 2026:

| Referensi | Penggunaan |
|---|---|
| [OWASP Top 10:2025](https://owasp.org/Top10/2025/) | Peta risiko; bukan urutan pengajaran |
| [OWASP WSTG v4.2](https://owasp.org/www-project-web-security-testing-guide/v42/) | Metode dan skenario pengujian |
| [OWASP ASVS](https://asvs.owasp.org/) — baseline 5.0.0 | Kontrol keamanan dan verifikasi perbaikan |
| [OWASP API Security Top 10:2023](https://owasp.org/API-Security/editions/2023/en/0x11-t10/) | Risiko khusus API |
| [PortSwigger Academy](https://portswigger.net/web-security/learning-paths) | Teori dan lab berizin |
| [Juice Shop Companion Guide](https://pwning.owasp-juice.shop/companion-guide/latest/part1/running.html) | Menjalankan target latihan |
| [Fedora Documentation](https://docs.fedoraproject.org/) | Rujukan lingkungan Fedora |
| [Nmap Reference Guide](https://nmap.org/book/man.html) | Makna opsi dan hasil scan |
| [Wireshark User's Guide](https://www.wireshark.org/docs/wsug_html_chunked/) | Capture dan analisis |
| [ZAP Documentation](https://www.zaproxy.org/docs/) | Scope, proxy, dan scanning |

Tambahkan tautan sumber spesifik saat menulis bab. Catat versi dependency/image yang benar-benar digunakan, bukan hanya tag latest. Nama paket dan perintah instalasi Fedora perlu diperiksa sebelum masuk tutorial.

## Cara mencentang

Centang hanya sesudah pengguna mengonfirmasi pencapaian atau memberikan bukti yang memadai. Hubungkan pencapaian ke entri LEARNING_LOG dan perbarui PROGRESS. Jangan mencentang fase hanya karena dokumentasinya sudah dibuat.
