# mikrotik
Membahas berbagai hal mengenai Mikrotik


Perintah ini untuk melakukan reset settingan / konfigurasi sehingga sangat bersih dan tidak ada backup yang tersedia : 

```text
/system reset-configuration no-defaults=yes skip-backup=yes

```
Ini source code yang berhasil terkoneksi ke mikrotik melalui Restful API dengan menggunakan module requests , dan berhasil menarik data berupa IP Address : 



```python

import requests

from requests.auth import HTTPBasicAuth

# IP address dan port Mikrotik

router_ip = "192.168.8.6"
port = 80

#user dan password untuk otentifikasi

username = "admin"

password = "kucing"



#URL dasar untuk akses API Mikrotik

base_url = f"http://192.168.8.6:80/rest"

ip_endpoint = "ip/address"

requests.packages.urllib3.disable_warnings()


# Fungsi untuk melakukan GET request ke API Mikrotik

try : 

    # Melakukan request untuk mendapatkan data IP Address 
    
    response = requests.get(f"{base_url}{ip_endpoint}", auth=HTTPBasicAuth(username, password))
    
    
    # mengecek status response
    
    if response.status_code == 200:
    
        ip_data = response.json()  # Mengambil data dalam format JSON
        
        print("IP Addresses : ")
        
        for ip in ip_data:
        
            print(f"ID : {ip['.id']}, Interface : {ip['interface']} , Address : {ip['address']}")
            
            
    else:
    
        print(f"Request gagal dengan status kode {response.status_code}: {response.tex}")
        
        
except requests.exceptions.RequestException as e:

    print(f"Gagal Terkoneksi ke Mikrotik API : {e}")




````





