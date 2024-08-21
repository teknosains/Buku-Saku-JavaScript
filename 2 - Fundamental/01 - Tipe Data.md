## Tipe Data di JavaScript

Sebuah nilai/_value_ akan selalu disimpan dalam suatu tipe data. Dan ada 8 Tipe Data di JavaScript yang harus kita kuasasi, ke-8 tipe data itu dikelompokan menjadi **Primitif** dan **Non-Primitif**.

##### Primitf

1. ```null```
2. ```undefined```
3. ```boolean```
4. ```number```
6. ```bigint```
7. ```string```
8. ```symbol```

##### Non-Primitif
8. ```object```

Ke-8 tipe data diatas secara umum sama fungsinya yaitu untuk menyimpan suatu nilai / _value_. Normalnya untuk men-check type data suatu value dapat menggunakan operator ```typeof```

```javascript
typeof 12;                  // "number"
typeof 200n                 // "bigint"
typeof "Buku";              // "string"
typeof true;                // "boolean"
typeof undefined;           // "undefined"
typeof null;                // "object" <-- ini bugs bawaan di JS. alih-alih tipe nya null malah object
typeof { name: 'Budi' };    // "object"
typeof [];                  // "object"
typeof function test(){};   // "function"
```
Silahkan buka tab ```console``` di browser dan coba sample code diatas.


#### 1. null

```null``` di javascript adalah _type_ spesial yang me-representasikan _ketiadaan_, _kosong_ atau _tidak diketahui / unkown_. ```null``` sering kali dijadikan _value_ default saat kita mendefinisikan sebuah variable untuk kemudian nilai nya akan di-override / diganti dengan nilai lain.

```javascript
let cuaca = null;

if (langit === 'biru') {
  cuaca = 'Cerah';
} else {
  cuaca = 'Mendung'
}
```
pada contoh diatas, kita bisa katakan bahwa nilai variable ```cuaca``` itu **tidak diketahui** atau **kosong**.

type ```null``` juga bersifat _falsy_, artinya jika di evalusasi, maka akan menjadi _false_ sehingga umum digunakan dalam conditional statement.

Perhatikan contoh berikut

```javascript
let umur = null;

if (umur) {
  console.log('Ada nilai umurnya');
} else {
  console.log('Tidak ada nilai umurnya');
}

// output: Tidak ada nilai umurnya

```
saat ```if (umur)``` di evaluasi oleh JavaScript engine, maka akan menjadi false sehingga eksekusi kode akan masuk ke blok ```else``` dibawah nya.

#### 2. undefined

Di JavaScript type ```undefined``` juga ada special type yang berarti belum di assign / di isi. Sama seperti ```null```, type ```undefined``` juga bersifat falsy.

Contoh

```javascript
let umur;
console.log(umur) 
// output: undefined
console.log(typeof umur) 
// output: "undefined"

// sifat falsy

let umur;

if (umur) {
  console.log('masuk sini');
} else {
  console.log('masuk sana');
}

// output: masuk sana
```
Deklarasi ```let umur;``` artinya bahwa sebuah variable sudah dideklarasikan namun nilai nya belum di assign / di isi.

#### 3. boolean

Boolean mempunyai dua value yaitu ```true``` dan ```false```. Type ini digunakan sebagai operator logika dalam conditional statement.

Contoh

```javascript
let cerah = true;

if (cerah === true) {
  console.log('Pergi keluar');
}

if (cerah) {
  console.log('Pergi keluar');
}

if (cerah === false) {
  console.log('Dirumah saja');
}

if (!cerah) {
  console.log('Dirumah saja');
}

```

#### 4. number

Number digunakan untuk menyimpan value integer (bilangan bulat) atau floating-point. Maksimal nilai integer yang mampu ditampung oleh ```number``` adalah ```±```2<sup>53</sup>-1. 

Contoh

```javascript

// integer

const umur = 12;
let tinggi = 120;

// floating-point

const pi = 3.14;
let panjang = 7.5;

```

#### 5. bigint

Sebagaimana tersirat di namanya, Bigint digunakan untuk menampung nilai integer yang lebih besar daripada ```number```. ```bigint``` memiliki notasi khusus dalam penulisannya value nya yaitu dengan menambahkan ```n``` dibelakang.

Contoh

```javascript
const angka = 1234567890123456789012345678901234567890n;
console.log(angka)

// output: "bigint"
```

#### 6. string

Untuk menyimpan suatu value dalam type ```string``` dapat menggunakan 3 cara yaitu pakai _single quote_, _double quote_ atau _backticks_.



```javascript
// single quote
const nama = 'Budi'

// double quote
const nama = "Budi"

// backticks
const nama = `Budi`;


```

#### 7. symbol

Dalam keseharian coding nanti, kita umumnya akan jarang menggunakan type ```symbol```. Kita akan bahas ```symbol``` lebih detail di lain kesempatan atau bab lain di series ini nanti.

#### 8. object

Type ```object``` adalah bintang nya JavaScript. Kita akan sangat sering membuat, membaca dan memanipulasi object dalam keseharian coding JavaScript nantinya. Untuk membuat object, minimal ada dua cara yaitu dengan menggunakan object _literal_ ```{ }``` atau pakai _constructor_ ```new Object()```

Contoh

```javascript
// membuat object langsung dengan object literal

const user = {
  nama: 'Budi',
  umur: 33,
  alamat: 'Jl. Kemayoran no 12, Jakarta'
};

// cara mengakses object
console.log(user.nama); // output: Budi

// membuat object dengan new Object()

const user = new Object();

user.nama = 'Budi';
user.umur = 12;
user.alamat = 'Jl. Kemayoran no 12, Jakarta';

console.log(user);

// output: {nama: 'Budi', umur: 12, alamat: 'Jl. Kemayoran no 12, Jakarta'}
```

#### Dimanakah ```Array``` ?

Di JavaScript Array termasuk keluarga ```object```. Oleh karena itu jika kita check type sebuah array maka hasilnya adalah ```object```

```javascript
const nomor = [1, 2, 3, 4, 5];

console.log(typeof nomor); // output: "object"
```

Disarankan untuk mencoba-coba coding sendiri dan menghafal tipe-tipe data diatas karena kedepan ke-8 type ini akan menemani keseharian kita saat coding JavaScript. Selain itu hal ini juga sering kali ditanyakan saat sesi Interview kerja.
