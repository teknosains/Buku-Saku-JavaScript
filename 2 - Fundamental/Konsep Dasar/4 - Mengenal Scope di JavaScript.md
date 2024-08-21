# Mengenal Scope di JavaScript


> **Perhatian!**. Materi ini sejujurnya memang bisa cukup sulit dicerna oleh pemula. _The good news is_ kamu boleh skip dulu materi ini dan langsung lanjut saja ke materi fundamental selanjutnya.

Scope adalah salah satu konsep fundamental yang **wajib** diketahui dan difahami sebelum lebih jauh belajar JavaScript. Scope sejatinya adalah _access_. Scope di JavaScript berbicara tentang bagaimana dan dimana variable-variable dapat diakses atau tidak dapat diakses.

Memahami scope di JavaScript begitu penting karena dapat membantu kita menulis code yang lebih efisien, meminimalisir bugs dan bisa juga membantu kita membuat ```pure function```, yaitu function murni yang tidak bergantung kepada variable atau object lain yang ada diluar function tersebut. Kita akan lebih dalam mengenal ```pure function``` di pembahasan berikutnya mengenai Function.

Ada tiga scope utama di JavaScript yang wajib diketahui yaitu:

- ```Global scope```
- ```Local scope```
- ```Block scope```

### Global scope
Sebuah variable dikatakan berada di _Global scope_ jika di deklarasi diluar function atau block tertentu. Global scope ini juga berarti variable yang ada disana bisa diakses dimanapun di script js kita bahkan di halaman web kita.

Misal kita punya sebuah file ```index.js``` yang isinya seperti berikut:

```javascript
let greeting = 'Hello world!';

// code yang lain
// code yang lain

console.log(greeting);

// Output: Hello world!

function sayHello() {
  console.log(greeting);
}

sayHello();

// Output: Hello world!
```

variable ```greeting``` diatas berada di global scope karenanya ia bersifat global, jadi bisa di akses dibaris manapun di file ```index.js``` tersebut.

Para pembuat browser sudah menyematkan global variable / object bernama ```window``` yang sering kita gunakan dan bisa di akses dimanapun dan di dalam file script js manapun.

Function-function seperti berikut ini sering kali digunakan dalam keseharian coding JavaScript nantinya.

```javascript
alert()
console.log()
setTimeout()
setInterval()
```
Function-function diatas adalah bagian dari object global ```window``` dan tersedia secara global. Jadi bisa di akses dimana saja
bahkan tanpa menuliskan object ```window``` nya khusus seperti berikut

```javascript
window.alert('hello');
window.console.log('hello);
```

cukup kita tulis seperti ini

```javascript
alert('hello');
console.log('hello);
```

### Local scope

Atau biasa disebut juga _Function scope_. Sebuah variable dikatakan berada di _Local scope_ jika di deklarasi didalam suatu function dan hanya bisa diakses didalam function itu sendiri pula.

contoh:

```javascript
function sayHello() {
  let greeting = 'Hello world!';
  console.log(greeting);
}
sayHello();

// Output: Hello world!
```

variable ```greeting``` diatas berada di _local scope_ jadi hanya bisa di akses didalam function ```sayHello()``` saja. Jika kita coba akses diluar function nya maka akan error.

```javascript
function sayHello() {
  let greeting = 'Hello world!';
}
console.log(greeting);
sayHello();

// ReferenceError: greeting is not defined
```

### Block scope

Sebuah variable dikatakan berada di _Block scope_ jika di deklarasi menggunakan ```let``` dan ```const``` dan berada didalam block  ```{ }```. Jadi variable ini hanya bisa diakses di dalam block tersebut.

contoh:

```javascript
let score = 70;

if (score >= 70) {
  let isPass = 'Yes';
  console.log(isPass);
}

// Output: Lulus
```

Jika kita coba akses ```isPass``` diluar kurawal ```{ }``` statement ```if``` nya, maka akan error. Karena variable ```isPass``` hanya bisa diakses di dalam block ```{ }``` ini.

```javascript
let score = 70;

if (score >= 70) {
  let isPass = 'Yes';
}
console.log(isPass);

// ReferenceError: isPass is not defined
```

Lain hal jika kita menggunakan ```var```, karena ```var``` selalu bersifat _Local scope_ maka meski di deklarasi di dalam block ```{ }``` baik itu dalam ```if```, ```for```, ```while``` dll (kecuali dalam Function), maka dia akan di _hoisting_ alias diangkat ke atas oleh JavaScript.

contoh:

```javascript
let score = 70;

if (score >= 70) {
  var isPass = 'Yes';
}
console.log(isPass);

// Output: Yes
```

di belakang layar akan diubah menjadi

```javascript
var isPass; // di angkat / hoisted ke sini
let score = 70;

if (score >= 70) {
  isPass = 'Yes';
}
console.log(isPass);

// Output: Yes
```

Jadi variable ```isPass``` tetap bisa di akses diluar block ```{ }```. Oleh karena saat ini deklarasi variable disarankan menggunakan ```let``` atau ```const``` saja.

### Lexical scope (tambahan)

Sebuah variable dikatakan berada di _Lexical scope_ jika di deklarasi diluar function namun dapat di akses didalam function tersebut.

contoh:

```javascript

function checkScore() {
  let score = 70;
  
  function printScore() {
    console.log(score);
  }

  printScore();
}

checkScore();

// Output: 70
```

Cara membaca scope diatas adalah yaitu: 

- bagi function checkScore(), variable ```score``` berada di local scope-nya.
- namun bagi function printScore(), variable ```score``` berada di lexical scope-nya.

Dengan kata lain lexical scope juga bisa diartikan yakni kemampuan sebuah function untuk dapat mengakses variable milik _parent_ nya.

```javascript
function parent() {
  let name = 'Agus';

  function child() {
    console.log('Budi bin ' + name);
  }

  child();
}

parent();

// Output: Budi bin Agus
```

### Hoisting

Hoisting adalah kondisi dimana JavaScript engine akan memindahkan semua deklarasi ```variable```, ```function``` dan ```class``` ke bagian atas dari _scope_ sebelum dieksekusi.

#### Hoisting variable

Misal kita punya sebuah file ```index.js``` yang berisi

```javascript
console.log(age);
var age = 'Budi';

// Output: undefined
```

Terlihat bahwa variable ```age``` tetap bisa di akses (tidak error) meski dipanggil sebelum dideklarasi ```var age = 'Budi'```. Itu karena variable dengan ```var``` akan dihosting keatas dan otomatis akan di inisialisasi default value ```undefined```. Sederhananya, si JavaScript engine dibelakang layar akan melakukan ini

```javascript
var age; // di hoisting kesini
console.log(age);
age = 'Budi';

// Output: undefined
```

Adapun deklarasi variable dengan ```let``` dan ```const``` sebenarnya tetap sama-sama di hoisting oleh JavaScript engine. Hanya saja mereka punya behavior yang berbeda dengan ```var```.

Perhatikan contoh berikut:

```javascript
console.log(age);
let age = 'Budi';

// ReferenceError: Cannot access 'age' before initialization

console.log(score);
const score = 70;

// ReferenceError: Cannot access 'score' before initialization
```

Sebenarnya dibelakang layar variable ```name``` dan ```score``` tetap dihoisting keatas namun tanpa dikasih default value. Sedangkan variable yang di deklarasi dengan ```let``` dan ```const``` hanya bisa diakses setelah di inisialisasi alias harus di kasih default value terlebih dahulu. Oleh karena itu contoh code diatas akan menghasilkan error.

Kita bisa perbaiki code nya menjadi seperti ini

```javascript
let age = 'Budi';
console.log(age);

// Output: Budi

const score = 70;
console.log(score);

// Output: 70
```

atas dasar

#### Hoisting function
...

#### Hoisting class
....

Mengingat begitu penting nya bagian ini, oleh karena itu baiknya dibaca lagi beberapa kali dan jika perlu dikombinasikan dengan sumber lainnya agar semakin faham.