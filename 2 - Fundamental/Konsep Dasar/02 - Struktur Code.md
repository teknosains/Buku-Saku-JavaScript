## Struktur Code

Seperti pada bahasa pemrograman lainnya, JavaScript juga punya struktur code yang harus diketahui sebelum lebih lanjut praktek coding. 

### Statement

Statement adalah sintaks instruksi atau kalimat perintah yang kita tulis agar di eksekusi oleh si JavaScript Engine atau Browser. Contoh sederhana Statement adalah seperti berikut

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

['Budi', 'Agus', 'Ujang'].forEach(name => alert(name));  

// error: Uncaught TypeError: Cannot read properties of undefined (reading '2')
```
Code seperti diatas akan error jika kita jalankan karena, oleh karena itu perlu pakai titik koma agar JavaScript Engine / Browser tahu bahwa ke-2 baris code diatas adalah statement yang berbeda


```javascript
alert("Hello world"); // <-- pakai titik koma disini

['Budi', 'Agus', 'Ujang'].forEach(name => alert(name)); 

```

### Comments

Comment berguna untuk memberi keterangan tambahan pada codingan kita. Dengan begitu kita atau programmer lainnya yang akan membaca codingan kita dikemudian hari lebih mudah memahami arti atau maksud dari codingan kita.

Comment tidak akan di eksekusi oleh JavaScript, jadi tidak perlu khawatir bisa jadi bugs atau masalah. Ada **2** cara yang umum untuk menulis _comment_ yaitu 

* menggunakan sintaks ```/* ... */``` untuk comment yang lebih dari satu baris
* menggunakan sintaks ```// .. ``` jika comment nya hanya satu baris saja

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

// check kondisi cuaca
if (cuaca === 'hujan') {
  console.log('Dirumah sajalah');
}

// contoh comment yang lebih advance, untuk dokumentasi internal

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

Comment juga berfungsi untuk me-nonaktifkan suatu statement agar tidak di eksekusi oleh JS Engine atau browser.

```javascript
// non-aktifkan sementara, kita ganti dengan yg baru

/*
function luasPersegi(panjang, lebar) {
  return panjang * lebar;
}
*/

// tanggal update: 3 Jan 2023 oleh Budi K

function luasPersegiPanjang(panjang, lebar) {
  return panjang * lebar;
}
```

```NOTES:``` Sebaiknya hanya gunakan comment jika kita memang benar-benar perlu saja. Tidak semua statement harus kita kasih comment.