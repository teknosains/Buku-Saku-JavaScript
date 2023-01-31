
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
const bukuButton = document.getElementById('buku-botton');
bukuButton.addEventListener('click', function() {
  alert('Buku Saku JavaScript')
});

```
function atau fitur diatas bukanlah bagian dari spesifikasi resmi JavaScript alias tidak ada implementasinya di JavaScript Engine. Fitur-fitur diatas adalah ```Web API``` yakni **fitur yang disediakan oleh browser** yang dapat di panggil oleh JavaScript.

Web API ada didalam _**window**_ object yang tersedia secara global (_Global scope_), bisa dipakai dimanapun dihalaman suatu aplikasi web.

Sebagai contoh,

```javascript
window.setTimeout(() => {
  console.log('Timer finished')
}, 1000 );

window.alert('Buku Saku JavaScript');
```
kode diatas adalah valid dan memang aslinya begitu. Namun karena **window** object yang bersifat **Global**, maka kita tidak perlu coding seperti diatas. Cukup kita tulis seperti berikut

```javascript
setTimeout(() => {
  console.log('Timer finished')
}, 1000 );

alert('Buku Saku JavaScript');
```

Nah sekarang kita jadi tahu bahwa **tidak semua** _codingan JS_ yang kita tulis nantinya adalah asli bawaan JS Engine. Ada banyak sekali fungsi/fitur yang ternyata disediakan oleh Browser.

Berikut list Web API selengkapnya yang bisa kamu pelajari. [Web API](https://developer.mozilla.org/en-US/docs/Web/API)

