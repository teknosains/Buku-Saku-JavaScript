---
fontsize: 12pt
highlight-style: pygments
pdf-engine: pdflatex
papersize: a4
geometry: top=1in, bottom=1in, left=1in, right=1in
header-includes: |
  \pagestyle{empty}
---
# Event di Browser

Setelah kita memahami bagaimana JavaScript berinteraksi dengan elemen HTML melalui DOM, berikutnya kita lanjut mengenal bagaimana JavaScript bisa merespons **aksi/interaksi dari pengguna**, seperti klik, ketik, scroll, dll. Inilah yang disebut dengan **event**.

### Apa itu Event?

**Event** adalah kejadian yang terjadi di halaman web, misalnya:

- User mengklik tombol → **click event**
- User mengetik di input teks → **input event**
- Halaman selesai dimuat → **load event**
- User submit form → **submit event**
- dan banyak lagi...

JavaScript bisa **mendeteksi dan merespons** event tersebut, sehingga halaman web jadi interaktif.

Pembahasan tentang Event di JavaScript itu sangat panjang dan tidak akan kita cover semua di materi ini. Pembahasan tentang Event akan disusun secara bertahap di series selanjutnya.

### Mengenal Event Type, Event Target, Event 

Sebelum kita membuat halaman web yang interaktif, penting untuk memahami konsep dasar dari sistem event di browser.

Minimal ada tiga istilah penting yang perlu kita pahami lebih dulu:

#### 1. Event Type

**Event type** adalah jenis event yang terjadi di halaman web. Browser punyai banyak daftar event yang biasa digunakan, dan masing-masing punya nama dan tipe tertentu.

Contoh event type yang sering digunakan:
- `click`: saat element diklik
- `mouseover`: saat kursor diarahkan ke element
- `keydown`: saat tombol keyboard ditekan
- `submit`: saat form disubmit

Event type inilah yang kita gunakan saat menentukan event ke elemen, misalnya:

```js
element.addEventListener('click', function() {
  // kode yang dijalankan saat klik
  // terjadi di suatu element
});
```

#### 2. Event Target
Event target adalah element tempat terjadinya event. Misalnya, kalau kita klik element ```<button>```, maka tombol itu adalah target dari event `click`.

Saat kita menggunakan event handler, kita bisa tahu element mana yang menjadi target dengan menggunakan `event.target`.

```html
<button id="myButton">Click me!</button>

<script>
  let button = document.getElementById('myButton');

  button.addEventListener('click', function(event) {
    console.log(event.target); // element <button> yang diklik
  });
</script>
```

#### 3. Event Handler atau Event Listener
Event handler atau biasa disebut juga event listener adalah fungsi JavaScript yang dijalankan sebagai respon dari sebuah event dengan tipe tertentu.

```js
button.addEventListener('click', function() {
  alert('button diklik');
});
```
Bagian ```function() { alert(...) }``` pada contoh diatas disebut **event handler** yang berfungsi untuk menangani event yang terjadi. Untuk lebih jelas kita coba variasi penulisan event handler seperti berikut:

```js
function showAlert() {
  alert('button diklik');
}

button.addEventListener('click', showAlert);
```

Variasi penulisan diatas secara fungsi sama dengan penulisan pada contoh sebelumnya. Terlihat fungsi ```showAlert``` dipanggil saat event `click` terjadi dan function `showAlert` ini disebut **event handler**.

Ketika kita menulis kode seperti ini:

### Cara Mendaftarkan Event Handler

Untuk merespon dan meng-handle event dalam suatu element HTML, kita harus mendaftarkan tipe event (event type) yang kita inginkan ke element tersebut agar bisa dieksekusi oleh browser. Caranya yang umum adalah menggunakan menggunakan DOM API `addEventListener()`. Method ini adalah salah satu bagian terpenting dari DOM API yang disediakan browser dan yang paling sering digunakan untuk _handle_ interaksi antara user dengan halaman web. 

Sebenarnya ada **dua cara dasar** untuk menambahkan event handler. Yang pertama adalah dengan menambahkan _property event_ khusus langsung di element HTML, seperti ini:

```html
<button 
  id="myButton" 
  onclick="alert('Tombol diklik!')"
>
  Click me!
</button>
```
atau variasi lainnya

```html
<button 
  id="myButton" 
  onclick="showAlert()"
>
  Click me!
</button>

<script>
  function showAlert() {
    alert('Tombol diklik!');
  }
</script>
```

Cara ini dikenal juga dengan istilah **inline event handler**. Setiap event type akan memiliki _property event_ yang sesuai, seperti ```onclick```, ```oninput```, ```onmouseover```, dan sebagainya.

Contoh:


| Tipe Event   | Deskripsi                              | Inline Event Handler |
|--------------|----------------------------------------|-----------------------|
| `click`      | Saat element diklik                     | `onclick`             |
| `mouseover`  | Saat kursor diarahkan ke elemen         | `onmouseover`         |
| `keydown`    | Saat tombol keyboard ditekan            | `onkeydown`           |
| `submit`     | Saat form di-submit                     | `onsubmit`            |
| dst...       | ...                                     | ...                   |


Yang kedua dan yang lebih modern dan umum digunakan adalah dengan menggunakan _method_ ```addEventListener()```.

Contoh beberapa event handler menggunakan ```addEventListener()```:

#### Contoh 1: Menangani Klik Tombol

```html
<button id="myButton">Klik saya</button>

<script>
  let btn = document.getElementById('myButton');

  btn.addEventListener('click', function() {
    alert('Tombol diklik!');
  });
</script>
```

#### Contoh 2: Menangani Input Teks

```html
<input type="text" id="nameInput" placeholder="Ketik nama kamu">
<p id="preview"></p>

<script>
  let input = document.getElementById('nameInput');
  let preview = document.getElementById('preview');

  input.addEventListener('input', function() {
    preview.innerText = 'Hai, ' + input.value;
  });
</script>
```

#### Contoh 3: Menangani Mouse Hover

```html
<div 
  id="box" 
  style="width: 200px; height: 100px; background-color: lightblue;"
>
</div>

<script>
  let box = document.getElementById('box');

  box.addEventListener('mouseover', function() {
    box.style.backgroundColor = 'orange';
  });

  box.addEventListener('mouseout', function() {
    box.style.backgroundColor = 'lightblue';
  });
</script>
```

#### Contoh 4: Menangani Submisi Form

```html
<form id="myForm">
  <input type="text" name="name" placeholder="Ketik nama kamu">
  <button type="submit">Kirim</button>
</form>

<script>
  let form = document.getElementById('myForm');

  form.addEventListener('submit', function(event) {
    event.preventDefault();
    alert('Form dikirim!');
  });
</script>
```

**Catatan**: _By default_ ketika sebuah form disubmit, browser lah yang akan melakukan proses submisi nya dan akan melakukan refresh halaman. Menambahkan ```event.preventDefault()``` memberi tahu browser bahwa yang akan menangani form submisi ini adalah JavaSript, karenanya si browser tidak akan melakukan refresh halaman.

### Jenis-Jenis Event Populer

| Nama Event  | Kapan Terjadi                        |
|-------------|--------------------------------------|
| `click`     | Saat elemen diklik                   |
| `dblclick`  | Saat elemen di double-klik           |
| `input`     | Saat isi input berubah               |
| `change`    | Saat nilai input berubah (dan blur)  |
| `submit`    | Saat form dikirim                    |
| `keydown`   | Saat tombol keyboard ditekan         |
| `load`      | Saat halaman selesai dimuat          |
| `mouseover` | Saat mouse diarahkan ke elemen       |
| `mouseout`  | Saat mouse meninggalkan elemen       |

### Mengenal `event object`

Setiap kali event terjadi dan handler function-nya dipanggil, browser akan otomatis memberikan sebuah object ke dalam function handler tersebut. Object ini disebut `event`, yang berisi informasi tentang event yang terjadi.

Contoh:

```js
button.addEventListener('click', function(event) {
  // element target yang diklik
  const btn = event.target; 
  // melihat tipe event nya apa
  console.log(event.type);   // 'click'
  // lihat semua informasi lainnya di event
  console.log(event);
});
```

Event object ini sangat bermanfaat dalam berbagai operasi dan manipulasi DOM. Salah satu contohnya misal kita punya aplikasi web yang punya fitur _like_ dan _share_ article ke sosial media. Dua fitur ini bisa kita buatkan 2 tombol namun dengan satu event handler. 

Kemudian melakukan aksi yang sesuai berdasarkan jenis tombol nya. Contohnya seperti ini:

```html
<button class="btn-action btn-like">Like</button>
<button class="btn-action btn-share">Share</button>

<script>
  // akses semua button yang punya class 'btn-action'
  const buttons = document.querySelectorAll('.btn-action');

  buttons.forEach(function (btn) {
    btn.addEventListener('click', function (event) {
      const target = event.target;
      const targetClass = target.classList;

      // Cek untuk membedakan button mana yang di klik  
      if (targetClass.contains('btn-like')) {
        doProcess('like');
      } else if (targetClass.contains('btn-share')) {
        doProcess('share');
      }
    });
  });
</script>
```

Event adalah salah satu fondasi utama untuk membuat aplikasi web kita menjadi interaktif dan dinamis. Dengan memahami konsep dasar seperti event type, event target, dan event handler, kita sudah bisa mulai membangun aplikasi web yang interaktif dan responsif terhadap aksi user.

Kita juga sudah mempelajari cara menggunakan `addEventListener()` sebagai metode yang lebih modern dan fleksibel untuk menangani berbagai jenis event di browser, serta contoh-contoh penggunaannya dalam situasi real-life.

Materi tentang event ini masih sangat luas, dan di bab-bab selanjutnya kita akan lanjutkan dengan topik lanjutan seperti event bubbling, delegation, dan cara kerja event system di JavaScript.

Yang jelas, sekarang kamu sudah punya bekal penting untuk membuat halaman web yang bukan hanya statis, tapi benar-benar bisa “berinteraksi” dengan user.
