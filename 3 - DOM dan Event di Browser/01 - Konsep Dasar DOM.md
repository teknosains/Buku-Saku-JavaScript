# Konsep Dasar DOM (Document Object Model)
Di pembahasan sebelumnya kita sudah banyak berbicara mengenai fundamental JavaScript beserta teorinya. Sekarang waktunya kita _refreshment_ dengan mengenal lebih dekat apa itu DOM dan bagaimana cara kerjanya.

DOM adalah cara browser merepresentasikan halaman web dalam bentuk pohon (tree). Setiap elemen atau _tag_ HTML dianggap sebagai _object_ yang bisa kita akses dan modifikasi menggunakan JavaScript. Ketika kita menulis kode HTML misal seperti berikut:

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
  <img width="428" alt="DOM Tree" src="https://github.com/user-attachments/assets/847deb5c-207d-481b-9330-aa15c0646137" >
</div>

dan seperti ini penampakan struktur-nya yang lebih detail

<div align="center">
  <img width="386" alt="DOM Tree 2" src="https://github.com/user-attachments/assets/4356cb03-2316-4f7b-8e8c-0ec913b2b712" />
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

Sebuah halaman web biasanya memuat banyak sekali elemen / tag html yang berulang-ulang seperti tag ```<div>``` yang biasanya sangat mendominasi sebuah halaman web. JavaScript butuh bantuan tambahan agar tahu ```<div>``` yang mana yang akan di akses dan mana yang tidak. Untuk itu, kita bisa menggunakan _id_ pada tag ```<div>``` seperti ini

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

  // untuk mengakses id, gunakan tanda #
</script>
```

Seringkali juga kita ingin agar JavaScript bisa memanipulasi semua tag yang sama namun dengan maksud / fungsi yang berbeda. Untuk itu, kita bisa menggunakan _class_ pada tag html nya sehingga nanti JavaScript tahu harus mengakses element mana di DOMnya.

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
  let menuItem = document.getElementsByClassName('menu-item');
  let listArticle = document.getElementsByClassName('list-article');

  // atau

  let menuItem = document.querySelector('.menu-item');
  let listArticle = document.querySelector('.list-article');

  // untuk mengakses class, gunakan tanda .
</script>
```

### Contoh manipulasi DOM

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
  let article = document.getElementByClassName('article');

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
