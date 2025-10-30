# Jarkom-Modul-3-2025-K-42
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

