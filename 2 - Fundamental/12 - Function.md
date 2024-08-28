# Function

Function adalah sebuah blok _code_ yang bersifat _reusable_ dan biasa digunakan untuk melakukan tugas spesifik.
Dikatakan _reusable_ karena dapat dijalankan kembali kapan saja dan dimana saja diperlukan.

Kita sudah sering lihat dan pakai contoh ```built-in``` function di browser seperti

```javascript
alert('Hello world!');
prompt('Masukan nama kamu:');
confirm('Apakah kamu yakin?');
console.log('Hello world!');
```
Dan kedepan kitapun harus terbiasa membuat dan menggunakan ```function``` buatan sendiri. 

sintaks:

function tanpa parameter

```javascript
function functionName() {
  // code
}
```

function dengan parameter

```javascript
function functionName(param1, param2, ...) {
  // code
}
```

Konsep function sangat mirip seperti function atau _fungsi_ yang kita pelajari dalam Matematika. Dimana sebuah fungsi biasa menerima _input_, memprosesnya lalu menghasilkankan _output_. Misal fungsi matematika berikut 

```math
f(x) = 2x + 1
```

kemudian fungsi ini kita panggil dengan memberi input ```x``` sebuah angka

```math
f(5) = 2 * 5 + 1 = 11
```

Dimana angka ```11``` diatas adalah _output_ yang dihasilkan oleh fungsi ```f```. Kalau kita tulis ke JavaScript kira-kira jadi seperti ini:

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

Sangat jelas terlihat bedanya, dengan function code diatas menjadi lebih terstruktur dan bisa di panggil berulang kali dengan paramater yang lebih dinamis.

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
  let account = getDataFromServer(username, password);
  if (account.exist) {
    return 'login success';
  }

  return 'Username atau password salah';
}

function doLogout() {
  sessionDestroy();
}
```

Bisa terlihat kalau penyusunan code kedalam _function-function_ membuat code lebih terstruktur, mudah dibaca, di modifikasi dan di _refactor_.

### Function Paramater & Argument

Paramater dalam sebuah function adalah variable yang gunakan untuk menampung sebuah value, sedangkan **Argument**
adalah si _value_ nya itu sendiri yang di kirim ke function. Bisa kita terlihat dalam ilustrasi dibawah

<div align="center">
 <img width="460" alt="Function" src="https://github.com/user-attachments/assets/b7471cb8-ba3c-47d0-8708-990ba0c96e67">
</div>

### Function Sebagai Object

Di JavaScript, function adalah ```first-class``` object. Artinya function itu bisa di _passing_ ke function lain atau
di _return_ sebagai sebuah value.

contoh function bisa di _passing_ ke function lain sebagai _argument_.

```javascript
function printMessage() {
  console.log('Hello World!');
}

setTimeout(printMessage, 3000);

// 3 detik kemudian:
// Output : Hello World!
```

contoh lain:

```javascript
function printNumber(num) {
  console.log(num);
}

function add(a, b) {
  return a + b;
}

printNumber(add(10, 10));

// Output : 20

```

contoh function bisa di return sebagai _value_

```javascript
```

### Pure Function
...