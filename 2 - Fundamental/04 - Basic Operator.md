# Basic Operator

Operator adalah symbol matematika yang menghasilkan suatu output ketika di evaluasi dari dua (atau lebih) nilai atau variable. 

Ada banyak operasi yang umum dilakukan saat kita coding di antaranya operasi standar matematika seperti ```penambahan```, ```pengurangan```, ```perkalian```, ```pembagian``` dan ```modulus```.

Kemudian yang paling sering kita coding juga adalah operator untuk ```assignment```, ```comparison```, ```logical```, ```increment/decrement``` dan ```concatenation```. Dan pada tingkat yang lebih _advance_ ada operator Bitwise, namun kita tidak akan membahas Bitwise dalam series ini.

### Operand dan Operator

Penting untuk memahami kedua istilah ini karena kita akan sering menyebut istilah ini dalam keseharian coding kita bahkan mungkin dalam _interview_ kerja.

- Operand: Nilai atau value yang akan dioperasikan
- Operator: Simbol matematika yang mengoperasikan operand
- Result: Hasil dari operasi

Sintaks:
```javascript
 x + y = z
```
Di mana ```x``` dan ```y``` adalah operand, ```+``` dan ```=``` adalah operator dan ```z``` adalah result.

Contoh:
```javascript
let x = 5;
let y = 10;
let z = x + y;
console.log(z); // 15
```

### Operator matematika sederhana

Symbol: ```+```, ```-```, ```*```, ```%```, ```/```, ```**```

Contoh:
```javascript
// operasi penambahan
let a = 4;
let b = 1;
console.log(a + b); // 5

// pengurangan
let x = 10;
let y = 20;
console.log(y - x); // 10

// perkalian
let a = 5;
let b = 10;
console.log(a * b); // 50

// pembagian
let a = 10;
let b = 5;
console.log(a / b); // 2

// modulus
let a = 10;
let b = 2;
console.log(a % b); // 0

// contoh penggunaan modulus untuk cek 
// suatu angka itu ganjil atau genap
let n = 6;

if (n % 2 === 0) {
  console.log('genap')
}

let m = 7;

if (m % 2 === 1) {
  console.log('ganjil')
}

// perpangkatan / exponensial
let z = 2 ** 2; // 2² = 4
```

### Operator assignment

Digunakan untuk meng-_assign_ sebuah value ke suatu variable.

Symbol: ```=```

Contoh:
```javascript
let age = 30;
let name = 'Budi';
let maritalStatus = false;
```
### Operator concatenation

Digunakan untuk menggabungkan dua atau lebih string menjadi suatu text/kalimat tertentu.

Symbol: ```+```

Contoh:
```javascript
let age = 30;
let name = 'Budi';

let result = 'My name is ' + name + ' and my age is ' + age;
console.log(result); 
// Output: My name is Budi and my age is 30;
```
Jika variable dengan tipe ```number``` di concat (```+```) dengan ```string```, maka variable bertipe ```number``` akan otomatis diubah menjadi ```string```.


### Operator increment/decrement

Umumnya digunakan dalam looping atau ketika ada kebutuhan untuk menambah ```+1``` atau mengurangi ```-1``` suatu nilai.

Symbol: ```++```, ```--```

Contoh: 
```javascript
// increment
let counter = 2;
counter++;
console.log(counter); // 3

// penulisan di atas counter++ itu 
// sebenarnya sama dengan
counter = counter + 1;

for (let i = 0; i < 10; i++) {
  console.log(i)
}

// decrement
let counter = 5;
counter--;
console.log(counter); // 4

for (let i = 10; i > 0; i--) {
   console.log(i)
}
```
**Catatan penting operator increment/decrement**
 
Operator ini dibagi menjadi 2 tipe yaitu Postfix dan Prefix.
 
```Postfix``` adalah ketika operator nya diletakan **setelah** variable, syntaks: ```counter++```, ```counter--```.

penulisan dengan cara Postfix membuat nilai variable akan di _return_ dahulu **sebelum** operasi increment/decrement dilakukan

Contoh:
```javascript
// sample #1
let counter = 2;
let x = counter++;
console.log(x); // 2

// sample #2
let counter2 = 3;
console.log(counter2++); // 3
```
Perhatikan pada 2 contoh code di atas, sekilas kita mengira nilai ```x``` harusnya ```3``` dan ```counter2``` harusnya ```4``` namun hasilnya berbeda.
Ini memang agak _tricky_ sehingga kita mesti berhati-hati.

Pada baris ```let x = counter++``` yang terjadi adalah variable ```counter``` akan segera me-return value originalnya yaitu ```2``` (sebelum proses increment/decrement terjadi) kemudian di assign ke ```x``` sehingga nilai ```x``` adalah 2, sama dengan nilai ```counter``` originalnya.

Kemudian pada sample ```#2```, nilai variable ```counter2``` tetap ```3```, karena saat proses evaluasi syntaks ```console.log(counter2++)```, nilai original dari ```counter2``` sudah di return duluan sehingga langsung ke-print ke console.

Nilai variable ```counter2``` akan ```4``` ketika kita kembali mengakses variable itu di baris berikut nya.

```javascript
let counter2 = 3;
console.log(counter2++); // 3
console.log(counter2++); // 4
```
Ini terjadi karena ```counter2``` sudah di increment/decrement sebelumnya di baris ke-2, sehingga saat kita akses berikutnya, maka nilai nya sudah bertambah.

> **Catatan**:
> Silahkan kamu coba sendiri contoh code di atas yah agar semakin paham.
 
```Prefix``` adalah ketika operator nya diletakkan **sebelum** variable, syntaks: ```++counter```, ```--counter```

Increment/decrement dalam bentuk ```prefix``` akan me-return value terbaru setelah proses increment/decrement nya terjadi

```javascript
let counter = 3;
console.log(++counter); // 4

let counter2 = 3;
console.log(--counter2); // 2
```

Di lapangan kebanyakan kita akan menggunakan operator ```++``` dan ```--``` itu ketika menggunakan ```loop```. Saat menggunakan loop, tidak menjadi masalah mau pakai bentuk Postfix atau Prefix.

```javascript
// Postfix
for (let i = 0; i < 5; i++) {
  console.log(i); // 0, 1, 2, 3, 4
}

for (let i = 4; i >= 0; --i) {
  console.log(i); // 4, 3, 2, 1, 0
}

// prefix
for (let i = 0; i < 5; ++i) {
 console.log(i); // 0, 1, 2, 3, 4
}
```