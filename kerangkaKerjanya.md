Berikut adalah kerangka aplikasi absensi siswa berbasis **Laravel + PWA** setelah pembaruan:

---

### **1. Pengguna dan Role**
1. **Admin**  
   - Mengimpor data siswa.
   - Mengelola data siswa secara keseluruhan.

2. **Wali Kelas**  
   - Mengelola data siswa di kelas yang dipimpinnya.
   - Menambah dan menghapus siswa dari kelas.
   - Memberi keterangan alasan absensi siswa.
   - Menerima notifikasi absensi siswa yang tidak hadir.
   - Melihat catatan yang dibuat oleh Guru Pengampu untuk evaluasi siswa.
   - Membuat laporan statistik (harian, mingguan, bulanan, semester).
   - Melaporkan siswa dengan ketidakhadiran tertinggi ke Guru BK.

3. **Guru Pengampu**  
   - Mengisi absensi siswa pada mata pelajaran.
   - Membuat catatan evaluasi siswa untuk Wali Kelas.
   - Menerima pengingat jika lupa melakukan absensi.

4. **Guru BK**  
   - Menerima laporan siswa bermasalah dari Wali Kelas.
   - Membuat dan mencetak surat pemanggilan orang tua.
   - Melacak riwayat pemanggilan orang tua dan tindakan lanjutan.

---

### **2. Modul Utama**
1. **Manajemen Pengguna**  
   - Modul autentikasi dan peran pengguna.

2. **Manajemen Siswa**  
   - Admin dan Wali Kelas dapat mengelola data siswa.

3. **Absensi Siswa**  
   - Guru Pengampu mencatat absensi.
   - Wali Kelas memberikan keterangan alasan siswa yang tidak hadir.

4. **Notifikasi**  
   - Pengingat untuk Guru Pengampu jika lupa absensi.
   - Wali Kelas menerima notifikasi absensi siswa.

5. **Catatan Siswa**  
   - Guru Pengampu mencatat evaluasi siswa.
   - Wali Kelas dapat membaca catatan untuk bahan evaluasi.

6. **Laporan Statistik**  
   - Laporan absensi harian, mingguan, bulanan, dan semester.
   - Wali Kelas, Guru BK, dan Admin memiliki akses.

7. **Pemanggilan Orang Tua**  
   - Wali Kelas melaporkan siswa bermasalah ke Guru BK.
   - Guru BK membuat dan mencetak surat pemanggilan.

8. **Pengingat (Reminder)**  
   - Membantu memastikan absensi, evaluasi, dan pemanggilan dilakukan tepat waktu.

9. **Rekapitulasi dan Unduhan**  
   - Fitur unduh laporan absensi siswa dalam berbagai periode (harian, mingguan, bulanan, semester).

---

### **3. Struktur Folder Laravel + PWA**
1. **app/**  
   - Models  
     - User.php  
     - Student.php  
     - ClassModel.php  
     - Absence.php  
     - Note.php  
     - Notification.php  
     - ParentalCall.php  
     - Reminder.php  
   - Http/  
     - Controllers  
       - UserController.php  
       - StudentController.php  
       - AbsenceController.php  
       - NoteController.php  
       - NotificationController.php  
       - ParentalCallController.php  
       - ReminderController.php  
     - Middleware  
       - RoleMiddleware.php  

2. **database/**  
   - Migrations  
     - create_users_table.php  
     - create_students_table.php  
     - create_classes_table.php  
     - create_absences_table.php  
     - create_notes_table.php  
     - create_notifications_table.php  
     - create_parental_calls_table.php  
     - create_reminders_table.php  

3. **resources/**  
   - Views  
     - Dashboard, absensi, manajemen siswa, laporan, dll.  
   - Js  
     - Vue.js components dan logic front-end.  
   - Css  
     - Stylesheet untuk desain aplikasi.  

4. **routes/**  
   - web.php (Routing utama aplikasi).  

5. **public/**  
   - Aset front-end yang dikompilasi (CSS, JS, gambar).  

6. **config/**  
   - Konfigurasi tambahan seperti notifikasi, database, dan lainnya.  

---

### **4. Struktur Database**
1. **users**  
   - `id`, `nama`, `email`, `kata_sandi`, `peran`, `created_at`, `updated_at`.

2. **students**  
   - `id`, `nama`, `id_kelas`, `nis`, `tanggal_lahir`, `alamat`, `created_at`, `updated_at`.

3. **classes**  
   - `id`, `nama_kelas`, `wali_kelas`, `created_at`, `updated_at`.

4. **absences**  
   - `id`, `id_siswa`, `id_kelas`, `tanggal`, `status_absensi`, `keterangan`, `created_at`, `updated_at`.

5. **notes**  
   - `id`, `id_siswa`, `id_guru`, `catatan`, `created_at`, `updated_at`.

6. **notifications**  
   - `id`, `id_pengguna`, `judul`, `pesan`, `status`, `created_at`, `updated_at`.

7. **parental_calls**  
   - `id`, `id_siswa`, `id_guru_bk`, `alasan`, `status`, `tanggal_pemanggilan`, `created_at`, `updated_at`.

8. **reminders**  
   - `id`, `id_pengguna`, `jenis_pengingat`, `tanggal`, `status`, `created_at`, `updated_at`.

---

### **5. Teknologi yang Digunakan**
- **Backend**: Laravel Framework.
- **Frontend**: Blade Templates atau Vue.js (untuk fitur dinamis).
- **Database**: MySQL.
- **PWA Features**: Laravel PWA Package untuk caching dan offline support.
- **Deployment**: Nginx/Apache, Laravel Forge, atau platform hosting seperti Vercel/Netlify.

---

