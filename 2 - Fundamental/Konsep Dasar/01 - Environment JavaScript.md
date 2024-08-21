## Environment JavaScript
Kita bisa bilang Environment JavaScript adalah tempat dimana code JavaScript bisa dijalankan. Saat ini minimal ada 3 environment yang wajib kita ketahui yaitu

* Browser environment
* Node environment
* Deno environment

#### 1. Browser environment
Ini yang paling umum dan yang kita tentu saja paling kenal. Code JavaScript yang kita tulis akan di eksekusi oleh JavaScript Engine yang dibawa oleh Browser yang kita pakai dan kemudian kita bisa lihat langsung _output_ nya di layar/halaman browser. 

Contoh:
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Buku Saku JavaScript</title>
  </head>
  <body>
    <h1>Selamat datang!</h1>
    <script>
      const title = 'Buku Saku JavaScript';
      window.alert(title);
    </script>
  </body>
</html>
```

Seperti terlihat pada sample code diatas, kita bisa letakkan langsung code JavaScript beserta code _HTML_ didalam tag ```<script></script>```

```html
<body>
  <h1>Selamat datang!</h1>
  <!-- code html lainnya diatas-->
  <!-- code JavaScript dibawah -->
  <script>
   const title = 'Buku Saku JavaScript';
   alert(title);
  </script>
</body>
```

Praktek yang umum dilakukan adalah membuat file javascript terpisah lalu kemudian di-_load_ di html-nya dengan cara seperti berikut:

```javascript
// file script.js

const title = 'Buku Saku JavaScript';
alert(title);
```

```html
<!-- file index.html -->
<body>
  <h1>Selamat datang!</h1>
  <script src="script.js"></script>
</body>
```
Manfaat dari memisahkan code JavaScript menjadi file tersendiri adalah struktur file project kita menjadi lebih rapih, lebih modular dan lebih mudah dibaca. Namun untuk project yang besar, adakalanya kita lebih memilih untuk langsung di _embedd_ di html seperti contoh sebelumnya. Ini bisa mengurangi beban network request ke server karena dengan menulis code seperti ini

```html
  <script src="script.js"></script>
```
si browser akan me-lakukan request ke server untuk me-load file ```script.js```. Namun tidak perlu terlalu dikhawatirkan untuk saat ini, silahkan gunakan cara mana yang kamu lebih suka.

#### 2. Node environment
Code JavaScript yang kita tulis bisa berjalan di Server berkat Node.JS. Kita bisa menulis JavaScript untuk membuat API dan kebutuhan lainnya yang berjalan di Server seperti halnya bahasa pemrograman lain yang kamu kenal seperti PHP, C#, Java dll.

Contoh code Node.JS
```javascript
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

#### 3. Deno environment
Deno adalah alternatif lain selain Node.JS jika kamu ingin _coding_ untuk backend (di server). Saat ini Deno mungkin belum terlalu populer namun sangat layak kita nantikan bagaimana perkembangan kedepannya di Indonesia. Jika makin banyak yang implementasi di Indonesia, maka mungkin kita bersegera mempelajarinya nanti.

Pelajari tentang Deno disitus resminya https://deno.land
