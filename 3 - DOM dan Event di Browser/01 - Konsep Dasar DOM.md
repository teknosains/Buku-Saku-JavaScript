# Konsep Dasar DOM (Document Object Model)
Di pembahasan sebelumnya kita sudah berbicara banyak mengenai fundamental JavaScript beserta teorinya. Sekarang waktunya kita selangkah lebih dekat untuk membuat aplikasi web dengan mengenal lebih dulu apa itu DOM dan bagaimana cara kerjanya.

DOM adalah representasi struktur halaman web dalam bentuk pohon (tree structure) yang dibuat oleh browser. Setiap elemen atau _tag_ HTML dianggap sebagai _object_ yang bisa kita akses dan modifikasi menggunakan JavaScript. Ketika kita menulis kode HTML misal seperti berikut:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Belajar JavaScript</title>
  </head>
  <body>
    <h1>Selamat datang!</h1>
  </body>
</html>
```
Maka kita bisa visualisasikan pohon DOM-nya seperti ini
<div align="center">
  <img width="428" alt="DOM Tree" src="https://private-user-images.githubusercontent.com/3906229/439656766-847deb5c-207d-481b-9330-aa15c0646137.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDg2NzgxMDIsIm5iZiI6MTc0ODY3NzgwMiwicGF0aCI6Ii8zOTA2MjI5LzQzOTY1Njc2Ni04NDdkZWI1Yy0yMDdkLTQ4MWItOTMzMC1hYTE1YzA2NDYxMzcucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI1MDUzMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNTA1MzFUMDc1MDAyWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YThmNTJiNDA4NjJjMDQzZjNiNWZhYjljNjM2NzQ5MmFjMzBmNDdmZDgyM2M1NTk5N2ZkMmM5MmQzYmQ5NmZjNSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.xt4nyMb6QCqQ5UN-X7JydCU2MDloM-yuJx2rgaYSfjg" >
</div>

dan seperti ini penampakan struktur-nya yang lebih detail

<div align="center">
  <img width="386" alt="DOM Tree 2" src="https://private-user-images.githubusercontent.com/3906229/439658022-4356cb03-2316-4f7b-8e8c-0ec913b2b712.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDg2NzgxMDIsIm5iZiI6MTc0ODY3NzgwMiwicGF0aCI6Ii8zOTA2MjI5LzQzOTY1ODAyMi00MzU2Y2IwMy0yMzE2LTRmN2ItOGU4Yy0wZWM5MTNiMmI3MTIucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI1MDUzMSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNTA1MzFUMDc1MDAyWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YTJjZTcxNTg0NzIxZjRiYzQ4NWJmNmM4YjRmNWIzYjgyNTgzZGMzNDFjYjI1NDMyYTlhZDRjYWNhYzRmZWQyNyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.5YCVHVAHQb8PROMQhieFlz8ETY0JsRB1kbS5deudUo4" />
</div>

Implementasi DOM sendiri sudah di standarisasi dan semua pembuat Browser wajib mengikuti sehingga sebuah halaman web, mau dibuka di browser apapun, harus bisa diakses dan dimanipulasi oleh JavaScript dengan cara dan standar yang sama. Dengan begini, developer tidak perlu _coding_ khusus untuk untuk masing-masing browser.

Sebagai contoh, jika kita ingin mengubah _content_ text yang ada di tag ```<h1>``` diatas menjadi "Selamat datang di Buku Saku JavaScript", kita bisa lakukan seperti berikut

```html
<script>
  let title = document.querySelector('h1');
  title.innerText = 'Selamat datang di Buku Saku JavaScript';
</script>
``` 

cukup satu kali coding seperti diatas, _output_ nya akan sama di semua Browser. 

### Fungsi utama DOM

Fungsi atau tujuan utama dari DOM adalah sebagai jembatan interaksi antara document HTML dengan JavaScript. Berkat DOM, JavaScript bisa berinteraksi dengan document HTML untuk mengakses dan memanipulasi elemen-elemen HTML dengan mengubah struktur, _style_, dan _content_-nya.

### Document Object

Agar javaScript bisa berinteraksi dengan document HTML, Browser menyediakan _object_ bernama ```document``` atau ```window.document```. Object ```document``` ini merupakan _root_ dari seluruh document HTML. Semua elemen HTML di document HTML bisa diakses melalui object ```document```.

```html
<script>
  // Misal: Mengakses element <h1>
  let title = document.querySelector('h1');

  // Misal: Mengakses element <body>
  let body = document.querySelector('body');
</script>

``` 

Sebuah halaman web biasanya memuat banyak sekali elemen / tag html yang berulang-ulang seperti tag ```<div>``` yang biasanya sangat mendominasi sebuah halaman web. JavaScript butuh bantuan tambahan agar tahu ```<div>``` yang mana yang ingin di akses dan mana yang tidak. Untuk itu, kita bisa menggunakan _id_ pada tag ```<div>``` seperti ini

```html
<body>
  <h1>Selamat datang!</h1>
  <div id="article">
    <p>Ini adalah isi artikel</p>
  </div>
  <div id="comment">
    <p>Ini adalah kolom komentar</p>
  </div>
</body>
```
Dan kita bisa mengaksesnya seperti berikut

```html
<script>
  let article = document.getElementById('article');
  let comment = document.getElementById('comment');

  // atau

  let article = document.querySelector('#article');
  let comment = document.querySelector('#comment');

  // untuk mengakses id, gunakan tanda # (hashtag)
</script>
```

Seringkali kita juga ingin agar JavaScript bisa memanipulasi beberapa elemen yang punya tag yang sama, tapi memiliki fungsi atau tujuan yang berbeda. Untuk itu, kita bisa menggunakan _class_ pada tag html nya sehingga nanti JavaScript tahu harus mengakses element mana di DOMnya.

```html
<body>
  <h1>Selamat datang!</h1>
  <ul id="menu">
    <li class="menu-item"><a href="#">Home</a></li>
    <li class="menu-item"><a href="#">About</a></li>
    <li class="menu-item"><a href="#">Contact</a></li>
  </ul>
  <ul id="articles">
    <li class="list-article"><a href="#">Title 1</a></li>
    <li class="list-article"><a href="#">Title 2</a></li>
    <li class="list-article"><a href="#">Title 3</a></li>
  </ul>
</body>
```

Dan kita bisa mengaksesnya seperti berikut

```html
<script>
  let menuItem = document
    .getElementsByClassName('menu-item');
  let listArticle = document
    .getElementsByClassName('list-article');

  // atau

  let menuItem = document.querySelector('.menu-item');
  let listArticle = document.querySelector('.list-article');

  // untuk mengakses class, gunakan tanda . (titik)
</script>
```

### DOM API

Setelah mengenal struktur DOM dan cara dasar mengakses elemen HTML, sekarang saatnya kita mengenal **DOM API**.

DOM API adalah kumpulan fitur (berupa properti dan method) yang disediakan oleh browser agar JavaScript bisa berinteraksi dengan halaman HTML. Fitur-fitur ini memungkinkan kita untuk:

- mengakses elemen HTML
- mengubah isi elemen
- menambah atau menghapus elemen
- mengatur atribut
- mengatur style
- dan banyak hal lainnya

DOM API biasanya digunakan melalui object `document`, karena object `document` adalah representasi dari halaman HTML yang sedang dibuka.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Belajar JavaScript</title>
  </head>
  <body>
    <h1>Selamat datang di Buku Saku JavaScript</h1>
    <script>
      console.log(document);
    </script>
  </body>
</html>
```

Coba ketik dan jalankan kodenya lalu buka browser console. 

<img width="593" alt="Document Object Model" style="border:1px solid #ddd;margin-bottom:20px" src="https://res.cloudinary.com/cepot/image/upload/v1748694170/Screenshot_2025-05-31_at_16.37.39_fbyulw.png" />


Terlihat di console output dari ```console.log(document)``` yaitu object ```document```. Terlihat bahwa output-nya sama persis dengan struktur HTML di atas. Ini membuktikan bahwa object document adalah representasi dari halaman HTML yang sedang dibuka. dan lewat object ```document``` ini JavaScript bisa berinteraksi dengan halaman HTML.

Contoh DOM API yang paling sering digunakan adalah ```document.getElementById(id)```. 

API ini digunakan untuk mengambil / mengakses elemen HTML berdasarkan atribut `id`-nya.

```html
<div id="info">Hello</div>

<script>
  // akses element
  let element = document.getElementById('info');
  element.innerText = 'Hello world!';
</script>
```

### Beberapa contoh interaksi dengan DOM

#### 1. Mengubah _content_ sebuah tag

```html
<script>
  let title = document.querySelector('h1');

  // merubah dengan content berupa Text
  title.innerText = 'Selamat datang di Buku Saku JavaScript';

  // merubah dengan content berupa HTML
  let title = document.querySelector('h1');
  title.innerHTML = '<strong>Selamat datang di Buku Saku JavaScript</strong>';
</script>
```

#### 2. Mengubah _style_ sebuah tag

```html
<script>
  let title = document.querySelector('h1');
  title.style.color = 'red';
  title.style.fontSize = '24px';
</script>
```

#### 3. Mengubah struktur html dengan manipulasi _attribute_ kedalam sebuah tag

```html
<script>
  let article = document.getElementsByClassName('article')[0];

  // menambahkan attribute data
  article.setAttribute('data-read', '1');

  // Menambahkan attribute style
  article.setAttribute('style', 'background-color: #f0f0f0'); 

  // Menghapus attribute style
  article.removeAttribute('style');
</script>
```

#### 4. Mengubah struktur html dengan manipulasi _element_ didalam sebuah tag

```html
<script>
  let article = document.getElementByClassName('article');

  // Menambahkan element baru
  let newElement = document.createElement('p');
  newElement.innerText = 'Ini adalah paragraf baru';
  article.appendChild(newElement);

  // Menghapus element
  article.removeChild(newElement);
</script>
```

### Traversal DOM (Menjelajah Element)

DOM itu seperti struktur pohon, jadi setiap element di dalamnya saling terhubung seperti hubungan _parent_, _child_, dan _sibling_. Selain mengakses element langsung dengan `querySelector` atau `getElementById`, JavaScript juga menyediakan cara untuk **menelusuri element** yang berhubungan dengan element lainnya.

Traversal DOM ini sangat berguna ketika kita sudah mengakses satu element, lalu ingin mencari:
- Element di dalamnya (child)
- Element di atasnya (parent)
- Element di sampingnya (sibling)

Berikut ini beberapa properti yang sering digunakan:

| Properti | Keterangan |
|----------|------------|
| `parentElement` | Element parent dari element tersebut |
| `children` | Semua element Child langsung |
| `firstElementChild` | Child pertama |
| `lastElementChild` | Child terakhir |
| `nextElementSibling` | Element setelahnya (sibling kanan) |
| `previousElementSibling` | Element sebelumnya (sibling kiri) |

Perhatikan contoh berikut

```html
<div id="container">
  <ul id="menu">
    <li class="item">Home</li>
    <li class="item">About</li>
    <li class="item">Contact</li>
  </ul>
</div>
```

Kita bisa akses dan telusuri element-element dalam kode HTML diatas seperti ini

```html
<script>
  document.addEventListener('DOMContentLoaded', function() {

    let menu = document.getElementById('menu');

    // Mengakses children langsung dari elemen ul
    let children = menu.children;

    // Mengakses child pertama dan terakhir
    let firstChild = menu.firstElementChild;
    let lastChild = menu.lastElementChild;

    // Mengakses parent 
    let parent = menu.parentElement;

    // Mengakses sibling dari li kedua
    let about = menu.children[1]; // <li>About</li>
    let prevElement = about.previousElementSibling; // Home
    let nextElement = about.nextElementSibling; // Contact

  });
</script>
```

> ⚠️ **Penting:**
>
> Untuk mengakses atau memanipulasi element HTML, kita perlu memastikan bahwa seluruh struktur HTML sudah selesai dimuat oleh browser.
>
> Jika tidak, element yang kita cari bisa saja belum tersedia, dan hasilnya akan `null` atau terjadi error.
>
> Salah satu cara aman untuk memastikan semua element sudah siap adalah dengan menjalankan JavaScript di dalam event `DOMContentLoaded`, seperti ini:
>
> ```html
> <script>
>   document.addEventListener('DOMContentLoaded', function () {
>     // kode JS utk manipulasi DOM  di sini
>   });
> </script>
> ```
>
> Dengan begitu, kita bisa menjalankan kode JavaScript dengan lebih aman tanpa khawatir element HTML belum tersedia saat diakses.


DOM API adalah jembatan utama antara JavaScript dan halaman web. Dengan DOM API, kita bisa membuat halaman yang interaktif, dinamis, dan bisa merespon aksi dari user. Hampir semua manipulasi halaman yang dilakukan oleh JavaScript menggunakan DOM API, baik yang sederhana seperti mengganti teks, maupun yang kompleks seperti menambah element baru ke dalam halaman.