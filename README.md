# ujian-akhir-semester-2A-bisnis-digital

Program yang digunakan dalam "SISTEM TOKO SENDAL ONLINE CITRA" ini menjalankan simulasi dasar sebuah toko online.

1.Melihat-lihat sendal apa saja yang dijual (beserta harganya dan berapa stoknya).

2.Memasukkan sendal yang kamu suka ke keranjang belanja.

3.Melihat kembali isi keranjang belanja kamu (sendal apa saja, berapa jumlahnya, dan berapa total harganya).

4.Melakukan pembayaran alias checkout.

5.Keluar dari toko kalau sudah selesai belanja.

adapun cara kerjanya :

1. yang pertama di sini ada menu-menu sendalnya beserta harga dan stok tersebut :

"Sandal Jepit Klasik": {"harga": 25000, "stok": 20},

"Sandal Gunung Adventurer": {"harga": 80000, "stok": 12},

"Sandal Kulit Santai": {"harga": 150000, "stok": 8},

"Sandal Slop Modern": {"harga": 60000, "stok": 15}

2. jika kamu tertarik dan suka kamu bisa menambahkan nya ke dalam keranjang

Pertama, program akan menanyakan sendal apa yang mau kamu beli dan berapa jumlahnya
 Lalu, program akan cek:
 
 "Ada sendal itu nggak di toko kita?" Kalau nggak ada, dia bilang "sendal tidak ditemukan".
 
 "Cukup nggak stoknya?" Kalau kamu minta 5 sendal, tapi stok cuma ada 3, dia akan bilang "stok tidak mencukupi".
 
"Kamu masukkin angka yang benar nggak?" Kalau kamu malah ngetik "lima" bukan "5", dia akan protes.

 Kalau semuanya aman, sendal itu akan ditambahkan ke keranjangmu, dan jumlah stok di gudang kita akan otomatis berkurang.
 
3. lihat_keranjang: Cek Isi Keranjangmu

Fitur ini akan menampilkan semua sendal yang sudah kamu masukkan ke keranjang, beserta jumlahnya dan total harganya. 

Kalau keranjangmu masih kosong, dia akan bilang "Keranjang Anda masih kosong."


4. checkout : Bayar Belanjaanmu

Kalau kamu sudah puas dengan isi keranjangmu dan siap bayar: Program akan menampilkan lagi ringkasan belanjaanmu (total harganya).

Lalu dia akan tanya, "Yakin mau bayar?"

Kalau kamu jawab "ya", dia akan bilang "Pembayaran berhasil!" dan mengosongkan keranjangmu, seolah-olah sendalnya sudah dikirim.
Kalau kamu jawab "tidak", proses pembayaran akan dibatalkan.


Pada intinya, program ini mensimulasikan alur belanja online yang sangat sederhana: mulai dari melihat barang, memasukkannya ke keranjang, hingga proses pembayaran. 


 **struktur data** utama yang digunakan dalam program toko sendal online ini. Dalam program ini, ada dua "tempat penyimpanan" informasi utama, yaitu `produk` dan `keranjang`. Keduanya menggunakan tipe data dictionary (kamus) dalam Python.

1. `produk`: Gudang Inventaris Toko

`produk` adalah dictionary utama yang berfungsi sebagai *basis data inventaris* atau *daftar stok barang* di toko kita. 
 Dictionary itu ibarat kamus sungguhan. Setiap kata (disebut *key* atau kunci) punya artinya sendiri (disebut *value* atau nilai). Nah, di `produk` ini:

Key-nya adalah Nama Produk (string) : Ini adalah nama sendal yang unik, seperti "Sandal Jepit Klasik", "Sandal Gunung    Adventurer", dll. Kita pakai nama ini untuk mencari detail sendal yang bersangkutan.

Value-nya adalah Dictionary Nested (Dictionary di dalam Dictionary): Ini adalah detail lengkap dari sendal tersebut. Jadi, di dalam setiap nama sendal, ada "sub-kamus" lagi yang berisi informasi spesifik tentang sendal itu. Sub-kamus ini punya dua item:

          `'harga'`: Menunjukkan harga sendal 
          
          `'stok'`: Menunjukkan jumlah stok sendal yang tersedia
          
    Ini contoh cara `produk` menyimpan datanya:

    ```python
    
    produk = {
    
        "Sandal Jepit Klasik": {"harga": 25000, "stok": 20},
        
        "Sandal Gunung Adventurer": {"harga": 80000, "stok": 12},
        
        # ... dan seterusnya untuk sendal lain
        
    }
   
Kenapa pakai struktur ini?

Cepat Mencari Informasi : Dengan `nama_produk` sebagai key, kita bisa dengan cepat mencari harga atau stok sendal tertentu tanpa harus memeriksa seluruh daftar.

Fleksibel : Mudah untuk menambah, menghapus, atau mengubah detail produk di masa mendatang.

Terorganisir: Informasi tentang setiap produk dikelompokkan dengan rapi dalam satu entri.

-----

2. `keranjang`: Keranjang Belanja Pelanggan

`keranjang` adalah dictionary yang berfungsi sebagai keranjang belanja virtual untuk pelanggan. Ini menyimpan semua item yang telah dipilih atau "dimasukkan" oleh pembeli.

    Sama seperti `produk`, `keranjang` juga dictionary:

Key-nya adalah Nama Produk (string): Sama seperti di `produk`, ini merujuk ke nama sendal yang telah dimasukkan ke keranjang.
Value-nya adalah Jumlah Kuantitas (integer): Ini adalah berapa banyak sendal dengan nama tersebut yang telah ditambahkan ke keranjang oleh pembeli.

 Ini contoh cara `keranjang` menyimpan datanya jika seseorang membeli 2 "Sandal Jepit Klasik" dan 1 "Sandal Slop Modern":

    ```python
    
    keranjang = {
    
        "Sandal Jepit Klasik": 2,
        
        "Sandal Slop Modern": 1
        
        # Jika keranjang kosong, isinya akan {0}
    }
    
Kenapa pakai struktur ini?

Mudah Melacak Item : Kita bisa langsung melihat produk apa saja yang ada di keranjang dan berapa jumlahnya.

Mudah Menambahkan/Mengurangi : Ketika pembeli menambah jumlah produk yang sama, kita tinggal memperbarui nilai (jumlah kuantitas) dari key produk tersebut.

Dinamis: Keranjang akan bertambah atau berkurang isinya sesuai pilihan pembeli.

Singkatnya, kedua dictionary ini adalah inti dari sistem penyimpanan data program. produk mencatat semua yang kita jual, dan keranjang mencatat apa saja yang sedang dibeli oleh satu pelanggan. Karena keduanya adalah dictionary, program bisa dengan sangat efisien mencari, menambah, dan mengubah informasi tentang sendal dan belanjaan.
