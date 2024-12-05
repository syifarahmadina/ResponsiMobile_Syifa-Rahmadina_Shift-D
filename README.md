ResponsiMobile_Syifa-Rahmadina_Shift-D


Tampilan Login: 

![LMA](https://github.com/user-attachments/assets/336932c1-41c1-42fe-a66f-073aab13e329)


Tampilan HomePage:


![image](https://github.com/user-attachments/assets/b88071e0-e58f-421a-8fc6-4333ef62b57d)


Tampilan Hapus:


![image](https://github.com/user-attachments/assets/c2f74d95-a06a-406a-ba32-af85f22b9c00)


Tampilan Edit:

![image](https://github.com/user-attachments/assets/ce14ad56-5c7f-422c-9884-a1a0272d44bf)


Tampilan Form:

![Form Tambah](https://github.com/user-attachments/assets/e87c21a1-d02d-46cc-99be-26d051b40d95)


Penjelasan CRUD:

Proses CRUD di `HomePage.vue` ini melibatkan operasi untuk **Create** (Membuat), **Read** (Membaca), **Update** (Memperbarui), dan **Delete** (Menghapus) mainan, dengan menggunakan Firebase Firestore sebagai layanan backend. Berikut penjelasan rinci tentang bagaimana setiap operasi CRUD bekerja:

### 1. **Read (Membaca Data Mainan)**:

   - Fungsi `loadToys` digunakan untuk mengambil daftar mainan dari Firestore.
     
   - Fungsi ini memanggil `firestoreService.getToys()`, yang kemungkinan besar mengambil daftar mainan dari database Firestore.
     
   - Daftar mainan kemudian disimpan dalam variabel ref `toys`, yang digunakan untuk menampilkan daftar mainan di halaman.
     
   - Ketika halaman dimuat atau di-refresh (melalui `handleRefresh`), daftar mainan akan dimuat ulang menggunakan fungsi ini.



### 2. **Create (Membuat Mainan Baru)**:

   - Ketika tombol "Add" (`ion-fab-button`) diklik, sebuah modal form (`InputModal`) dibuka untuk menginput data mainan baru.
     
   - Fungsi `handleSubmit` menangani pembuatan mainan baru.
     
     - Jika nama mainan diisi, fungsi ini memeriksa apakah `editingId` sudah diset:
       
       - **Jika `editingId` kosong** (mainan baru), maka fungsi ini memanggil `firestoreService.addToy(toy)` untuk menambahkan mainan baru ke database Firestore.
         
       - **Jika `editingId` diset** (mode edit), maka fungsi ini memanggil `firestoreService.updateToy(editingId.value, toy)` untuk memperbarui data mainan yang sudah ada.
         
   - Setelah berhasil membuat atau memperbarui mainan, daftar mainan dimuat ulang dan pesan sukses ditampilkan menggunakan toast.



### 3. **Update (Memperbarui Mainan yang Ada)**:

   
   - Ketika pengguna menggeser item mainan (menggunakan `ion-item-sliding`), fungsi `handleEdit` akan dipanggil.
     
   - Fungsi ini mengatur `editingId` dengan ID mainan yang sedang diedit, dan memuat data mainan yang ada ke dalam variabel ref `toy`.
     
   - Modal akan dibuka dengan data yang ada, dan pengguna dapat memperbarui detail mainan.
     
   - Ketika pengguna mengirimkan formulir, fungsi `handleSubmit` akan memperbarui mainan yang ada (jika `editingId` diset) atau membuat mainan baru.

 
### 4. **Delete (Menghapus Mainan)**:
    
   - Ketika pengguna menggeser untuk membuka opsi hapus, fungsi `handleDelete` akan dipanggil.
     
   - Fungsi ini memanggil `firestoreService.deleteToy(toy.id!)` untuk menghapus mainan yang dipilih dari Firestore.
     
   - Setelah penghapusan, daftar mainan dimuat ulang, dan pesan sukses ditampilkan.

