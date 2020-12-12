# Jarkom_Modul4_Lapres_C01
Praktikum Modul 4 Jaringan Komputer 2020

## NAMA ANGGOTA KELOMPOK :

**1. Devi Hainun Pasya (05111840000014)**

**2. Kevin Christian Hadinata (05111840000066)**

## PEMBAHASAN SOAL

Membuat Subnetting dan Routing dari topologi berikut :

![]()

## **VLSM (Variable Length Subnet Masking)**

**Langkah 1** - Menentukan jumlah dan memberi nama subnet yang terdapat dalam topologi.

![]()

**Langkah 2** - Menentukan jumlah alamat IP yang dibutuhkan oleh tiap-tiap subnet dan melakukan labelling netmask berdasarkan jumlah IP yang dibutuhkan dengan mengacu pada tabel subnet.

![]()

Berdasarkan total IP dan netmask yang dibutuhkan, maka dapat digunakan netmask **/19** untuk memberikan pengalamatan padaa subnet.

**Langkah 3** - Subnet besar yang dibentuk memiliki NID **192.168.0.0** serta netmask /19. Selanjutnya hitung pembagian IP berdasarkan NID dan netmask tersebut menggunakan pohon. Kemudian lakukan subnetting dengan pohon yang telah dibuat untuk membagi IP sesuai dengan kebutuhan masing-masing subnet yang ada.

![]()

**Langkah 4** - Dari pohon tersebut, akan didapatkan pembagian IP sebagai berikut :

![]()

### **Praktik penerapan metode VLSM diatas menggunakan Cisco Packet Tracer (CPT).**

1. Membuat Topologi

Penambahan elemen-elemen dalam topologi dilakukan sesuai dengan tata cara yang terdapat di modul Subnetting dan Routing. Dengan hasil sebagai berikut :

![]()

2. Subnetting 

Dilakukan pengaturan IP untuk masing-masing interface yang ada pada setiap device sesuai dengan pembagian subnet pada pohon VLSM yang telah dibuat. Interface diatur dengan meng-klik device, lalu memilih menu **Config > INTERFACE > "nama interface"**. Karena terdapat banyak device, maka hanya akan ditunjukkan beberapa.

***Interface Router - Router***

Mengambil contoh pada subnet **A10** yaitu antar router SURABAYA dan PASURUAN. Atur IP pada interface SURABAYA mengarah ke PASURUAN dengan menambahkan NID +1 dari subnet **A10** yaitu **192.168.0.5**. Sebagai berikut :

![]()

Kemudian atur juga IP pada interface PASURUAN yang mengarah ke SURABAYA dengan menambahkan NID +2 dari subnet **A10** yaitu **192.168.0.6**. Sebagai berikut :

![]()

Langkah ini diterapkan untuk mengatur alamat IP setiap interface router ke router dalam device yang terdapat dalam topologi. Dimana dalam topologi kami yaitu subnet **A9, A10, A14, A15**.

***Interface Router - Client***

Mengambil contoh pada subnet **A6** yaitu antar router PROBOLINGGO dan client BONDOWOSO. Atur IP pada interface PROBOLINGGO mengarah ke BONDOWOSO dengan menambahkan NID +1 dari subnet **A6** yaitu **192.168.0.129**. Sebagai berikut :

![]()

Kemudian atur juga IP pada interface BONDOWOSO yang mengarah ke PROBOLINGGO pada menu **Desktop > IP Configuration** dengan menambahkan NID +2 dari subnet **A6** yaitu **192.168.0.130**. Sebagai berikut :

![]()

Langkah ini diterapkan untuk mengatur alamat IP setiap interface router ke router dalam device yang terdapat dalam topologi. Dimana dalam topologi kami yaitu subnet **A2, A3, A4, A5, A6, A7, A8, A12, dan A13**.

***Interface Router - Server***

Konfigurasi kurang lebih sama dengan Router - Client tapi IP yang yang ditambahkan adalah IP DMZ masing-masing kelompok yang dibagi 2, karena terdapat 2 server dalam topologi, yaitu MALANG dan MOJOKERTO. 

IP DMZ kelompok C01 adalah **10.151.77.16**, maka untuk server MOJOKERTO dihasilkan range IP antara **10.151.77.16 - 10.151.77.19** sedangkan untuk server MALANG dihasilkan range IP antara **10.151.77.20 - 10.151.77.23**.

Mengambil contoh pada subnet **A1** yaitu antar server MOJOKERTO dan router SURABAYA. Atur IP pada interface SURABAYA mengarah ke MOJOKERTO dengan menambahkan IP DMZ +2 yaitu **10.151.77.18**. Sebagai berikut :

![]()

Kemudian atur juga IP pada interface MOJOKERTO yang mengarah ke SURABAYA dengan menambahkan NID +1 dari subnet **A10** yaitu **10.151.77.17**. Sebagai berikut :

![]()

3. Routing

Berikut adalah tabel perhitungan routing :

![]()

Pada CPT, routing dilakukan dengan memilih menu **Config > ROUTING > Static** dalam device router. Untuk menambahkan sebuah Static Routes, yang perlu diisi antara lain :

<li> Network : Network ID yang akan dihubungkan.
<li> Mask : Netmask dari suatu subnet.
<li> Next Hop : IP yang dituju ketika ingin menuju subnet poin 1 (Gateway).

***Routing SURABAYA***

SURABAYA merupakan router utama, perlu dikenalkan dengan subnet bukan tetangganya, antara lain A9, A6, A4, A3, A8, A7, A5, A15, A13, A12, A11 (Server Malang). Maka ditambahkan routing sebagai berikut :

![]()

Dalam Static Routing juga dibutuhkan ***default routing*** agar router dapat mengirimkan paket sesuai dengan tujuan. Default routing diterapkan pada router yang berada dibawah router utama (SURABAYA).

***Routing PASURUAN***

Router PASURUAN perlu dikenalkan dengan subnet yang bukan tetangganya, yaitu default, A6, dan A7. Maka ditambahkan routing sebagai berikut :

![]()

***Routing PROBOLINGGO***

Router PROBOLINGGO berada di ujung (tidak ada router lagi di cabangnya), maka hanya perlu dikenalkan dengan default. Maka ditambahkan routing sebagai berikut :

![]()

***Routing BATU***

Router BATU perlu dikenalkan dengan subnet yang bukan tetangganya, yaitu default, A3, A12, A13, dan A11 (Server Malang). Maka ditambahkan routing sebagai berikut :

![]()

***Routing MADIUN***

Router MADIUN berada di ujung (tidak ada router lagi di cabangnya), maka hanya perlu dikenalkan dengan default. Maka ditambahkan routing sebagai berikut :

![]()

***Routing KEDIRI***

Router KEDIRI perlu dikenalkan dengan subnet yang bukan tetangganya, yaitu default dan A12. Maka ditambahkan routing sebagai berikut :

![]()

***Routing BLITAR***

Router BLITAR berada di ujung (tidak ada router lagi di cabangnya), maka hanya perlu dikenalkan dengan default. Maka ditambahkan routing sebagai berikut :

![]()

### HASIL :

Berikut beberapa hasil testing subnetting dan routing dengan menggunakan tombol dengan ikon surat pada toolbar CPT :

![]()

## **CIDR (Classless Inter-Domain Routing)**

*****Langkah 1*** - Melakukan Pengelompokkan**

Melalui topologi yang telah disediakan di soal, kita dapat melakukan pengelompokkan pada *subnet*, dimulai dari *subnet* yang berada paling jauh dari *router* utama (**SURABAYA**).

![]()

Langkah ini juga menghasilkan pohon CIDR sebagai berikut:

![]()

*****Langkah 2*** - Melakukan Konfigurasi pada *Interfaces***

Melalui ```etc/network/interfaces``` di tiap UML, kita akan menghubungkan tiap-tiap *subnet* sesuai dengan hubungannya dengan *subnet* lain. <br/>
Misal, Surabaya akan terhubung dengan:
<li> Cloud di eth0,
<li> SAMPANG di eth1 (melalui switch 1),
<li> PASURUAN di eth2 (melalui switch baru),
<li> BATU di eth3 (melalui switch baru), dan
<li> MOJOKERTO di eth4 (melalui switch 13).

Untuk memperoleh *address* (sekaligus *gateway*) tiap jalur, dapat mengambil referensi dari pengelompokkan dan pohon CIDR yang telah dibuat pada langkah sebelumnya, serta tabel *subnet mask*.

*****Langkah 3*** - Melakukan Routing**

Menggunakan *command* ``route add -net <NID subnet> netmask <netmask> gw <IP gateway>``, kita dapat menambahkan *route* pada setiap UML. Dalam kasus ini, kita hanya perlu menambahkan *routing* pada:
<li> SURABAYA => PASURUAN, BATU, DMZ MALANG
<li> BATU => KEDIRI, MALANG (Lewat Kediri), MADIUN
<li> PASURUAN => PROBOLINGGO
<li> KEDIRI => BLITAR

Dengan *setting* sebagai berikut:
#### SURABAYA
```
route add -net 192.168.128.0 netmask 255.255.192.0 gw 192.168.192.2
route add -net 192.168.0.0 netmask 255.255.224.0 gw 192.168.32.2
route add -net 10.151.77.20 netmask 255.255.255.252 gw 192.168.32.2
```

#### PASURUAN
```
route add -net 192.168.128.0 netmask 255.255.240.0 gw 192.168.144.2
```

#### BATU
```
route add -net 192.168.0.0 netmask 255.255.248.0 gw 192.168.8.2
route add -net 10.151.77.92 netmask 255.255.255.252 gw 192.168.8.2
route add -net 192.168.16.0 netmask 255.255.252.0 gw 192.168.18.3
```
#### KEDIRI
```
route add -net 192.168.0.0 netmask 255.255.248.0 gw 192.168.4.3
```
