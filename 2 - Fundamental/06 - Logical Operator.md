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
let statusBayar = 'Lunas';

// saat semua operand bernilai true
if (score > 60 && statusBayar === 'Lunas') {
  console.log('Lulus');
}

// jika salah satu operand bernilai false
if (score < 60 && statusBayar === 'Lunas') {
  console.log('Tidak Lulus');
}
```

#### 2. Logical **||** "**OR**"

Akan bernilai ```true``` jika ada minimal satu _operand_ yang bernilai ```true```. Jika semua operandnya ```false``` maka akan bernilai ```false```

Contoh:
```javascript
let score = 70;
let statusBayar = 'Lunas';

// semua operand bernilai true
if (score > 60 || statusBayar === 'Lunas') {
  console.log('Lulus');
}

// salah satu operand bernilai true
if (score < 60 || statusBayar === 'Lunas') {
  console.log('Tidak Lulus');
}

// kedua operand bernilai false
if (score < 60 || statusBayar !== 'Lunas') {
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