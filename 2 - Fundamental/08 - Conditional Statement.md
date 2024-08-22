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

Switch statement baru digunakan ketika percabangan dengan ```if...else``` sudah mulai sulit dibaca dan memang kondisinya sudah semakin banyak
namun kita hanya punya **satu** expression atau condition untuk diperbandingkan.

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

Normalnya ```switch``` lebih cocok digunakan ketika kita punya **satu** expression yang ingin di _compare_ dengan
beberapa _value_ yang memungkinkan.

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

Perhatikan bahwa kita hanya punya **satu** expression yakni ```cuaca```, dan kita ingin _compare_ isi 
dari ```cuaca``` dengan beberapa kemungkinan value seperti ```terang```, ```mendung```, ```hujan```, dll.

Seandai kita punya lebih dari satu condition, misalkan kita punya ```cuaca``` dan ```suhu``` maka mungkin
memakai ```if``` akan lebih cocok. Misal:

```javascript
if (cuaca === 'terang' && suhu >= 30) {
  console.log('Nonton diluar');
} else if (cuaca === 'mendung' && suhu < 30) {
  // ..dst
}
```

Contoh berikut ini harusnya lebih meyakinkan kita kalau ```switch``` lebih cocok saat kita punya **satu**
condition untuk di _compare_ dengan beberapa bahkan banyak _value_ yang memungkinkan.

```javascript

function printDayName(day) {

  let dayName = '';

  switch (day) {
    case 1:
      dayName = 'Senin';
      break;
    case 2:
      dayName = 'Selasa';
      break;
    case 3:
      dayName = 'Rabu';
      break;
    case 4:
      dayName = 'Kamis';
      break;
    case 5:
      dayName = 'Jumat';
      break;
    case 6:
      dayName = 'Sabtu';
      break;
    case 7:
      dayName = 'Minggu';
      break;
    default:
      dayName = 'Hari tidak dikenali';
      break;
  }

  return dayName;

}

console.log(
  printDayName(7)
);

// Output: Minggu
```

Kalau diperhatikan lagi, menggunakan contoh potongan code yang sama, penulisan dengan ```switch``` terlihat lebih mudah dibaca dan code menjadi lebih clean. 
Untuk kondisi percabangan yang cukup banyak, jika menggunakan ```if...else``` maka secara natural mata kita akan scan tiap kondisi pada  ```if...else``` nya sampai akhir.

#### Fitur ```fall-through``` di statement ```switch```

Bagaimana kalau kita ingin multiple condition dengan ```switch```?. ```switch``` punya behaviour spesial yang 
biasa disebut ```fall-through```, yaitu kondisi dimana jika sebuah ```case``` tidak punya statement ```break```,
maka eksekusi code akan dilanjutkan ke ```case``` selanjutnya sampai ketemu ```break```.

```fall-through``` ini dapat bisa dibilang se-prilaku dengan condition ```OR``` di ```if``` saat kita punya
multiple condition.

contoh:

```javascript
function workStatus(day) {

  let status = '';

  switch (day) {
    case 1:
    case 2:
    case 3:
    case 4:
    case 5:
      status = 'Hari kerja';
      break;
    case 6:
    case 7:
      status = 'Hari libur kerja';
      break;
    default:
      status = 'Hari tidak dikenali';
      break;
  }

  return status;

}

console.log(
  workStatus(4)
);

// Output: Hari kerja

console.log(
  workStatus(6)
);

// Output: Hari libur kerja
```


**Catatan**: penjelasan diatas bukan untuk menyimpulkan ```switch``` lebih baik dari```if...else```. Keduanya sama namun harus digunakan sesuai dengan fungsi dan kasusnya masing-masing. 
