# Object

Dipembahasan sebelumnya mengenal **Tipe Data**, kita sudah menyinggung tentang```Object``` yang merupakah salah satu tipe data di JavaScript, namun Object ini adalah tipe data non-primitif. 

Object adalah sebuah _collection_ data yang memungkinkan kita untuk menyimpan data dalam bentuk pasangan ```key:value``` yang disebut dengan _property_.

sintaks:

```javascript
{
  key: value,
  key2: value2,
  // ...
  keyN: valueN
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
  age: 33
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
      mapService: ['Google', 'Waze', 'Apple']
    }
  }
};
```

Object ```user``` terlihat lebih kompleks dari sebelumnya. Didalamnya ada property ```address``` yang
juga value nya adalah sebuah object. Kemudian property ```address``` masih punya property yang juga sebuah object yaitu ```mapLocation```.

### Mengakses Property Object

_Properties_ object dapat di akses dengan menggunakan _dot notation_ dan _bracket notation_.

Mengakses object dengan _dot notation_

```javascript
let user = {
  name: 'Budi',
  age: 33
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
  year: 2003
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

Untuk mengantisipasi pengaksesan property yang tidak ada didalam object (agar meminimalisir bugs), ada beberapa cara yang kita bisa dilakukan seperti menggunakan _optional chaining_, operator ```in```, ```property !== undefined``` dan ```Object.hasOwnProperty()```.

contoh:

```javascript
// optional chaining

let email = user?.email || 'default@email.com';

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


