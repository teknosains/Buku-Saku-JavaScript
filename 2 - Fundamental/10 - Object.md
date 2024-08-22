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