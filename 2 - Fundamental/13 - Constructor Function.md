# Constructor Function

Di materi sebelumnya kita sudah membahas fundamental ```Function``` dan hal-hal mendasar yang kami rasa wajib untuk diketahui dan dikuasasi. Berikutnya dalam bagian ini kita akan membahas **Constructor Function** yang secara teknis sebenarnya sama dengan Function biasa namun ada beberapa point mendasar yang menjadi pembeda. 

Karena itulah kami sengaja memisahkan pembahasan Constructor Function ini dengan pembahasan Function sebelumnya. Ada dua point mendasar yang menjadi pembeda yaitu:

1. Constructor Function harus dipanggil menggunakan keyword ```new```
2. Nama Function nya harus diawali dengan huruf kapital

sintaks:

```javascript
// mendefinisikan
function Person(param) {
 //...
}

// panggil dan inisialisasi constructor nya
let person = new Person('value');
```

Ketika constructor function dipanggil menggunakan keyword ```new```, ia akan melakukan tiga proses dibawah

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

dan memang ini juga merupakan cara yang direkomendasi ketika membuat object. Namun seiring berjalannya waktu, kita akan butuh cara lain untuk membuat object yang lebih fleksibel dan dinamis. Untuk menjawab kebutuhan ini, maka kita bisa pakai bantuan Constructor Function.

Bagi kamu yang mungkin pernah coding pakai bahasa pemrograman yang support ```OOP``` seperti Java atau PHP, Constructor Function di JavaScript ini sangat mirip konsepnya. Diatas sudah kita sebutkan kalau Constructor Function di panggil menggunakan keyword ```new``` dan mengakses property object nya dengan keyword ```this```, mirip dengan yang ada di bahasa pemrograman lain. Kemudian ada istilah ```constructor``` dan juga inheritance,  jadi memang secara konsep mirip dengan ```OOP``` dibahasa pemrograman lainnya. Kita akan jelaskan lebih lanjut.

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

Lalu jika kita ingin membuat object ```user``` lainnya, kita bisa _reuse_ constructor function ```User``` diatas seperti berikut:

```javascript
let user2 = new User('Agus', 30);

console.log(user2.name); // Agus
console.log(user2.age); // 30
```

### Methods di Constructor Function

Method adalah function yang dibuat didalam constructor function untuk melakukan tugas tertentu yang berkaitan dengan object nya. Kamu boleh cek kembali pembahasan **Array Method** di materi tentang Array sebelumnya untuk menambahkan pemahaman mengenai **Methods**. Karena sejatinya methods yang akan kita bahas di materi ini juga sama.

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

```login```, ```logout``` dalam constructor function ```Auth``` diatas adalah **method**. Dan kita bisa membuat banyak method sesuai dengan kebutuhan tentunya. Konsep method ini juga identik dengan konsep ```OOP``` di bahasa pemrograman lainnya. Misal kalau kita buat dalam ```C#```

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

sintaks:

```javascript
function Cfn(params) {
 //...
}

Cfn.prototype.someMethod = function () {
  //...
}
```

#### Method prototype vs biasa

### Lebih Dalam Mengenai keyword ```this``` di Constructor Function dan Function Biasa