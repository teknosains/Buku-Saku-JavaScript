# Conditional Statement

Conditional statement atau percabangan digunakan untuk untuk membuat atau menentukan keputusan. Ada tiga cara untuk membuat percabangan yaitu dengan ```if..else```, ```switch``` dan ```ternary```. Ternary sendiri sudah kita bahas di halaman sebelumnya _so_ sekarang kita akan hanya focus mengenal ```if..else``` dan ```switch```.


### if...else

Sintaks:
```javascript
if (condition) {
 // masuk sini jika kondisi true 
} else {
 // masuk sini jika kondisi false
}
```

Ada beberapa ragam penulisan statement ```if..else``` yang umum digunakan seperti ```if``` tanpa ```else```.

sintaks:

```javascript
if (condition) {
  // masuk sini jika kondisi true
}

// jalankan code lain
```
contoh:

```javascript
let score = 60;
let defaultStatus = 'Lulus';

if (score < 70) {
  defaultStatus = 'Tidak Lulus';
}

let name = 'Agus';
let gender = 'Pria';

console.log('Agus' + defaultStatus + ' ujian');

// Output: Agus Tidak Lulus ujian
```

contoh lain:

```javascript
function checkStatus(score) {
  if (score < 70) {
    return 'Tidak Lulus';
  }

  return 'Lulus';
}

console.log(
  checkStatus(60)
);

// Output: Tidak Lulus
```

Berikutnya adalah penulisan ```if...else``` tanpa kurung kurawal ```{...}```. Contoh:
```javascript
let score = 60;

if (score < 70) console.log('Tidak lulus');
else console.log('Lulus');

// Output: Tidak lulus
```

Cara penulisan diatas valid-valid saja sebenarnya namun akan lebih memudahkan untuk dibaca dan dimengerti kalau kita menuliskan ```if...else``` dengan kurung kurawal. 

```javascript
let score = 60;

if (score < 70) {
  console.log('Tidak lulus');
} else {
  console.log('Lulus');
}

// Output: Tidak lulus
```

Kelemahan berikutnya dari penulisan tanpa kurung kurawal adalah bahwa kita hanya bisa menulis **satu baris** statetement saja. Jika lebih dari satu maka akan _Error_.

contoh:
```javascript
let score = 60;

if (score < 70) 
  console.log('Tidak lulus');
  console.log('Code lainnya');
else 
  console.log('Lulus');

// SyntaxError: Unexpected token 'else'
```

### if...else if...else
Sesuai kebutuhan, statement ```if...else``` bisa kita tulis lebih dari satu kali dan bahkan sebanyak-banyaknya. Meskipun kalau kebanyakan akan membuat _code_ kita terlihat jelek dan tidak efisien.

contoh:
```javascript
function checkWeather(cuaca) {
  
  if (cuaca === 'terang') {
    return 'Nonton diluar';
  } else if (cuaca === 'mendung') {
    return 'Nonton di tetangga';
  } else if (cuaca === 'hujan') {
    return 'Nonton di rumah';
  } else {
    return 'Cuaca tidak dikenali';
  }

}

let nonton = checkWeather('berasap');
console.log(nonton);

// Output: Cuaca tidak dikenali
```
Pada contoh diatas, JavaScript pertama kali akan cek apakah ```cuaca === 'terang'```. Jika _falsy_, maka lanjut ke kondisi berikutnya ```cuaca === 'mendung'```. Jika masih _falsy_ juga, maka lanjut ke kondisi berikutnya ```cuaca === 'hujan'```. Jika _falsy_ juga, maka akan masuk ke blok ```else``` terakhir ```return 'Cuaca tidak dikenali''```.


### Nested if...else
Secara sederhana, kondisi Nested atau bersarang (sebaiknya jangan pakai istilah _bersarang_ dalam keseharian nanti yah :D ) digunakan saat kita butuh ada ```if``` didalam ```if``` dan ini sangat umum digunakan dalam keseharian coding.

contoh:
```javascript
let score = 60;
let behaviour = 'Baik';
let status = '';

if (score < 70) {
  if (score >= 60) {
     if (behaviour === 'Baik') {
       status = 'Lulus bersyarat';
     } else if (behaviour === 'Tidak Baik') {
       status = 'Tidak lulus';
     } 
  } else {
    status = 'Tidak lulus';
  }
} else {
  status = 'Lulus';
}

console.log(status);

// Output: Lulus bersyarat
```
Pada contoh diatas pertama JavaScript akan cek apakah ```score < 70```, jika ```true``` maka akan lanjut ke ```if``` dibawahnya
untuk cek ```score >= 60```, jika ternyata score nya >= 60 maka harus di cek juga _behaviour_-nya, kira-kira begitu seterusnya.

### switch

Switch statement baru digunakan ketika percabangan dengan ```if...else``` sudah mulai sulit dibaca dan memang kondisinya sudah semakin banyak.

sintaks:
```javascript
switch (condition) {
  case value1:
    // jalanin code ini
    break;
  case value2:
    // jalanin code ini
    break;
  default:
    // kondisi gk ada yg match? jalanin code ini
    break;
}
```

contoh:
```javascript
function checkWeather(cuaca) {
  
  let nonton = '';

  switch (cuaca) {
    case 'terang':
      nonton = 'Nonton diluar';
      break;
    case 'mendung':
      nonton = 'Nonton di tetangga';
      break;
    case 'hujan':
      nonton = 'Nonton di rumah';
      break;
    default:
      nonton = 'Cuaca tidak dikenali';
      break;  
  }

  return nonton;

}

let nonton = checkWeather('berasap');
console.log(nonton);

// Output: Cuaca tidak dikenali
```
Kalau diperhatikan lagi, menggunakan contoh potongan code yang sama, penulisan dengan ```switch``` terlihat lebih mudah dibaca dan code menjadi lebih clean. Untuk kondisi percabangan yang cukup banyak, jika menggunakan ```if...else``` maka secara natural mata kita akan scan tiap kondisi pada  ```if...else``` nya sampai akhir.

**Catatan**: penjelasan diatas bukan untuk menyimpulkan ```switch``` lebih baik dari```if...else```. Keduanya sama namun harus digunakan sesuai dengan fungsi dan kasusnya masing-masing. 