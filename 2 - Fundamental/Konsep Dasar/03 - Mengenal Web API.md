
## Mengenal function/fitur Yang Sebenarnya Bukan Bagian Dari JavaScript

Suatu saat kita akan sampai ke tahap web development yang lebih dalam dan menemukan kode-kode seperti:

```javascript
alert()

console.log()

setTimeout()

setInterval()

localStorage

sessionStorage

// event listener
const btn = document.getElementById('btn');
btn.addEventListener('click', function() {
  alert('Buku Saku JavaScript');
});

```
function atau fitur di atas bukanlah bagian dari spesifikasi resmi JavaScript alias tidak ada implementasinya di JavaScript Engine. Fitur-fitur di atas adalah `Web API` yakni **fitur yang disediakan oleh browser** yang dapat dipanggil oleh JavaScript. 

Jadi para pembuat browser seperti Google (Chrome), Mozilla (Firefox), Apple (Safari), Microsoft (Edge), dll semacam memiliki konsensus bersama untuk mengimplementasikan Web API di atas di browser masing-masing sehingga lebih
universal dan mudah bagi para developer. Bayangkan misal fitur ```console.log()``` hanya tersedia di Chrome saja tapi di Firefox tidak ada...misal saja di Firefox maunya ```console.print()```, Edge ```console.display()``` maka ini akan membuat repot para developer/programmer.

Web API ada di dalam _**window**_ object yang tersedia secara global (_Global scope_), bisa dipakai di mana pun di halaman suatu aplikasi web.

Sebagai contoh:

```javascript
window.setTimeout(() => {
  console.log('Timer finished')
}, 1000 );

window.alert('Buku Saku JavaScript');
```
Karena **window** object yang bersifat **Global**, maka kita tidak perlu coding seperti di atas. Cukup kita tulis seperti berikut

```javascript
setTimeout(() => {
  console.log('Timer finished')
}, 1000 );

alert('Buku Saku JavaScript');
```

Nah sekarang kita jadi tahu bahwa **tidak semua** _codingan JS_ yang kita tulis nantinya adalah asli bawaan JS Engine. Ada banyak sekali fungsi/fitur yang ternyata disediakan oleh Browser.

List Web API selengkapnya yang bisa kamu pelajari lebih lanjut di https://developer.mozilla.org/en-US/docs/Web/API

