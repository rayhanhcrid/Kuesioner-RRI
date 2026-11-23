# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

- **Petugas asesmen** (asesor) di Lapas Kelas II B Cianjur. Mereka mengisi instrumen sambil mewawancarai narapidana/klien pemasyarakatan, satu orang per sesi, lalu mengirim hasilnya. Perangkat campuran: laptop/PC di meja ruang asesmen dan HP/tablet yang dipegang saat wawancara; keduanya harus nyaman.
- **Pimpinan** (Kasi, Kalapas) membuka Dashboard untuk memantau siapa saja yang sudah diasesmen dan membaca hasilnya.
- **Admin/operator data** membuka Dashboard untuk merekap dan mengunduh data.
- Petugas asesmen juga membuka Dashboard untuk mengecek dan merevisi asesmen yang sudah mereka kirim.

## Product Purpose

Mengganti pengisian manual formulir Asesmen Risiko Residivisme (Instrumen RRI) dan Asesmen Kebutuhan Kriminogenik menjadi formulir digital yang menghitung skor dan kategori otomatis, mencetak dokumen resmi siap tanda tangan, dan mengumpulkan hasil dari semua perangkat ke satu Dashboard. Berhasil bila petugas bisa menyelesaikan satu asesmen tanpa kertas dan tanpa salah hitung, dan pimpinan bisa melihat serta mengunduh semua hasil dari satu tempat.

## Operating Context

- Asesmen wajib dilaksanakan berdasarkan Pedoman Pelaksanaan Asesmen Risiko Residivisme dan Asesmen Kebutuhan Kriminogenik tahun 2021. Teks pertanyaan, pilihan jawaban, nilai, dan rentang kategori berasal dari pedoman itu dan tidak boleh diubah.
- Alur satu asesmen: Identitas & Lembar Persetujuan (informed consent) → RRI Bagian A (10 butir bernilai, total 0–17) → RRI Bagian B, C (khusus perempuan), D (khusus narkotika) sebagai daftar periksa Ya/Tidak → Kebutuhan Kriminogenik (7 faktor, total 0–39) → Hasil & Cetak → Kirim Data.
- Kategori skor: Rendah, Sedang, Tinggi, Sangat Tinggi.
- Dokumen cetak/PDF mengikuti format resmi (Lembar Persetujuan, Instrumen RRI, Instrumen Kebutuhan Kriminogenik, kolom tanda tangan petugas dan narapidana). Format cetak tidak ikut dirombak tampilan layar.
- Data bersifat RAHASIA.

## Capabilities and Constraints

- Satu file statis `index.html` tanpa build step, di-hosting di GitHub Pages; `npm run dev` (Vite) hanya untuk preview lokal.
- Draf dan "Data Tersimpan" disimpan di localStorage perangkat; ekspor CSV, cadangan/impor JSON.
- "Kirim Data" mengirim ke Supabase (project lucid-aim, schema privat `rri`) lewat RPC `rri_submit`; Dashboard membaca lewat RPC `rri_dashboard` dengan password yang dicek di server.
- Dashboard: total data, pencarian, daftar data terkirim yang bisa dibuka kembali di formulir untuk diubah dan dikirim ulang, unduh PDF per orang, unduh rekap Excel (CSV).
- Bahasa antarmuka: Bahasa Indonesia.

## Brand Commitments

- Logo Pemasyarakatan wajib dipakai.
- Warna navy dan emas khas Pemasyarakatan wajib dipakai (dikonfirmasi pengguna).
- Label RAHASIA pada antarmuka.
- Nama instansi: Lapas Kelas II B Cianjur.

## Evidence on Hand

- Logo Pemasyarakatan tertanam sebagai data URI di `index.html`.
- Seluruh isi instrumen (pertanyaan, catatan, opsi, nilai) ada di `index.html`.
- Tidak ada foto, data statistik, atau testimoni; jangan mengarang data asesmen nyata.

## Product Principles

1. Pedoman 2021 adalah sumber kebenaran: isi instrumen dan cara hitung tidak pernah dikorbankan demi tampilan.
2. Petugas sedang mewawancarai orang: formulir harus bisa diisi cepat tanpa kehilangan posisi, di laptop maupun HP.
3. Skor dan kelengkapan selalu terlihat, sehingga kesalahan hitung dan butir yang terlewat tertangkap sebelum dicetak atau dikirim.
4. Data narapidana rahasia: akses Dashboard dijaga dan tidak ada yang bocor ke tempat yang tidak perlu.
5. Tampil sebagai alat kerja resmi Pemasyarakatan yang serius dan rapi, bukan aplikasi gaya startup.
