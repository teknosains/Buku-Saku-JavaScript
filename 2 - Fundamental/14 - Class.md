# Class

Jika konsep OOP sudah terlihat cukup jelas dan bisa dilakukan dengan Constructor Function seperti pada pembahasan sebelumnya, maka dengan adanya ```Class``` akan terlihat semakin lebih nyata lagi ke-OOP-an nya layaknya bahasa pemrograman OOP-based seperti Java atau C#.

```Class``` mulai perkenalkan / ditambahkan ke JavaScript pada ES6 di bulan Juni tahun 2015 silam. Jadi jika kamu masih menggunakan browser keluaran 2015 kebawah, syntax ```Class``` itu tentu tidak bisa dipakai. Juga secara teknis, ```Class``` itu sama saja dengan Constructor Function, yakni sama-sama dibangun di atas fitur mekanisme pewarisan / inheritance dengan prototype (Prototype-based). 

Jadi ```Class``` tidak memperkenalkan fitur baru di JavaScript, semata-mata hanya menambah _cara baru_ untuk membuat dan memanipulasi object dengan sintaks yang lebih _clean_ dan lebih ke-OOP-an.

Untuk kembali me-refresh sedikit mengenai pewarisan prototype, kamu bisa kembali baca materi Constructor Function tepat sebelum materi Class ini.

Sintaks:

```javascript
class ClassName {
  constructor() {
    // ...
  }
}
```

JavaScript secara fundamental merupakan bahasa pemrograman berbasis _prototype_. Secara sederhana _prototype_ itu adalah **ketika sebuah object mewarisi _property_ dan _method_ dari object lain**. Kita coba lihat lagi contoh di Constructor Function sebelumnya:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.sayGreet = function() {
  console.log(
    `Halo saya ${this.name}, umur ${this.age}thn.`
  );
};

const person1 = new Person('Budi', 20);
person1.sayGreet(); 
// Output: Halo saya Budi, umur 20thn.
```

```person1``` disini adalah sebuah _object_ juga dan ia mewarisi _method_ ```sayGreet``` dari ```Person``` melalui _prototype_.

```javascript
console.log(typeof person1); // object
console.log(person1 instanceof Person); // true
```

Sekarang kita coba lihat contoh penerapan ```Class``` untuk code di atas berikut:

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  sayGreet() {
    console.log(
      `Halo saya ${this.name}, umur ${this.age}thn.`
    );
  }
}

const person1 = new Person('Budi', 20);
person1.sayGreet(); 
// Output: Halo saya Budi, umur 20thn.
```

Terlihat jelas secara _functionality_ sama persis dengan contoh sebelumnya namun dengan sintaks yang terlihat lebih _clean_ dan lebih ke-OOP-an :D .

Muncul pertanyaan, jadi sekarang kita sebaiknya pakai ```Class``` atau Constructor Function, Function Biasa atau Object literal biasa untuk membuat dan manipulasi object?. Jawaban kami pribadi silahkan gunakan mana saja sesuai preferensi kamu. Atau jika kamu bekerja di perusahaan, ya _mungkin_ terima nasib saja ikuti yang sudah berjalan kecuali kamu bisa meyakinkan pada senior atau developer lainnya untuk menggunakan opsi yang kamu pilih.

Kami pribadi (terinspirasi juga oleh **Eric Elliott**, seorang JavaScript Guru penulis buku ***O'REILLY - Programming JavaScript Applications***) lebih ***banyak*** menggunakan functions dan object biasa karena kami rasa lebih flexible, simple, support functional programming dan lebih terkesan _nature_ nya JavaScript. Saya berikan contoh case serupa menggunakan function biasa.

```javascript
function createPerson(name, age) {
  return {
    name: name,
    age: age,
    sayGreet: function() {
      console.log(
        `Halo saya ${this.name}, umur ${this.age}thn.`
      );
    }
  };
}

const person1 = createPerson('Budi', 20);
person1.sayGreet();
// Output: Halo saya Budi, umur 20thn.
```

Terlihat juga dari function di atas adalah tidak perlunya menggunakan keyword ```new``` untuk membuat instance object nya. Function ```createPerson``` disebut juga dengan istilah _Factory Function_ yaitu ketika sebuah function me-_return_ object baru.

sintaks factory function:

```javascript
function factoryFunction(prop1, prop2, ...) {
  // return object
  return {
    // ..
  };
}
```

Ok kembali focus ke pembahasan ```Class```, kita akan bahas beberapa point penting mengenai ```Class``` di materi ini. 

### Keyword `this` dalam Class

Saat kita membuat class di JavaScript, kita akan sering menggunakan keyword `this`. Dalam konteks class, `this` selalu merujuk ke **instance object** yang sedang dibuat dari class tersebut.

Perhatikan contoh berikut:

```javascript
class User {
  constructor(nama) {
    this.nama = nama;
  }

  sayHello() {
    console.log(`Halo, saya ${this.nama}`);
  }
}

// this disini milik instance object user1

const user1 = new User("Budi");
user1.sayHello(); 
// Output: Halo, saya Budi
```

Di dalam method constructor, `this.nama = nama` artinya kita menyimpan nilai nama ke dalam instance object. Kemudian di method `sayHello()`, `this.nama` akan mengambil nilai yang sudah disimpan sebelumnya di object tersebut.

Setiap kali kita buat instance object baru dengan keyword **new**, maka _this_ di dalam class akan mengacu ke object baru tersebut. Ini berlaku untuk semua method di dalam class, bukan hanya constructor.

Perhatikan contoh berikut:

```javascript
const user2 = new User("Goku");
user2.sayHello(); 
// Output: Halo, saya Goku

const user3 = new User("Bejita");
user3.sayHello(); 
// Output: Halo, saya Bejita
```

Terlihat bahwa masing-masing object punya value _this_ yang berbeda, sesuai dengan siapa yang memanggil method-nya.

### Method ```constructor```

Method ini adalah method spesial di dalam sebuah ```Class``` yang berguna untuk menginisialisasi dan membuat object baru. Hanya boleh ada tepat satu method ```constructor``` di dalam sebuah class sebab akan muncul error ```SyntaxError``` kalau ada atau tidak sengaja kebuat lebih dari satu.

Di dalam ```constructor``` pula property-property selain property berbentuk method dibuat. Perhatikan contoh berikut:

```javascript
class Person {
  constructor() {
    // property dalam disini
    this.name = name;
    this.age = age;
  }
}
```

```constructor``` juga adalah method yang akan **pertama** kali dijalankan ketika class nya dipangil ```new Person()```.

```javascript
console.log(
  new Person('Budi', 20)
);
// Output: Person { name: 'Budi', age: 20 }
```

### Method di Dalam Class

Method di dalam class adalah function yang biasa digunakan untuk melakukan berbagai operasi yang berkaitan dengan objectnya.

```javascript
class Auth {
  constructor(username, password) {
    this.username = username; 
    this.password = password;
  }

  doLogin() {
    // pura-pura cek data ke server
    if (checkAccount(this.username, this.password)) {
      Session.create({
        username: this.username
      })
    }
  }

  doLogout() {
    Session.destroy(this.username);
  }

}
```

### Method Spesial setter dan getter

***Setter*** adalah method spesial yang digunakan untuk mengubah value dari sebuah property sedangkan ***Getter*** adalah method yang digunakan untuk mengambil value dari property itu. Setter dan getter didefinisikan di dalam class dengan keyword ***set*** dan ***get*** kemudian digunakan setelah class nya dipangil / dibuat instance nya.

Perhatikan contoh berikut:

```javascript
class Segitiga {
  constructor(alas, tinggi) {
    this.alas = alas;
    this.tinggi = tinggi;
    this._satuan = 'cm';
  }
  
  // setter
  set satuan(newSatuan) {
    this._satuan = 'm';
  }
  // getter
  get satuan() {
    return this._satuan;
  }
  
  hitungLuas() {
    return 1/2 * this.alas * this.tinggi;
  }
}

const segitiga1 = new Segitiga(3, 5)
const luas = segitiga1.hitungLuas();

// ambil nilai satuan dgn getter
// segitiga1.satuan;

console.log(
  `Luas segitiga = ${luas}${segitiga1.satuan}²`
);
// Output: Luas segitiga = 7.5cm²

// kita modif satuan nya
// dengan setter
segitiga1.satuan = 'm';

console.log(
  `Luas segitiga = ${luas}${segitiga1.satuan}²`
);
// Output: Luas segitiga = 7.5m²
```

Perhatikan bahwa setter dan getter ```satuan()``` di atas menggunakan  **nama yang sama** ```satuan```. Ini supaya lebih konsisten dari segi konteksnya karena ia merujuk ke modifikasi data yang sama dalam ini ya si _satuan_ itu. 

Perhatikan expression ```this._satuan``` kemudian ```set satuan()``` dan ```get satuan()```. ***Harus dibedakan*** penamaannya karena kalau tidak akan error ```RangeError```

```javascript
class Segitiga {
  constructor(alas, tinggi) {
    //...
    this.satuan = 'cm';
  }
  
  set satuan(newSatuan) {
    // ..
  }
  get satuan() {
    // ..
  }
}

const segitiga1 = new Segitiga(3, 5);
// RangeError: Maximum call stack size exceeded
```
Oleh karena itu kita misal gunakan ```this._satuan``` (pakai tanda _) untuk property nya.

### Static Method

Di dalam sebuah Class, sejatinya semua property dan method itu bukan milik si Class nya, namun nantinya akan jadi milik si instance nya. Coba perhatikan contoh berikut:

```javascript
class Segitiga {
  constructor(alas, tinggi) {
    this.alas = alas;
    this.tinggi = tinggi;
  }
  
  hitungLuas() {
   // ...  
  }

}

const segitiga1 = new Segitiga(3, 5);
```

method constructor, property ```alas```, ```tinggi``` dan ```hitungLuas()``` itu sebenarnya bukan milik si class ```Segitiga``` namun milik si instance ```segitiga1```. Agar lebih memahami, coba cek di console browser dengan cara berikut:

```javascript
console.log(Segitiga);
// Ouput: 
//  class Segitiga
//     length: 2
//   > prototype: {}
```

Nah agar si class nya memiliki method milik dia sendiri maka kita pakai keyword ```static```. Contoh:

```javascript
class Segitiga {
  constructor(alas, tinggi) {
    this.alas = alas;
    this.tinggi = tinggi;
  }
  
  hitungLuas() {
   // ...  
  }

  static namaSegitiga() {
    return 'Siku-siku'
  }

}
```

jika kita coba cek lagi di console maka akan terlihat sekarang class ```Segitiga``` memiliki methodnya sendiri ```namaSegitiga()```.

```javascript
console.log(Segitiga);
// Ouput: 
//  class Segitiga
//     length: 2
//   > namaSegitiga: f namaSegitiga()
```

untuk mengakses method static tersebut langsung dengan menggunakan ```[Nama Class].[Nama Method]``` Contoh:

```javascript
Segitiga.namaSegitiga();  
// Output: Siku-siku
```

Kapan static digunakan di dunia nyata? ada beberapa case misal jika kita ingin membuat sebuah _utility_ library semisal:

```javascript
class Utils {
  static encrypt(str) {
    // ...
  }
  static random() {
    // ...
  }
  static uuid() {
    // ...
  }
}
```

nantinya bisa langsung dipakai oleh siapapun tanpa perlu membuat instance dengan keyword ```new```. Contoh:

```javascript
Utils.encrypt('my password');
Utils.random();
Utils.uuid(); 
```

Dan library bawaan **Math** adalah contoh nyata dari konsep ini. Kita sering lihat dan pakai fungsi-fungsi di Math seperti:

```javascript

console.log(Math.PI); // 3.141..
console.log(Math.sqrt(16)); // 4
console.log(Math.max(1, 2, 3)); // 3
console.log(Math.random()); // random antara 0 dan 1
```

### Inheritance

Inheritance adalah kemampuan sebuah class untuk _mewarisi_ property dan method dari class lain. Dengan class di JavaScript, kini semakin terlihat lebih ke-OOP-an nya layaknya bahasa pemrograman lain. Inheritance di Class dilakukan dengan menggunakan keyword ```extends``` dan ```super```. Contoh: 

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  sayGreet() {
    console.log(
      `Halo saya ${this.name}, umur ${this.age}thn.`
    );
  }
}

class Student extends Person {
  constructor(name, age, nim) {
    super(name, age);
    this.nim = nim;
  }
}

let student = new Student('Budi', 20, '12345');
student.sayGreet();
// Output: Halo saya Budi, umur 20thn.
```

Dengan konsep inheritance, terlihat bahwa di class ```Student``` tidak perlu lagi kita tuliskan 

```javascript
this.name = name;
this.age = age;
```

karena sudah diwariskan otomatis dari class ```Person```. Termasuk juga method ```sayGreet()``` tidak perlu lagi di tulis di dalam class Student. Kecuali jika kita ingin meng-override method tersebut dengan alasan misal ingin menambahakan _behavior_ yang berbeda.

```javascript
class Student extends Person {
  constructor(name, age, nim) {
    super(name, age); // <-- wajib disini posisinya
    this.nim = nim;
  }

  // override method
  sayGreet() {
    console.log(`
      Halo,
      saya ${this.name}, umur ${this.age}thn, 
      NIM ${this.nim}.
    `);
  }
}

let student = new Student('Budi', 20, '12345');
student.sayGreet();
// Output: Halo saya Budi, umur 20thn, NIM 12345.
```

expression ```super(name, age);``` di atas digunakan untuk meng-_call_ dan menginisialisasi constructor parent class-nya yakni ```Person```.
Dengan kata lain, expression ```super(name, age);``` itu sama dengan ```new Person('Budi', 20)``` yang fungsinya untuk menginisialisasi instance dari class ```Person```.

Memahami Class dengan baik akan sangat membantu kita menulis code yang lebih terstruktur, mudah di-_maintain_, _reusable_ dan lebih efisien. Silahkan kembali diulang dan dicoba contoh-contoh code dalam pembahasan ini.