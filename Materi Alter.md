# Menambahkan Colom
Strutur awal pada tabel mobil:
![image](before.png)

## Struktur
```mysql
ALTER TABLE nama_tabel ADD nama_kolom varchar(10) AFTER nama_kolom;

```
## Contoh Query
```mysql

 ALTER TABLE mobil ADD batas_peminjam varchar(10) AFTER peminjam;

```
 
`After` Opsional untuk digunakan, jika tidak menggunakan klausa ini maka secara default kolom yang dibuat akan berada di akhir. Jika kolom ingin ditaruh pada awal kolom maka gunakan klausa `First`. dan hasilnya sebagai berikut:

Hasil
![image](Materi%20alter/asetbs/after.png)

___
## Anasisis
1. **ALTER TABLE mobil**: Ini adalah perintah untuk mengubah struktur tabel yang sudah ada, yang dalam hal ini disebut "mobil". Perintah ALTER TABLE digunakan untuk menambahkan, menghapus, atau memodifikasi kolom atau indeks dalam tabel yang sudah ada.
    
2. **ADD batas_peminjam varchar(10)**: Bagian ini menentukan perubahan yang akan dilakukan pada tabel. Di sini, kita menambahkan kolom baru bernama "batas_peminjam" ke tabel "mobil". Tipe data kolom baru adalah VARCHAR, yang berarti itu akan menyimpan string teks, dengan panjang maksimum 10 karakter. Ini ditentukan dengan "(10)" setelah VARCHAR.
    
3. **AFTER peminjam**: Bagian ini menentukan posisi di mana kolom baru akan ditambahkan dalam tabel. Dalam hal ini, kolom baru "batas_peminjam" akan ditambahkan setelah kolom "peminjam". Ini menentukan urutan kolom dalam tabel.
## Kesimpulan
- Tabel "mobil" akan mengalami perubahan struktur.
- Sebuah kolom baru dengan nama "batas_peminjam" akan ditambahkan ke tabel "mobil".
- Kolom baru tersebut akan memiliki tipe data VARCHAR dengan panjang maksimum 10 karakter.
- Kolom baru ini akan ditempatkan setelah kolom "peminjam" dalam struktur tabel.
  
## Tambahan
Contoh Query
```mysql

update mobil set batas_peminjam="2024-04-24" where peminjam is not null;

```

  

Hasil
![image](+.png)

  

# Menambahkan Nama Colum
## Struktur
```mysql
ALTER TABLE nama_tabel CHANGE nama_kolom deadline varchar(10);
```
## Contoh Query
```mysql

ALTER TABLE mobil CHANGE batas_peminjam deadline varchar(10);

```

  
## Hasil
![image](rename.png)

## Analisis
1. **ALTER TABLE mobil**: Seperti sebelumnya, ini adalah perintah untuk mengubah struktur tabel yang sudah ada, dalam hal ini, tabel "mobil".
    
2. **CHANGE batas_peminjam deadline varchar(10)**: Bagian ini menentukan perubahan yang akan dilakukan pada kolom. Secara khusus, ini mengubah nama kolom "batas_peminjam" menjadi "deadline". Tipe data kolom tetap VARCHAR dengan panjang maksimum 10 karakter. Jadi, perintah ini juga mengubah nama kolom serta menetapkan tipe data dan panjangnya.
## Kesimpulan
- Tabel "mobil" akan mengalami perubahan pada kolom tertentu.
- Kolom yang semula bernama "batas_peminjam" akan diubah namanya menjadi "deadline".
- Tipe data kolom tetap VARCHAR dengan panjang maksimum 10 karakter.
  
# Mengubah Tipe Data

## Struktur
```mysql
ALTER TABLE nama_tabel MODIFY nama_kolom DATE;

```
## Contoh Query
```mysql

ALTER TABLE mobil MODIFY deadline DATE;

```

  

## Hasil
![image](tipedata.png)

## Analisis
1. **ALTER TABLE mobil**: Ini adalah perintah untuk mengubah struktur tabel yang sudah ada, dalam hal ini, tabel "mobil".
    
2. **MODIFY deadline DATE**: Bagian ini menentukan perubahan yang akan dilakukan pada kolom "deadline". Secara khusus, ini mengubah tipe data kolom "deadline" dari VARCHAR menjadi DATE. Dengan mengubah tipe data menjadi DATE, kolom "deadline" sekarang akan dapat menyimpan nilai-nilai tanggal.
## Kesimpulan
- Tabel "mobil" akan mengalami perubahan pada definisi kolom tertentu.
- Kolom "deadline" dalam tabel "mobil" akan mengalami perubahan tipe data dari VARCHAR menjadi DATE.
- Setelah perubahan ini, kolom "deadline" akan dapat menyimpan nilai-nilai tanggal.
# Menambahkan Constraint

## Struktur
```mysql
ALTER TABLE nama_tabel

    -> ALTER nama_kolom SET DEFAULT 'nilai_kolom';
```
## Contoh Query
```mysql

ALTER TABLE mobil

    -> ALTER deadline SET DEFAULT 'Ready';

```

  

## Hasil
![image](ready.png)

## Analisi
1. **ALTER TABLE mobil**: Seperti sebelumnya, ini adalah perintah untuk mengubah struktur tabel yang sudah ada, dalam hal ini, tabel "mobil".
    
2. **ALTER deadline SET DEFAULT 'Ready'**: Bagian ini menentukan perubahan yang akan dilakukan pada kolom "deadline". Secara khusus, ini menetapkan nilai default 'Ready' untuk kolom "deadline". Ini berarti jika sebuah baris baru ditambahkan ke tabel dan kolom "deadline" tidak diberikan nilai, maka nilainya akan secara otomatis diatur sebagai 'Ready'.
## Kesimpulan
- Tabel "mobil" akan mengalami perubahan pada definisi kolom "deadline".
- Perintah tersebut menetapkan nilai default 'Ready' untuk kolom "deadline".
- Ini berarti jika sebuah baris baru ditambahkan ke tabel dan kolom "deadline" tidak diberikan nilai, maka nilai default 'Ready' akan diberikan secara otomatis.
## Tambahan

### Contoh Query
```mysql

INSERT INTO mobil

    -> (id_pelanggan,no_plat,no_mesin,warna,pemilik,peminjam,harga_rental)

    -> values (7,"B 4532 H","RPL2122","Hitam","Valen",NULL,100000);

```

  

### Hasil
![image](++.png)

# Menghapus Constraint

## Struktur
```mysql
ALTER TABLE nama_tabel
ALTER nama_kolom DROP DEFAULT;
```
## Contoh Query
```MYSQL
ALTER TABLE daftar_mobil
ALTER deadline DROP DEFAULT;
```

## Hasil
![[h.hps-constrain.jpeg]]

## Analisis
1. **ALTER TABLE daftar_mobil**: Ini adalah perintah untuk mengubah struktur tabel yang sudah ada, dalam hal ini, tabel "daftar_mobil".
    
2. **ALTER deadline DROP DEFAULT**: Bagian ini menentukan perubahan yang akan dilakukan pada kolom "deadline". Secara khusus, ini menghapus nilai default yang mungkin telah ditetapkan sebelumnya untuk kolom "deadline". Setelah perintah ini dieksekusi, kolom "deadline" tidak akan lagi memiliki nilai default.
## Kesimpulan
- Tabel "daftar_mobil" akan mengalami perubahan pada definisi kolom "deadline".
- Nilai default yang telah ditetapkan untuk kolom "deadline" akan dihapus.
- Setelah perintah ini, jika sebuah baris baru ditambahkan ke tabel tanpa nilai untuk kolom "deadline", kolom tersebut tidak akan diisi dengan nilai default dan akan dibiarkan kosong atau NULL jika tidak diberikan nilai lain.

