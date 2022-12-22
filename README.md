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
Sebelum melakukan instalasi, jalankan  
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.186.0.0/16
```  
pada router Strix
Dan untuk setiap node, jalankan  
```
echo nameserver 192.168.122.1 > /etc/resolv.conf
```  
### Instalasi ISC-DHCP-Server
Selanjutnya Wise sebagai DHCP server, install isc-dhcp-server di Wise  
```
apt-get update
apt-get install isc-dhcp-server
```  

### Konfiguraso DHCP Server
**A. Menentukan interface mana yang akan diberi layanan DHCP**  
A.1. Buka file konfigurasi interface  
edit file konfigurasi isc-dhcp-server pada ```/etc/default/isc-dhcp-server```    

A.2. Tentukan interface  
Coba perhatikan topologi yang telah kalian buat. Contoh dari topologi yang dibuat adalah interface dari server Wise yang menuju ke switch bawah adalah eth0, maka kita akan memilih interface eth0 untuk diberikan layanan DHCP.  
<img width="704" alt="Screenshot 2022-12-07 at 11 46 50 AM" src="https://user-images.githubusercontent.com/57696730/206090816-6b9faf54-a413-49a0-90fe-16887e0f39f9.png">


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
Edit file konfigurasi isc-dhcp-server pada ```/etc/dhcp/dhcpd.conf```  

B.2. Tambahkan script berikut  
```
subnet 192.186.6.64 netmask 255.255.255.0 {
        option routers 192.186.6.65;
}
# Blackbell A5
subnet 192.186.4.0 netmask 255.255.254.0 {
	range 192.186.4.2 192.186.5.254;
	option routers 192.186.4.1;
	option broadcast-address 192.186.5.255;
	option domain-name-servers 192.186.6.66;
	default-lease-time 600;
	max-lease-time 7200;
}

# Briar A6
subnet 192.186.6.0 netmask 255.255.255.192 {
	range 192.186.6.2 192.186.6.62;
	option routers 192.186.6.1;
	option broadcast-address 192.186.6.63;
	option domain-name-servers 192.186.6.66;
	default-lease-time 600;
	max-lease-time 7200;
}

# Desmond A8
subnet 192.186.0.0 netmask 255.255.252.0 {
	range 192.186.0.2 192.186.3.254;
	option routers 192.186.0.1;
	option broadcast-address 192.186.3.255;
	option domain-name-servers 192.186.6.66;
	default-lease-time 600;
	max-lease-time 7200;
}

# Forger A2
subnet 192.186.6.128 netmask 255.255.255.128 {
	range 192.186.6.130 192.186.6.254;
	option routers 192.186.6.129;
	option broadcast-address 192.186.6.255;
	option domain-name-servers 192.186.6.66;
	default-lease-time 600;
	max-lease-time 7200;
 
}
```
***Lalu Westalis sebagai DHCP Relay***  
```
apt-get update
apt-get install isc-dhcp-relay -y
```  
disini kita akan melakukan forward DHCP server dari ```IP 192.186.6.67``` karena WISE memiliki IP address tersebut dan sesuai topologi, kita juga akan melakukan forward pada eth1 eth2 eth3  
lalu kita akan memulai relay dengan command  
```
service isc-dhcp-relay start
```  
Eden sebagai DNS Server:
```
echo "nameserver 192.168.122.1" > /etc/resolv.conf
apt update
apt install bind9 -y
echo 'options {
	directory "/var/cache/bind" ;
	forwarders {
		192.168.122.1;
	allow-query { any; ) ;
	auth-nxdomain no;	
	listen-on-v6 { any; ) ;
> /etc/bind/named.conf.options
service bind9 restart
```
Ostania dan Westalis sebagai DHCP Relay:
```
apt-get update
apt-get install isc-dhcp-relay

echo ;
SERV'RS-"192.186.7.131"
ethi eth2 eth3"
OPTIONS=""
'>/etc/defautt/isc-dhcp- relay
service isc-dhcp-relay restart
```
Garden dan SSS sebagai Web Server:
```
apt-get update
apt-get install apache2 -Y
service apache2 start
echo "$HOSTNAME" > /var/www/htmt/index.htmtl

```

1. Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Strix menggunakan iptables, tetapi Loid tidak ingin menggunakan MASQUERADE.
Script pada Strix:
```
IPETH0="$(ip -br a | grep eth0 | awk '{print $NF}' | cut -d'/' -f1)"
iptables -t nat 0A POSTROUTING -o eth 0 -j SNAT --to-source "$IPETH0" -s 192.186.0.0/21
```
2. Kalian diminta untuk melakukan drop semua TCP dan UDP dari luar Topologi kalian pada server yang merupakan DHCP Server demi menjaga keamanan.
Script pada Strix:
```
iptables -A FORWARD -d 192.186.6.121 -i eth0 -p tcp -j DROP
iptables -A FORWARD -d 192.186.6.121 -i eth0 -p udp -j DROP
```
3. Loid meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 2 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.
Script pada Eden dan Wise:
```
iptables -A INPUT -m state --state ESTABLISHED.RELATED -j ACCEPT
iptables -A INPUT -p icmp -m connlimit --connlimit-above 2 --connlimit-mask 0 -j DROP
```

4. Akses menuju Web Server hanya diperbolehkan disaat jam kerja yaitu Senin sampai Jumat pada pukul 07.00 - 16.00.
Script pada Garden:
```
iptables -A INPUT -s 192.186.7.131/25 -m time --timestart 07:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
iptables -A INPUT -s 192.186.7.131/25 -j REJECT
```
Script pada SSS:
```
iptables -A INPUT -s 192.186.7.132/25 -m time --timestart 07:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
iptables -A INPUT -s 192.186.7.132/25 -j REJECT
```
5. Karena kita memiliki 2 Web Server, Loid ingin Ostania diatur sehingga setiap request dari client yang mengakses Garden dengan port 80 akan didistribusikan secara bergantian pada SSS dan Garden secara berurutan dan request dari client yang mengakses SSS dengan port 443 akan didistribusikan secara bergantian pada Garden dan SSS secara berurutan.
Script pada Garden:
```
iptables -A prerouting -t -nat -p tcp --dport80 -d 192.186.7.131 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.186.7.132

iptables -A prerouting -t -nat -p tcp --dport80 -d 192.186.7.131 -j DNAT --to-destination 192.186.7.132

iptables -A INPUT -s 192.186.7.131/25 -j REJECT
```

Script pada SSS:
```
iptables -A prerouting -t -nat -p tcp --dport80 -d 192.186.7.132 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.186.7.131

iptables -A prerouting -t -nat -p tcp --dport80 -d 192.186.7.132 -j DNAT --to-destination 192.186.7.131
```

6. Karena Loid ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level.
Script pada Strix:
```
iptables -N LOGGING
iptables -A INPUT -j LOGGING
iptables -A OUTPUT -j LOGGING
iptables -A LOGGING -m limit --limit 2/min -j LOG --log-prefix "IPTables-Dropped: " --log-level 4
iptables -A LOGGING -j DROP

echo '
kern.warning/var/log/iptables.log
' >> /etc/rsyslog.conf
/etc/init.d/rsyslog restart
```





