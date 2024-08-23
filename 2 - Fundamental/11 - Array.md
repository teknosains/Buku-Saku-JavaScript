# Array

Sebelumnya kita sudah membahas tentang Object yang digunakan untuk menyimpan data dalam format ```key:value```.
Maka Array pun pada hakikatnya sama seperti Object yaitu digunakan untuk menyimpan data. Namun data dalam Array
disusun dalam bentuk _list_ berurutan.

sintaks:

```javascript
const variable = [item1, item2, item3, ...];
```

Array sangat bermanfaat untuk menyimpan sejumlah atau sekumpulan data kedalam sebuah variable. Misal kita punya data daftar beberapa negara, alih-alih menuliskan code nya dalam bentuk seperti ini

```javascript
const negara1 = 'Indonesia';
const negara2 = 'Malaysia';
const negara3 = 'Singapura';
const negara4 = 'Filipina';
const negara5 = 'Brunei';
```

maka lebih baik jika disimpan ke dalam sebuah **variable** saja dengan bantuan array menjadi seperti ini

```javascript
const negara = [
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

Jadi data tipe apapun bisa dimasukan kedalam array meskipun pada praktek nya kebanyakan kita tentu saja akan
menyimpan data ke dalam array sesuai dengan kesamaan tipe data nya seperti list data yang berupa _string_ saja atau _object_ saja.

Untuk membuat array, kita bisa menggunakan array literal ```[ ]``` atau _constructor_ ```new Array()```:

```javascript
let arr = [];
let arr = new Array();
```

Dan seperti halnya Object, cara pertama adalah yang paling sering digunakan. Jadi kedepan kamu baiknya terus membuat array menggunakan array literal ```[ ]```.

### Mengakses Element Array dengan ```index```

Hal yang paling fundamental mengenai array adalah bahwa element array disusun dengan penomoran berurut yang disebut dengan ```index```. Element pertama dalam array diindex ```0``` dan terakhir ```N-1```. dimana ```N``` adalah **panjang** dari array.

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

Dari pola diatas juga terlihat bahwa jika kita ingin mengakses element array yang terakhir kita tinggal menuliskan ```cars.length - 1```, tidak peduli seberapa banyak element array nya.

```javascript
let lastElement = cars[cars.length - 1];

console.log(cars[lastElement]); 
// Output: Wuling
```

### Mengakses Element Array dengan Loop

Semakin besar array maka tentu gk mungkin lagi di akses satu persatu, artinya kita harus pakai bantuan loop.
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

Ketiga cara diatas sama-sama akan menghasilkan output:

```javascript
John
Doe
Mark
```

Dari ketiga cara diatas mana yang sebaiknya digunakan ?. Bebas, gunakan yang mana saja yang kita mau, namun banyak orang (termasuk kami) lebih sering menggunakan ```Object.map()```.

```Object.map()``` nyaman digunakan untuk mengolah array yang biasa datang dari _backend_ atau server.
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

Dan adalah hal yang normal kalau kita butuh modif lagi menjadi array baru sesuai dengan kebutuhan. Untuk hal semacam ini kita bisa gunakan ```Object.map()``` seperti ini:

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

Variable ```newArr``` diatas kini berisi array yang baru hasil modifikasi dari array aslinya (dari API / Backend).

```javascript
newArr = [
  { idx: 0, countryID: 1, countryName: "Indonesia" },
  { idx: 1, countryID: 2, countryName: "Malaysia" },
  ...
]
```

### Array Methods

Saking begitu seringnya array dipakai saat _coding_ membuat aplikasi, JavaScript menyediakan banyak sekali **methods** _tinggal-pakai_ yang digunakan untuk mengolah array.

Array methods adalah sejumlah fungsi-fungsi _built-in_ yang disediakan agar developer mudah mengolah array sesuai dengan kebutuhan. Secara umum Array methods dibagi menjadi beberapa kategori yaitu:

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

- **Search methods**

  Yaitu kumpulan method-method yang biasa digunakan untuk nge-_search_ element array. Misalnya ```Array.indexOf()```, ```Array.lastIndexOf()```, ```Array.includes()```, ```Array.find()```, dll.

  Misal kita perlu mencari index dari element ```'Doe'```, kita bisa gunakan ```Array.indexOf()```.

  contoh:

  ```javascript
  const person = ['John', 'Doe', 'Mark'];
  const index = person.indexOf('Doe');
  
  console.log(index);
  // Output: 1
  ```

- **Iteration methods**

  Yaitu kumpulan method-method yang biasa digunakan untuk nge-_loop_ array dan melakukan operasi-operasi yang diinginkan. Misalnya ```Array.forEach()```, ```Array.map()```, ```Array.filter()```, ```Array.reduce()```, dll.

- **Sorting methods**

  Yaitu kumpulan method-method yang biasa digunakan untuk nge-_sort_ / mengurutkan array. Misalnya ```Array.sort()```, ```Array.reverse()```, dll.

Semua method-method diatas tidak mungkin kita bahas satu-satu dalam buku ini. Untuk mengetahui semua method-method yang tersedia, silahkan visit [MDN JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

Pada pembahasan berikutnya kita mungkin akan banyak menggunakan contoh-contoh code menggunakan Array. Oleh karena itu agar semakin terbiasa, baiknya di baca ulang dan dicoba lagi beberapa kali yah.


### Array Multidimensi

Array multidimensi adalah array yang terdiri dari array lainnya atau bisa juga dibilang nested array.

contoh:

```javascript
let arr = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

console.log(arr[1][2]);
// Output: 6

console.log(arr[0]);
// Output: [ 1, 2, 3 ]
```

Ketika membangun _real-world_ aplikasi, kita akan sering menggunakan array multidimensi yang di _combine_ dengan Object. Biasanya array multidimensi campur object ini didapat dari API / Backend. Seperti contoh:

```javascript
{
  status: true,
  message: "success",
  data: [
    { 
      id: 1, 
      country: "Indonesia", 
      province: [
        "DKI Jakarta",
        "Jawa Barat",
        "Jawa Tengah",
        "Jawa Timur",
        // ...
      ] 
    },
    // ...
  ]
}
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

  Catatan: saat menggunakan ```Array.indexOf()```, jika sebuah element tidak ada di dalam array maka ```-1``` akan direturn.
