# Jarkom-Modul-3-2025-K42
| Nama | NRP |
| :-------- | :------- | 
| S. Farhan Baig | 5027241097| 
| Dimas Satya Andhika | 5027241032 |

# Soal 1
<img width="2710" height="1620" alt="image" src="https://github.com/user-attachments/assets/9c7e3f19-d04d-4741-9393-76710c4bbc0a" />

### Durin
```
auto eth0
iface eth0 inet dhcp
    up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
    up echo 1 > /proc/sys/net/ipv4/ip_forward

auto eth1
iface eth1 inet static
    address 10.232.1.1
    netmask 255.255.255.0

auto eth2
iface eth2 inet static
    address 10.232.2.1
    netmask 255.255.255.0

auto eth3
iface eth3 inet static
    address 10.232.3.1
    netmask 255.255.255.0

auto eth4
iface eth4 inet static
    address 10.232.4.1
    netmask 255.255.255.0

auto eth5
iface eth5 inet static
    address 10.232.5.1
    netmask 255.255.255.0
```
### Elendil
```
auto eth0
iface eth0 inet static
    address 10.232.1.2
    netmask 255.255.255.0
    gateway 10.232.1.1
```
### Isildur
```
auto eth0
iface eth0 inet static
 address 10.232.1.3
 netmask 255.255.255.0
 gateway 10.232.1.1
```
### Anarion
```
auto eth0
iface eth0 inet static
 address 10.232.1.4
 netmask 255.255.255.0
 gateway 10.232.1.1
```
### Miriel
```
auto eth0
iface eth0 inet static
 address 10.232.1.5
 netmask 255.255.255.0
 gateway 10.232.1.1
```
### Elros
```
auto eth0
iface eth0 inet static
 address 10.232.1.100
 netmask 255.255.255.0
 gateway 10.232.1.1
```
### Amandil
```
auto eth0
iface eth0 inet dhcp
```
### Gilgalad
```
auto eth0
iface eth0 inet dhcp
```
### Khamul
```
auto eth0
iface eth0 inet dhcp
```
### Erendis
```
auto eth0
iface eth0 inet static
 address 10.232.3.2
 netmask 255.255.255.0
 gateway 10.232.3.1
```
### Amdir
```
auto eth0
iface eth0 inet static
 address 10.232.3.3
 netmask 255.255.255.0
 gateway 10.232.3.1
```
### Aldarion
```
auto eth0
iface eth0 inet static
 address 10.232.4.2
 netmask 255.255.255.0
 gateway 10.232.4.1
```
### Palantir
```
auto eth0
iface eth0 inet static
 address 10.232.4.3
 netmask 255.255.255.0
 gateway 10.232.4.1
```
### Narvi
```
auto eth0
iface eth0 inet static
 address 10.232.4.4
 netmask 255.255.255.0
 gateway 10.232.4.1
```
### Minastir
```
auto eth0
iface eth0 inet static
 address 10.232.5.2
 netmask 255.255.255.0
 gateway 10.232.5.1
```
### Pharazon
```
auto eth0
iface eth0 inet static
 address 10.232.2.2
 netmask 255.255.255.0
 gateway 10.232.2.1
```
### Celebrimbor
```
auto eth0
iface eth0 inet static
 address 10.232.2.3
 netmask 255.255.255.0
 gateway 10.232.2.1
```
### Oropher
```
auto eth0
iface eth0 inet static
 address 10.232.2.4
 netmask 255.255.255.0
 gateway 10.232.2.1
```
### Celeborn
```
auto eth0
iface eth0 inet static
 address 10.232.2.5
 netmask 255.255.255.0
 gateway 10.232.2.1
```
### Galadriel
```
auto eth0
iface eth0 inet static
 address 10.232.2.6
 netmask 255.255.255.0
 gateway 10.232.2.1
```
Berikut konfigurasi sementasa pada setiap node agar dapat berkomunikasi dengan Valinor/Internet

# Soal 2
### Aldarion
<img width="980" height="88" alt="image" src="https://github.com/user-attachments/assets/ed7b22f2-07cb-42db-8519-76dfec1ff85a" />

Masuk ke node Aldarion dan jalankan perintah berikut
```
echo "nameserver 192.168.122.1" > /etc/resolv.conf
apt update
apt install isc-dhcp-server -y
```
setelah itu buka `/etc/default/isc-dhcp-server` dan isi dengan
```
INTERFACESv4="eth0"
```
lanjutkan dengan mengedit config berikut `/etc/dhcp/dhcpd.conf`
```
default-lease-time 600;
max-lease-time 3600;
authoritative;

# LAN1 - Manusia
subnet 10.232.1.0 netmask 255.255.255.0 {
    range 10.232.1.6 10.232.1.34;
    range 10.232.1.68 10.232.1.94;
    option routers 10.232.1.1;
    option broadcast-address 10.232.1.255;
    option domain-name-servers 192.168.122.1;
    default-lease-time 1800;
}

# LAN2 - Elf
subnet 10.232.2.0 netmask 255.255.255.0 {
    range 10.232.2.35 10.232.2.67;
    range 10.232.2.96 10.232.2.121;
    option routers 10.232.2.1;
    option broadcast-address 10.232.2.255;
    option domain-name-servers 192.168.122.1;
    default-lease-time 600;
}

# LAN3 - Server zone (relay)
subnet 10.232.3.0 netmask 255.255.255.0 {
    option routers 10.232.3.1;
}

# LAN4 - Database (Aldarion, Palantir, Narvi)
subnet 10.232.4.0 netmask 255.255.255.0 {
    option routers 10.232.4.1;
}

# LAN5 - Proxy & LB
subnet 10.232.5.0 netmask 255.255.255.0 {
    option routers 10.232.5.1;
}

# Khamul
host khamul {
    hardware ethernet 02:42:22:01:5f:00; 
    fixed-address 10.232.3.95;
}
```
lalu restart server
```
service isc-dhcp-server restart
service isc-dhcp-server status
```
### Durin
<img width="2306" height="180" alt="image" src="https://github.com/user-attachments/assets/7b1111ee-db47-4482-a031-f0a22cb7e057" />

Lakukan beberapa instalasi sebelum melakukan konfigurasi pada router, instalasi seperti berikut:
```
apt update
apt install isc-dhcp-relay -y
```
setelah itu edit config `/etc/default/isc-dhcp-relay` dan isi dengan:
```
SERVERS="10.232.4.2"
INTERFACES="eth1 eth2 eth3 eth4 eth5"
OPTIONS=""
```
lalu jalankan
```
/usr/sbin/dhcrelay -q -i eth1 -i eth2 -i eth3 -i eth4 -i eth5 10.232.4.2 &
ps aux | grep dhcrelay
```
### Khamul
<img width="2188" height="180" alt="image" src="https://github.com/user-attachments/assets/f2738d20-9268-4dde-9ae6-d56115936be2" />

Ubah config pada node khamul menjadi
```
auto eth0
iface eth0 inet dhcp
    hwaddress ether 02:42:22:01:5f:00
```

Lalu jalankan perintah di bawah
```
echo "nameserver 192.168.122.1" > /etc/resolv.conf
apt update
apt install isc-dhcp-client -y
ip addr flush dev eth0
dhclient eth0
ip a
```
### Amandil
<img width="2190" height="134" alt="image" src="https://github.com/user-attachments/assets/650609d2-d3a5-43fd-affa-e6192157ab39" />

```
ip addr add 10.232.1.10/24 dev eth0
ip route add default via 10.232.1.1
echo "nameserver 192.168.122.1" > /etc/resolv.conf
apt update
apt install isc-dhcp-client -y
ip addr flush dev eth0
dhclient eth0
ip a
```
Berikan IP sementara untuk instalasi lalu ganti IP menggunakan dari DHCP server

### Gilgalad
<img width="2198" height="138" alt="image" src="https://github.com/user-attachments/assets/90b9037b-eca7-4406-9f58-496244fa59f6" />

```
ip addr add 10.232.2.10/24 dev eth0
ip route add default via 10.232.2.1
echo "nameserver 192.168.122.1" > /etc/resolv.conf
apt update
apt install isc-dhcp-client -y
ip addr flush dev eth0
dhclient eth0
ip a
```
Berikan IP sementara untuk instalasi lalu ganti IP menggunakan dari DHCP server

# Soal 3
### Minastir
Jalankan perintah di bawah di Minastir
```
echo "nameserver 192.168.122.1" > /etc/resolv.conf
apt update
apt install bind9 -y
```
dan buka `/etc/bind/named.conf.options` lalu isi dengan
```
options {
    directory "/var/cache/bind";

    // DNS luar (forwarder)
    forwarders {
        192.168.122.1;   
        8.8.8.8;         
    };

    allow-query { any; }; 
    recursion yes;           
    dnssec-validation no;
    listen-on-v6 { any; };
```
lalu jalankan dengan perintah
```
/usr/sbin/named -c /etc/bind/named.conf -g &
```

### Khamul (Bebas)
Jalankan perintah di bawah untuk pengujian
```
echo "nameserver 10.232.5.2" > /etc/resolv.conf
ping -c 3 google.com
dig @10.232.5.2 google.com
```
