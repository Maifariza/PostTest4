 # POST-TEST 4 PRAKTIKUM PBO

### **Disusun Oleh**

===========================================================================

                                                                

**Maifariza Aulia Dyas - 2409116032**                         

                                                                

   Sistem Informasi - A - 2024                                  

                                                               

===========================================================================
 
### **SISTEM MANAJEMEN KOLEKSI BARANG ANTIK**

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/30c70b77-8e8b-4624-ae41-24ccd3bcf31c" />



  <h1 align="center">AntikAesthetic 🔎⏳</h1>
    
 -------------------------------------------------------------------------
 

   AntikAesthetic adalah program sederhana berbasis Java untuk menyimpan dan mengelola koleksi barang antik. Tujuannya adalah agar data dapat lebih tertata, mudah dicari, dan tidak ribet.  Dengan aplikasi ini, pencatatan yang biasanya dilakukan secara manual kini bisa dilakukan otomatis sehingga dapat mengurangi salah input.
   
   Program ini menyediakan fitur utama berupa CRUD (Create, Read, Update, Delete) dan pencarian. Melalui fitur tersebut, pengguna dapat menambahkan barang baru ke dalam koleksi, menampilkan seluruh data barang dalam bentuk tabel, memperbarui data tertentu berdasarkan ID, hingga menghapus barang yang sudah tidak diperlukan. 
   
   Fitur pencarian tersedia untuk memudahkan pengguna menemukan barang tertentu hanya dengan memasukkan kata kunci, baik dari nama, kategori, maupun asal barang. 

   Setiap barang antik yang disimpan dalam sistem digambarkan sebagai sebuah objek dengan atribut yang cukup lengkap, mulai dari ID unik, nama barang, kategori, asal, tahun pembuatan, material, kondisi, sumber perolehan, hingga harga perolehan. Seluruh data ini dikelola menggunakan struktur ArrayList, sehingga penyimpanan menjadi lebih fleksibel dan juga memudahkan proses manipulasi data seperti menambah, menampilkan, memperbarui, maupun menghapus.

---


<h1 align="center">Penerapan MVC dan Struktur Packages Program</h1>

1. Package model (Model)
   
    > Package ini berisi class Model yang merepresentasikan data barang antik. Class ini memiliki beberapa properti seperti id, nama, kategori, asal, tahun, material, kondisi, sumber, dan hargaPerolehan. Semua properti dibuat dengan access modifier private untuk menjaga prinsip enkapsulasi. Data diakses dan diubah melalui getter dan setter, serta diinisialisasi menggunakan konstruktor. Dengan adanya package ini, semua data barang antik tersimpan rapi dalam bentuk objek.

2. Package service (Controller)

    > Package ini berisi class Service yang mengatur logika bisnis program. Semua operasi CRUD (Create, Read, Update, Delete) dijalankan di sini, termasuk juga fitur pencarian data dan validasi input. Controller ini menerima perintah dari View (Main), memprosesnya dengan memanfaatkan data dari Model, lalu mengembalikan hasilnya kembali ke View. Dengan cara ini, logika program terpusat di satu tempat dan tidak tercampur dengan tampilan.

3. Package main (View)
   
    > Package ini berisi class Main yang menjadi entry point program. Class ini berfungsi sebagai View, yaitu menampilkan menu utama kepada user dan menerima input pilihan. Setelah menerima input, class ini akan memanggil fungsi yang sesuai di Controller (Service). Karena hanya berfungsi sebagai antarmuka pengguna, class ini tidak diwajibkan memiliki properti maupun konstruktor.


---

<h1 align="center">Penjelasan Penerapan Abstraction</h1>

Pada program ini, konsep abstraction diterapkan dengan membuat abstract class dan interface.

1. **Abstract Class – Barang**
  
   <img width="422" height="83" alt="image" src="https://github.com/user-attachments/assets/0f02ab1d-ee3d-4816-838d-42c62bc7227c" />

   Kelas Barang dijadikan abstract karena di dalamnya ada method yang belum memiliki implementasi, yaitu hitungAsuransi() dan getTipe(). Abstract class ini juga menyimpan properti umum semua barang (seperti id, nama, kategori, asal, tahun, dll). Dengan cara ini, kita bisa memastikan setiap subclass (barangLelang, barangWarisan, barangUmum) wajib mengisi sendiri logika khusus untuk metode yang abstrak tadi.

2. **Interface – Penilaian**
  
   <img width="462" height="82" alt="image" src="https://github.com/user-attachments/assets/a9af0310-3991-4deb-9b75-8ae8ec98c1f6" />

   Selain abstract class, program juga menggunakan interface Penilaian yang mendefinisikan method estimasiNilai(double faktorKondisi). Interface ini diimplementasikan oleh class Barang, lalu diturunkan ke semua subclass. Artinya, setiap jenis barang pasti bisa dihitung nilai estimasinya, tetapi dengan cara yang mungkin berbeda.

   Jadi, kombinasi antara abstract class dan interface inilah yang menjadi bentuk nyata dari abstraction dalam program ini.

---

<h1 align="center">Penjelasan Penerapan Polymorphism</h1>

Konsep polymorphism dalam program ini muncul dalam dua bentuk: overloading dan overriding.

1. **Polymorphism dengan Overloading**

   **a. Class Barang**

   <img width="702" height="182" alt="image" src="https://github.com/user-attachments/assets/ef6b875f-0008-48ae-8b05-3940f947afa1" />

   > Pada class Barang, terdapat method infoSingkat() dan infoSingkat(boolean tampilHarga). Keduanya memiliki nama yang sama tetapi parameter berbeda. Ini contoh method overloading, karena kita bisa memanggil fungsi infoSingkat() dengan cara yang berbeda sesuai kebutuhan (menampilkan ringkasan saja, atau ringkasan sekaligus harga).
   
   **b. Class Service**
   
   <img width="665" height="142" alt="image" src="https://github.com/user-attachments/assets/c23ed2af-70d2-4734-9b35-494dd7705ed5" />

   > Selain itu, di class Service juga ada method tampilkanTabelBarang() dan tampilkanTabelBarang(boolean showFooter) yang fungsinya sama-sama menampilkan daftar barang, tapi parameternya berbeda.

3. **Polymorphism dengan Overriding**

   <img width="600" height="328" alt="image" src="https://github.com/user-attachments/assets/1d00d6cf-30eb-4141-9a38-b74d47da8209" />

  
   Pada class barangLelang, barangWarisan, dan barangUmum, semua melakukan override terhadap method abstract hitungAsuransi() dan getTipe() dari class Barang.

   Masing-masing subclass punya logika berbeda. Misalnya, barangLelang menghitung asuransi 1.5% dengan tambahan markup, sedangkan barangWarisan hanya 0.8%, dan barangUmum 1.0%.

   Method infoSingkat() juga dioverride supaya hasil ringkasannya otomatis menambahkan label tipe barang (LELANG, WARISAN, atau UMUM).

   Bahkan di barangLelang, method estimasiNilai(double faktorKondisi) juga dioverride untuk menambahkan markup 5% dibanding perhitungan normal.

Dengan penerapan ini, walaupun kita memanggil method yang sama (hitungAsuransi(), infoSingkat()), hasilnya akan berbeda tergantung objek yang digunakan. Inilah inti dari polymorphism: satu nama method, perilaku berbeda sesuai jenis objek.

---

<h1 align="center">Struktur Program</h1>

Program yang saya buat terdiri dari beberapa kelas yang memiliki peran masing-masing.

 1. Main.java

    <img width="884" height="781" alt="image" src="https://github.com/user-attachments/assets/bee6126e-1e87-47b4-a9c0-98c24bf7d428" />

    > Kelas utama berada di Main.java yang berfungsi sebagai entry point program. Di dalam kelas ini terdapat menu interaktif yang digunakan pengguna untuk menambah, menampilkan,       memperbarui, menghapus, dan mencari data barang. Main juga menjadi penghubung langsung dengan kelas Service agar logika program dapat berjalan sesuai perintah pengguna.
    
 2. Service.java

    <img width="863" height="861" alt="image" src="https://github.com/user-attachments/assets/c585e91a-ceb8-4be2-9ae2-409e471aae9c" />


    > Selanjutnya ada kelas Service.java yang berada di dalam package service. Kelas ini bertanggung jawab mengelola data barang, mulai dari penyimpanan, penambahan data baru, penghapusan, pencarian, hingga menampilkan seluruh data. Dengan kata lain, Service menjadi pusat logika bisnis program.

 3. Barang.java

    <img width="756" height="844" alt="image" src="https://github.com/user-attachments/assets/ca35764e-ce02-4a13-afc3-b3bb7e5e2a90" />


    > Untuk data inti, saya menggunakan package model. Di dalamnya terdapat kelas Barang sebagai superclass. Kelas Barang menyimpan semua properti umum, seperti id, nama, kategori, asal, tahun, material, kondisi, sumber, dan hargaPerolehan. Semua atribut dibuat private dan diakses menggunakan getter dan setter, sehingga konsep encapsulation diterapkan.

    Dari kelas Barang, saya membuat dua subclass, yaitu barangLelang dan barangWarisan. Kedua kelas ini mewarisi semua atribut yang ada di kelas Barang, tapi punya cara kerja khusus karena saya menggunakan method overriding pada method infoSingkat().

    a. Subclass barangLelang.java

    <img width="844" height="238" alt="image" src="https://github.com/user-attachments/assets/b9e21e51-9eff-483b-ad47-62ac99cd50f1" />

     > Pada kelas barangLelang, method infoSingkat() dioverride untuk menambahkan informasi tambahan berupa keterangan “tipe: LELANG”.
     
     > Dengan demikian, ketika objek dari kelas ini dipanggil, sistem tidak hanya menampilkan data dasar (seperti ID, nama, kategori, asal, dan sumber), tetapi juga memberikan penanda khusus bahwa barang tersebut berasal dari lelang. Hal ini membantu pengguna agar langsung mengetahui asal barang hanya dengan melihat ringkasan.
    
    b. Subclass baranngWarisan.java

    <img width="851" height="232" alt="image" src="https://github.com/user-attachments/assets/5ee49e4e-6bf5-406a-ba59-e074cf7199b5" />

    > Sementara itu, pada kelas barangWarisan, method yang sama juga dioverride. Bedanya, hasil ringkasan akan menampilkan tambahan “tipe: WARISAN”. Artinya, meskipun atribut-atribut utama seperti nama, kategori, asal, dan sumber diwarisi dari superclass Barang, subclass ini mampu memberikan informasi lebih detail.

    c. Subclass barangUmum.java
    
    <img width="805" height="404" alt="image" src="https://github.com/user-attachments/assets/fe3b6740-ef01-45ef-94d3-cf86287ed4c2" />
    
    > Blablabla

 4. Penilaian.java

    <img width="450" height="118" alt="image" src="https://github.com/user-attachments/assets/114b0092-f773-42b8-8997-b5a30054ba67" />


---

<h1 align="center">Alur Program AntikAesthetic</h1>

  Saat pertama kali dijalankan, sistem langsung menyiapkan data awal berupa beberapa barang antik yang otomatis dimasukkan ke dalam koleksi. Setelah itu, pengguna langsung dibawa ke menu utama yang berisi enam pilihan, yaitu tambah barang, tampilkan barang, perbarui barang, hapus barang, cari barang, dan keluar program.

1. **Mulai dan tampilkan menu utama**
   
   Setiap kali program berjalan, menu utama akan selalu pertama ditampilkan. Dari sini, pengguna bisa memilih fitur apa yang ingin dilakukan dengan memasukkan angka 1 hingga 6.

2. **Tambah barang baru**
   
   Jika pengguna memilih menu tambah barang, sistem akan meminta data barang satu per satu, seperti nama, kategori, asal, tahun pembuatan, material, kondisi, sumber perolehan, dan harga.

   Input yang diberikan akan divalidasi agar sesuai dengan aturan (misalnya tahun harus angka antara 0–3000, harga tidak boleh negatif). Setelah semua data diisi dengan benar, barang akan ditambahkan ke koleksi dan ditampilkan pesan bahwa barang berhasil disimpan.

3. **Menampilkan semua barang**
   
   Pada menu ini, sistem menampilkan daftar lengkap koleksi barang antik dalam bentuk tabel yang rapi. Jika belum ada barang sama sekali, program akan memberi tahu bahwa data masih kosong.

4. **Memperbarui barang berdasarkan ID**
   
   Jika pengguna ingin mengubah data barang, pengguna diminta memasukkan ID barang yang ada. Jika ID ditemukan, setiap data lama akan ditampilkan dalam tanda kurung, dan pengguna bisa memilih untuk menggantinya atau membiarkannya tetap sama.

   Misalnya, jika kolom nama dikosongkan, maka nama lama akan tetap dipakai. Setelah diperbarui, program menegaskan bahwa perubahan berhasil dilakukan.

5. **Menghapus barang berdasarkan ID**
   
   Di menu hapus, pengguna juga perlu memasukkan ID barang. Kalau ID tidak ditemukan, akan muncul pesan bahwa data tidak ada. Jika ID valid, sistem meminta konfirmasi terlebih dahulu. Hanya jika pengguna mengetik “y”, barang benar-benar akan dihapus dari koleksi.

6. **Mencari barang**
   
   Fitur ini memungkinkan pengguna mencari barang dengan kata kunci tertentu, baik berdasarkan nama, kategori, maupun asal barang. Jika kata kunci ditemukan pada salah satu barang, hasilnya akan ditampilkan dalam bentuk tabel. Selain itu, sistem juga menampilkan ringkasan hasil pencarian dengan tambahan informasi khusus, sehingga pengguna dapat lebih mudah memahami jenis barang yang ditemukan.

   Jika tidak ada barang yang sesuai, program akan menampilkan pesan bahwa tidak ada hasil yang cocok.
   

7. **Keluar dari program**
   
   Menu terakhir digunakan untuk menutup aplikasi. Sebelum benar-benar keluar, sistem meminta konfirmasi. Kalau pengguna mengetik “y”, program berhenti dengan ucapan terima kasih. Jika tidak, pengguna kembali ke menu utama.
   
---

<h1 align="center">⏳ Menu Utama AntikAesthetic ⏳</h1>

<img width="776" height="289" alt="image" src="https://github.com/user-attachments/assets/02a777fb-04ed-43ee-86f5-5dc2a5298a12" />


Pada awal program, pengguna akan langsung diarahkan ke Menu Utama AntikAesthetic. Menu ini berfungsi sebagai menu utama untuk mengakses seluruh fitur yang tersedia. Terdapat enam pilihan utama yang bisa dipilih sesuai kebutuhan.

   1. Tambah Barang, digunakan untuk menambahkan data barang antik baru dengan mengisi atribut seperti nama, kategori, asal, tahun pembuatan, material, kondisi, sumber perolehan, dan harga perolehan.

   2. Tampilkan Semua Barang, menampilkan seluruh koleksi barang antik yang tersimpan dalam bentuk tabel agar mudah dibaca.

   3. Perbarui Barang, memungkinkan pengguna memperbarui data barang tertentu dengan memasukkan ID barang yang ingin diubah.

   4. Hapus Barang, menghapus data barang dari koleksi berdasarkan ID barang yang ingin dihapus.

   5. Cari Barang, memudahkan pengguna menemukan data barang tertentu dengan memasukkan kata kunci pencarian seperti nama/kategori/asal barang yang ingin dicari.
   
   6. Keluar, digunakan untuk menutup program. Sebelum benar-benar keluar, sistem akan menampilkan konfirmasi agar tidak terjadi kesalahan.

--------------------------------------------------------------------------------------------------------------------------------------------------------------

# **Jika memilih opsi 1 maka akan diarahkan ke Tambah Barang**

<img width="600" height="377" alt="image" src="https://github.com/user-attachments/assets/5c6f965b-67cd-466c-a238-47b529445c26" />

 Ketika pengguna menginputkan angka 1 pada menu utama maka akan diarahkan ke menu "Tambah Barang AntikAesthetic" seperti yang tertera pada gambar di atas ini.


<img width="511" height="298" alt="image" src="https://github.com/user-attachments/assets/aa1a8488-abe5-4c84-ab4b-7b8d7d74c4f1" />


Lalu, program akan menampilkan form input untuk menambahkan data barang antik baru ke dalam sistem.

Seperti pada gambar, user ingin menambah barang Patung Ganesha. Setelah itu, user diminta mengisi informasi lainnya secara berurutan, mulai dari kategori barang, asal, tahun pembuatan, material, kondisi barang, sumber perolehan, hingga harga perolehan.


### Pemberitahuan Jika Berhasil

<img width="464" height="54" alt="image" src="https://github.com/user-attachments/assets/408ffe7a-4b6d-4956-aac9-fba391e5e2f2" />


Setelah semua data selesai diisi, sistem akan otomatis memberikan ID unik untuk barang baru tersebut dan menambahkannya ke dalam koleksi. 

### Pengecekan Ulang

<img width="1297" height="689" alt="image" src="https://github.com/user-attachments/assets/82f5227c-8690-4b8f-b3ba-f64144f73549" />


Lalu untuk melihat daftar koleksi yang telah ditambahkan, user mengetik 2. Di bagian akhir, program menampilkan instruksi “Tekan Enter untuk melanjutkan…” agar pengguna bisa kembali ke menu utama dan melanjutkan ke fitur lain sesuai kebutuhan.

## **Validasi Input**

### Jika Inputan tahun tidak di antara 0 - 3000

<img width="605" height="203" alt="image" src="https://github.com/user-attachments/assets/1d927882-98ae-4606-9a3e-fbc24066c114" />


Ketika pengguna mengisi data barang baru, setiap input akan dicek dulu apakah sesuai dengan aturan yang berlaku. Pada contoh di atas, pengguna mencoba memasukkan tahun pembuatan dengan nilai -200. Karena sistem sudah diberi aturan bahwa tahun harus berada dalam rentang 0 sampai 3000, maka input tersebut dianggap tidak valid.

Program kemudian langsung menampilkan pesan peringatan “Harus di antara 0 dan 3000.”. Setelah itu, pengguna diminta kembali untuk mengisi nilai tahun yang benar. 

### Jika Inputan Kosng

<img width="580" height="138" alt="image" src="https://github.com/user-attachments/assets/f809256c-c79d-4924-8416-1741cc1e6b36" />


Apabila pengguna mencoba menambahkan barang baru namun tidak mengisi data pada kolom yang diminta, maka program akan menampilkan pesan peringatan. 

Misalnya, ketika pengguna menekan Enter tanpa mengetikkan nama barang, sistem akan menampilkan pesan “Input tidak boleh kosong”.

--------------------------------------------------------------------------------------------------------------------------------------------------------------

# **Jika memilih opsi 2 maka akan diarahkan ke Tampilkan Barang**

<img width="1279" height="629" alt="image" src="https://github.com/user-attachments/assets/baebb6d6-729f-4a91-a8e5-9ddef25e8309" />


  Jika pengguna memilih opsi 2 pada menu utama, maka program akan diarahkan ke fitur Tampilkan Semua Barang. Pada bagian ini, sistem akan menampilkan seluruh koleksi barang dari AntikAesthetic yang sudah tersimpan dalam database program. Data ditampilkan dalam bentuk tabel agar lebih terstruktur dan mudah dipahami.

  Tabel tersebut berisi informasi penting yang dibagi ke dalam beberapa kolom, yaitu ID, Nama, Kategori, Asal, Tahun Pembuatan, Material, Kondisi, Sumber Perolehan, dan Harga. Setiap baris dalam tabel mewakili satu objek barang antik, sementara ID berfungsi sebagai penanda unik sehingga data dapat dengan mudah diidentifikasi saat ingin diperbarui atau dihapus.

  Melalui tampilan ini, pengguna dapat dengan mudah melihat keseluruhan koleksi barang antik hanya dalam satu layar. Format tabel yang rapi membuat data lebih mudah dibaca, dipahami, dan dibandingkan antar barang. Hal ini membantu pengguna ketika ingin menilai kondisi, harga, atau asal-usul barang tertentu secara cepat.

  Setelah seluruh data ditampilkan, program akan memberikan instruksi kepada pengguna untuk menekan tombol Enter agar dapat melanjutkan ke langkah berikutnya. Tekanan tombol Enter ini akan mengembalikan pengguna ke menu utama, sehingga pengguna dapat memilih kembali menu yang lain sesuai kebutuhan, misalnya menambah barang, memperbarui, menghapus, atau keluar dari program.
  
--------------------------------------------------------------------------------------------------------------------------------------------------------------

# **Jika memilih opsi 3 maka akan diarahkan ke Update Barang**


<img width="1319" height="720" alt="image" src="https://github.com/user-attachments/assets/51aa6c1e-336f-4fab-83c3-0beef394cd9c" />


Ketika pengguna memilih opsi 3 pada menu utama, maka program akan diarahkan ke fitur Update Barang. Ketika program di jalankan, akan ditampilkan terlebih dahulu daftar barang yang ada di Antikaethetic agar bisa melihan pada ID berapa barang ingin di Update.

<img width="608" height="375" alt="image" src="https://github.com/user-attachments/assets/8403e627-b6ea-4a12-a71d-640c33f34931" />


Lalu, sistem meminta pengguna untuk memasukkan ID dari barang yang ingin diperbarui. ID ini digunakan sebagai penanda unik setiap barang dalam koleksi.

Setelah ID dimasukkan, program akan menampilkan form dengan data lama sebagai referensi. Pengguna dapat mengosongkan input (menekan Enter) jika ingin mempertahankan nilai lama, atau mengetikkan data baru untuk mengganti informasi.

Program akan menampilkan data lama seperti nama barang, kategori, asal, tahun pembuatan, material, kondisi, sumber perolehan, dan harga. Pengguna bisa mengubah salah satu atau beberapa data. Seperti pada gambar diatas, pengguna ingin memperbarui data pada barang dengan ID 1 (Vas Dinasti Ming). Namun, ia hanya ingin merubah data kondisi pada ID 1 saja yang tadinya kondisi "Baik" menjadi "Rusak". Setelah menekan Enter, program akan menyimpan perubahan tersebut dan menampilkan pesan “Data ID 1 berhasil diperbarui” yang menandakan bahwa perubahan data sudah berhasil dilakukan.

### Pengecekan Ulang

<img width="1057" height="517" alt="image" src="https://github.com/user-attachments/assets/965531cc-8cb4-417c-8cf0-92d5ff813f4e" />


Setelah memperbarui data, pilih menu 2 (Tampilkan Semua Barang) untuk mengecek hasilnya. Daftar koleksi akan menampilkan informasi terbaru termasuk perubahan pada nama, kategori, kondisi, dan kolom lainnya sehingga pengguna bisa memastikan update yang telah dilakukan sebelumnya sudah tersimpan dengan benar.

## **Validasi Input**

### Jika Input ID yang tidak terdaftar

<img width="1023" height="687" alt="image" src="https://github.com/user-attachments/assets/129d39d7-6b7d-4912-92a7-78627e0f3129" />

Apabila pengguna memasukkan sebuah ID yang tidak ada dalam koleksi, sistem akan langsung memberikan pesan peringatan berupa "ID tidak ditemukan". Pesan ini muncul untuk memberi tahu pengguna bahwa ID yang dimasukkan tidak sesuai dengan data yang tersedia di dalam tabel.

Pengguna mencoba memperbarui barang dengan ID "21", sementara koleksi hanya berisi ID dari 1 sampai 20, maka sistem menolak perintah tersebut. Dengan begitu, tidak ada risiko pengguna tanpa sengaja memperbarui atau menghapus data yang sebenarnya tidak ada.

### Jika Input huruf

<img width="1021" height="680" alt="image" src="https://github.com/user-attachments/assets/c3e9e9bb-d86a-430b-9ca2-e378fdee1def" />

Pada tahap ini, sistem dilengkapi dengan validasi agar hanya angka yang dapat diterima pada kolom ID. Jika pengguna secara tidak sengaja atau sengaja memasukkan teks berupa huruf, seperti contoh "iya", maka sistem akan langsung menolak input tersebut.

Program kemudian memberikan pesan peringatan "Harus berupa angka" untuk mengingatkan pengguna bahwa input ID hanya bisa berupa angka.

### Jika Inputan Kosong

<img width="1295" height="755" alt="image" src="https://github.com/user-attachments/assets/6c26c745-501b-47c9-8881-5758f1750edd" />

Apabila pengguna menekan Enter tanpa mengetikkan angka apapun pada kolom ID, sistem akan langsung menampilkan pesan "ID tidak ditemukan". Hal ini terjadi karena input yang kosong dianggap tidak valid oleh program.

--------------------------------------------------------------------------------------------------------------------------------------------------------------
 
# **Jika memilih opsi 4 maka akan diarahkan ke Hapus Barang**

<img width="1269" height="729" alt="image" src="https://github.com/user-attachments/assets/d80d2100-c4d4-493d-b14f-b5af4682ec76" />

Ketika pengguna memilih opsi 4 pada menu utama, sistem akan mengarahkan ke fitur Hapus Barang. Pada saat fitur ini dijalankan, program terlebih dahulu menampilkan daftar seluruh barang yang ada di koleksi AntikAesthetic. Dengan demikian, pengguna dapat melihat ID masing-masing barang sebelum menentukan data mana yang ingin dihapus.


<img width="319" height="81" alt="image" src="https://github.com/user-attachments/assets/43875892-1e22-43b7-b704-2e3e6f03f3b7" />

Setelah ID dimasukkan, sistem akan melakukan pengecekan apakah ID tersebut benar-benar ada di dalam daftar koleksi barang atau tidak. Jika ID ditemukan, sistem tidak akan langsung menghapus data barangnya, melainkan akan memberikan konfirmasi tambahan berupa pertanyaan "Yakin hapus ID... (y/n)?". Konfirmasi ini dibuat untuk menghindari kesalahan pengguna, misalnya jika tanpa sengaja salah mengetik ID.

### Jika Input "n"

<img width="312" height="128" alt="image" src="https://github.com/user-attachments/assets/f20f63cd-adfe-4293-814f-7195a45339f2" />


Apabila pengguna mengetik n, artinya proses penghapusan dibatalkan. Program akan menampilkan pesan bahwa data tidak jadi dihapus, lalu pengguna diminta menekan Enter untuk kembali ke menu utama. Dengan begitu, data tetap aman dan tidak berubah sedikit pun.

### Jika Input "y"

<img width="433" height="129" alt="image" src="https://github.com/user-attachments/assets/2b2cbd6b-7c20-47bc-9008-ac91741a885a" />


Sebaliknya, jika pengguna mengetik y, maka sistem akan benar-benar menghapus data dengan ID yang tadi dimasukkan. Setelah itu, muncul pesan bahwa data berhasil dihapus. Sama seperti sebelumnya, pengguna kemudian menekan Enter untuk kembali ke menu utama.

## **Validasi Input**

### Jika Input ID yang tidak terdaftar

<img width="373" height="110" alt="image" src="https://github.com/user-attachments/assets/0de4c638-2bb7-4415-ab85-288858d2abbc" />

Apabila pengguna memasukkan ID yang tidak ada dalam daftar koleksi, sistem akan menolak input tersebut dan menampilkan pesan:

"Data dengan ID ... tidak ditemukan."

Pesan ini berfungsi sebagai validasi untuk memberi tahu pengguna bahwa ID yang dimasukkan salah atau tidak tersedia. Dengan begitu, pengguna dapat segera memperbaikinya sebelum melanjutkan.

### Jika Input ID selain angka


<img width="407" height="140" alt="image" src="https://github.com/user-attachments/assets/3e0cab4e-187a-4b04-8df1-d67ae3adfa16" />

Jika pengguna memasukkan input bukan berupa angka, misalnya mengetik huruf seperti "iya" atau "tidak", sistem akan menolak masukan tersebut dan memberikan peringatan:

"Harus berupa angka."

Validasi ini memastikan bahwa hanya angka yang dapat diterima pada kolom ID, sehingga sistem dapat memproses perintah dengan benar. Setelah itu, pengguna perlu mengulangi input hingga sesuai dengan aturan.

--------------------------------------------------------------------------------------------------------------------------------------------------------------

# **Jika memilih opsi 5 maka akan diarahkan ke Cari Barang**

<img width="344" height="71" alt="Screenshot 2025-09-09 151206" src="https://github.com/user-attachments/assets/b4a9184a-472e-4655-a79b-e7dfdfc68fd1" />

Fitur ini dipakai untuk menemukan data dengan cepat. Cukup ketik kata kunci di kolom input, lalu sistem akan mencari yang mengandung kata tersebut pada Nama, Kategori, atau Asal. 


### Cari Berdasarkan Nama Barang

<img width="1155" height="321" alt="image" src="https://github.com/user-attachments/assets/0b2c5047-b4f0-461b-98dc-678f0d9b8d48" />

Pada contoh di atas, pengguna melakukan pencarian dengan kata kunci “Jam Saku”. Sistem menampilkan data barang yang sesuai dalam bentuk tabel lengkap, meliputi ID, nama, kategori, asal, tahun, material, kondisi, sumber, dan harga. Setelah itu, sistem juga menampilkan ringkasan yang lebih sederhana.

Nah, di bagian ringkasan inilah peran override terlihat. Method infoSingkat() yang ada pada masing-masing kelas barang dipanggil secara otomatis. Jika barang tersebut merupakan barang biasa, ringkasannya hanya menampilkan data standar seperti nama, kategori, asal, dan sumber. Namun, apabila barang berasal dari subclass seperti barangLelang atau barangWarisan, hasil ringkasannya akan menampilkan tambahan keterangan khusus, misalnya "tipe: LELANG" atau "tipe: WARISAN".

Hal ini membuat sistem lebih mudah digunakan, sebab jika pengguna ingin mengetahui mana barang warisan dan mana yang barang lelang, informasi penting sudah ditampilkan tanpa perlu melakukan pengecekan manual.

### Cari Berdasarkan Kategori

<img width="1144" height="348" alt="image" src="https://github.com/user-attachments/assets/a4bec835-f2a7-45d5-91d9-1f87291aa865" />

Pada contoh pencarian berdasarkan kategori, pengguna mengetikkan kata kunci “Patung”. Sistem kemudian menampilkan semua barang yang termasuk dalam kategori tersebut. Informasi yang ditampilkan tidak hanya berupa tabel detail seperti ID, nama, asal, tahun, material, kondisi, sumber, dan harga, tetapi juga ringkasan singkat di bagian bawahnya.

Ringkasan ini memanfaatkan fitur override pada method infoSingkat(). Artinya, apabila objek tersebut berasal dari subclass seperti barangWarisan atau barangLelang, maka hasil ringkasannya akan ditambahkan keterangan tipe khusus, misalnya “tipe: WARISAN” atau “tipe: LELANG”. Dengan begitu, pengguna dapat langsung membedakan jenis perolehan barang tanpa perlu melihat detail tabel satu per satu.

### Cari Berdsarkan Asal

<img width="1167" height="434" alt="image" src="https://github.com/user-attachments/assets/0d6161e0-2c5c-43cd-98fd-cd2b72234fa2" />

Begitu pula pada pencarian berdasarkan asal. Misalnya, pengguna mengetik kata kunci “Jawa”. Sistem akan menampilkan semua barang yang memiliki asal dari daerah Jawa. Tabel utama memberikan informasi detail, sementara ringkasan di bawah tabel tetap memanfaatkan override untuk memperjelas tipe barang.

Dengan adanya ringkasan tersebut, pengguna tidak hanya melihat data mentah, tetapi juga langsung memperoleh gambaran singkat yang lebih mudah dipahami. Misalnya, “#15 Keris Pusaka (Senjata) | asal: Jawa | sumber: Lelang | tipe: LELANG”. Informasi tambahan ini membuat sistem lebih praktis digunakan, terutama saat jumlah data yang ditampilkan cukup banyak.

## **Validasi Input**

### Input Kata Kunci yang tidak terdaftar

<img width="588" height="162" alt="image" src="https://github.com/user-attachments/assets/5ef731a9-287d-4d20-a71d-da1a0da3b06d" />

ika pengguna mengetikkan kata kunci yang tidak cocok dengan data apa pun, sistem akan menampilkan pesan seperti:

Oops.. Tidak ada hasil untuk: ...

Pesan ini berfungsi untuk memberi tahu pengguna bahwa barang dengan kata kunci tersebut tidak ada di dalam koleksi.

### Inputan Kosong

<img width="578" height="157" alt="image" src="https://github.com/user-attachments/assets/ede3fd20-64ed-47df-b22f-cde8efca027c" />

Jika kolom kata kunci dibiarkan kosong, sistem otomatis menolak input tersebut dan menampilkan peringatan:

Input tidak boleh kosong

Setelah itu, pengguna akan diminta kembali untuk memasukkan kata kunci yang valid. Dengan begitu, sistem memastikan bahwa pencarian selalu dilakukan menggunakan kata kunci yang benar.

--------------------------------------------------------------------------------------------------------------------------------------------------------------

# **Jika memilih opsi 6 maka akan diarahkan Keluar Program AntikAesthetic**

Ketika menginputkan angka 6 pada menu utama, sistem akan keluar dari program. Sebelum keluar, program akan mengonfirmasi kembali sebelum kita benar-benar keluar. Kita akan ditanya "Apakah yakin kamu ingin keluar? (y/n)".

### Jika memilih "y"

<img width="462" height="294" alt="Screenshot 2025-09-09 130258" src="https://github.com/user-attachments/assets/a97dda3e-362e-4a05-ad42-5d8d46a551bd" />

Saat pengguna memilih menu 6 lalu mengetik y pada konfirmasi, maka program akan tertutup dan menampilkan pesan “Terima kasih Telah Menggunakan Program AntikAesthetic!!”.

### Jika memilih "n"

<img width="469" height="283" alt="Screenshot 2025-09-09 130223" src="https://github.com/user-attachments/assets/7b4a8cb2-1fb8-4a97-a604-6ede66c4fb95" />

Proses keluar dibatalkan. Program akan menampilkan pesan “<< Kembali ke menu utama AntikAesthetic >>” dan pengguna akan kembali ke menu utama AntikAesthetic.

## **Validasi Input**

### Jika memilih selain "y" dan "n"

<img width="470" height="282" alt="Screenshot 2025-09-09 130125" src="https://github.com/user-attachments/assets/85249312-528a-48ab-a541-6b516fda71d6" />

Setelah pengguna memilih menu 6, sistem akan meminta konfirmasi (y/n). Jika yang diketik bukan y atau n (misalnya i), input dianggap tidak valid dan proses keluar dibatalkan. 

Program menampilkan pesan “<< Kembali ke menu utama AntikAesthetic >>” lalu meminta pengguna menekan Enter untuk kembali ke menu utama.

--------------------------------------------------------------------------------------------------------------------------------------------------------------

# **Jika user input selain opsi 1-6. Menginputkan menu menggunakan huruf dan mengosongkan inputan**

**Menginputkan Huruf**

<img width="729" height="332" alt="image" src="https://github.com/user-attachments/assets/e88a4486-3e27-4b5a-b503-c91fade6e99b" />

Apabila pengguna tidak mengetikkan angka 1–6, tetapi justru memasukkan huruf (misalnya hai atau abc), sistem akan langsung menganggap input tersebut tidak valid. Hal ini karena program hanya dirancang untuk menerima input berupa angka sesuai opsi yang tersedia pada menu utama.

Setelah mendeteksi input huruf, program akan menampilkan pesan “Pilihan tidak valid.”. Pesan ini dimaksudkan sebagai peringatan agar pengguna tahu bahwa yang dimasukkan tidak sesuai format yang benar. Setelah itu, program meminta pengguna menekan tombol Enter untuk kembali, lalu menampilkan kembali menu utama. 

Pengguna juga diarahkan untuk memperbaiki kesalahannya dan memasukkan angka yang sesuai dengan daftar pilihan menu.

**Mengosongkan Inputan**

<img width="457" height="254" alt="Screenshot 2025-09-09 125912" src="https://github.com/user-attachments/assets/67ec9884-670c-462b-8dd6-cbb210c67051" />

Jika pengguna tidak mengetikkan apa pun (input kosong) lalu langsung menekan Enter pada saat diminta memilih menu, maka sistem akan membaca input tersebut sebagai tidak valid. Dalam kondisi ini, program tidak akan mengeksekusi perintah apa pun, melainkan langsung menampilkan pesan peringatan dan membawa pengguna kembali ke menu utama. Dengan begitu, alur program tetap aman, tidak terjadi error, dan pengguna diberi kesempatan untuk memilih ulang opsi yang benar.
