# Jarkom_Modul4_Lapres_C01
Praktikum Modul 4 Jaringan Komputer 2020

## NAMA ANGGOTA KELOMPOK :

**1. Devi Hainun Pasya (05111840000014)**

**2. Kevin Christian Hadinata (05111840000066)**

## PEMBAHASAN SOAL

Membuat Subnetting dan Routing dari topologi berikut :

![]()

### **VLSM (Variable Length Subnet Masking)**

**Langkah 1** - Menentukan jumlah dan memberi nama subnet yang terdapat dalam topologi.

![]()

**Langkah 2** - Menentukan jumlah alamat IP yang dibutuhkan oleh tiap-tiap subnet dan melakukan labelling netmask berdasarkan jumlah IP yang dibutuhkan dengan mengacu pada tabel subnet.

![]()

Berdasarkan total IP dan netmask yang dibutuhkan, maka dapat digunakan netmask **/19** untuk memberikan pengalamatan padaa subnet.

**Langkah 3** - Subnet besar yang dibentuk memiliki NID **192.168.0.0** serta netmask /19. Selanjutnya hitung pembagian IP berdasarkan NID dan netmask tersebut menggunakan pohon. Kemudian lakukan subnetting dengan pohon yang telah dibuat untuk membagi IP sesuai dengan kebutuhan masing-masing subnet yang ada.

![]()

**Langkah 4** - Dari pohon tersebut, akan didapatkan pembagian IP sebagai berikut :

![]()

**Praktik penerapan metode VLSM diatas menggunakan Cisco Packet Tracer (CPT).**

1. Membuat Topologi

Penambahan elemen-elemen dalam topologi dilakukan sesuai dengan tata cara yang terdapat di modul Subnetting dan Routing. Dengan hasil sebagai berikut :

![]()

2. Subnetting 

Dilakukan pengaturan IP untuk masing-masing interface yang ada pada setiap device sesuai dengan pembagian subnet pada pohon VLSM yang telah dibuat. Interface diatur dengan meng-klik device, lalu memilih menu **Config > INTERFACE > "nama interface"**. Karena terdapat banyak device, maka hanya akan ditunjukkan beberapa.

*Interface Router ke Router*

Mengambil contoh pada subnet **A10** yaitu antar router SURABAYA dan PASURUAN. Atur IP pada interface SURABAYA mengarah ke PASURUAN dengan menambahkan NID +1 dari subnet **A10** yaitu **192.168.0.5**. Sebagai berikut :

![]()

Kemudian atur juga IP pada interface PASURUAN yang mengarah ke SURABAYA dengan menambahkan NID +2 dari subnet **A10** yaitu **192.168.0.6**. Sebagai berikut :

![]()

Langkah ini diterapkan untuk mengatur alamat IP setiap interface router ke router dalam device yang terdapat dalam topologi. Dimana dalam topologi kami yaitu subnet **A9, A10, A14, A15**.

*Interface Router ke Client*

Mengambil contoh pada subnet **A6** yaitu antar router PROBOLINGGO dan client BONDOWOSO. Atur IP pada interface PROBOLINGGO mengarah ke BONDOWOSO dengan menambahkan NID +1 dari subnet **A6** yaitu **192.168.0.129**. Sebagai berikut :

![]()

Kemudian atur juga IP pada interface BONDOWOSO yang mengarah ke PROBOLINGGO pada menu **Desktop > IP Configuration** dengan menambahkan NID +2 dari subnet **A6** yaitu **192.168.0.130**. Sebagai berikut :

![]()

Langkah ini diterapkan untuk mengatur alamat IP setiap interface router ke router dalam device yang terdapat dalam topologi. Dimana dalam topologi kami yaitu subnet **A2, A3, A4, A5, A6, A7, A8, A12, dan A13**.

*Interface Router ke Server*

Konfigurasi kurang lebih sama dengan Router - Client tapi IP yang yang ditambahkan adalah IP DMZ masing-masing kelompok yang dibagi 2, karena terdapat 2 server dalam topologi, yaitu MALANG dan MOJOKERTO. 

IP DMZ kelompok C01 adalah **10.151.77.16**, maka untuk server MOJOKERTO dihasilkan range IP antara **10.151.77.16 - 10.151.77.19** sedangkan untuk server malang dihasilkan range IP antara **10.151.77.20 - 10.151.77.23**.

Mengambil contoh pada subnet **A1** yaitu antar server MOJOKERTO dan router SURABAYA. Atur IP pada interface MOJOKERTO mengarah ke SURABAYA dengan menambahkan IP DMZ +1 yaitu **10.151.77.17**. Sebagai berikut :

![]()
