---
tags:
  - php
  - area
Links: "[[My Areas]]"
---
---
# Standar Output & String Operator

## 1. echo & print
Merupakan standar output yang biasa digunakan untuk mencetak sesuatu ke layar
```php
<?php 
print("Selamat Datang");
echo "Arlen Bayu Wijaya";
?>
```

## 2. print_r() & var_dump()
Biasa digunakan untuk debug program yang ingin dijalankan
```php
<?php
$variable = 10;
var_dump($varible);
print_r($variable);
?>
```

## 3. Operator pada String
Operator pada php hampir sama dengan bahasa pemrograman pada umumnya yaitu tambah, kurang, kali, bagi, dll. Pada php memiliki satu operator khusus pada string yang gunanya untum melengkapi string selanjutnya.
```php
<?php 
$nama = "Arlen ";
$nama .= "Bayu ";
$nama .= "Wijaya";
echo $nama; // variabel nama akan berisi Arlen Bayu Wijaya
?>
```

---

