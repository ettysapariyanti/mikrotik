# mikrotik
Membahas berbagai hal mengenai Mikrotik


Perintah ini untuk melakukan reset settingan / konfigurasi sehingga sangat bersih dan tidak ada backup yang tersedia : 

```text
/system reset-configuration no-defaults=yes skip-backup=yes

```

#Isi File untuk memeriksa keberadaan file SQLite, tujuannya adalah untuk memastikan adanya database SQLite dari kumpulan  file yng ada: 

```text

import os

import sqlite3


# source code dasar untuk mengecek keberadaan file database sqlite.

# sehingga tidak terjadi pembuatan database baru dengan nama yang berbeda


lokasiFileDatabase = '/home/steven/proyekPython/latihan1/kumpulandata1.db'


cekKeberadaanFile = os.path.exists(lokasiFileDatabase)

print(cekKeberadaanFile)


```








