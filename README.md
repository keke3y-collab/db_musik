# Database: db\_musik 🎵

Dokumentasi ini berisi langkah-langkah pembuatan database, tabel, manipulasi data, serta pengujian berbagai jenis **Join** pada MariaDB.


## 🗂️ Struktur Database

Database ini bernama `db_musik` dan terdiri dari dua tabel utama yang saling berelasi:

### 1\. Tabel: `tb_artis`

Digunakan untuk menyimpan data musisi atau band.

  * **id\_artis**: Primary Key, Integer, Auto Increment.
  * **nama\_artis**: Varchar(50).

### 2\. Tabel: `tb_lagu`

Digunakan untuk menyimpan data judul lagu yang terhubung ke tabel artis.

  * **id\_lagu**: Primary Key, Integer, Auto Increment.
  * **judul\_lagu**: Varchar(100).
  * **id\_artis**: Foreign Key (Referensi ke `tb_artis`).

   
## 📑 Data yang Tersedia

Daftar artis dan lagu yang telah diinputkan meliputi:

  * **Kekal** (Nadin Amizah)
  * **Membasuh & Evakuasi** (Hindia)
  * **Berita Kehilangan** (Feast)
  * **Kalibata, 2012** (Perunggu)
  * **Seberapa Pantas** (Sheila On 7)
  * **LANY** (Terdaftar sebagai artis, namun belum memiliki lagu)

## 🔍 Pengujian Query
### 1\. Inner Join

Menampilkan lagu yang memiliki pasangan artis yang tepat.

```sql
SELECT tb_artis.nama_artis, tb_lagu.judul_lagu 
FROM tb_artis 
INNER JOIN tb_lagu ON tb_artis.id_artis = tb_lagu.id_artis;
```
Hasil Query:
| nama_artis | judul_lagu |
| :--- | :--- |
| Nadin Amizah | Kekal |
| Hindia | Membasuh |
| Feast | Berita Kehilangan |
| Perunggu | Kalibata, 2012 |
| Sheila On 7 | Seberapa Pantas |
| Hindia | Evakuasi |

**Catatan:** Artis **LANY** tidak muncul di sini karena Inner Join hanya mengambil data yang memiliki pasangan di kedua tabel.

### 2\. Left Join

Menampilkan semua artis, termasuk yang belum memiliki lagu (seperti **LANY**).

```sql
SELECT tb_artis.nama_artis, tb_lagu.judul_lagu 
FROM tb_artis 
LEFT JOIN tb_lagu ON tb_artis.id_artis = tb_lagu.id_artis;
```
Hasil Query:
| nama_artis | judul_lagu |
| :--- | :--- |
| Nadin Amizah | Kekal |
| Hindia | Membasuh |
| Hindia | Evakuasi |
| Feast | Berita Kehilangan |
| Perunggu | Kalibata, 2012 |
| Sheila On 7 | Seberapa Pantas |
| LANY | NULL |
### 3\. Right Join

Menampilkan semua data dari tabel kanan dan mencocokkannya ke tabel kiri.

```sql
SELECT tb_lagu.judul_lagu, tb_artis.nama_artis 
FROM tb_lagu 
RIGHT JOIN tb_artis ON tb_lagu.id_artis = tb_artis.id_artis;
```
Hasil Query:
| judul_lagu | nama_artis |
| :--- | :--- |
| Kekal | Nadin Amizah |
| Membasuh | Hindia |
| Evakuasi | Hindia |
| Berita Kehilangan | Feast |
| Kalibata, 2012 | Perunggu |
| Seberapa Pantas | Sheila On 7 |
| NULL | LANY |
