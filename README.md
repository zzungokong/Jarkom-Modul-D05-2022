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

