# tugas1_KomdatJarkom
# Topologi
![](assets/VLSM.png)

# Subneting
## 2. Kebutuhan Jaringan (Perhitungan yang Benar)

Tabel berikut menguraikan kebutuhan host untuk setiap subnet dan menentukan prefix (Netmask) yang paling efisien. Kebutuhan 6 host, misalnya, membutuhkan 8 IP (6 host + 2 NID/Broadcast), yang pas dengan blok `/29`.

| Ruang / Kebutuhan | Kebutuhan Host | Total IP (Host + 2) | Ukuran Blok (2^n) | Prefix Efisien (32 - n) | Host Usable |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Sekretariat | 380 | 382 | 512 | **/23** | 510 |
| Bidang Kurikulum | 220 | 222 | 256 | **/24** | 254 |
| Bidang Guru & Tendik | 95 | 97 | 128 | **/25** | 126 |
| Bidang Sarana Prasarana | 45 | 47 | 64 | **/26** | 62 |
| Bidang Pengawas Sekolah | 18 | 20 | 32 | **/27** | 30 |
| Server & Admin | 6 | 8 | 8 | **/28** | 14 |
| Router Interlink | 6 | 8 | 8 | **/29** | 2 |
| Tunnel / VPN | 2 | 4 | 4 | **/30** | 2 |

---
# VSLM
![](assets/vslm.png)
![](assets/VLSM.png)
### Tabel Alokasi VLSM (Metode Pohon / Tree)

| Subnet / Departemen | NID | Range Block | Netmask | Broadcast | Host Usable | Rentang IP yang Dapat Dipakai |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Bidang Guru & Tendik | `10.116.0.128` | `10.116.0.128 - 10.116.0.255` | `255.255.255.128 (/25)` | `10.116.0.255` | 126 | `10.116.0.129 - 10.116.0.254` |
| Bidang Kurikulum | `10.116.1.0` | `10.116.1.0 - 10.116.1.255` | `255.255.255.0 (/24)` | `10.116.1.255` | 254 | `10.116.1.1 - 10.116.1.254` |
| Bidang Sarana Prasarana | `10.116.0.64` | `10.116.0.64 - 10.116.0.127` | `255.255.255.192 (/26)` | `10.116.0.127` | 62 | `10.116.0.65 - 10.116.0.126` |
| Bidang Pengawas Sekolah | `10.116.0.32` | `10.116.0.32 - 10.116.0.63` | `255.255.255.224 (/27)` | `10.116.0.63` | 30 | `10.116.0.33 - 10.116.0.62` |
| Server & Admin | `10.116.0.8` | `10.116.0.8 - 10.116.0.15` | `255.255.255.248 (/29)` | `10.116.0.15` | 6 | `10.116.0.9 - 10.116.0.14` |
| Sekretariat | `10.116.2.0` | `10.116.2.0 - 10.116.3.255` | `255.255.254.0 (/23)` | `10.116.3.255` | 510 | `10.116.2.1 - 10.116.3.254` |
| Router (Interlink) | `10.116.0.0` | `10.116.0.0 - 10.116.0.3` | `255.255.255.252 (/30)` | `10.116.0.3` | 2 | `10.116.0.1 - 10.116.0.2` |
| Tunnel / Point-to-Point | `10.116.0.4` | `10.116.0.4 - 10.116.0.7` | `255.255.255.252 (/30)` | `10.116.0.7` | 2 | `10.116.0.5 - 10.116.0.6` |


# CIDR
![](assets/CIDR1.png)
![](assets/CIDR.png)
### Tabel Alokasi CIDR (Metode Sequential / Berurutan)

| Subnet / Departemen | NID | Range Block | Netmask | Broadcast | Host Usable | Rentang IP yang Dapat Dipakai |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Bidang Guru & Tendik | `10.116.3.0` | `10.116.3.0 - 10.116.3.127` | `255.255.255.128 (/25)` | `10.116.3.127` | 126 | `10.116.3.1 - 10.116.3.126` |
| Bidang Kurikulum | `10.116.2.0` | `10.116.2.0 - 10.116.2.255` | `255.255.255.0 (/24)` | `10.116.2.255` | 254 | `10.116.2.1 - 10.116.2.254` |
| Bidang Sarana Prasarana | `10.116.3.128` | `10.116.3.128 - 10.116.3.191`| `255.255.255.192 (/26)`| `10.116.3.191` | 62 | `10.116.3.129 - 10.116.3.190`|
| Bidang Pengawas Sekolah | `10.116.3.192` | `10.116.3.192 - 10.116.3.223`| `255.255.255.224 (/27)`| `10.116.3.223` | 30 | `10.116.3.193 - 10.116.3.222`|
| Server & Admin | `10.116.3.224` | `10.116.3.224 - 10.116.3.231`| `255.255.255.248 (/29)`| `10.116.3.231` | 6 | `10.116.3.225 - 10.116.3.230`|
| Sekretariat | `10.116.0.0` | `10.116.0.0 - 10.116.1.255` | `255.255.254.0 (/23)` | `10.116.1.255` | 510 | `10.116.0.1 - 10.116.1.254` |
| Router (Interlink) | `10.116.3.232` | `10.116.3.232 - 10.116.3.235`| `255.255.255.252 (/30)`| `10.116.3.235` | 2 | `10.116.3.233 - 10.116.3.234`|
| Tunnel / Point-to-Point | `10.116.3.236` | `10.116.3.236 - 10.116.3.239`| `255.255.255.252 (/30)`| `10.116.3.239` | 2 | `10.116.3.237 - 10.116.3.238`|

