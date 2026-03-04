**🎵 Database: db_musik 🎧**

Proyek ini berisi dokumentasi langkah-langkah pembuatan database, tabel, manipulasi data, serta pengujian berbagai jenis Join pada MariaDB.

**🗂️ Struktur Database**

Database ini bernama db_musik. Terdiri dari dua tabel utama yang saling berelasi:
1. Tabel: **tb_artis** Digunakan untuk menyimpan data musisi atau band.
   + id_artis: Primary Key, Integer, Auto Increment.
   + nama_artis: Varchar(50).
2. Tabel: **tb_lagu** Digunakan untuk menyimpan data judul lagu yang terhubung ke tabel artis.
   + id_lagu: Primary Key, Integer, Auto Increment.
   + judul_lagu: Varchar(100).id_artis: Foreign Key (Referensi ke tb_artis).
   
**📑 Data yang Tersedia**
Daftar artis dan lagu yang telah diinputkan meliputi:
+ Kekal (Nadin Amizah) 
+ Membasuh & Evakuasi (Hindia) 
+ Berita Kehilangan (Feast) 
+ Kalibata, 2012 (Perunggu) 
+ Seberapa Pantas (Sheila On 7) 

## 🔍 Pengujian Query
### 1\. Inner Join

Menampilkan lagu yang memiliki pasangan artis yang tepat.

```sql
SELECT tb_artis.nama_artis, tb_lagu.judul_lagu 
FROM tb_artis 
INNER JOIN tb_lagu ON tb_artis.id_artis = tb_lagu.id_artis;
```

### 2\. Left Join

Menampilkan semua artis, termasuk yang belum memiliki lagu (seperti **LANY**).

```sql
SELECT tb_artis.nama_artis, tb_lagu.judul_lagu 
FROM tb_artis 
LEFT JOIN tb_lagu ON tb_artis.id_artis = tb_lagu.id_artis;
```

### 3\. Right Join

Menampilkan semua data dari tabel kanan dan mencocokkannya ke tabel kiri.

```sql
SELECT tb_lagu.judul_lagu, tb_artis.nama_artis 
FROM tb_lagu 
RIGHT JOIN tb_artis ON tb_lagu.id_artis = tb_artis.id_artis;
```
