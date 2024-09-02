# Object

Dipembahasan sebelumnya mengenal **Tipe Data**, kita sudah menyinggung tentang```Object``` yang merupakah salah satu tipe data di JavaScript, namun Object ini adalah tipe data non-primitif. 

Object adalah sebuah _collection_ data yang memungkinkan kita untuk menyimpan data dalam bentuk pasangan ```key:value``` yang disebut dengan _property_.

sintaks:

```javascript
{
  key: value,
  key2: value2,
  // ...
  keyN: valueN,
}
```

dimana setiap property dipisahkan oleh tanda koma ```,```.

contoh:

```javascript
let user = {
  name: 'Budi', // key: value
  age: 33
};
```

Object ```user``` diatas dikatakan memiliki 2 property yang berisi ```name``` dan ```age``` berserta _value_ nya masing-masing. Bayangkan _property_ dari sebuah object adalah karakteristik yang secara khusus melekat ke si object itu sendiri.

Object ```user``` misalnya, menunjukan bahwa ia adalah orang atau manusia sehingga minimal ia akan punya dua _property_ yang melekat yaitu pasti memiliki nama, umur, jenis kelamin, tinggi badan, asal negara dsb.


Untuk membuat object, minimal ada dua cara yaitu dengan menggunakan object literal ```{ }``` atau pakai constructor ```new Object()```.

Contoh membuat object dengan object literal ```{ }```

```javascript
let user = {
  name: 'Budi',
  age: 33,
};
```

sedangkan membuat object dengan constructor ```new Object()``` adalah seperti berikut

```javascript
let user = new Object();
user.name = 'Budi';
user.age = 33;
```

Semua contoh diatas akan menghasilkan output yang sama saat di _console_.

```javascript
[Object] {
  age: 33,
  name: "Budi"
}
```

Disarankan juga ketika membuat object langsung, kita menambahkan koma ```,``` pada property terakhir. Ini disebut sebagai ```trailing comma``` yang fungsinya untuk membuat lebih mudah saat menambah, menghapus atau memindahkan posisi property.

contoh:

```javascript
let user = {
  name: 'Budi',
  age: 33, // trailing comma
}
```

Secara umum membuat object langsung dengan object literal ```{ }``` adalah cara yang direkomendasi. Kamu bisa mulai membiasakan membuat object langsung dengan object literal ```{ }``` dari sekarang.

### Nested Object

Saat membuat real-world aplikasi, sangat umum banget membuat object yang lebih kompleks seperti object yang property nya ada object lain atau object turunannya.

contoh:

```javascript
let user = {
  name: 'Budi',
  age: 33,
  address: {
    city: 'Jakarta',
    country: 'Indonesia',
    street: 'Jl. Kemayoran no 12',
    postalCode: 1020,
    mapLocation: {
      lattitude: -6.2088,
      longitude: 106.8451,
      zoomLevel: 18,
      markerTitle: 'Jl. kemayoran no 12',
      mapService: ['Google', 'Waze', 'Apple'],
    }
  }
};
```

Object ```user``` terlihat lebih kompleks dari sebelumnya. Didalamnya ada property ```address``` yang
juga value nya adalah sebuah object. Kemudian property ```address``` masih punya property yang juga sebuah object yaitu ```mapLocation```.

### Mengakses Property Object

_Properties_ object dapat di akses dengan menggunakan _dot notation_ atau _bracket notation_.

Mengakses object dengan _dot notation_

```javascript
let user = {
  name: 'Budi',
  age: 33,
};

console.log(user.name); // Budi
console.log(user.age); // 33
```

contoh _dot notation_ untuk nested object

```javascript
let user = {
  name: 'Budi',
  age: 33,
  address: {
    city: 'Jakarta',
  }
};

console.log(user.address.city); // Jakarta
```

Kemudian dengan _bracket notation_ seperti berikut

```javascript
let user = {
  name: 'Budi',
  age: 33,
  address: {
    city: 'Jakarta',
  }
};

let name = user['name'];
let city = user['address']['city'];

console.log(name); // Budi
console.log(city); // Jakarta
```

Saat menggunakan bracket notation, nama property atau _key_ nya harus dijadikan _string_. Misal _key_ ```name``` menjadi ```'name'``` atau dengan kutip dua ```"name"```.

Keseringannya untuk mengakses property object memang biasa pakai _dot notation_, tapi banyak _case_ dimana _bracket notation_ biasa dipakai seperti saat ada kebutuhan untuk mengakses property secara dinamis.
Nama property atau _key_ nya di set dinamis dalam bentuk variable. Contoh

```javascript
const car = {
  name: 'xpander',
  type: 'sedan',
  color: 'blue',
  year: 2003,
};

let key = prompt('Masukan key yang ingin diakses');

alert(car[key]); // blue
```

<div align="center">
  <img src="https://github.com/user-attachments/assets/f442150d-c1e2-4230-b52c-6e0c49563e71" 
  width="460"
  />
</div>

Output dari contoh diatas akan sesuai dengan nama property / key yang di input. Misal _key_ ```color``` akan menghasilkan _value_ ```blue``` dst.

Ketika mengakses nama property yang tidak ada didalam object maka akan menghasilkan _undefined_. Contoh

```javascript
let user = {
  name: 'Budi',
  age: 33,
  address: {
    city: 'Jakarta',
  }
};

console.log(user.email); // undefined
console.log(user['email']); // undefined
```

Untuk mengantisipasi pengaksesan property yang tidak ada didalam object (agar meminimalisir bugs), ada beberapa cara yang kita bisa dilakukan seperti menggunakan operator ```in```, ```property !== undefined```, dan ```Object.hasOwnProperty()```.

contoh:

```javascript
// operator "in"

if ('email' in user) {
  console.log(user.email);
}

// hasOwnProperty()

if (user.hasOwnProperty('email')) {
  console.log(user.email);
}

// !== undefined

if (user.email !== undefined) {
  console.log(user.email);
}
```

#### Mengakses Property Object Dengan ```Destructuring```

Cara lainnya untuk mengekases property sebuah object adalah dengan menggunakan ```Destructuring``` dengan sintaks:

```javascript
let { key1, key2, ... } = object
```

Misal property pada contoh object berikut

```javascript
let user = {
  name: 'Budi',
  age: 33,
  address: {
    city: 'Jakarta',
  }
};
```
dapat diakses dengan cara ```destructuring``` seperti berikut:

```javascript
let { name, age, address } = user;

console.log(name); // Budi
console.log(age); // 33
console.log(address); // { city: "Jakarta" }
```

#### Mengakses Property Object Dengan ```for-in```

Statement loop ```for-in``` secara khusus digunakan untuk mengakses / mengiterasi semua property dalam sebuah object. Contoh

```javascript
let user = {
  name: 'Budi',
  age: 33,
  address: {
    city: 'Jakarta',
  }
};

for (let key in user) {
  console.log(user[key]);
}

// Output:
Budi
33
Object {
  city: "Jakarta"
}
```

Untuk nested object maka bisa nested ```for-in``` juga seperti berikut:

```javascript
for (let key in user) {
  if (typeof user[key] === 'object') {
    for (let nestedKey in user[key]) {
      console.log(user[key][nestedKey]);
    }
  } else {
    console.log(user[key]);
  }
}
```

Pada contoh diatas ada penambahan pengecekan ```typeof user[key] === 'object'``` agar loop ```for-in``` yang kedua
(nested) hanya akan di eksekusi jika _value_ dari salah satu property object ```user``` adalah sebuah object.
Dalam contoh diatas berarti _value_ dari property ```address``` lah yang berupa object.

Bagaimana jika nested object nya ada banyak, misal kedalamannya lebih dari 5? Untuk kasus seperti itu maka kita bisa gunakan bantuan loop ```while``` (dengan modifikasi khusus tentunya ) dan bahkan dengan function rekursif.
Kita tidak akan membahasnya lebih detail dalam materi ini karena akan panjang sekali dan bisa membuat kamu pusing dan melewatkan hal-hal yang justru lebih ditekankan dalam pembahasan ini.

### Operasi-operasi Pada Object

Object akan sering kita modifikasi seperti menambahkan property baru, mengubah value nya dan menghapusnya.

#### Menambahkan Property Baru

Untuk menambahkan property baru, kita bisa menggunakan _bracket notation_ dan _dot notation_ seperti contoh berikut:

```javascript
const userLogin = {
  username: 'budi',
  password: 'secret',
};

userLogin.isLogin = true;
userLogin['email']= 'budi@email.com'

console.log(userLogin);
```

Pada contoh diatas kita menambahkan property baru ```isLogin``` dan ```email``` sehingga object ```userLogin```
akan menjadi seperti berikut (ketika di console)

```javascript
Object {
  email: "budi@email.com",
  isLogin: true,
  password: "secret",
  username: "budi"
}
```

#### Mengubah Value Property

Untuk mengubah value sebuah property, kita juga bisa menggunakan _bracket notation_ dan _dot notation_ seperti contoh berikut:

```javascript
const userLogin = {
  username: 'budi',
  password: 'secret',
};

userLogin.username = 'agus';
userLogin['password']= 'newsecret';

console.log(userLogin);

// Output:
Object {
  password: "newsecret",
  username: "agus"
}
```

#### Menghapus Property

Untuk menghapus sebuah property kita bisa menggunakan operator ```delete```. Contoh:

```javascript
const userLogin = {
  username: 'budi',
  password: 'secret',
};

delete userLogin.username;

// Output:
Object {
  password: "secret"
}
```

### Computed Property

Adalah nama property atau _key_ yang dibuat menggunakan kurung siku ```[variable]``` untuk membuat property ini menjadi
dinamis.

contoh:

```javascript
function printRating(jenis, bintang) {
  return {
    [`${jenis}Name`]: 'Doraemon',
    [`${jenis}Rating`]: `Dapat bintang ${bintang}`
  }
}

const film = printRating('film', 5);
const serial = printRating('serial', 4);
```

Misal pada contoh diatas kita ingin membuat sebuah fungsi untuk mencetak rating anime Doraemon dalam bentuk film atau serial-nya. Contoh diatas akan menghasilkan output seperti berikut:

```javascript
Object {
  filmName: "Doraemon",
  filmRating: "Dapat bintang 5"
}

Object {
  serialName: "Doraemon",
  serialRating: "Dapat bintang 4"
}
```

sehingga kita bisa akses property nya dengan cara seperti ini

```javascript
const film = printRating('film', 5);

console.log(film.filmName); 
// Output: Doraemon

console.log(film.filmRating); 
// Output: Dapat bintang 5

const serial = printRating('serial', 4);

console.log(serial.serialName); 
// Output: Doraemon

console.log(serial.serialRating); 
// Output: Dapat bintang 4
```

Computed property tidak usah terlalu dipusingkan dulu karena seujujur nya memang cukup jarang ketemu _case_ yang mengharuskan pakai computed property. Nanti saat kita membuat aplikasi yang kompleks, baru kita akan
ketemu _case_ yang mungkin harus pakai computed property.

### Bagaimana Object Disimpan Di Memory

Object di JavaScript disimpan di memory menggunakan _reference_. Maksudnya adalah ketika kita me-assign object ke sebuah variable, si variable itu akan memiliki _reference_ ke object yang ada di memory atau bisa dibilang si variable itu "tahu" dimana alamat si object tadi di memory.

Perhatikan contoh berikut:

```javascript
let user = {
  name: "Budi",
  age: 33,
};
```

Diatas kita punya sebuah _object_ ```{ name: "Budi", age: 33 }``` yang di assign ke variable ```user```. Ini artinya si object-nya sendiri disimpan oleh si _JavaScript Engine_ disuatu lokasi di memory, dan tidak ada yang tahu lokasinya dimana kecuali si variable ```user```. Dengan kata lain si variable ```user``` ini punya _reference_ atau _pointer_ ke lokasi memory tempat si object ```{ name: "Budi", age: 33 }``` disimpan.

Maka ketika kita akses property nya misal ```user.name```, si _JavaScript Engine_ akan mencari alamat memory nya dimana dan ambil value dari object-nya.

Nah karena behaviour object ini, satu hal yang **sangat penting** untuk di perhatikan yaitu ketika variable sebuah object di _copy_ ke variable lain, maka yang sebenarnya di copy itu bukan object-nya melainkan si _reference_ nya.

Coba kita ulang, object diatas ```{ name: "Budi", age: 33 }``` saat ini hanya variable ```user``` saja yang tahu keberadaanya dimana di memory. Jika kita putuskan misal variable ```user2``` juga harus tahu keberadaanya dimana maka kita lakuan operasi _copy_ seperti ini.

```javascript
let user = {
  name: "Budi",
  age: 33,
};

let user2 = user; // copy reference-nya
```
Sekarang (lihat contoh diatas) artinya si object-nya sendiri **tetap satu** (tidak di copy / duplikat), namun sekarang variable ```user2``` juga tahu alamat atau lokasi object ```{ name: "Budi", age: 33 }``` di memory karena yang di copy dari ```user``` adalah _reference_ nya saja. Agar lebih terbayang, perhatikan ilustrasi berikut:

<img width="564" alt="Object reference3" src="https://github.com/user-attachments/assets/b7755633-c935-4229-9645-9c3ca727a647">

Terlihat bahwa sekarang masing-masing variable ```user``` dan ```user2``` sama-sama punya _reference_ ke object yang sama yaitu ```{ name: "Budi", age: 33 }```. Dan keduanya pun akan punya akses yang sama ke object itu.

```javascript
console.log(user.name); 
// Output: Budi
console.log(user2.name);
// Output: Budi 
```

Karena yang di copy adalah _reference_ nya, maka **jika ada modifikasi** object oleh salah satu variable maka yang lain pun akan ikut berubah. Bisa terlihat pada contoh berikut:

```javascript
user.name = "Agus";

console.log(user.name); 
// Output: Agus
console.log(user2.name);
// Output: Agus
```

Konsep _copy by-reference_ pada object ini sangat penting untuk di fahami, oleh karena itu sebaiknya kamu juga sekalian coba langsung contoh diatas yah.

Kalau begitu bagaimana jika kita hanya ingin men-duplikat object nya saja? (bukan copy reference nya) sehingga meski object aslinya di modif, tidak akan pengaruh ke object _cloningan_-nya. Ada beberapa cara untuk melakukannya diantaranya adalah

- Menggunakan ```Object.assign()```

  ```javascript
  let user = {
    name: "Budi",
    age: 33,
  };

  let user2 = {};

  Object.assign(user2, user);

  // misal modif dikit
  user.name = "Agus";

  console.log(user); 
  // Output: { age: 33, name: "Agus" }
  console.log(user2); 
  // Output: {  age: 33, name: "Budi" }
  ```

  Terlihat bahwa sekarang variable ```user2``` sudah punya object nya sendiri hasil _clone_ dari object ```user```.

- Menggunakan ```structuredClone()``` khusus untuk nested object

  Jika object kita cukup kompleks yaitu punya nested object satu level, dua level, dan seterusnya, maka tidak bisa pakai ```Object.assign()``` seperti diatas. Ini karena setiap nested object akan juga di copy by-reference yang membuat behaviour nya akan sama seperti pada **_ilustrasi object-001_** diatas.
  
  Untuk case ini, kita bisa menggunakan function ```structuredClone()``` untuk membuat meng-_clone_ object-nya.

  ```javascript
  let user = {
    name: "Budi",
    age: 33,
    address: {
      city: "Jakarta",
      province: "DKI",

    },
  };

  let user2 = structuredClone(user);
  ```
- Menggunakan spread operator ```...obj```

  ```javascript
  let user = {
    name: "Budi",
    age: 33,
  };

  let user2 = { ...user };
  ```


Materi tentang Object di bab Fundamental inisudah selesai, baiknya di baca ulang dan di coba lagi sendiri sampai betul-betul dikuasasi. Pembahasan tentang Object (yang lebih advance) sendiri masih akan berlanjut di chapter-chapter berikutnya.