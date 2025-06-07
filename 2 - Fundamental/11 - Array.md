# Array

Sebelumnya kita sudah membahas tentang Object yang digunakan untuk menyimpan data dalam format ```key:value```.
Maka Array pun pada hakikatnya sama seperti Object yaitu digunakan untuk menyimpan data. Namun data dalam Array
disusun dalam bentuk _list_ berurutan.

sintaks:

```javascript
variable = [item1, item2, item3, ...];
```

Array sangat bermanfaat untuk menyimpan sejumlah atau sekumpulan data ke dalam sebuah variable. Misal kita punya data daftar beberapa negara, alih-alih menuliskan code nya dalam bentuk seperti ini

```javascript
const country1 = 'Indonesia';
const country2 = 'Malaysia';
const country3 = 'Singapura';
const country4 = 'Filipina';
const country5 = 'Brunei';
```

maka lebih baik jika disimpan ke dalam sebuah **variable** saja dengan bantuan array menjadi seperti ini

```javascript
const country = [
  'Indonesia', 
  'Malaysia', 
  'Singapura', 
  'Filipina', 
  'Brunei'
];
```
Data di dalam sebuah array sering juga disebut sebagai _element_. Dan element array dapat berupa _string_, _number_, _boolean_, _object_ dan bahkan _array_ juga. Misalnya

```javascript
const myArray = [
  'Indonesia',
  79,
  true,
  { ibuKota: 'Nusantara', pulau: 'Kalimantan'},
  [17, 'Agustus', 1945]
];
```

Jadi data tipe apapun bisa dimasukan ke dalam array meskipun pada praktek nya kebanyakan kita tentu saja akan
menyimpan data ke dalam array sesuai dengan kesamaan tipe data nya seperti list data yang berupa _string_ saja atau _object_ saja.

Untuk membuat array, kita bisa menggunakan array literal ```[ ]``` atau _constructor_ ```new Array()```:

```javascript
let arr = [];
let arr = new Array();
```

Dan seperti halnya Object, cara pertama adalah yang paling sering digunakan. Jadi kedepan kamu baiknya terus membuat array menggunakan array literal ```[ ]```.

### Mengakses Element Array dengan ```index```

Hal yang paling fundamental mengenai array adalah bahwa element array disusun dengan penomoran berurut yang disebut dengan ```index```. Element pertama dalam array di-index ```0``` dan terakhir ```N-1```. dimana ```N``` adalah **panjang** dari array.

**Panjang** array adalah jumlah banyaknya element di dalamnya dan bisa di ketahui dengan menggunakan property ```length```.

```javascript
let cars = ['BMW', 'Toyota', 'Wuling'];

console.log(cars.length);
// Output: 3
```

Oleh karena itu untuk mengakses element array adalah dengan menggunakan nomor ```index``` nya seperti berikut:

```javascript
let cars = ['BMW', 'Toyota', 'Wuling'];

console.log(cars[0]); // BMW
console.log(cars[1]); // Toyota
console.log(cars[2]); // Wuling
```

Dari pola di atas juga terlihat bahwa jika kita ingin mengakses element array yang terakhir kita tinggal menuliskan ```cars.length - 1```, tidak peduli seberapa banyak element array nya.

```javascript
let lastElement = cars[cars.length - 1];

console.log(cars[lastElement]); 
// Output: Wuling
```

### Mengakses Element Array dengan Loop

Semakin besar array maka tentu tidak mungkin lagi di akses satu persatu, artinya kita harus pakai bantuan loop.
Semua jenis loop bisa digunakan namun dalam materi ini kita akan contohkan menggunakan loop ```for```, ```for-of``` dan ```Array.map()``` saja.

Perhatikan contoh berikut:

```javascript
const person = ['John', 'Doe', 'Mark'];

// for

for (let i = 0; i < person.length; i++) {
  console.log(person[i]);
}

// for-of

for (const i of person) {
  console.log(i);
}

// Array.map()

person.map((val, index) => {
  console.log(val);
});
```

Ketiga cara di atas sama-sama akan menghasilkan output:

```javascript
John
Doe
Mark
```

Dari ketiga cara di atas mana yang sebaiknya digunakan ?. Bebas, gunakan yang mana saja yang kita mau, namun banyak orang (termasuk kami) lebih sering menggunakan ```Array.map()```.

```Array.map()``` nyaman digunakan untuk mengolah array yang biasa datang dari _backend_ atau server.
Misal kita dapat response dari sebuah API / backend dengan format seperti berikut:

```javascript
{
  status: true,
  message: "success",
  data: [
    { id: 1, country: "Indonesia" },
    { id: 2, country: "Malaysia" },
    { id: 3, country: "Singapura" },
    { id: 4, country: "Filipina" },
  ]
}
```

Dan adalah hal yang normal kalau kita butuh modifikasi lagi menjadi array baru sesuai dengan kebutuhan. Untuk hal semacam ini kita bisa gunakan ```Array.map()``` seperti ini:

```javascript
let arr = response.data;

let newArr = arr.map(function(val, index) {
   return {
    idx: index,
    countryID: val.id,
    countryName: val.country
  }
});

console.log(newArr);
```

Variable ```newArr``` di atas kini berisi array yang baru hasil modifikasi dari array aslinya (dari API / Backend).

```javascript
newArr = [
  { idx: 0, countryID: 1, countryName: "Indonesia" },
  { idx: 1, countryID: 2, countryName: "Malaysia" },
  ...
]
```

### Destructuring Array

Destructuring adalah cara cepat untuk mengambil/mengakses nilai dari sebuah array dan menyimpannya ke dalam variable.

Contoh:

```javascript
const arr = ['John', 'Doe', 'Mark'];

const [first, second, third] = arr;

console.log(first); // John
console.log(second); // Doe
console.log(third); // Mark
```

Dengan destructuring, kita juga bisa melewatkan element tertentu.

contoh:

```javascript
const arr = ['John', 'Doe', 'Mark'];

const [first, , third] = arr;

console.log(first); // John
console.log(third); // Mark

const [ , , last] = arr;
console.log(last); // Mark
```

Destructuring array ini juga adalah teknik fundamental yang diterapkan di library JavaScript paling populer, ReactJS. Ini menjadi hal paling wajib yang harus dipahami oleh developer ReactJS.

Di ReactJS, developer sering menggunakan **destructuring array** terutama ketika menggunakan fitur _react hook_ seperti `useState` (Biasa digunakan untuk menyimpan state/data).

Contoh penggunaan `useState`:

```jsx
import { useState } from 'react';

function Contoh() {
  // array destructuring
  const [count, setCount] = useState(0); //state awal: 0

  return (
    <div>
      <p>Nilai saat ini: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Tambah
      </button>
    </div>
  );
}
```

**Catatan**: Contoh ReactJS diatas hanya untuk menunjukan bahwa  teknik destructuring array adalah salah satu teknik yang banyak digunakan dalam pengembangan aplikasi web modern. Jika kita sudah paham fundamentalnya dari sekarang, tentunya nanti akan jadi lebih mudah saat kita mulai terjun menggunakan library-library populer JavaScript seperti ReactJS.

### Array Methods

Saking seringnya array dipakai saat _coding_ membuat aplikasi, JavaScript menyediakan banyak sekali **methods** _siap-pakai_ yang digunakan untuk mengolah array.

Array methods adalah sejumlah fungsi _built-in_ yang disediakan agar developer mudah mengolah array sesuai dengan kebutuhan. Secara umum Array methods dibagi menjadi beberapa kategori yaitu:

- **Basic methods**

  Yaitu kumpulan method-method yang biasa digunakan untuk memanipulasi array. Misalnya ```Array.push()```, ```Array.pop()```, ```Array.unshift()```, ```Array.shift()```, ```Array.splice()```, ```Array.join()```, dll. 

  Misal kita perlu untuk membuang element terakhir dari array, kita bisa gunakan ```Array.pop()```.

  contoh:

  ```javascript
  const person = ['John', 'Doe', 'Mark'];
  person.pop();

  console.log(person);
  // Output: [ 'John', 'Doe' ]
  ```
  atau ingin menggabungkan semua element array menjadi sebuah _string_, kita bisa gunakan ```Array.join()```.

  contoh:

  ```javascript
  const person = ['John', 'Doe', 'Mark'];
  let separator = '-';
  person.join(separator);

  console.log(person);
  // Output: John-Doe-Mark
  ```

  Operasi lain yang paling sering dilakukan adalah menambahkan element baru ke dalam array. Misal kita perlu menambahkan element baru ```'Goku'``` ke dalam array `person` kita bisa gunakan ```Array.push()```.

  contoh:

  ```javascript
  const person = ['John', 'Doe', 'Mark'];
  person.push('Goku');

  console.log(person);
  // Output: [ 'John', 'Doe', 'Mark', 'Goku' ]
  ```
  contoh lain misal kita punya sebuah array yang menyimpan data **keranjang belanja** (shopping cart):

  ```javascript
  let cart = [
    { name: 'Laptop', qty: 1 },
    { name: 'Mouse', qty: 2 }
  ];
  ```

  Lalu user menambahkan item baru ke dalam keranjang, maka tinggal kita gunakan ```Array.push()``` saja seperti ini:

  ```javascript
  cart.push({ name: 'Keyboard', qty: 1 });

  console.log(cart);
  // Output:
 
  [
    { name: 'Laptop', qty: 1 },
    { name: 'Mouse', qty: 2 },
    { name: 'Keyboard', qty: 1 }
  ]
  ```

- **Search methods**

  Yaitu kumpulan method-method yang biasa digunakan untuk mencari element array. Misalnya ```Array.indexOf()```, ```Array.lastIndexOf()```, ```Array.includes()```, ```Array.find()```, dll.

  Misal kita perlu mencari index dari element ```'Doe'```, kita bisa gunakan ```Array.indexOf()```.

  contoh:

  ```javascript
  const person = ['John', 'Doe', 'Mark'];
  const index = person.indexOf('Doe');
  
  console.log(index);
  // Output: 1

  // jika index < 0 artinya element yang
  // dicari tidak ditemukan
  if (index < 0) {
    console.log('Element tidak ditemukan');
  }
  ```

  contoh lain, mencari element dengan `Array.includes()`

  ```javascript
  const person = ['John', 'Doe', 'Mark'];

  function findByName(name) {
    return person.includes(name);
  };

  console.log(
    findByName('Budi')
  );
  // Output: false

  console.log(
    findByName('Mark')
  );
  // Output: true
  ```

  **Catatan**: ``findByName()`` di atas adalah sebuah `function`. Penjelasan mengenai function akan kita bahas pada materi Function dihalaman selanjutnya.

- **Iteration methods**

  Yaitu kumpulan method-method yang biasa digunakan untuk me-_loop_ array dan melakukan operasi-operasi yang diinginkan. Misalnya ```Array.forEach()```, ```Array.map()```, ```Array.filter()```, ```Array.reduce()```, dll. 
  
  <small>(_lihat bagian akhir materi Array ini untuk penjelasan lebih lanjut tentang iteration methods_)</small>

- **Sorting methods**

  Yaitu kumpulan method-method yang biasa digunakan untuk men-_sort_ / mengurutkan array. Misalnya ```Array.sort()```, ```Array.reverse()```, dll.

Semua method-method di atas tidak mungkin kita bahas satu-satu dalam buku ini. Untuk mengetahui semua method-method yang tersedia, bisa kunjungi [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).


### Array Multidimensi

Array multidimensi adalah array yang terdiri dari array lainnya atau bisa juga dibilang nested array.

contoh:

```javascript
let matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

console.log(matrix[1][2]);
// Output: 6

console.log(matrix[0]);
// Output: [ 1, 2, 3 ]
```

### Validasi-validasi dalam Array

Saat menggunakan array, hampir pasti kita akan butuh untuk melakukan validasi sebuah array. Beberapa validasi yang umum dilakukan yaitu:

- Check array kosong

  contoh:

  ```javascript
  let arr = [];

  if (arr.length === 0) {
    console.log('array kosong');
  }
  ```
- Check apakah variable sebuah array

  contoh:

  ```javascript
  let arr = [];

  if (Array.isArray(arr)) {
    console.log('variable arr adalah array');
  }
  ```
- Check apakah sebuah element exist

  contoh:

  ```javascript
  const person = ['John', 'Doe', 'Mark'];
  
  if (person.includes('Doe')) {
    console.log('Doe ada di dalam array person');
  }

  if (person.indexOf('Doe') !== -1) {
    console.log('Doe ada di dalam array person');
  }
  ```

  Catatan: saat menggunakan ```Array.indexOf()```, jika sebuah element tidak ada di dalam array maka akan me-return ```-1```.


### Iteration methods: Method yang paling sering dipakai dalam Array

JavaScript menyediakan beberapa method khusus di dalam array yang sangat sering dipakai untuk **melakukan iterasi** (pengulangan). Kita bisa melakukan berbagai hal seperti:
- menampilkan data satu per satu
- memfilter data
- membuat array baru dari array lama
- menjumlahkan isi array

Cara ini jauh lebih **ringkas dan modern** dibandingkan menggunakan loop `for` atau `while` biasa.

Berikut ini adalah beberapa method iterasi yang paling umum dan wajib kamu kenal:

#### 1. `forEach()`

Digunakan untuk menjalankan sebuah aksi untuk setiap element dalam array. Method ini **tidak me-return nilai baru**, jadi hanya menjalankan aksi yang diinginkan saja.

```javascript
const buah = ['apel', 'jeruk', 'mangga'];

buah.forEach(function(item, index) {
  console.log(index + ': ' + item);
});
```

#### 2. `map()`

Digunakan untuk membuat array baru dengan mengubah setiap element dalam array lama.

```javascript
const buah = ['apel', 'jeruk', 'mangga'];

const buahBaru = buah.map(function(item) {
  return 'buah ' + item;
});

console.log(buahBaru);
// Output: [ 'buah apel', 'buah jeruk', 'buah mangga' ]
```

`Array.map()` cocok digunakan untuk proses transformasi data tanpa mengubah data aslinya.

#### 3. `filter()`

Digunakan untuk menyaring data berdasarkan kondisi tertentu. Hasilnya adalah array baru yang hanya berisi item yang lolos syarat.

```javascript
const numbers = [1, 2, 3, 4, 5, 6];

// get angka genap saja
const odd = numbers.filter(function(item) {
  return item % 2 === 0;
});

console.log(odd); // [2, 4, 6]
```

contoh lain `Array.filter()` yang sering dilakukan yaitu untuk _search_ data.

```javascript
const product = [
  { id: 1, name: "Laptop", stock: 5 },
  { id: 2, name: "Mouse", stock: 0 },
  { id: 3, name: "Keyboard", stock: 3 },
  { id: 4, name: "Monitor", stock: 0 }
];

function searchProduct(keyword) {
  if (!keyword) {
    console.log('Harap masukan keyword');
    return;
  };
  
  return product.filter(function(item) {
   let search = item.name
     .toLowerCase()
     .includes(
       keyword.toLowerCase()
     );
   return search;
  });
}

console.log(
  searchProduct('to')
);

// Output:
// Semua data yang mengandung kata 'to'
```

#### 4. `find()`

Mirip dengan `filter()`, tapi hanya mengembalikan **satu** elemen pertama yang cocok dengan kondisi.

```javascript
const fruits = ['apel', 'jeruk', 'mangga'];

const search = fruits.find(function(item) {
  return item === 'jeruk';
});

console.log(search); // 'jeruk'
```

#### 5. `reduce()`

Biasa digunakan untuk menggabungkan semua nilai dalam array menjadi satu hasil akhir. Bisa untuk menjumlahkan, menghitung total, atau membuat object baru dari array.

```javascript
const numbers = [1, 2, 3, 4];

const total = numbers.reduce(function(acc, current) {
  return acc + current;
}, 0);

console.log(total); // 10
```

Jika kita perhatikan, semua iteration method diatas menggunakan **function** sebagai _argument_ seperti berikut

```javascript
arr.forEach(function() {...});
arr.map(function() {...});
arr.filter(function() {...});
arr.find(function() {...});
arr.reduce(function() {...});
```

function ini disebut **callback function** yang akan dipanggil atau dijalan oleh si _method_ nya sebanyak jumlah element array. Dalam konteks operasi pada array, function seperti `map()` atau `filter()` itu sebenarnya **tidak tahu** apa yang harus dilakukan terhadap **setiap** element nya. Jadinya kita mesti **kasih tahu mereka** melalui function.

Contoh Sederhana:

```javascript
const numbers = [1, 2, 3];

const result = numbers.map(function(n) {
  return n * 2;
});

// atau bisa penulisan bentuk lainnya
// agar lebih jelas

const multiplyByTwo = function(n) {
  return n * 2;
};
const result = numbers.map(multiplyByTwo);

console.log(result); // [2, 4, 6]
```
penjelasan contoh diatas:

 - Method `map()` akan memanggil function callback `multiplyByTwo()` sebanyak isi array. Dalam contoh ini berarti sebanyak 3 kali.
 - Setiap kali dipanggil, parameter item akan berisi elemen array saat itu / current.
 - Kita sendiri yang beri tahu si `map()` untuk melakukan apa yang kita inginkan, dalam contoh ini berarti kita ingin melakukan perkalian 2 pada setiap elemen array.


 
Pembahasan selengkapnya tentang Function ada halaman selanjutnya.


Pada materi-materi berikutnya kita mungkin akan banyak menggunakan contoh-contoh code menggunakan Array. Oleh karena itu agar semakin terbiasa, baiknya di baca ulang dan dicoba lagi beberapa kali yah.
