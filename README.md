# Tugas Praktikum { Pertemuan ke 7 } <img src=https://qph.fs.quoracdn.net/main-qimg-648763cc041459725b62108f4fdf5b91 width="110px" >


|*Nama|NIM|Kelas|Matkul*|
|----|---|-----|------|
|DELFYNO DWI PRASTYO|312310480|TI.23.A5|Basis Data|

# Soal Latihan Praktikum

## Data Model Mapping


Mahasiswa (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds)
Dosen (kd_ds, nama)
Matakuliah (kd_mk, nama, sks)
JadwalMengajar (kd_ds, kd_mk, hari, jam, ruang)
KRSMahasiswa (nim, kd_mk, kd_ds, semester, nilai)

- Buat DDL Script berdasarkan skema ERD tersebut diatas. 
- Jalankan script DDL tersebut pada DBMS MySQL.

*Langkah-langkahnya :*

*1. Buat dulu script untuk table Mahasiswa :*


create table Mahasiswa (
    nim varchar(10) PRIMARY KEY,
    nama varchar(25) NOT NULL,
    jenis_kelamin ENUM('Laki-Laki', 'Perempuan'),
    tgl_lahir DATE,
    jalan varchar(15) NOT NULL,
    kota varchar(15) NOT NULL,
    kodepos varchar(5) NOT NULL,
    no_hp varchar(15) NOT NULL,
    kd_ds varchar(10) NOT NULL,
    FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds)
    );


![Screenshot 2024-04-29 090802](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/b318e8a1-ba54-4365-87e4-073f4b6f4a11)



*Tampilkan hasil table :*

desc Mahasiswa;

![Screenshot 2024-04-29 091544](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/085d13c1-3982-4af8-a022-3299834add40)


*2. Buat script untuk table Dosen :*

create table Dosen (
    kd_ds varchar(10) PRIMARY KEY,
    nama varchar(35) NOT NULL
    );


![ss per 7,,,,18](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/9bef5b67-9439-40a7-a173-90c4f03441d0)


*Tampilkan tabel :*

desc Dosen;

![Screenshot 2024-04-29 092035](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/9c239115-5773-477b-a295-d9ea59eabb42)


*3. Buat script untuk Mata kuliah :*

create table Matakuliah (
    kd_mk varchar(10) PRIMARY KEY,
    nama varchar(30) NOT NULL,
    sks INT NOT NULL
    );


![Screenshot 2024-04-29 092105](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/6e8072a1-dfe6-437a-8628-4facfcbd7b4e)


*Tampilkan table :*

desc Matakuliah;

![ss per 7,,,,21](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/e9db91bb-0035-41b6-85d9-7f3d6dc36e76)


*4. Buat script untuk jadwal mengajar :*

create table JadwalMengajar (
    kd_ds varchar(10) NOT NULL,
    kd_mk varchar(10) NOT NULL,
    hari ENUM('Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu', 'Minggu') NOT NULL,
    jam TIME NOT NULL,
    ruang varchar(555) NOT NULL,
    PRIMARY KEY (kd_ds, kd_mk, hari, jam),
    FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds),
    FOREIGN KEY (kd_mk) REFERENCES Matakuliah(kd_mk)
    ); 


![HH](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/319a2830-ae78-4380-9d86-ca6388e1dd3f)

*Tampilkan table :*

desc JadwalMengajar;

![HH2](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/0262d0ec-aefb-43ae-b7f5-62f483052c36)


*5. Buat script untuk KRSMahasiswa :*

CREATE TABLE KRSMahasiswa (
    nim varchar(10) NOT NULL,
    kd_mk varchar(10) NOT NULL,
    kd_ds varchar(10) NOT NULL,
    semester varchar(10) NOT NULL,
    nilai FLOAT NOT NULL,
    PRIMARY KEY (nim, kd_mk),
    FOREIGN KEY (nim) REFERENCES Mahasiswa(nim),
    FOREIGN KEY (kd_mk) REFERENCES Matakuliah(kd_mk),
    FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds)
    );


![ss per 7,,,,24](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/f449fd3d-0f70-47d5-894e-92a8322ca590)



*Tampilkan table :*

desc KRSMahasiswa;

![ss per 7,,,,2](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/cf38bc27-97dc-4357-94d1-f60cd301a799)


# Soal Latihan Praktikum

Berdasarkan table Mahasiswa pada praktikum sebelumnya: (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds)

**Isi data pada table tersebut sebanyak minimal 5 record data. Tampilkan semua isi/record tabel!**

- Ubah data tanggal lahir mahasiswa yang bernama Ari menjadi: 1979-08-31!

- Tampilkan satu baris / record data yang telah diubah tadi yaitu record dengan nama Ari saja!

- Hapus Mahasiswa yang bernama Dina!

- Tampilkan record atau data yang tanggal kelahirannya lebih dari atau sama dengan 1996-1-2!

- Tampilkan semua Mahasiswa yang berasal dari Bekasi dan berjenis kelamin perempuan!

- Tampilkan semua Mahasiswa yang berasal dari Bekasi dengan kelamin laki-laki atau Mahasiswa yang berumur lebih dari 22 tahun dengan kelamin wanita!

- Tampilkan data nama dan alamat mahasiswa saja dari tabel tersebut

- Tampilkan data mahasiswa terurut berdasarkan nama.

*1. Mengisi tabel dengan minimal 5 record data :*

insert into mahasiswa (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds) values 
-> (11223344,"ari santoso","Laki-laki","1998-10-12","","Bekasi","","",""), 
-> (11223345,"ario talib","Laki-laki","1999-11-16","","Cikarang","","",""), 
-> (11223346,"dina marlina","Perempuan","1997-12-01","","Karawang","","",""), 
-> (11223347,"lisa ayu","perempuan","1996-01-02","","Bekasi","","",""), 
-> (11223348,"tiara wahidah","perempuan","1980-02-05","","Bekasi","","",""), 
-> (11223349,"anton sinaga","laki-laki","1988-03-10","","Cikarang","","","");


![YY](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/b5ce54ae-5bd3-45f5-9a7b-04eb4069b856)


*2. Menampilkan semua isi/record pada tabel bisa menggunakan kode berikut :*

select*from mahasiswa;

![YY2](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/ae1bb566-b0e2-4149-836a-34c53368cc6c)


*3. Mengubah data tanggal lahir mahasiswa yang bernama Ari menjadi : 1979-08-31 menggunakan kode berikut :*

update mahasiswa set tgl_lahir='1979-08-31' where nim=11223344;

![YY2](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/ed810cd6-38a4-4d7a-bd5b-c387d2dac113)


*4. Menampilkan satu baris / record data yang telah diubah tadi yaitu record dengan nama Ari saja dengan cara sebagai berikut :*

select*from mahasiswa where nim=11223344;

![JJ](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/73d48846-b28f-43f6-81c7-f6172b503098)


*5. Menghapus Mahasiswa yang bernama Dina dengan cara sebagai berikut:*

delete from mahasiswa where nim=11223346;

![Screenshot 2024-04-29 091318](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/e587c259-6c4e-4c17-9d73-6bbce8eed6dc)


*6. Menampilkan record atau data yang tanggal kelahirannya lebih dari atau sama dengan 1996-1-2 dengan cara sebagai berikut :*

select*from mahasiswa where tgl_lahir<='1996-1-2';

![KK](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/1db670bd-d302-43c0-b944-6638b9022fb1)

*7. Menampilkan semua Mahasiswa yang berasal dari Bekasi dan berjenis kelamin perempuan dengan cara sebagai berikut :*

select*from Mahasiswa where kota='bekasi' and jenis_kelamin='Perempuan';

![KK](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/c74997b0-8662-43a5-8068-8fc4c34e7ab4)

*8. Menampilkan semua Mahasiswa yang berasal dari Bekasi dengan kelamin laki-laki atau Mahasiswa yang berumur lebih dari 22 tahun dengan kelamin wanita dengan cara sebagai berikut :*

select * from mahasiswa where kota='Bekasi' and jenis_kelamin='Laki-laki' 
or tgl_lahir<='2002-4-22' 
and jenis_kelamin='Perempuan';


![NNN](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/13ead60a-32f5-4241-9bc5-4f68f48f9b30)


*9. Menampilkan data nama dan jalan mahasiswa saja dari tabel tersebut dengan cara sebagai berikut :*

select nama, jalan from mahasiswa;

![Screenshot 2024-04-29 091511](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/3b83fdec-590b-44e0-8c13-658835452b9f)


*10. Menampilkan data mahasiswa terurut berdasarkan nama dengan cara sebagai berikut :*

select*from mahasiswa -> order by nama asc;

![Screenshot 2024-04-29 091544](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/14f5d5d7-3e06-4e75-bd16-26f334064a74)


# Evaluasi dan Pertanyaan

**Tulis semua perintah-perintah SQL percobaan di atas beserta outputnya!**

*1. Menambah data :*

INSERT INTO <table> (field1, ..., fieldn) VALUE (value1, ..., valuen)

Contoh :

INSERT INTO biodata (nim, nama, alamat) VALUE ('1234','Uyun','Bekasi');

![Screenshot 2024-04-29 091724](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/c66f8c6e-631e-490e-95af-0356dd2454f7)


*2. Menampilkan data :*

SELECT * FROM <table> SELECT [field1, ..., fieldn] FROM <table>

Contoh :

SELECT*FROM biodata;

![ss per 7,,,16](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/d0227fdf-ec13-4452-804e-ebb24e9a7568)


*3. Mengubah data :*

UPDATE <table> SET field1=val1, ..., fieldn=valn WHERE <kondisi>;

Contoh :

UPDATE biodata SET nama='Nurul', alamat='Setu' WHERE nim='1234';

![ss per 7,,,16](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/ee347fa7-6b8b-4a37-af42-15f3ab9509ed)


*4. Menghapus data :*

DELETE FROM <table> WHERE <kondisi>

Contoh :

DELETE FROM biodata WHERE nim=‘12334’

![ss per 7,,,,17](https://github.com/SamuelTindaon/tugas-pertemuan-7/assets/147571483/68a61f1e-b0c6-4a6e-8a5f-8e057a8d70db)


**Apa bedanya penggunaan BETWEEN dan penggunaan operator >= dan <= ?**

- (misal: tgl_lahir BETWEEN '1990-10-10' AND '1992-10-11')

- (misal: tgl_lahir >= '1990-10-10' AND tgl_lahir <= '1992-10-11')

*Jawaban nya :*

Operator between ini untuk menangani operasi “jangkauan” sedangkan operator >= dan <= termasuk pada operator relasional. Operator yang digunakan yntuk perbandingan antara dua buah nilai. Jenis dari operator ini adalah: = , >, <, >=, <=, <>

**Berikan kesimpulan anda!**

Data Manipulation Language (DML) adalah bahasa pemrograman yang digunakan untuk mengakses, memanipulasi, dan mengelola data dalam sebuah database. DML memungkinkan pengguna untuk melakukan operasi seperti penyisipan data baru, pembaruan data yang sudah ada, penghapusan data, dan kueri data untuk pengambilan informasi yang diperlukan.

Dalam DML, pengguna dapat menggunakan perintah SQL (Structured Query Language) untuk mengakses data. SQL adalah bahasa standar untuk mengakses dan mengelola data dalam database relasional. Perintah SQL yang digunakan dalam DML termasuk menambah, mengubah, menghapus, dan menampilkan data seperti yang telah dipraktekan diatas.

**Buat laporan praktikum yang berisi, langkah-langkah praktikum beserta screenshot yang sudah dilakukan dalam bentuk dokumen.**

<img src=https://pngimg.com/uploads/google_drive/google_drive_PNG9.png width="110px" >

- [Link Laporan Praktikum](https://docs.google.com/document/d/1ZAfeS9WCGe560KWWInXV93w66mofY1fy/edit?usp=sharing&ouid=117024232096925929007&rtpof=true&sd=true)

## Finish....
