# Comparison Operator


Atau Operator Perbandingan adalah operator yang digunakan untuk membandingkan dua buah _value_ atau variable. Ada banyak operator perbandingan yang biasa digunakan untuk membandingkan dua buah variable yaitu: 

| Operator | Deskripsi |
| -------- | --------- |
| ==       | Sama dengan |
| ===      | _Strict equality_, Cek kesamaan value **dan** tipe data-nya |
| !=       | Tidak sama dengan |
| !==      | _Strict equality_, Cek ketidaksamaan value **atau** tipe data-nya |
| >        | Lebih dari |
| <        | Kurang dari |
| >=       | Lebih dari atau sama dengan |
| <=       | Kurang dari atau sama dengan |

Output dari operator perbandingan ini adalah ```true``` atau ```false```.

Perhatikan contoh operator perbandingan beserta outputnya berikut:

```javascript
let x = 5;
let y = 5;

console.log(x == y); // true
console.log(x === y); // true
console.log(x != y); // false
console.log(x >= y); // true
console.log(x <= y); // true

let a = '5';
let b = 5;

console.log(a == b); // true
console.log(a === b); // false, karena tipe data-nya berbeda

let c = 3;
let d = 5;

console.log(c < d); // true
console.log(c > d); // false
console.log(c >= d); // false
console.log(c <= d); // true

let name = 'Budi';
let name2= 'Agus';

console.log(name == name2); // false
console.log(name === name2); // false
console.log(name != name2); // true
```

Seringkali kita juga harus hati-hati ketika membandingkan type data yang berbeda seperti pada contoh dibawah

1. JavaScript akan mengkonversi string menjadi number

```javascript
let a = 5;
let b = '3';

console.log(a > b); // true
console.log('01' == 1); // true
```
2. Untuk boolean, ```true``` dikonversi menjadi ```1```, ```false``` dikonversi menjadi ```0```

```javascript

console.log(true == 1); // true
console.log(false == 0); // true
console.log(false === 0); // false, karena Strict check
```

Pada prakteknya sebaiknya kita mendahulukan penggunaan **strict equality** operator karena ini
sangat membantu untuk mencegah dan meminimalisir **bugs**.