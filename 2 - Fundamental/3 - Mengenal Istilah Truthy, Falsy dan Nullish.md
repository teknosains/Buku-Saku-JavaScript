# Mengenal Istilah Truthy, Falsy dan Nullish
Memahami ketiga istilah diatas sangat penting mengingat istilah-istilah ini sering banget dipakai ketika
kita baca tutorial, komunikasi atau ngobrol dengan programmer lain. Jadi ini wajib kita hafal dan sering kita gunakan juga nantinya dalam keseharian coding.



### Truthy

Adalah sebuah _value_ yang selalu bernilai ```true```. Semua _value_ adalah ```true``` kecuali yang didefinisikan sebagai **Falsy** atau **Nullish**. Untuk menguji suatu value _Truthy_ dapat menggunakan ```Boolean(value)```

contoh:

```javascript
console.log(true); // true

let name = 'Agus';
console.log(Boolean(name)); // true

let age = 20;
console.log(Boolean(age)); // true

if (name) {
  console.log('Nama saya ' + name);
} else {
  console.log('Nama harus diisi');
}

// Output: Nama saya Agus

```

Dalam contoh diatas variable ```name``` bernilai truthy dan bisa digunakan dalam _conditional statement_ untuk menguji
apakah variable ```name``` ada isinya atau tidak.

### Falsy

Adalah sebuah value yang selalu bernilai ```false``` jika di evaluasi dengan ```Boolean(value)```.
Daftar falsy value adalah ```false```, ```0```, ```-0```, ```0n```, ```''```, ```null```, ```undefined```, ```NaN```.

contoh:

```javascript
console.log(false); // false

let name = '';
console.log(Boolean(name)); // false

if (name) {
  console.log('Nama saya ' + name);
} else {
  console.log('Nama harus diisi');
}

// Output: Nama harus diisi
```

### Nullish

Adalah sebuah value yang selalu bernilai ```null``` **atau** ```undefined```. Perhatikan bahwa Nullish adalah bagian dari Falsy yang artinya akan selalu false jika di evaluasi dengan ```Boolean(value)```.

contoh:

```javascript
console.log(null); // null
console.log(undefined); // undefined

let name;
console.log(name); // undefined
```

Perhatikan bahwa variable ```name``` hanya di deklarasikan (tanpa di definisikan atau di beri sebuah value). Oleh karena itu variable ```name``` akan secara _default_ akan bernilai ```undefined```.

Sebagai tambahan, jika kita mendeklarasikan sebuah variable menggunakan keyword ```const``` (tanpa mendefinisikan value), maka JavaScript akan me-return _SyntaxError: Missing initializer in const declaration_.

contoh:

```javascript
const name;
console.log(name);

// SyntaxError: Missing initializer in const declaration

const name = 'Agus';
console.log(name); 

// Output: Agus

```

