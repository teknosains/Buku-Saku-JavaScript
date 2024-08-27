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

Function kita buat saat code-code yang kita tulis dirasa butuh untuk dijadikan satu proses sendiri yang bisa di panggil berkali-kali. Ini juga membuat code kita menjadi lebih terstruktur dan mudah dibaca.

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

Contoh lagi yang lebih real misal kita membuat fitur untuk mengelola _Account_ dalam aplikasi. Kita bisa susun
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

  if (save === true) {
    return 'Register berhasil';
  }

  return 'Register gagal';
}

function doLogin(username, password) {
  // pura-pura nya get data ke DB
  let account = getDataFromServer(username, password);
  if (account.exist) {
    return 'login success';
  }

  return 'login failed';
}

function doLogout() {
  sessionDestroy();
}
```

### Function Sebagai Object

Di JavaScript, function adalah ```first-class``` object. Artinya function itu bisa di _pass_ ke function lain atau
di _return_ sebagai sebuah value.

contoh function bisa di pass ke function lain sebagai _argument_.

```javascript

```

contoh function bisa di return sebagai _return value_

```javascript
```

### Pure Function
...