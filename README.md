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
### Khamul
<img width="2188" height="180" alt="image" src="https://github.com/user-attachments/assets/f2738d20-9268-4dde-9ae6-d56115936be2" />


### Amandil
<img width="2190" height="134" alt="image" src="https://github.com/user-attachments/assets/650609d2-d3a5-43fd-affa-e6192157ab39" />


### Gilgalad
<img width="2198" height="138" alt="image" src="https://github.com/user-attachments/assets/90b9037b-eca7-4406-9f58-496244fa59f6" />

