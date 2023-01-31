## Struktur Coding

Seperti pada bahasa pemrograman lainnya, JavaScript juga punya struktur code yang harus diketahui sebelum lebih lanjut praktek coding. 

### Statement

Statement adalah syntax instruksi atau kalimat perintah yang kita tulis agar di eksekusi oleh si JavaScript Engine atau Browser. Contoh sederhana Statement adalah seperti berikut

```javascript
// statement untuk mendefinisakan variable
const umur = 12;
```

```javascript
// statement untuk menampilkan alert di browser
alert('Buku Saku JavaScript');
```

```javascript
// statement untuk menulis sesuatu ke console browser
console.log('Selamat datang');
```

```javascript
// statement untuk pengecekan kondisi
if (umur < 12) {
  console.log('Kamu masih kecil');
} else {
  console.log('Kamu sudah besar');
}
```

### Titik Koma / Semicolons

Titik koma atau semicolon biasa digunakan sebagai pemisah antara satu statement dengan yang lainnya. Namun di JavaScript kita _sudah_ bisa coding tanpa pakai titik koma. 

```javascript
const umur = 12;
console.log(umur);
```
Ada statement yang by-default tidak memerlukan titik koma seperti pada ```conditional statement```, ```loop``` dan ```function``` 

```javascript
// contoh pada conditional statement

if (umur < 12) {
  
} else {
  
}  // <-- tidak perlu ada titik coma disini

switch (umur) {
  case:
  default:
     
} // <-- tidak perlu ada titik coma disini
```

```javascript
// contoh pada loop

for (let i = 0; i < 5; i++) {

} // <-- tidak perlu ada titik coma disini

while (true) {

} // <-- tidak perlu ada titik coma disini

```

```javascript
// contoh pada function

function printName() {

} // <-- tidak perlu ada titik coma disini

class Animal {

} // <-- tidak perlu ada titik coma disini

```

Rekomendasi saya tetap gunakan titik koma karena ada beberapa situasi dimana code kita akan ```error``` jika tidak pakai titik koma. Contoh seperti berikut

```javascript
alert("Hello world")

[1, 2, 3].forEach(alert);  

// error: Uncaught TypeError: Cannot read properties of undefined (reading '2')
```
Code seperti diatas akan error jika kita jalankan karena, oleh karena itu perlu pakai titik koma agar JavaScript Engine / Browser tahu bahwa ke-2 baris code diatas adalah statement yang berbeda


```javascript
alert("Hello world"); // <-- pakai titik koma disini

[1, 2, 3].forEach(alert);  

```

### Comments
Comment berguna untuk memberi keterangan tambahan pada codingan kita. Dengan begitu kita atau programmer lainnya yang akan membaca codingan kita dikemudian hari lebih mudah memahami arti atau maksud dari codingan kita.

Comment tidak akan di eksekusi oleh JavaScript, jadi tidak perlu khawatir bisa jadi bugs atau masalah. Ada **2** cara yang umum untuk menulis _comment_ yaitu 

* menggunakan syntax ```/* ... */``` untuk comment yang lebih dari satu baris
* menggunakan syntax ```// .. ``` jika comment nya hanya satu baris saja

```javascript

/*
   ini adalah untuk check kondisi status usia berdasarkan umur
   dari seseorang.
    
   Outputnya hanya ada 2 yatu *kecil* atau *besar* saja
*/
if (umur < 12) {
  console.log('Kamu masih kecil');
} else {
  console.log('Kamu sudah besar');
}


// jika hujan, stay di rumah saja
if (hujan === true) {
  console.log('Dirumah sajalah');
}


// contoh comment yang lebih advance, untuk documentasi internal

/**
* fungsi untuk menghitung luas persegi
* 
* @param {number} panjang, panjang dari persegi
* @param {number} lebar, lebar dari persegi
* @return {number} luas persegi
*/
function luasPersegi(panjang, lebar) {
  return panjang * lebar;
}

```


```NOTES:``` Sebaiknya hanya gunakan comment jika kita memang benar-benar perlu saja. Tidak semua statement harus kita kasih comment. 

