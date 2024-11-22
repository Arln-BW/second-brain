---
tags:
  - area
  - js
Links: "[[Programming]]"
---
---
Linked with [[1 - JavaScript Introduction]]
# Pendahuluan

DOM (Document Object Model) adalah antarmuka pemrograman untuk HTML yang merepresentasikan halaman web, sehingga program dapat mengubah dan memanipulasi strukturnya. Untuk mengetahuinya bisa mengetikkan

```js
console.log(document);
```

Dalam memori DOM atau Document direpresentasitan sebagai object yang kemudian akan dimanipulasi sebagai model. Model sendiri tersimpan sebagai pohon hirarki DOM (DOM Tree). Ada konsep/representasi DOM Tree yaitu node(simpul). Tiap node bisa berupa element (tag pada html), atribute (href) dan text (isi content/teks).

Di dalam JavaScript terdapat konsep window, dan window dapat berisi hal mengenai: Document, History dan Location.

---
# DOM Tree

Semua element beserta isi pada element html merupakan node(simpul). Setiap simpul memiliki struktur hirarki yang disebut DOM Tree. Node memiliki beberapa tipe, seperti : element, attribute, text, CDATA Section, entity reference, entity, processing instruction, comment, Document type, Document fragment dan notation.

Element a (anchor), href merupakan attribute dan 'Tekan di sini' merupakan text.
```html
<a href="google.com">Tekan di sini</a>
```

## 1. Istilah-Istitilah pada DOM Tree

Saat memilih hanya satu dari element, atrribute, text atau beberapa hal yang ada dalam html itu disebut dengan node

>[!NOTE]
> Syarat node hanya boleh memilih satu dari tipe yang ada

Namun ada beberapa perbedaan saat memilih beberapa dari node, seperti cara mengelolanya dan mengelompokkannya. Terdapat 2 pengelompokkan node yaitu :
1. . Nodelist
	Beberapa node yang dipilih dan node tersebut terdiri dari beberapa tipe berbeda. Nodelist sendiri tidak live
2. HTMLCollection
	Beberapa node yang dipilih dan node tersebut hanya berisi element pada HTML saja.  HTMLCollection bersifat live

## 2. Struktur Hirarki DOM

1. Root Node
	Node yang menjadi sumber dari semua node lain di dalam DOM yang merupakan Document
2. Parent Node
	Node yang berada 1 tingkat diatas node yang lain. Contoh : body adalah Parent dari h1, p, p, div dan a 
3. Child Node
	Node yang berada 1 tingkat dibawah node yang lain. Contoh : h1 adalah Child dari body

---
# DOM Selection Method

## 1. Jenis-Jenis DOM Selection

Terdapat beberapa function pada JavaScipt untuk memilih element yang terdapat pada html.
1. getElementById();
	Untuk memilih satu element pada html yang berdasarkan id yang dimiliki dan function ini akan menghasilkan element
2. getElementsByTagName()
	Untuk memilih beberapa element pada html berdasarkan tag-nya. Fucntion ini akan menghasilkan HTMLCollection
3. getElementsByClassName()
	Untuk memilih beberapa element pada html berdasarkan class yang dimiliki. Function ini akan menghasilkan HTMLCollection
4. querySelector() dan querySelectorAll()
	Untuk memilih element berdasarkan selectornya. querySelector() akan menghasilkan element dan querySelectorAll() akan menghasilkan nodelist

## 2. Penarapan DOM Selection

HTML code yang akan dimanipulasi beberapa elemennya.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Dom Selection</title>
  <style>
    * {
        border: 2px solid #dedede;
        padding: 15px;
        margin: 15px;
    }
    html {
      margin: 0;
      padding: 0;
    }
    body {
      max-width: 600px;
      margin: 30px auto;
      font-family: sans-serif;
      color: #333;
    }
  </style>
</head>
<body>
  <h1 id="judul">Hello World</h1>
  <div id="container">
      <section id="a">
          <p class="p1">paragraf 1</p>
          <a href="https://www.instagram.com/arln.bw/">Instagram Arlen Bayu</a>
          <p class="p2">paragraf 2</p>
          <p class="p3">paragraf 3</p>
      </section>
      <section id="b">
          <p>paragraf 4</p>
          <ul>
              <li>item 1</li>
              <li>item 2</li>
              <li>item 3</li>
          </ul>
      </section>
  </div>
  <script src="1-selection.js"></script>
</body>
</html>
```

### a. document.getElementById()

Funtion ini akan memilih berdasarkan id yang dimiliki oleh elemen html. Sebagai contoh akan dipilih id container yang dimasukkan ke variabel contain

```js
const contain = getElementById('container');
```

Selanjutnya, variabel contain tersebut dapat diubah style atau attribute yang dimiliki

```js
contain.style.backgroundColor = 'red';
```
