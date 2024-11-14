# Constructor Function

Di materi sebelumnya kita sudah membahas fundamental ```Function``` dan hal-hal mendasar yang kami rasa wajib untuk diketahui dan dikuasasi. Berikutnya dalam bagian ini kita akan membahas **Constructor Function** yang secara teknis sebenarnya sama dengan Function biasa namun ada beberapa point mendasar yang menjadi pembeda. 

Di JavaScript sendiri ada beberapa Constructor Function _built-in_ (bawaan) yang sering digunakan seperti ```new Object()```, ```new Array()```, ```new Date()```, ```new String()``` dll. Misal saat kita butuh untuk mendapatkan _datetime_ saat ini kita bisa pakai ```new Date()```

```javascript
let now = new Date();

console.log(now);
// Output: Thu Oct 24 2024 16:21:39 GMT+0700

console.log(now.toLocaleString());
// Output: 10/24/2024, 4:24:43 PM
```

Untuk pembahasan ini kami sengaja memisahkan pembahasan Constructor Function ini dengan pembahasan Function sebelumnya karena ada beberapa point perbedaan keduanya misalnya

1. Constructor Function harus dipanggil menggunakan keyword ```new```
2. Nama Function nya diawali dengan huruf kapital
3. Constructor Function menggunakan keyword ```this``` untuk mengakses property object

sintaks:

```javascript
// mendefinisikan
function Person(param) {
 //...
}

// panggil dan inisialisasi constructor nya
let person = new Person('value');
```

Dimana variable ```person``` yang adalah berupa _object_ biasa disebut juga sebagai _instance_. Lebih tegasnya _instance_ dari ```Person```. 

> <small>_```instance``` adalah sebuah object yang dibuat atau dihasilkan dari constructor function._</small>

Ketika constructor function dipanggil menggunakan keyword ```new```, secara ringkas ia akan melakukan tiga proses dibawah

1. Sebuah _object_ baru yang kosong dibuat lalu di-_assign_ ke ```this```.
2. Lalu eksekusi apa-apa yang ada di body function tersebut.
3. Lalu ```this``` nya di return sevara implicit

Coba kita visual kan lagi agar lebih mudah difahami. Ketika kita membuat constructor function seperti dibawah ini:

```javascript
function User(name, age) {
  this.name = name;
  this.age = age;
}

let user = new User('Budi', 20);
```

dibelakang dia di sebenarnya akan dibuatkan / di define implicit object untuk ```this``` yaitu ```this = {} ```. Kemudian di paling akhir, si ```this``` akan di return secara implicit juga yaitu ```return this```. Perhatikan ilustrasi code berikut

```javascript
function User(name, age) {
  // this = {};
  //..
  this.name = name;
  this.age = age;
  // ..
  // return this;
}
```

yang di _comment_ itu adalah code _implicit_ yang dilakukan oleh si javascript engine, jadi **tidak perlu lagi kita tuliskan**.


### Kegunaan Constructor Function

Constructor Function biasa digunakan untuk membuat ```object``` dengan lebih dinamis. Dalam materi sebelumnya tentang ```Object```, kita sudah biasa membuat object langsung dengan object literal ```{ }``` seperti ini

```javascript
let user = {
  name: 'Budi',
  age: 20
};
```

dan memang ini juga merupakan cara yang umum dipakai ketika membuat object. Namun seiring berjalannya waktu, kita akan butuh cara lain untuk membuat object yang lebih fleksibel dan dinamis. Untuk menjawab kebutuhan ini, maka kita bisa pakai bantuan Constructor Function.

Bagi kamu yang mungkin pernah coding pakai bahasa pemrograman yang support ```OOP``` seperti Java, C# atau PHP, Constructor Function di JavaScript ini sangat mirip dengan konsep ```class``` di bahasa pemrograman lain. Diatas sudah kita sebutkan kalau Constructor Function di panggil menggunakan keyword ```new``` dan mengakses property object nya dengan keyword ```this```, mirip dengan yang ada di bahasa pemrograman lain. Kemudian ada istilah ```constructor``` dan juga ```inheritance```,  jadi memang secara konsep mirip dengan ```OOP``` dibahasa pemrograman lainnya. Kita akan jelaskan lebih lanjut nanti.

Kembali lagi ke fungsi utama Constructor Function untuk membuat object lebih dinamis, kita akan membuat sebuah object seperti dibawah:

```javascript
function User(name, age) {
  this.name = name;
  this.age = age;
}

let user = new User('Budi', 20);

console.log(user.name); // Budi
console.log(user.age); // 20
```

Lalu jika kita ingin membuat instance / object ```user``` lainnya, kita bisa _reuse_ constructor function ```User``` diatas seperti berikut:

```javascript
let user2 = new User('Agus', 30);

console.log(user2.name); // Agus
console.log(user2.age); // 30
```

### Method di Constructor Function

Method adalah function yang dibuat didalam constructor function untuk melakukan tugas tertentu yang berkaitan dengan object nya. Kamu boleh cek kembali pembahasan **Array Method** di materi tentang Array sebelumnya untuk menambahkan pemahaman mengenai **Method**. Karena sejatinya method yang akan kita bahas di materi ini juga sama.

sintaks:

```javascript
function Cfn(params) {
  //...
  this.someMethod = function () {
    //...
  };
}
```

Misal kita membuat sebuah fitur ```Auth``` yang didalam nya ada 2 fungsi utama yaitu ```login``` dan ```logout```. Kita buat seperti ini:

```javascript
function Auth(username, password) {
  this.username = username;
  this.password = password;

  this.login = function () {
    // pura-pura nya cek data ke server
    let verify = checkAccount(this.username, this.password);
    if (verify) {
      setSession({
        username: this.username,
        status: 'logged in',
        loginAt: new Date()
      });
      
      return 'login success';
    }

    return 'invalid username or password';
    
  };

  this.logout = function () {
    destroySession(this.username);

    return 'logout success';
  };
  
}
```

Kemudian saat ingin login, kita panggil di Constructor Function ```Auth``` seperti ini:

```javascript
let auth = new Auth('Budi', 'secret123');

// proses login
auth.login();
```

dan jika ingin logout dengan cara seperti ini:

```javascript
// proses logout
auth.logout();
```

```login```, ```logout``` dalam constructor function ```Auth``` diatas adalah **method**. Dan kita bisa membuat banyak method sesuai dengan kebutuhan tentunya. Konsep method ini juga sangat mirip dengan konsep method di bahasa pemrograman lain yang support ```OOP```. Misal kalau kita buat dalam ```C#```

```csharp
using System;

public class Auth
{
    private string username;
    private string password;

    public Auth(string username, string password)
    {
        this.username = username;
        this.password = password;
    }

    public string Login()
    {
       //...
    }
    public string Logout()
    {
       //...
    }     
}

public class Program
{
    public static void Main()
    {
        Auth auth = new Auth("Budi", "secret123");

        // proses login
        auth.Login();
    }
}
```

### Membuat Method Dengan ```Prototype```

> <small>Catatan: ```Prototype``` akan dibahas tersendiri secara khusus di chapter berikutnya. Pada materi constructor function ini, kamu tidak harus mengenal lebih dalam dahulu tentang ```Prototype```.</small>

Ketika sebuah Constructor Function di inisialisasi / dipanggil dengan keyword```new```, ia akan memiliki property spesial yang disebut```prototype```. Kita bisa lihat / buktikan dengan cara seperti berikut:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

let agus = new Person('Agus', '30');

console.dir(agus);
// Output:

// cek di browser Chrome
Person { name: 'Agus', age: '30' }
  > [[Prototype]]: Object

// cek di browser Safari
Person { name: 'Agus', age: '30' }
  > Person Prototype

// cek di browser Firefox
Object { name: 'Agus', age: '30' }
  > <prototype>: Object{...}
```

Cara setiap browser menampilkan output console bisa berbeda-beda saat kita coba eksekusi ke ```console```. Tapi terlihat bahwa property baru bernama ```prototype``` sudah **terbuat** dan siap digunakan. Untuk membuat method-method dengan ```protoptype``` di Constructor Function, kita mengikuti sintaks berikut:

```javascript
function Cfn(params) {
 //...
}

Cfn.prototype.someMethod = function () {
  //...
}
```

Misal kita membuat sebuah fitur calculator sangat-sangat sederhana dengan 2 method utama yaitu ```add``` dan ```multiply```. Bisa kita  buat seperti ini:

```javascript
function Calc(a, b) {
  this.a = a;
  this.b = b;

  this.add = function () {
    return this.a + this.b;
  }
  
  this.multiply = function () {
    return this.a * this.b;
  }
}
```

Cara diatas menggunakan method biasa yaitu ketika method nya di define langsung _didalam_ si constructor function nya. Meski cara diatas sah-sah saja, tidak akan error dan tetap akan sukses menghasilkan output yang benar, tetapi secara umum cara yang lebih direkomendasi adalah menggunakan ```prototype```. 

Kita refaktor ```Calc``` diatas menjadi seperti ini:

```javascript
function Calc(a, b) {
  this.a = a;
  this.b = b;
}

Calc.prototype.add = function () {
  return this.a + this.b;
}

Calc.prototype.multiply = function () {
  return this.a * this.b;
} 

let calc = new Calc(10, 10);
console.log(calc.add()); // 20
console.log(calc.multiply()); // 100
```

Keyword ```this``` pada method prototype (misal ```this.a```) juga bisa digunakan untuk mengakses property si Constructor Function-nya. Kemudian memang terlihat juga dengan ```prototype``` , code nya jadi lebih panjang dan terksesan kurang _clean_. Namun cara ini lebih direkomendasi dengan beberapa alasan yaitu:

1. **Lebih hemat memori**
   
   * Jika method didefinisikan langsung di dalam Constructor Function, setiap instance dari object akan memiliki salinan method tersebut. Ini bisa memakai lebih banyak memori jika banyak instance yang dibuat. Misal Constructor Function ```Person``` dibawah ini

      ```javascript
      function Person(name) {
        this.name = name;
        this.sayHello = function() {
          return `Halo, ${this.name}`;
        };
      }

      let person1 = new Person('Agus');
      let person2 = new Person('Bob');
      let person3 = new Person('Wati');
      // ...
      let personN = new Person('Nama N');
      ```
      Jika ```Person``` dipanggil berkali-kali, maka setiap _instance_ person1, person2 dst dibelakang layar akan **dibuatkan** method ```sayHello()``` yang sama sehingga masing-masing instance diatas akan punya method ```sayHello()``` sendiri.

      Kita bisa test dan buktikan via console di browser, maka akan terlihat outputnya seperti ini

      ```javascript
      console.log(person1);
      // Output: Person {name: 'Agus', sayHello: ƒ()}
      console.log(person2);
      // Output: Person {name: 'Bob', sayHello: ƒ()}
      ```
      Terlihat kalau semua instance person1, person2 dst masing-masing dibuatkan method ```sayHello()``` sendiri dan disimpan ke memori tentunya. Berbeda jika kita gunakan **prototye** dimana method ```sayHello()``` hanya akan dibuat sekali di memori dan selanjutnya akan di _share_ atau di **wariskan** ke semua instance.

      Perhatikan contoh berikut:

      ```javascript
      function Person(name) {
        this.name = name;
      }

      Person.prototype.sayHello = function() {
        return `Hello, ${this.name}`;
      };

      let person1 = new Person('Agus');
      let person2 = new Person('Bob');

      console.log(person1);
      // Output: Person {name: 'Agus'}
      console.log(person2);
      // Output: Person {name: 'Bob'}
      ```

      Terlihat pada output di console, tidak ada method ```sayHello()``` yang nempel langsung ke _instance_-nya. Secara sederhana bisa dibilang method ```sayHello()``` tetap nempel ke si Constructor Function ```Person``` nya dan bisa dipakai bareng-bareng oleh semua instance nya atau dengan kata lain, semua instance ```Person``` tetap bisa mengakses method prototype ```sayHello()``` yang sama. 

      Seperti pada contoh berikut:

      ```javascript
      console.log(person1.sayHello()); // Hello, Agus
      console.log(person2.sayHello()); // Hello, Bob
      ```

2. **Performance lebih baik**
  
   Method yang dibuat via prototype tidak akan di _re-create_ lagi setiap kali ada instance-instance baru yang di inisialisasi / dibuat. Ini tentu mempercepat proses pembuatan object / instance nya.

3. **Lebih _common_ digunakan oleh para developer**

### Lebih Dalam Mengenai keyword ```this```

Keyword ```this``` semacam sudah menjadi konsensus umum di kebanyakan bahasa pemrograman terutama yang support OOP. Pun di JavaScript, hanya saja di JavaScript ```this``` ini seringkali menjadi kebingungan bagi developer terutama pemula. Oleh karena itu, kita akan coba bahas beberapa hal tentang ```this``` di JavaScript agar membantu semua memahami behavior dan cara kerjanya.

#### 1. ```this``` di Browser global scope

Di browser, ```this``` ini by default mengacu ke object _window_ yang merupakan object global di browser. Jadi ketika kita coba panggil / akses langsung

```javascript
console.log(this);
// Output: Window {window: Window, self: Window, ...}

// sama dengan

console.log(window);
// Output: Window {window: Window, self: Window, ...}

window === this; // true
```

Dengan ```this``` ini kita bisa akses semua property dan method yang ada di object _window_ seperti yang umum kita kenal semisal ```alert```, ```confirm```, ```console``` dll. Contoh

```javascript
this.alert('hello'); 
// sama dengan
window.alert('hello');
// Output: muncul popup alert

this.confirm('Are you sure to delete this?');
// sama dengan
window.confirm('Are you sure to delete this?');
// Output: muncul popup konfirmasi

this.console.log('hello');
// sama dengan
window.console.log('hello');
// Output: hello
```

namun karena di browser sifatnya _global_, kita jadi **tidak perlu lagi** menuliskan ```this``` ketika mengakses semua _property_ object _window_.

Di environment ```Node.JS``` ```this``` ini mengacu ke object _global_. 

```javascript
global === this; // true

global.console.log('hello');
// sama dengan
this.console.log('hello');
// Output: hello
```

#### 2. ```this``` di dalam Function

Khusus di dalam function, ```this``` ini tergantung bagaimana si function itu dipanggil. Ketika function dipanggil seperti biasa akan berbeda dengan jika function dipanggil menggunakan keyword ```new``` (sebagai Constructor Function, ini yang menjadi bahasan kita).

Perhatikan contoh berikut:

```javascript
function Person(name) {
  console.log(this);
}

// panggil biasa
Person('Budi'); 
// Output: Window {window: Window, self: Window, ...}

// panggil menggunakan keyword new
new Person('Budi'); 
// Output: {name: 'Budi'}
```

Jadi di Construction Function, ```this``` itu sebagai **pointer** ke property-property yang ada didalamnya namun di dalam function biasa ```this``` ini mengacu ke object _window_.

#### 3.```this``` di dalam Method object

```javascript
let person = {
  name: 'Budi',
  sayHello: function() {
    console.log(`Hello, ${this.name}`);
    console.log(this === person); // true
  }
};

person.sayHello();
// Output: Hello, Budi
```

```this``` dalam method sebuah object mengacu ke si object itu sendiri. Dalam contoh diatas berarti ```this``` nya mengacu ke object ```person```. Terlihat juga kalau kita cek ```this === person```, hasilnya adalah ```true```.

#### 4. ```this``` di Event Handler

Di _event handler_ seperti misalnya ```addEventListener```, by default ```this``` ini mengacu ke _element_ yang di _target_ oleh event tersebut. Contoh:

```javascript
let button = document.querySelector('button');

button.addEventListener('click', function() {
  console.log(this);
  console.log(this.innerText);
});

// Output: <button>Click me</button> 
// Output: Click me
```

Namun jika _event handler_-nya menggunakan arrow function, maka ```this``` ini akan mengacu ke object _window_. 

```javascript
let button = document.querySelector('button');  

button.addEventListener('click', () => {
  console.log(this);
})
// Output: Window {window: Window, self: Window, ...}
```

Jadi ```this``` di JavaScript itu tergantung _context_ dimana dia berada. Karena perbedaan behaviour ini maka wajib bagi developer JavaScript untuk faham bagaimana cara kerja ```this``` di JavaScript.