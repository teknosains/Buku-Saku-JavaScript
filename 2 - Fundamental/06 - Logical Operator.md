# Logical Operator


Logical Operator atau operator logika digunakan untuk menentukan relasi _logic_ suatu statement yang biasa digunakan untuk membuat *keputusan*. Ada 4 tipe operator logika di JavaScript yaitu:

| Operator | Deskripsi |
| -------- | --------- |
| &&       | AND       |
| ll       | OR      |
| !        | NOT     |
| ??       | Nullish Coalescing |

Sintaks
```javascript

result = a && b; // AND
result = a || b; // OR
result = !a; // NOT
result = a ?? b; // Nullish Coalescing
```

#### 1. Logical **&&** "**AND**"
Akan bernilai ```true``` jika kedua _operand_ bernilai ```true```. Jika salah satu operandnya ```false``` maka akan bernilai ```false```

Contoh:

```javascript
let score = 70;
let statusPayment = 'Lunas';

// saat semua operand bernilai true
if (score > 60 && statusPayment === 'Lunas') {
  console.log('Lulus');
}

// jika salah satu operand bernilai false
if (score < 60 && statusPayment === 'Lunas') {
  console.log('Tidak Lulus');
}
```

#### 2. Logical **||** "**OR**"

Akan bernilai ```true``` jika ada minimal satu _operand_ yang bernilai ```true```. Jika semua operandnya ```false``` maka akan bernilai ```false```

Contoh:
```javascript
let score = 70;
let statusPayment = 'Lunas';

// semua operand bernilai true
if (score > 60 || statusPayment === 'Lunas') {
  console.log('Lulus');
}

// salah satu operand bernilai true
if (score < 60 || statusPayment === 'Lunas') {
  console.log('Tidak Lulus');
}

// kedua operand bernilai false
if (score < 60 || statusPayment !== 'Lunas') {
  console.log('Tidak Lulus');
} else {
  console.log('Lulus');
}
```

#### 3. Logical **!** "**NOT**"
Operator NOT akan mengubah operand menjadi boolean ```true / false``` dan me-return nilai kebalikannya.

Contoh:

```javascript
console.log(!true); // false
console.log(!false; // true
console.log(!0); // true

let name = '';

console.log(!name); // true

if (!name) {
  console.log('name harus diisi');
} else {
  console.log('Selamat datang ' + name);
}

// Output: name harus diisi
```

Kemudian ada operator Double NOT ```!!``` yang terkadang juga dipakai untuk mengkonversi sebuah _value_ ke boolean.

Contoh:

```javascript
console.log(!!true); // true
console.log(!!false); // false

let name = 'Agus';

console.log(!!name); // true

if (!!name) {
  console.log('name harus diisi');
} else {
  console.log('Selamat datang ' + name);
}

// Output: name harus diisi
```

#### 4. Logical **??** "**Nullish Coalescing**"

Operator ini me-return _value_ operand sebelah kanan jika operand sebelah kiri _Nullish_ yaitu saat value nya ```null``` atau ```undefined```. 

Contoh:

```javascript
const name = null ?? 'Agus';
console.log(name); // Agus

const age = null;
const minimumAge = age ?? 20;
console.log(minimumAge); // 20

let married = null; // bernilai undefined
let isMarried = married ?? 'Belum menikah';
console.log(isMarried); // Belum menikah

let married = 'Sudah menikah';
let isMarried = married ?? 'Belum menikah';
console.log(isMarried); // Sudah menikah
```

Operator ini cocok digunakan jika kita ingin mendefinisikan sebuah variable yang bergantung ke variable lain namun kita sudah cukup yakin jika _variable lain_ itu **akan** bernilai ```null``` atau ```undefined```.


Misal ada variable lain yang dibuat oleh programmer lain atau bawaan dari sebuah library

```javascript
// libraryOrang.js

const defaultColor = null; // null atau undefined
```
kemudian kita ingin membuat extensi versi kita sendiri

```javascript
const myColor = defaultColor ?? 'blue';
console.log(myColor); // blue
```

#### Kombinasi Operator Logika

Saat kita dihadapkan dengan beberapa kondisi logic untuk menentukan sebuah keputusan, kita bisa menggunakan kombinasi operator logika untuk membuat _flow_ logic yang lebih kompleks.

Contoh:

```javascript
let score = 70;
let statusPayment = 'Lunas';
let isOlympicChampion = true;

if (
  (score > 60 && statusPayment === 'Lunas') 
  || isOlympicChampion
) {
  console.log('Lulus');
}
```

contoh lain:

```javascript
let height = null;
let width = null;

// penting: gunakan tanda kurung ()
let area = (height ?? 10) * (width ?? 20);
console.log(area); // 200
```

Gunakan kurung () saat mengombinasikan beberapa operator agar _flow_ logic nya lebih terlihat jelas. Selain itu tanda kurung juga memastikan urutan eksekusi _statement_ sesuai dengan yang seharusnya. 

Pada contoh `??` operator di atas, tanpa kurung seperti ini

```javascript
let height = null;
let width = null;
let area = height ?? 10 * width ?? 20;

console.log(area); // 0
```
akan jadi masalah karena operator * (perkalian) akan dijalankan terlebih dahulu sebelum operator ?? untuk mendapatkan nilai dari height.

Dalam kasus ini statement ```10 * width``` akan di eksekusi duluan, karena operator * (perkalian) memiliki prioritas lebih tinggi dari operator `??`. 

Juga karena untuk alasan **safety*, JavaScript tidak membolehkan operator `??` dikombinasikan langsung (tanpa tanda kurung) dengan operator `&&` dan `||`.

Perhatikan contoh berikut:

```javascript
let score = null;
let statusPayment = null;

let status = score && statusPayment ?? 'Eligible';
// SyntaxError: Unexpected token '??'

// sintaks yang benar harusnya
// dikombinasikan pakai tanda kurung
let status = (score && statusPayment) ?? 'Eligible';
```

**Operator logika** sangat penting dipahami dan ini adalah salah _fitur_ bahasa pemrograman yang paling sering ditulis saat _coding_. Coba kita review sedikit poin-poin utama dari operator logika:

1. **AND (&&)** - Seperti syarat yang harus dipenuhi semua
2. **OR (||)** - Seperti pilihan, salah satu terpenuhi sudah cukup
3. **NOT (!)** - Untuk me-return nilai boolean
4. **Nullish (??)** - Untuk memberi nilai cadangan/default jika null/undefined

> **Tips Praktis:**
> - Mulailah dengan operator yang sederhana (! dan &&)
> - Tulis kode yang mudah dibaca, jangan terlalu banyak operator dalam satu baris
> - Gunakan tanda kurung () jika mengombinasikan beberapa operator agar _flow_ logic nya lebih terlihat jelas

Operator logika akan sering kita gunakan saat membuat aplikasi, terutama untuk validasi form, pengecekan kondisi, dan pengambilan keputusan dalam dalam aplikasi.