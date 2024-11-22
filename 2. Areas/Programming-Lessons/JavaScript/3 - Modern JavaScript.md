---
tags:
  - area
  - js
Links: "[[Programming]]"
---
`Linked with [[1 - JavaScript Introduction]]`
# Membuat Object

## 1. Object Literal

JavaScript merupakan bahasa pemrograman yang berbasis simple-object, artinya sebagian besar terdiri dari objek-objek yang dapat diubah.

Object literal merupakan object yang berisi nilai-nilai yang terdapat pada sebuah text atau properti.

```js
let hero1 = {
    name : "Alucard",
    energi : 340,
    serang : function(value){
        this.energi -= value;
        return `Kamu memberikan serangan ${value}. Sisa energi ${this.energi}`
    },
    makan: function(value){
        this.energi += value;
        return `Halo ${this.name}, selamat makan`
    }
}
```

## 2. Function Declaration

Obect yang dibuat menggunakan sebuah function yang akan mengembalikan sebuah nilai berupa object.

```js
function Heroes2(nama, energi){
    let hero = {};
    hero.nama = nama;
    hero.energi = energi;
    hero.makan = function(value){
        this.energi += value;
        return `Halo ${this.name}, selamat makan`;
    };
    hero.serang = function(value){
        this.energi -= value;
        return `Halo ${this.nama}, kamu telah melakukan serangan`
    }
    return hero;
}
```

>[!NOTE]
>Kelemahan menggunakan function declaration terletak dalam pengelolaan memori. Semakin banyak object method dibuat maka setiap memanggil function tersebut juga akan memanggil object method yang sama

## 3. Constructor

Metode ini menggunakan keyword new untuk membuat objectnya dan dari segi pengelolaan memori jauh lebih efektif dari metode yang sebelumnya.

1. Membuat object terpisah yang nantinya akan digunakan di dalam funtion

```js
const methodHeroes = {
    makan: function(value){
        this.energi += value;
        return (`Halo ${this.nama}, selamat makan`);
    },
    
    serang: function(value){
        this.energi -= value;
        return (`Halo ${this.nama}, kamu telah melakukan serangan`)
    },
    
    heal: function(value){
        this.energi += (value/2);
        return (`Hero Telah disembuhkan`)
    }
}
```

2. Membuat function dan memanggil object di dalam funtion yang telah dibuat

```js
function Heroes3(nama, energi){  
    this.nama = nama;
    this.energi = energi;
    this.makan = methodHeroes.makan; 
    this.serang = methodHeroes.serang;
    this.heal = methodHeroes.heal;
}
```

3. Cara menggunakan function dengan menggunakan keyword new sebelum nama function

```js
let ucup = new Heroes3("Ucup", 50);
```

>[!NOTE]
>Ada kelemahan saat menggunakan metode ini. Saat ingin menambahkan object method baru pada methodHeroes maka pada function Heroes3 harus memanggil object baru yang telah dibuat pada methodHeroes, hal ini akan sangat merepotkan jika object method yang dibuat banyak.

## 4. Object.create()

Metode membuat object dengan menggunakan builtin function pada JavaScript, hal ini bertujuan agar memudahkan saat develop pada function dan object method yang berbeda. Saat membuat object.create(), function ini akan memuat object dan method yang telah dimasukkan, hal ini juga dapat meminimalisir kekurangan yang terdapat pada metode yang ke-3. Cara melakukan :

1. Membuat object beserta method yang ingin digunakan
```js
const methodHeroes1 = {
    makan: function(value){
        this.energi += value;
        return (`Halo ${this.nama}, selamat makan`);
    },
    serang: function(value){
        this.energi -= value;
        return (`Halo ${this.nama}, kamu telah melakukan serangan`)
    }
}
```

2. Membuat function dan memasukkan object method yang telah dibuat
```js
function Heroes3(nama, energi){  
    let hero = Object.create(methodHeroes1); // menghubungkan method yang telah dibuat
    hero.nama = nama;
    hero.energi = energi;
    return hero;
}
```

>[!NOTE]
>Tetap saja menggunakan cara ini ada kekurangan yaitu, saat membuatnya harus menyertakan dua hal yang berbeda yaitu function sebagai blueprint dan object method yang berisikan method sebagai pendukung dari function yang telah dibuat

## 5. Prototype

Prototype merupakan metode membuat blueprint dengan cara menambahkan kata prototype setelah function lalu diikuti oleh object method pendukung. Untuk memuatnya dalam sebuah variabel dibutuhkan kata kunci new sebelum function yang berisi argumen. Cara membuat :

1. Membuat function
```js
function Heroes(nama, energi){  
    this.nama = nama;
    this.energi = energi;
}
```

2. Mengetikkan nama function lalu diikuti keyword prototype dan menyertakan nama object
```js
Heroes.prototype.makan = function(value){
    this.energi += value;
    return (`Halo ${this.nama}, selamat makan`);
}
Heroes.prototype.serang = function(value){
    this.energi -= value;
    return (`Halo ${this.nama}, kamu telah melakukan serangan`);
}
Heroes.prototype.istirahat = function(jam){
    this.energi += (jam/2);
    return (`Halo ${this.nama}, selamat beristirahat`);
}
```

3. Membuat variabel dan menyertakan keyword new sebelum mengetikkan nama function
```js
let jamal = new Heroes("Jamal", 30);
```
