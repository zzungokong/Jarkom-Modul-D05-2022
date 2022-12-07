# Jarkom-Modul-5-D03-2022

### Kelompok D03

| **No** | **Nama**                   | **NRP**    |
| ------ | -------------------------- | ---------- |
| 1      | Antonio Taifan Montana     | 5025201219 |
| 2      | Wina Tungmiharja           | 5025201242 |
| 3      | Vania Rizky Juliana Wachid | 5025201215 |

```PREFIX IP Kelompok = 192.186```  

1. Kondisi Node Awal  

 <img width="789" alt="Screenshot 2022-12-06 at 1 29 26 PM" src="https://user-images.githubusercontent.com/57696730/205837917-f033780e-8986-4aba-a2ef-970365b2480f.png">  

Perhitungan IP  

| Subnet    | Alias                  | Jumlah IP | Netmask |
| --------- | ---------------------- | --------- | ------- |
| A1        | westalis - eden - wise | 3         | 29      |
| A2        | westalis - forger      | 63        | 25      |
| A3        | westalis - strix       | 2         | 30      |
| A4        | strix - ostania        | 2         | 30      |
| A5        | ostania - blackbell    | 256       | 23      |
| A6        | ostania - briar        | 31        | 26      |
| A7        | ostania - garden - sss | 3         | 29      |
| A8        | westalis - desmond     | 701       | 22      |
| Jumlah IP |                        | 1061      | 21      |

Pohon IP  

<img width="855" alt="Screenshot 2022-12-06 at 1 32 22 PM" src="https://user-images.githubusercontent.com/57696730/205838367-16cb15de-3dda-4a1d-ab63-a18dc8650061.png">

Berikut hasil pembagian IP per node per subnet  
| Subnet | Node      | IP            | Length | Netmask         |
| ------ | --------- | ------------- | ------ | --------------- |
| A1     | westalis  | 192.186.6.65  | /29    | 255.255.255.248 |
| A1     | eden      | 192.186.6.66  | /30    | 255.255.255.249 |
| A1     | wise      | 192.186.6.67  | /31    | 255.255.255.250 |
| A2     | westalis  | 192.186.6.129 | /25    | 255.255.255.128 |
| A2     | forger    | 192.186.6.130 | /25    | 255.255.255.128 |
| A3     | westalis  | 192.186.6.81  | /30    | 255.255.255.252 |
| A3     | strix     | 192.186.6.82  | /30    | 255.255.255.252 |
| A4     | strix     | 192.186.6.85  | /30    | 255.255.255.252 |
| A4     | ostania   | 192.186.6.86  | /30    | 255.255.255.252 |
| A5     | ostania   | 192.186.4.1   | /23    | 255.255.254.0   |
| A5     | blackbell | 192.186.4.2   | /23    | 255.255.254.0   |
| A6     | ostania   | 192.186.6.1   | /26    | 255.255.255.192 |
| A6     | briar     | 192.186.6.2   | /26    | 255.255.255.192 |
| A7     | ostania   | 192.186.6.73  | /29    | 255.255.255.248 |
| A7     | garden    | 192.186.6.74  | /29    | 255.255.255.249 |
| A7     | sss       | 192.186.6.75  | /29    | 255.255.255.250 |
| A8     | westalis  | 192.186.0.1   | /22    | 255.255.252.0   |
| A8     | desmond   | 192.186.0.2   | /22    | 255.255.252.0   |

Maka didapat topologi seperti ini:  
<img width="814" alt="Screenshot 2022-12-06 at 1 47 43 PM" src="https://user-images.githubusercontent.com/57696730/205841092-835f2cf3-e150-4d9d-af97-2ec963150da8.png">  

Selanjutnya dilakukan konfigurasi per nodenya  

### Node Eden  
```
auto eth0
iface eth0 inet static
address 192.186.6.66
netmask 255.255.255.248
gateway 192.186.6.65
```  
### Node Wise  
```
auto eth0
iface eth0 inet static
address 192.186.6.67
netmask 255.255.255.248
gateway 192.186.6.65
```  
### Router Westalis  
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.186.6.81
netmask 255.255.255.252
gateway 192.186.6.82

auto eth1
iface eth1 inet static
address 192.186.0.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.186.6.129
netmask 255.255.252.128

auto eth3
iface eth3 inet static
address 192.186.6.65
netmask 255.255.255.248
```  
### Router Strix
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.186.6.85
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.186.6.82
netmask 255.255.255.252
```
### Node Garden
```
auto eth0
iface eth0 inet static
address 192.186.6.74
netmask 255.255.255.248
gateway 192.186.6.73
```  
### Node SSS
```
auto eth0
iface eth0 inet static
address 192.186.6.75
netmask 255.255.255.248
gateway 192.186.6.73
```  
### Node Ostania
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.186.6.86
netmask 255.255.255.252
gateway 192.186.6.85

auto eth1
iface eth1 inet static
address 192.186.4.1
netmask 255.255.254.0

auto eth2
iface eth2 inet static
address 192.186.6.1
netmask 255.255.255.192

auto eth3
iface eth3 inet static
address 192.186.6.73
netmask 255.255.255.248
```  
### Node Forger
```
auto eth0
iface eth0 inet static
address 192.186.6.130
netmask 255.255.255.128
gateway 192.186.6.129
```  
### Node Desmond
```
auto eth0
iface eth0 inet static
address 192.186.0.2
netmask 255.255.252.0
gateway 192.186.0.1
```  
### Node Blackbell
```
auto eth0
iface eth0 inet static
address 192.186.4.2
netmask 255.255.254.0
gateway 192.186.4.1
```  
### Node Briar
```
auto eth0
iface eth0 inet static
address 192.186.6.2
netmask 255.255.255.192
gateway 192.186.6.1
```  

# Routing Strix
Pada routing, subnet bagian bawah diatur agar melewati westalis dan subnet bagian kanan melewati ostania.
```
# kanan
route add -net 192.186.4.0 netmask 255.255.254.0 gw 192.186.6.86
route add -net 192.186.6.0 netmask 255.255.255.192 gw 192.186.6.86
route add -net 192.186.6.72 netmask 255.255.255.248 gw 192.186.6.86

# bawah
route add -net 192.186.0.0 netmask 255.255.252.0 gw 192.186.6.81
route add -net 192.186.6.128 netmask 255.255.255.128 gw 192.186.6.81
route add -net 192.186.6.64  netmask 255.255.255.248 gw 192.186.6.81
```  

# DHCP
### Instalasi ISC-DHCP-Server
Selanjutnya Wise sebagai DHCP server, install isc-dhcp-server di Wise  
```
apt-get update
apt-get install isc-dhcp-server
```  

### Konfiguraso DHCP Server
**A. Menentukan interface mana yang akan diberi layanan DHCP**  
A.1. Buka file konfigurasi interface  
edit file konfigurasi isc-dhcp-server pada /etc/default/isc-dhcp-server  

A.2. Tentukan interface  
Coba perhatikan topologi yang telah kalian buat. Contoh dari topologi yang dibuat adalah interface dari server Wise yang menuju ke switch bawah adalah eth0, maka kita akan memilih interface eth0 untuk diberikan layanan DHCP.  

**B. Melakukan konfigurasi pada isc-dhcp-server**
Ada banyak hal yang dapat dikonfigurasi, antara lain:
```
Range IP
DNS Server
Informasi Netmask
Default Gateway
dll.
```  

B.1. Buka file konfigurasi DHCP dengan perintah
Edit file konfigurasi isc-dhcp-server pada /etc/dhcp/dhcpd.conf  

B.2. Tambahkan script berikut
