Berikut adalah **kerangka aplikasi absensi pembelajaran siswa** yang telah diperbarui dengan fitur terbaru:

---

### **Kerangka Aplikasi Absensi Pembelajaran Siswa (Laravel + PWA)**

#### **Role Pengguna:**
1. **Admin**
2. **Wali Kelas**
3. **Guru Pengampu**
4. **Guru BK**

---

### **1. Admin**
- **Impor Data Siswa**: Mengimpor data siswa dari file eksternal (CSV, Excel).
- **Kelola Data Pengguna**: Mengelola akun pengguna seperti Wali Kelas, Guru Pengampu, dan Guru BK.
- **Laporan Statistik**: Mengakses laporan absensi siswa (harian, mingguan, bulanan, dan per semester).

---

### **2. Wali Kelas**
- **Mengelola Data Siswa di Kelas**: Menambah dan menghapus siswa dari kelas yang dipimpin.
- **Memberi Keterangan Absensi**: Memberikan keterangan alasan untuk siswa yang tidak hadir (sakit, izin, dll.).
- **Menerima Notifikasi Absensi**: Notifikasi otomatis jika ada siswa yang tidak hadir.
- **Laporan Statistik**: Mengakses laporan absensi siswa untuk bahan referensi harian, mingguan, bulanan, dan per semester.
- **Pemantauan Ketidakhadiran Siswa**: Melaporkan siswa dengan tingkat ketidakhadiran tinggi ke Guru BK untuk pemanggilan orang tua.
- **Fitur Pengingat (Reminder)**: Pengingat untuk memastikan keterangan absensi atau pemanggilan orang tua dilakukan tepat waktu.
- **Catatan Siswa**: Melihat catatan siswa yang diisi oleh Guru Pengampu sebagai bahan evaluasi.

---

### **3. Guru Pengampu**
- **Absensi**: Mencatat kehadiran siswa di setiap pelajaran.
- **Laporan Statistik**: Mengakses laporan absensi siswa untuk referensi pengajaran.
- **Fitur Pengingat (Reminder)**: Sistem mengingatkan Guru Pengampu jika lupa mengabsensi siswa pada jam pelajaran tertentu.
- **Catatan Siswa**: Mengisi catatan untuk siswa, yang nantinya dapat dilihat oleh Wali Kelas untuk bahan evaluasi.

---

### **4. Guru BK**
- **Pemanggilan Orang Tua**: Membuat surat pemanggilan orang tua untuk siswa dengan masalah absensi atau perilaku.
- **Laporan Pemanggilan Orang Tua**: Melacak riwayat pemanggilan orang tua dan tindakan yang telah diambil.
- **Fitur Pengingat (Reminder)**: Pengingat terkait tindak lanjut pemanggilan orang tua.

---

### **Fitur-Fitur Utama Aplikasi:**
1. **Absensi Siswa**: Setiap Guru dapat mencatat kehadiran siswa.
2. **Laporan Absensi**: Laporan absensi berdasarkan harian, mingguan, bulanan, dan per semester.
3. **Notifikasi Absensi**: Wali Kelas menerima notifikasi jika ada siswa yang tidak hadir.
4. **Pemanggilan Orang Tua**: Guru BK membuat dan mengelola surat pemanggilan orang tua.
5. **Pengingat (Reminder)**: Sistem pengingat untuk Guru Pengampu, Wali Kelas, dan Guru BK.
6. **Laporan Statistik**: Admin, Wali Kelas, dan Guru Pengampu dapat mengakses laporan statistik absensi.
7. **Catatan Siswa**: Guru Pengampu mengisi catatan siswa, yang dapat dilihat oleh Wali Kelas untuk bahan evaluasi.

---

### **Struktur Database**

1. **Tabel Users**: 
   - **id** (Primary Key)
   - **name**
   - **email**
   - **password**
   - **role** (Admin, Wali Kelas, Guru Pengampu, Guru BK)

2. **Tabel Students**:
   - **id** (Primary Key)
   - **name**
   - **nis**
   - **class_id** (Foreign Key to Classes)
   - **status** (Active, Inactive)

3. **Tabel Classes**:
   - **id** (Primary Key)
   - **name** (Class name)
   - **teacher_id** (Foreign Key to Users)

4. **Tabel Absences**:
   - **id** (Primary Key)
   - **student_id** (Foreign Key to Students)
   - **date**
   - **status** (Absent, Present, Excused)
   - **reason** (Optional)

5. **Tabel Parental Calls**:
   - **id** (Primary Key)
   - **student_id** (Foreign Key to Students)
   - **date_of_call**
   - **reason_for_call**
   - **action_taken**

6. **Tabel Notifications**:
   - **id** (Primary Key)
   - **user_id** (Foreign Key to Users)
   - **message**
   - **type** (Absence, Reminder, Parental Call)
   - **status** (Read, Unread)

7. **Tabel Notes**:
   - **id** (Primary Key)
   - **student_id** (Foreign Key to Students)
   - **note** (Content of the note)
   - **created_by** (Foreign Key to Users, identifies who created the note)
   - **created_at**

---

### **Alur Pengguna**
1. **Guru Pengampu**:
   - Login → Mencatat Absensi → Mengakses Laporan Absensi → Mengisi Catatan Siswa → Menerima Pengingat jika lupa absensi.

2. **Wali Kelas**:
   - Login → Mengelola Siswa → Menerima Notifikasi Absensi → Memberikan Keterangan Absensi → Melaporkan Ketidakhadiran Tinggi ke Guru BK → Mengakses Laporan Statistik → Melihat Catatan Siswa.

3. **Guru BK**:
   - Login → Melihat Laporan Ketidakhadiran → Membuat Pemanggilan Orang Tua → Mengakses Laporan Pemanggilan Orang Tua.

4. **Admin**:
   - Login → Mengelola Data Siswa → Mengelola Pengguna → Mengakses Laporan Statistik.

---

Jika ada tambahan atau koreksi, beri tahu saya!
