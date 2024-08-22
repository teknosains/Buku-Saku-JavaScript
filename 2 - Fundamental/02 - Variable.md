## Variable

Setiap bahasa pemrograman pasti memiliki mekanisme untuk menyimpan suatu informasi. Dalam bahasa pemrograman, suatu informasi akan disimpan
kedalam sebuah **Variable**. Sebagai contoh informasi profile seseorang dapat disimpan dalam variable seperti ini:

```javascript
let nama = 'Agus';
let umur = 20;
let alamat = 'Jl. Ujung berung Bandung';
```
Dimana **nama, umur dan alamat** adalah sebuah _variable_. Untuk membuat sebuah variable di JavaScript cukup menggunakan keyword ```let``` atau ```const```.

Struktur sebuah variable secara sederhana mengikuti pola berikut:

```javascript
[keyword] [nama variable] = [value];

// atau

[keyword] [nama variable];

```



### Cara Membuat Variable

Untuk membuat atau _mendeklarasikan_ sebuah variable di JavaScript, gunakan keyword ```let``` atau ```const``` diikuti dengan nama variable nya.

Contoh

```javascript
const tahun;
let judul;
let bahasa;
```
Kemudian variable diatas dapat kita isi / _definisi_ dengan informasi apapun sebagai contoh

```javascript
const tahun = 2023;

let judul;

judul = 'Buku Saku JavaScript'

let bahasa = 'JavaScript';
```

> **Note**
> 
> Jika mendeklaraskan variable menggunakan ```const``` maka _value_ nya harus langsung didefinisikan karena value dari variable
```const``` tidak bisa didefinisi/diubah belakangan.
> ```javascript
> const tahun;
> // atau
> const tahun;
> tahun = 2023;
> // Error: Missing initializer in const declaration
> ```
> ```javascript
> const tahun = 2023;
> tahun = 2024
> // Error: Assignment to constant variable
> ```
> ```javascript
> const tahun = 2023;
> // OK
> ```

### Variable dan Tipe Data

**Variable** dapat menyimpan informasi dalam berbagai jenis tipe data seperti _object, number, string, boolean_ dll.

```javascript
let nama = 'Agus'; // string
let umur = 20; // number
let statusMenikah = false; // boolean

// variable diisi dengan object
let user = {
  nama: 'Agus',
  umur: 20,
  statusMenikah: false
};

// variable diisi dengan array
let listBuah = ['Apel', 'Jambu', 'Jeruk'];

// variable untuk menyimpan DOM object
const app = document.getElementById('app');
```

### Aturan Penamaan Variable

Ada beberapa aturan penaaman **variable** di JavaScript yang wajib kita patuhi diantaranya:
- Nama variable wajib hanya terdiri dari huruf, kombinasi huruf-angka, simbol ```$``` dan ```_``` 
   
  contoh:

  ```javascript
  let email = 'email@github.com'; // OK
  let email2 = 'email2@github.com'; // OK
  
  let $ = 'Tanda Dollar'; // OK, tapi tidak umum
  let _ = 'Tanda underscore'; // OK, tapi tidak umum
  
  let $email = 'email@github.com'; // OK
  let _email = 'email@github.com'; // OK
  let user_email = 'email@github.com'; // OK

  let email-user = 'email@github.com'; // Error
  let email+user = 'email@github.com'; // Error
  
  // Special character juga tidak boleh
  
  let #email = 'email@github.com'; // Error
  let #$+- = 'Halo'; // Error
  ```
- Tidak boleh hanya digit/angka dan tidak boleh didahului angka
  
  contoh:

  ```javascript
  let 3email = 'email@gmail.com'; // Error
  let 1234 = 'email@gmail.com'; // Error
  ```
- Tidak boleh menggunakan _reserved keyword_ seperti ```let```, ```const```, ```var```, ```class```, ```function```, ```return```, ```this```, ```new``` dan yang lainnya. Untuk melihat daftar _reserved keyword_ lengkap, silahkan baca di [MDN - Reserved Keyword](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#keywords) atau https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#keywords

  contoh:

  ```javascript
  let class = 'Windows'; // Error
  let function = 'Github'; // Error
  let return = 'Apple'; // Error
  ```
- Variable itu Case-sensitive
  
  contoh:

  ```javascript
  let NAMA = 'Budi';
  let nama = 'Budi';
  let Nama = 'Budi';

  // Ketiganya adalah variable yang berbeda
  ```
- Direkomendasi menggunakan format **camelCase** 

  contoh:

  ```javascript
  let namaLengkap = 'Agus Hidayat';
  let alamatLengkap = 'Jl. Palmerah no 12 Rt/Rw 01/03';
  let namaIbuKandung = 'Marni Hidayat';
  ```
- Direkomendasi menggunakan bahasa inggris
  
  Penggunaan bahasa **inggris** dalam penamaan _variable_ akan membuat code lebih selaras dengan syntax-syntax JavaScript yang memang dibuat dalam bahasa inggris.

  contoh:

  ```javascript
  let name = 'Agus';
  let address = 'Jl. Palmerah no 12 Rt/Rw 01/03'
  
  function getUserInfo() {
    return 'My name is ' + name + ', address is at ' + address;
  }
  ```
  
Buat dan namailah variable sesuai dengan aturan dan rekomendasi agar code kita lebih clean dan lebih terlihat profesional. Selanjutnya, pada contoh-contoh code dalam series **Buku Saku JavaScript** ini, kita akan menamai variable dengan bahasa inggris yah.

### Konkatenasi / penggabungan Variable dan String

Ini adalah salah satu operasi yang paling sering kita gunakan dalam JavaScript. Akan selalu ada situasi di mana kita ingin menggabungkan variable dengan string untuk membentuk suatu kalimat / string baru. Ada 2 cara untuk melakukannya yaitu dengan bantuan operator ```+```, dan ```template literal```.

contoh:

```javascript
let name = 'Budi';
let age = 33;

let greeting = 'Halo nama saya ' + name + ', umur saya ' + age + '.';

console.log(greeting);

// Output: Halo nama saya Budi, umur saya 33 tahun.
```

Kemudian karakter backticks atau disebut juga _template literal_ ada untuk lebih memudahkan kita menggabungkan variable dengan string. Ketika menggunakan template literal, variable ditulis dengan format ```${variable}```.

contoh:

```javascript
let name = 'Budi';
let age = 33;

let greeting = `Halo nama saya ${name}, umur saya ${age} tahun.`;

console.log(greeting);

// Output: Halo nama saya Budi, umur saya 33 tahun.
```

Saat dibutuhkan untuk menggabungkan / konkatenasi string dengan variable yang cukup panjang / kompleks, gunakanlah _backticks_ / template literal.

  

