# Function

Function adalah sebuah blok _code_ yang bersifat _reusable_ dan biasa digunakan untuk melakukan tugas spesifik.
Dikatakan _reusable_ karena dapat dijalankan kembali kapan saja dan dimana saja diperlukan.

Kita sudah sering lihat dan pakai contoh ```built-in``` function di browser seperti

```javascript
alert('Hi JS!');
prompt('Masukan nama kamu:');
confirm('Apakah kamu yakin?');
console.log('Hi JS!');
```
Dan kedepan kitapun harus terbiasa membuat dan menggunakan ```function``` buatan sendiri. 

sintaks:

Function tanpa parameter

```javascript
function functionName() {
  // code
}
```

Function dengan parameter

```javascript
function functionName(param1, param2, ...) {
  // code
}
```

Konsep function sangat mirip seperti function atau _fungsi_ yang kita pelajari dalam Matematika. Dimana sebuah fungsi biasa menerima _input_, memprosesnya lalu menghasilkankan _output_. Misal fungsi matematika berikut 

&emsp;<math xmlns="http://www.w3.org/1998/Math/MathML"><mi>f</mi><mo>(</mo><mi>x</mi><mo>)</mo><mo>&#xA0;</mo><mo>=</mo><mo>&#xA0;</mo><mn>2</mn><mi>x</mi><mo>&#xA0;</mo><mo>+</mo><mo>&#xA0;</mo><mn>1</mn></math>

kemudian fungsi ini kita panggil dengan memberi input <math xmlns="http://www.w3.org/1998/Math/MathML"><mi>x</mi></math> sebuah angka

&emsp;<math xmlns="http://www.w3.org/1998/Math/MathML"><mi>f</mi><mo>(</mo><mn>5</mn><mo>)</mo><mo>=</mo><mn>2</mn><mo>&#x2217;</mo><mn>5</mn><mo>+</mo><mn>1</mn><mo>=</mo><mn>11</mn></math>

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

Paramater dalam sebuah function adalah variable yang gunakan untuk menampung sebuah value, sedangkan **Argument**
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

**Note**: Function diatas juga bisa langsung di panggil seperti berikut. (perhatikan kurung nya dua kali)

```javascript
let msg = printName('Mr.')('Budi');
console.log(msg);
// Output: Hello Mr. Budi!
```

-  **Function di-_assign_ ke variable**

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

Karena di JavaScript function itu _first-class_ object, maka akan kita temui banyak sekali berbagai operasi dan penggunaannya. Oleh karena itu wajib banget latihan terus membuat function dengan berbagai variasi dan contoh-contoh seperti diatas agar semakin faham dan terbiasa.

### Pure Function
...