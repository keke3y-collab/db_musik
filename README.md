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

**🔍 Pengujian Query**
🤝 1. Inner Join
Menampilkan lagu yang memiliki pasangan artis yang tepat.
