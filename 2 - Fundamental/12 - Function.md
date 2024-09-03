# Function

Function adalah sebuah blok _code_ yang bersifat _reusable_ dan biasa digunakan untuk melakukan tugas spesifik.
Dikatakan _reusable_ karena dapat dipanggil kembali kapan saja dan dimana saja diperlukan.

Kita sudah sering lihat dan pakai contoh ```built-in``` function di browser seperti

```javascript
alert('Hi JS!');
prompt('Masukan nama kamu:');
confirm('Apakah kamu yakin?');
console.log('Hi JS!');
```
Dan kedepan kitapun harus terbiasa membuat dan menggunakan ```function``` buatan sendiri. 

sintaks:

```javascript
// tanpa parameter

function functionName() {
  // body
}

// dengan parameter

function functionName(param1, param2, ...) {
  // body
}
```

Agar sebuah function bisa jalan atau melakukan tugasnya tentu saja harus dipanggil dulu. Dibawah adalah contoh cara _call_ sebuah function.

```javascript
function functionName(param1) {
  console.log('Hi JS!');
}

functionName(); // call

// Output: Hi JS!
```

Konsep function sangat mirip seperti function atau _fungsi_ yang kita pelajari dalam Matematika. Dimana sebuah fungsi biasa menerima _input_, memprosesnya lalu menghasilkan _output_. Misal fungsi matematika berikut 

&emsp;&nbsp;<math xmlns="http://www.w3.org/1998/Math/MathML"><mi>f</mi><mo>(</mo><mi>x</mi><mo>)</mo><mo>&#xA0;</mo><mo>=</mo><mo>&#xA0;</mo><mn>2</mn><mi>x</mi><mo>&#xA0;</mo><mo>+</mo><mo>&#xA0;</mo><mn>1</mn></math>

kemudian fungsi ini kita panggil dengan memberi input <math xmlns="http://www.w3.org/1998/Math/MathML"><mi>x</mi></math> sebuah angka

&emsp;&nbsp;<math xmlns="http://www.w3.org/1998/Math/MathML"><mi>f</mi><mo>(</mo><mn>5</mn><mo>)</mo><mo>=</mo><mn>2</mn><mo>&#x2217;</mo><mn>5</mn><mo>+</mo><mn>1</mn><mo>=</mo><mn>11</mn></math>

Angka ```11``` diatas adalah _output_ yang dihasilkan oleh fungsi ```f```. Kalau kita tulis ke JavaScript kira-kira jadi seperti ini:

```javascript
function f(x) {
  return 2 * x + 1;
}

console.log(f(5));
// Output: 11
```

Saat coding, Function kita buat saat code-code yang kita tulis dirasa butuh untuk dijadikan satu proses sendiri yang bisa di panggil berkali-kali. Ini juga membuat code kita menjadi lebih terstruktur dan mudah dibaca.

```javascript
let a = 5;
let b = 10;

let c = a + b;

console.log(c);
// Output: 15
```

Daripada menuliskan code seperti diatas, lebih baik kita jadikan function seperti berikut:

```javascript
function add(a, b) {
  return a + b;
}

let c = add(5, 15);
console.log(c);
// Output: 15

let e = add(10, 10);
console.log(e);
// Output: 20
```

Sangat jelas terlihat bedanya, dengan function code diatas menjadi lebih terstruktur dan bisa di panggil berulang kali dengan _argument_ yang lebih dinamis.

Contoh lagi yang lebih _real_ misal kita membuat fitur untuk mengelola _Account_ dalam aplikasi. Kita bisa susun
proses-proses yang terjadi kedalam sebuah file dengan function-function yang sesuai.

Misal kita buat sebuah file ```account.js``` dengan isi seperti:

```javascript
function registerUser(form) {
  let user = {
    username: form.username,
    password: form.password,
    email: form.email,
    name: form.name,
  };

  let save = submitToServer(user);
  if (save) {
    return 'Register berhasil';
  }

  return 'Register gagal. Silahkan coba lagi';
}

function doLogin(username, password) {
  // pura-pura nya get data ke DB
  let verify = verifyAccout(username, password);
  if (verify) {
    return 'login success';
  }

  return 'Username atau password salah';
}

function doLogout() {
  sessionDestroy();
}
```

Bisa terlihat kalau penyusunan code kedalam _function-function_ membuat code lebih terstruktur, mudah dibaca, di modifikasi dan di _refactor_.

### Statement ```return```

Hal yang umum saat membuat function adalah kita tulis juga statement ```return``` di akhir function. Statement ```return``` normalnya digunakan untuk men-_stop_ eksekusi function dan me-return _value_-nya, namun kadang juga ```return``` digunakan **hanya** untuk men-_stop_ eksekusi function seperti saat melakukan _debugging_.

```javascript
function checkStatus(score) {
  if (score > 70) {
    return 'Lulus';
  }

  return 'Tidak lulus';
}
```

Statement ```return``` saat digunakan untuk _debug_

```javascript
function doLogin(username, password) {
  if (username !== '') {
    console.log('masuk sini');
    return;
    // code dibawah gk akan di eksekusi
    let check = checkToServer(username, password);
    // ...
  }

  return 'Malah masuk sini';
}
```

Function juga sah-sah saja meski tidak punya statement ```return```. Namun jika tidak ada statement ```return``` nya, by default JavaScript sebenarnya akan me-return ```undefined```. Kita bisa buktikan behaviour ini dengan cara berikut

```javascript
function doLogin() {
  // kosongin aja  
}

let login = doLogin();
console.log(login);

// Output: undefined
```

### Function Paramater & Argument

Paramater dalam sebuah function adalah variable yang digunakan untuk menampung sebuah value, sedangkan **Argument**
adalah si _value_ nya itu sendiri yang di kirim ke function. Agar lebih mudah difahami, perhatikan ilustrasi dibawah

<div align="center">
 <img width="460" alt="Function" src="https://github.com/user-attachments/assets/0e0df713-feda-4182-85e2-a4cccd6579d8">
</div>

### Function Sebagai Object

Di JavaScript, function adalah ```first-class``` object. Artinya function itu bisa di _passing_ ke function lain, di _return_ dari function dan di-_assign_ ke sebuah variable.

- **Function di _passing_ ke function lain sebagai _argument_**

```javascript
function printMessage() {
  console.log('Hi JS!');
}

setTimeout(printMessage, 3000);

// 3 detik kemudian:
// Output: Hi JS!
```

contoh lain:

```javascript
function printNumber(num) {
  console.log(num(10,10));
}

function add(a, b) {
  return a + b;
}

printNumber(add);

// Output: 20
```

Sering juga orang (termasuk kami :D) menulis seperti ini, langsung masukin function nya _as argument_

```javascript
setTimeout(function () {
  console.log('Hi JS!');
}, 3000);

// 3 detik kemudian:
// Output: Hi JS!

let btn = document.getElementById('button');
btn.addEventListener('click', function () {
  alert('Hi JS!');
});
```

Di javascript function tanpa paramater-pun bisa kita passing-kan argument dan bisa kita cek isinya apa saja dengan statement ```argument```. Perhatikan dan cobalah contoh berikut:

```javascript
function tanpaParamater() {
  console.log(arguments); 
  // Output: { 0: 'Budi', 1: '35', 2: 'Pria' }
  console.log(arguments.length);
  // Output: 3
  console.log(arguments[0]); 
  // Output: Budi
}

tanpaParamater('Budi', '35', 'Pria');
```

- **Function bisa di return dari function**

```javascript
function printName(prefix) {
  return function (name) {
    return `Hello ${prefix} ${name}!`;
  }
}

let msg = printName('Mr.');
console.log(
  msg('Budi')
);
// Output: Hello Mr. Budi!
```

**Note**: Function diatas juga bisa langsung di panggil seperti berikut.

```javascript
let msg = printName('Mr.')('Budi');
console.log(msg);
// Output: Hello Mr. Budi!
```
Perhatikan kurung nya dua kali, ```printName('Mr.')('Budi')```, ini disebut juga dengan _currying_. Kita akan bahas lebih dalam tentang _currying_ di Chapter 3.

-  **Function bisa di-_assign_ ke variable**

```javascript
const printName = function(name) {
  console.log(name);
}

printName('Budi');
// Output: Budi

let printTitle = function(title) {
  console.log('S.kom');
}

printTitle();
// Output: S.kom
```

Penulisan function ke sebuah variable disebut juga dengan istilah _function expression_.

Karena di JavaScript function itu _first-class_ object, maka akan kita temui banyak sekali berbagai operasi dan penggunaannya. Oleh karena itu wajib banget latihan terus membuat function dengan berbagai variasi dan contoh-contoh seperti diatas agar semakin faham dan terbiasa.

### Mengenal istilah Pure Function

_Pure Function_ adalah function yang memenuhi dua syarat berikut:

1. Jika diberikan argument / input yang sama, maka outputnya tetap atau selalu sama
2. Tidak menghasilkan _side-effect_. 

Perhatikan contoh berikut

```javascript
function add(a, b) {
  return a + b;
}

console.log(sum(1, 2)); // 3
console.log(sum(1, 2)); // 3

console.log(add(2, 3)); // 5
console.log(add(2, 3)); // 5
```

Function ```add()``` diatas adalah _pure_ karena ketika diberi input yang sama meski di panggil berulang kali, maka outputnya tetap sama. Karena jika tiba-tiba hasilnya beda, maka tentu ini berpotensi bahaya dan malah akan jadi bugs. Oleh karena itu _pure function_ sebisa mungkin harus hindari mengakses variable global.

```javascript
let minAge = 17; // di global scope

function canDrive(age) {
  if (age < minAge) {
    return false;
  }

  return true;
}
```

Function ```canDrive()``` diatas bergantung ke variable ```minAge``` artinya jika value ```minAge``` nya berubah maka outputnya akan berubah. Bagaimana jika tiba-ba variable ```minAge``` ada yang rubah jadi _string_ misal?

Kemudian _pure function_ juga tidak boleh boleh menghasilkan _side-effect_ yaitu jika sebuah function ternyata melakukan sesuatu yang bisa merubah _external state_. Contoh side-effect diantaranya adalah:

1. Print ke console
2. Melakukan http request ke network
3. Me-mutasi objects atau array
4. Merubah value variable global
5. Manipulasi DOM

Perhatikan contoh berikut dimana function nya merubah _external state_.

```javascript
let total = 0;

function addTotal(value) {
  total += value;

  return total;
}

console.log(addTotal(1)); // 1
console.log(addTotal(1)); // 2
```

Terlihat bahwa function ```addTotal()``` diatas dapat merubah nilai variable ```total``` dan ketika dipanggil beberapa kali dengan input yang sama, akan menghasilkan output yang berbeda. Maka ini bukan _pure_ function, tetapi disebut dengan _impure_ function. 

Contoh lainnya misal jika sebuah function bisa memutasi / merubah array yang di _passing_ kedalam nya.

```javascript
function printList(arr) {
  arr.push('Budi'); // merubah array

  return arr;
}
```

Namun contoh dibawah ini adalah _pure_ function

```javascript
function sumOfArray(array) {
  return array.reduce(function(sum, item) {
    return sum + item;
  });
}

console.log(
  sumOfArray([1, 2])
);
// Output: 3

console.log(
  sumOfArray([1, 2])
);
// Output: 3
```

Karena function ```sumOfArray()``` diatas tidak merubah / memutasi array ```array``` yang di _passing_ dan akan tetap mengembalikan value yang sama jika diberi input yang sama meski di panggil berkali-kali.

Kemudian bahkan bukan dikatakan _pure function_ meski hanya nge-print ke console seperti ini

```javascript
function printList(arr) {
  // proses lain
  console.log(arr); 
}
```

karena print sesuatu ke console artinya function itu melakukan operasi I/O (input output).

Dari penjelasan dan contoh-contoh diatas, menjadi lebih _clear_ pula bagi kita apa itu _impure function_. Setiap function yang kebalikan dari kriteria _pure_ function, disebut _impure function_. Coba kita beri contoh satu kali lagi, perhatikan ```built-in``` function dibawah ini

```javascript
console.log(Math.random());
// Output: 0.8015508440779233

console.log(Math.random());
// Output: 0.6170121093075762
```
```Math.random()``` adalah contoh paling nyata _impure function_. Setiap kali dipanggil akan menghasilkan output yang berbeda. 

Khusus ketika kita _bermain_ dengan Object dan Array, direkomendasikan untuk membuat function yang _pure_ yaitu tidak memutasi object original nya, namun dengan membuat / me-return object baru yang sudah dimodif. Perhatikan contoh _impure function_ berikut

```javascript
function makeAnimal(obj) {
  obj.species = 'Ayam';
  // other process
  // ...
  return obj;
}

let originalObject = { species: 'Kucing', color: 'Coklat' };

let newAnimal = makeAnimal(originalObject);

console.log(originalObject);
// Output: { color: "Coklat", species: "Ayam" }

console.log(newAnimal);
// Output: { color: "Coklat", species: "Ayam" }
```

Terlihat kalau ```originalObject``` ternyata akhirnya jadi sama dengan ```newAnimal```, padahal mungkin yang kita harapkan adalah ```originalObject``` tetap sama alias tidak berubah. Bayangkan misal ada bagian code lain yang sedang memakai variable ```originalObject```, maka akan ikut berubah juga.

```javascript
let anggora = originalObject;

console.log(anggora);
// Output: { color: "Coklat", species: "Ayam" }
```

Dalam case ini, maka sebaiknya gunakan _pure function_. Kita rubah function ```makeAnimal()``` menjadi _pure function_ seperti ini

```javascript
function makeAnimal(obj) {
  return {
    ...obj, // spread operator
    species: 'Ayam'
  };
}

let originalObject = { species: 'Kucing', color: 'Coklat' };

let newAnimal = makeAnimal(originalObject);

console.log(originalObject); 
// Output: { species: 'Kucing', color: 'Coklat' }

console.log(newAnimal); 
// Output: { species: 'Ayam', color: 'Coklat' }
```

Pada versi ini, function ```makeAnimal()``` membuat object baru menggunakan _spread operator_ pada paramater object ```obj``` dan mengubah property ```species``` menjadi ```Ayam```. Dengan cara ini, object aslinya yaitu ```originalObject``` tetap sama alias tidak berubah.

Antara _Pure Function_ dan _Impure Function_ keduanya sebenarnya bukan untuk diperbandingkan dan bukan pula yang satu lebih baik dari yang lain. Keduanya digunakan sesuai dengan use-case nya (yang tepat) masing-masing.

> Notes: Karena materi mengenai Function sudah pasti panjang, kami kembali menyarankan agar mengulang semua materi Function diatas dan mencoba nya sendiri sebelum lanjut ke pembahsan Function selanjutnya.


### Function Expression

Kita sudah mengetahui bahwa Function adalah ```first-class``` object di JavaScript yang salah satu cirinya adalah bahwa function bisa di _assign_ ke variable. Kemampuan ini juga disebut sebagai ```Function Expression```, bertambah lagi istilah yang harus kita hafal, tapi disinilah justru letak seni nya kita belajar fundamental.

Yang kita sudah pelajari dari potongan-potongan contoh diatas kebanyakannya adalah kita membuat function dengan ```Function Declaration```. Yaitu ketika membuat function dengan sintaks ```function functionName() { ... }```

```javascript
// Function Declaration

function printMessage(name) {
  return `Hi, ${name}. Selamat Datang!`;
}
```

Adapun ```Function Expression```, kita bisa gunakan keyword ```var```, ```let``` dan ```const``` untuk deklarasi variable nya kemudian me-assign function nya. Perhatikan contoh berikut:

```javascript
const printMessage = function (name) {
  return `Hi, ${name}. Selamat Datang!`;
};

console.log(printMessage('Budi'));
// Output: Hi, Budi. Selamat Datang!

let printTitle = function (title) {
  return `Gelar: ${title}`;
};

console.log(printTitle('Sarjana'));
// Output: Gelar: Sarjana
```

Kita bebas membuat function dengan ```Function Declaration``` atau ```Function Expression``` namun yang yang diperhatikan adalah adanya perbedaan kondisi _hoisting_ (lihat materi ```Konsep Dasar > Mengenal Scope di JavaScript```) pada _function declaration_ dan _function expression_. Function expression tidak di ```hoisting``` sehingga hanya bisa di panggil **setelah di definisikan**.

```javascript
let printTitle = function (title) {
  return `Gelar: ${title}`;
};

console.log(printTitle('Sarjana'));
// Output: Gelar: Sarjana
```

Dalam contoh ini, function ```printTitle``` hanya bisa di panggil setelah ```printTitle``` di definisikan. Jika tidak, maka akan error seperti ini

```javascript
console.log(printTitle('Sarjana'));

let printTitle = function (title) {
  return `Gelar: ${title}`;
};

// Output: ReferenceError: Cannot access 'printTitle' 
//         before initialization
```

Berbeda dengan Function Declaration yang di ```hoisting```, function ```printTitle``` bisa di panggil bahkan **sebelum** ```printTitle``` di definisikan. 

```javascript
console.log(printTitle('Sarjana'));

function printTitle(title) {
  return `Gelar: ${title}`;
}

// Output: Gelar: Sarjana
```

Berikutnya, Function Expression juga bisa di tulis menggunakan ```Arrow Function``` yang akan kita bahas secara khusus dibawah ini

### Arrow Function

Arrow function adalah alternatif lain ketika membuat function menggunakan function expression. Seperti _nama_-nya, arrow function menggunakan operator ```=>```, sudah tidak lagi menggunakan statement ```function```.

Beberapa sintaks ```Arrow Function``` yang bisa digunakan

```javascript

// tanpa parameter

const functionName = () => {
  // code...
}

// dengan satu parameter

const functionName = param => {
  // code...
}

// dengan parameter lebih dari satu

const functionName = (param1, param2, ...) => {
  // code...
}
```

Misal kita punya function expression berikut

```javascript
const printMessage = function (name) {
  return `Hi, ${name}. Selamat Datang!`;
};
```

Maka kita bisa buat / konversi ke bentuk arrow function menjadi

```javascript
const printMessage = (name) => {
  return `Hi, ${name}. Selamat Datang!`;
};
```

Ketika expression nya pendek atau satu baris saja, arrow function bisa di tulis tanpa kurung ```{ }```.  Perhatikan contoh berikut

```javascript
let add = (a, b) => {
  return a + b;
};
```

Kita bisa ubah kedalam bentuk arrow function tanpa ```{ }``` menjadi seperti ini

```javascript
let add = (a, b) => a + b;

console.log(add(10, 10));
// Output: 20
```

Perhatikan bahwa statement ```return``` dan kurung ```{ }``` dihilangkan, menjadikan penulisan nya lebih singkat. Namun bagi sebagian orang, mungkin penulisan seperti itu bukan pilihan utama dan memang bagi pemula bisa cukup membingungkan. Jadi tidak ada masalah jika kita lebih _prefer_ menuliskan ```return``` dan ```{ }``` nya

```javascript
let add = (a, b) => {
  return a + b;
};
```

karena penulisan seperti diatas cukup memberikan flexsibilitas dan lebih terlihat "familiar" bagi semua orang.

Karena _simplicity_-nya juga, arrow function menjadi favorit banyak developer JavaScript dan paling sering digunakan sebagai _callback_ function. Perhatikan contoh berikut:

```javascript
setTimeout(function () {
  console.log('Hi JS!');
}, 3000);
```

Penulisan diatas bisa ditulis kedalam bentuk arrow function seperti ini

```javascript
setTimeout(() => {
  console.log('Hi JS!');
}, 3000);

// 3 detik kemudian:
// Output: Hi JS!
```

contoh lagi, arrow function banyak digunakan sebagai callback untuk method-method ```built-in``` dalam ```Array```.

```javascript
let arr = [1, 2, 3, 4, 5];

let arr2 = arr.map((val) => val + 1);

console.log(arr2);
// Output: [2, 3, 4, 5, 6]
```

contoh lagi

```javascript
let data = [
  { name: "Budi", age: 33 },
  { name: "Ahmad", age: 27 },
  { name: "Siti", age: 30 },
];

let data2 = data.filter((val) => val.age > 30);

console.log(data2);
// Output: [{ name: "Budi", age: 33 }]
```

contoh satu lagi

```javascript
let data2 = data.map((val, index) => {
  return {
    ...val,
    country: "Indonesia",
    no: index + 1,
  }
});

console.log(data2);
// Output:

/*
[{name: 'Budi', age: 33, country: 'Indonesia', no: 1},
{name: 'Ahmad', age: 27, country: 'Indonesia', no: 2},
{name: 'Siti', age: 30, country: 'Indonesia', no: 3}]
*/
```

Sekarang kamu bisa mulai perbanyak dan membiasakan memakai arrow function saat membuat _callback_ function terutama saat bermain dengan method-method ```built-in``` di ```Array```
