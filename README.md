# labpy05
# Praktikum 5

# flowchart
![foto](https://github.com/ridhofebriann/labpy05/blob/main/flowchart.png?raw=true)

### penjelelasan flowchart

### 1. Mulai Program

  Program dimulai dan siap untuk menerima input dari pengguna.

### 2. Tampilkan Menu Utama

   Program menampilkan pilihan menu kepada pengguna:
(T)ambah
(U)bah
(H)apus
(C)ari
(L)ihat
(K)eluar

### 3. Input Pilihan Menu

Pengguna diminta untuk memasukkan pilihan menu yang diinginkan.

### 4. Pemeriksaan Pilihan

Program memeriksa pilihan yang dimasukkan oleh pengguna:

### Jika pengguna memilih 'T' (Tambah):

  1. Program meminta pengguna untuk memasukkan data mahasiswa baru:
Nama
NIM
Nilai UTS
Nilai UAS
Nilai Tugas
  2. Program menghitung nilai akhir menggunakan rumus:
Nilai Akhir = (Nilai Tugas * 30%) + (Nilai UTS * 35%) + (Nilai UAS * 35%)
  3. Data mahasiswa disimpan dalam struktur data (dictionary) dengan nama sebagai kunci dan NIM, UTS, UAS, Tugas, dan Nilai Akhir sebagai nilai.
  4.Program kembali ke langkah 2 untuk menampilkan menu utama.

### Jika pengguna memilih 'U' (Ubah):

  1.Program meminta pengguna untuk memasukkan nama mahasiswa yang ingin diubah.
  2.Program memeriksa apakah nama tersebut ada dalam data:
   
    Jika nama ditemukan:
Program meminta pengguna untuk memasukkan data baru (NIM, UTS, UAS, Tugas).
Program menghitung nilai akhir yang baru dan memperbarui data mahasiswa.
    
    Jika nama tidak ditemukan:
Program menampilkan pesan bahwa nama tidak ditemukan.
Program kembali ke langkah 2 untuk menampilkan menu utama.

### Jika pengguna memilih 'H' (Hapus):

Program meminta pengguna untuk memasukkan nama mahasiswa yang ingin dihapus.
Program memeriksa apakah nama tersebut ada dalam data:

Jika nama ditemukan:

Program menghapus data mahasiswa dari struktur data.
Program menampilkan pesan bahwa data telah dihapus.

Jika nama tidak ditemukan:

Program menampilkan pesan bahwa nama tidak ditemukan.
Program kembali ke langkah 2 untuk menampilkan menu utama.

### Jika pengguna memilih 'C' (Cari):

Program meminta pengguna untuk memasukkan nama mahasiswa yang ingin dicari.
Program memeriksa apakah nama tersebut ada dalam data:

Jika nama ditemukan:

Program menampilkan informasi lengkap tentang mahasiswa (Nama, NIM, UTS, UAS, Tugas, Nilai Akhir).

Jika nama tidak ditemukan:

Program menampilkan pesan bahwa nama tidak ditemukan.
Program kembali ke langkah 2 untuk menampilkan menu utama.

### Jika pengguna memilih 'L' (Lihat):

Program memeriksa apakah ada data mahasiswa yang tersimpan:

Jika ada data:

Program menampilkan semua data mahasiswa dalam format tabel.

Jika tidak ada data:

Program menampilkan pesan bahwa tidak ada data yang tersedia.
Program kembali ke langkah 2 untuk menampilkan menu utama.

### Jika pengguna memilih 'K' (Keluar):

Program berhenti dan keluar dari loop, mengakhiri proses.

Jika pengguna memasukkan pilihan yang tidak valid:

Program menampilkan pesan bahwa pilihan tidak tersedia dan kembali ke langkah 2 untuk menampilkan menu utama. 




### Program Data Mahasiswa

Pada praktikum 5, kita akan membuat program sederhana untuk membuat data mahasiswa menggunakan Dictionary dengan python.

#### Codingan Praktikum 5

```python
data_mahasiswa = {}

while True:
    c = input("\n(T)ambah, (U)bah, (H)apus, (C)ari, (L)ihat, (K)eluar: ")

    if c.lower() == 't':
        print("Tambah Data")
        nama = input("Nama           : ")
        nim = int(input("NIM            : "))
        uts = int(input("Nilai UTS      : "))
        uas = int(input("Nilai UAS      : "))
        tugas = int(input("Nilai Tugas    : "))
        akhir = tugas*30/100 + uts*35/100 + uas*35/100
        data_mahasiswa[nama] = nim, uts, uas, tugas, akhir

    elif c.lower() == 'u':
        print("Ubah Data")
        nama = input("Masukkan Nama  : ")
        if nama in data_mahasiswa.keys():
            nim = int(input("NIM            : "))
            uts = int(input("Nilai UTS      : "))
            uas = int(input("Nilai UAS      : "))
            tugas = int(input("Nilai Tugas    : "))
            akhir = tugas * 30 / 100 + uts * 35 / 100 + uas * 35 / 100
            data_mahasiswa[nama] = nim, uts, uas, tugas, akhir
        else:
            print("Nama {0} tidak ditemukan".format(nama))

    elif c.lower() == 'h':
        print("Hapus Data")
        nama = input("Masukkan Nama  : ")
        if nama in data_mahasiswa.keys():
            del data_mahasiswa[nama]
        else:
            print("Nama {0} Tidak Ditemukan".format(nama))

    elif c.lower() == 'c':
        print("Cari Data")
        nama = input("Masukkan Nama : ")
        if nama in data_mahasiswa.keys():
            print("="*73)
            print("|                             Daftar Mahasiswa                          |")
            print("="*73)
            print("| Nama            |       NIM       |  UTS  |  UAS  |  Tugas  |  Akhir  |")
            print("="*73)
            print("| {0:15s} | {1:15d} | {2:5d} | {3:5d} | {4:7d} | {5:7.2f} |"
                  .format(nama, nim, uts, uas, tugas, akhir))
            print("="*73)
        else:
            print("Nama {0} Tidak Ditemukan".format(nama))

    elif c.lower() == 'l':
        if data_mahasiswa.items():
            print("="*78)
            print("|                               Daftar Mahasiswa                             |")
            print("="*78)
            print("|No. | Nama            |       NIM       |  UTS  |  UAS  |  Tugas  |  Akhir  |")
            print("="*78)
            i = 0
            for z in data_mahasiswa.items():
                i += 1
                print("| {no:2d} | {0:15s} | {1:15d} | {2:5d} | {3:5d} | {4:7d} | {5:7.2f} |"
                      .format(z[0][:13], z[1][0], z[1][1], z[1][2], z[1][3], z[1][4], no=i))
            print("=" * 78)
        else:
            print("="*78)
            print("|                               Daftar Mahasiswa                             |")
            print("="*78)
            print("|No. | Nama            |       NIM       |  UTS  |  UAS  |  Tugas  |  Akhir  |")
            print("="*78)
            print("|                                TIDAK ADA DATA                              |")
            print("="*78)

    elif c. lower() == 'k':
        break

    else:
        print("Pilih menu yang tersedia")
```

#### Penjelasan :

1.) Pertama kita membuat sebuah dictionary kosong yang nantinya akan diinputkan data ketika program dijalankan.
```python
data_mahasiswa = {}
```

2.) Lalu kita membuat kondisi perulangan dan sebuah keterangan untuk pilihan menu yang akan menjalankan program.
```python
while True:
    c = input("\n(T)ambah, (U)bah, (H)apus, (C)ari, (L)ihat, (K)eluar: ")
```

3.) Membuat syntax untuk menambahkan data.
```python
    if c.lower() == 't':
        print("Tambah Data")
        nama = input("Nama           : ")
        nim = int(input("NIM            : "))
        uts = int(input("Nilai UTS      : "))
        uas = int(input("Nilai UAS      : "))
        tugas = int(input("Nilai Tugas    : "))
        akhir = tugas*30/100 + uts*35/100 + uas*35/100
        data_mahasiswa[nama] = nim, uts, uas, tugas, akhir
```
Disini apabila kita menginputkan 't' maka kita akan diminta untuk menginputkan beberapa data. Data yang kita inputkan akan masuk ke dictionary 'data_mahasiswa' yang telah dibuat tadi dengan data 'nama' sebagai keys dan sisanya sebagai valuesnya.

4.) Membuat syntax untuk mengubah data.
```python
    elif c.lower() == 'u':
        print("Ubah Data")
        nama = input("Masukkan Nama  : ")
        if nama in data_mahasiswa.keys():
            nim = int(input("NIM            : "))
            uts = int(input("Nilai UTS      : "))
            uas = int(input("Nilai UAS      : "))
            tugas = int(input("Nilai Tugas    : "))
            akhir = tugas * 30 / 100 + uts * 35 / 100 + uas * 35 / 100
            data_mahasiswa[nama] = nim, uts, uas, tugas, akhir
        else:
            print("Nama {0} tidak ditemukan".format(nama))
```
Apabila kita menginput 'u' maka akan ada keterangan untuk mengubah data dan kita akan diminta untuk menginputkan nama yang mau diubah datanya, apabila nama tidak ada maka outputnya "Nama {} tidak ditemukan". Dimana `{}` adalah nama/data yang mau kita ubah.

5.) Membuat syntax untuk menghapus data.
```python
    elif c.lower() == 'h':
        print("Hapus Data")
        nama = input("Masukkan Nama  : ")
        if nama in data_mahasiswa.keys():
            del data_mahasiswa[nama]
        else:
            print("Nama {0} Tidak Ditemukan".format(nama))
```
Apabila kita menginput 'h' maka kita akan diminta menginput nama yang akan dihapus. Jika nama ada di dalam dictionary, maka system akan menghapus keys/nama tersebut beserta valuesnya pada statement `del data_mahasiswa[nama]`.

6.) Membuat syntax untuk mencari data.
```python
    elif c.lower() == 'c':
        print("Cari Data")
        nama = input("Masukkan Nama : ")
        if nama in data_mahasiswa.keys():
            print("="*73)
            print("|                             Daftar Mahasiswa                          |")
            print("="*73)
            print("| Nama            |       NIM       |  UTS  |  UAS  |  Tugas  |  Akhir  |")
            print("="*73)
            print("| {0:15s} | {1:15d} | {2:5d} | {3:5d} | {4:7d} | {5:7.2f} |"
                  .format(nama, nim, uts, uas, tugas, akhir))
            print("="*73)
        else:
            print("Nama {0} Tidak Ditemukan".format(nama))
```
Apabila kita menginputkan 'c' maka kita akan diminta untuk memasukkan nama yang akan dicari. Apabila nama yang dicari ada di dalam dictionary maka outputnya akan menampilkan data dari nama tersebut.

7.) Membuat syntax untuk melihat atau menampilkan data.
```python
    elif c.lower() == 'l':
        if data_mahasiswa.items():
            print("="*78)
            print("|                               Daftar Mahasiswa                             |")
            print("="*78)
            print("|No. | Nama            |       NIM       |  UTS  |  UAS  |  Tugas  |  Akhir  |")
            print("="*78)
            i = 0
            for z in data_mahasiswa.items():
                i += 1
                print("| {no:2d} | {0:15s} | {1:15d} | {2:5d} | {3:5d} | {4:7d} | {5:7.2f} |"
                      .format(z[0][:13], z[1][0], z[1][1], z[1][2], z[1][3], z[1][4], no=i))
            print("=" * 78)
        else:
            print("="*78)
            print("|                               Daftar Mahasiswa                             |")
            print("="*78)
            print("|No. | Nama            |       NIM       |  UTS  |  UAS  |  Tugas  |  Akhir  |")
            print("="*78)
            print("|                                TIDAK ADA DATA                              |")
            print("="*78)
```
Apabila kita menginput 'l' maka sistem akan menampilkan data - data yang sudah kita masukkan. Jika kita belum memasukkan data maka outputnya menjadi "TIDAK ADA DATA".

8.) Membuat syntax untuk menghentikan perulangan.
```python
    elif c. lower() == 'k':
        break
```
Apabila kita menginput 'k' maka program akan langsung berhenti.

9.) Membuat syntax untuk apabila memilih pilihan yang tidak ada di menu.
```python
    else:
        print("Pilih menu yang tersedia")
```
Jika kita menginputkan selain yang ada pada menu (t, u, h, c, l, k) maka kita akan diminta untuk memilih menu yang tersedia.

### Tampilan Program Saat Dijalankan

##### Tambah Data + Lihat Data
![tambah data1]()

##### Ubah Data + Lihat Data
![ubah data1]()

##### Cari Data
![cari data]()

##### Hapus Data + Lihat Data
![hapus data]()

##### Keluar
![keluar]()
