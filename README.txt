SiGaji — Proyek Modul 5 Pemrograman Platform Desktop
Teknologi: Python 3.10+ dengan Tkinter, MySQL 8+, mysql-connector-python.
1. Buat venv: python -m venv venv; aktifkan sesuai sistem operasi.
2. Pasang driver: python -m pip install -r requirements.txt
3. Jalankan schema.sql di server MySQL yang Anda kelola melalui klien SQL/phpMyAdmin.
4. (Opsional) Buat akun payroll_app lokal dengan hak SELECT, INSERT, UPDATE, DELETE pada db_penggajian_modul5. Praktikum ini memakai akun root XAMPP.
5. Salin config.example.ini menjadi config.ini dan isi password, port, host, database.
6. Uji koneksi: python cek_koneksi.py; kemudian python app.py.
7. Uji logika: python -m unittest -v test_model.py (tanpa MySQL/GUI).
Database tidak dihapus saat aplikasi ditutup. Script schema memakai CREATE IF NOT EXISTS;
script tersebut bukan alat migrasi dan tidak memperbarui tabel lama yang berbeda.
NIK adalah kode internal, bukan nomor identitas kependudukan. Gunakan data rekaan.
Simulasi: bruto = pokok + tunjangan + jam_lembur*tarif; netto = bruto-potongan.
Nominal berupa integer rupiah (tanpa titik/koma); tidak ada aturan pajak/BPJS otomatis.
Satu gaji per karyawan per YYYY-MM. Tidak disediakan edit/hapus transaksi gaji;
riwayat menyimpan snapshot identitas dan nominal saat transaksi dibuat.
Karyawan bersejarah tidak dapat dihapus; gunakan status nonaktif.
Ekspor slip TXT dan rekap CSV melalui Laporan. CSV yang dimulai simbol formula dilindungi.
Tutup/buka layar dari menu setelah perubahan untuk memuat data terkini. Dashboard via File.
Error teknis dicatat dalam penggajian.log, jangan memasukkan config.ini ke Git/unggahan tugas.
Tkinter hanya di main thread. Contoh database sinkron dengan timeout koneksi 5 detik;
untuk server jarak jauh/volume besar, lanjutkan ke worker dan queue/after agar UI tidak tertahan.
XAMPP dapat menyertakan MariaDB, bukan MySQL Oracle. Verifikasi SELECT VERSION();
kode SQL ini menggunakan subset yang kompatibel untuk laboratorium, tetapi uji pula
pada versi MySQL yang digunakan kelas. Tidak memerlukan Apache untuk aplikasi desktop.