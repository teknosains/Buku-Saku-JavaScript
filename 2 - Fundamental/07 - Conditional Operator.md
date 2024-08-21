# Conditional Operator

Conditional Operator atau disebut juga _ternary operator_ adalah operator yang biasa digunakan sebagai _shortcut_ dari statement ```if-else```.

Sintaks:
```javascript
condition ? expression1 : expression2
```

Pada contoh diatas, jika ```condition``` bernilai _Truthy_, maka ```expression1``` akan di eksekusi, jika ```condition``` bernilai _Falsy_ atau _Nullish_, maka ```expression2``` akan di eksekusi.

contoh:

```javascript
let score = 70;

// dengan if-else

let status = '';
if (score > 60) {
  status = 'Lulus';
} else {
  status = 'Tidak lulus';
}
console.log(status); 
// Output: Lulus

// dengan ternary "?"

let status = score > 60 ? 'Lulus' : 'Tidak lulus';
console.log(status);
// Output: Lulus
```

Ternary operator cocok digunakan untuk membuat sebuah variable yang value nya bergantung kepada suatu kondisi tertentu. Terlihat
operator ini juga membuat _conditional statement_ menjadi lebih ringkas (cukup satu baris atau istilah populer nya one liner).

```Condition``` pada ternary operator bisa lebih dari satu kondisi dan ini umum dilakukan pada praktek coding di dunia nyata (real world). 

contoh:
```javascript
let score = 70;
let gpa = 3.5;
let status2 = (gpa >= 3.5 && score >= 70) ? 'Cumlaude' : 'Tidak Cumlaude';
console.log(status2);
// Output: Cumlaude
```

### Conditional Chains

Mirip dengan pengunaan statement ```if...else if...else```, ternary operator juga bisa digunakan untuk membuat kondisi berantai.

Perhatikan statement berikut:

```javascript
let score = 70;
let status = '';

if (score >= 90) {
  status = 'Lulus sempurna';
} else if (score >= 60 && score < 90) {
  status = 'Lulus bersyarat';
} else {
  status = 'Tidak lulus';
}

console.log(status);

// Output: Lulus bersyarat
```

dapat ditulis menggunakan ternary operator seperti ini:

```javascript
let score = 70;
let status = score >= 90 ? 'Lulus sempurna' 
  : score >= 60 ? 'Lulus bersyarat' 
  : 'Tidak lulus';

console.log(status);

// Output: Lulus bersyarat
```
**Tips**: Jika belum terbiasa atau merasa kondisi berantai itu malah sulit, gunakan ```else if``` saja.
