# Loop

Loop atau perulangan adalah salah satu konsep paling fundamental dalam sebuah bahasa pemrograman. Loop ini memungkinkan komputer untuk melakukan sebuah tugas yang sama berkali-kali secara otomatis atau sesuai dengan batasan yang kita tentukan tanpa kita menulis tugas itu satu per satu.

Misal kita diminta untuk mencetak bilangan ```1``` sampai ```100```. Dengan cara convensional, kita menulis dengan cara seperti di bawah satu persatu 100 kali.

```javascript
console.log(1);
console.log(2);
console.log(3);
...
console.log(70);
...
...
console.log(99);
console.log(100);
```

Nah daripada menulis manual satu persatu, kita bisa pakai bantuan loop. Misal _case_ di atas kita selesaikan dengan ```for``` loop menjadi:

```javascript
for (let i = 1; i <= 100; i++) {
  console.log(i);
}
```

Di JavaScript ada beberapa cara untuk melakukan perulangan atau loop, yaitu menggunakan statement ```for``` loop, ```while``` loop dan ```do..while``` loop. Ada juga perulangan dengan statement ```for-in``` dan  ```for-of```. Yang dua terakhir akan lebih khusus kita bahas di materi tentang Object dan Array.


### ```for``` loop

```for``` adalah loop yang paling umum digunakan terlebih jika kita tahu diawal berapa jumlah iterasi yang akan dilakukan.

sintaks:

```javascript
for(begin; condition; step) {
  // lakukan iterasi baris code di dalam sini
}
```

contoh:

```javascript
for (let i = 1; i <= 100; i++) {
  console.log(i);
}
```

Code di atas sejatinya adalah memerintahkan JavaScript untuk mencetak bilangan ```1``` sampai ```100``` menggunakan ```for``` loop.


#### Cara kerja ```for``` loop

Secara sederhana berikut adalah cara kerja ```for``` loop. Misal code berikut

```javascript
for (let i = 1; i < 5; i++) {
  console.log(i);
}
```

cara kerjanya adalah seperti berikut

```javascript
step #1 : inisialisasi let i = 1
step #2 : Cek nilai i < 5, Jika benar maka #3, Jika salah maka #5
step #3 : eksekusi console.log(i);
step #4 : increment i atau i++
step #5 : exit loop
```

output:

```javascript
1
2
3
4
```

Di internal JavaScript saat eksekusi Loop di atas nilai dari ```i``` sebenarnya sampai dengan angka ```5```. Tapi karena kondisi ```i < 5``` dan
jika dievaluasi menjadi ```5 < 5``` hasilnya adalah false, maka loop nya berhenti dan yang akan di print hanya sampai angka ```4``` saja.

Lalu kemana angka ```5``` nya?. Kita bisa lihat angka ```5``` nya jika memakai keyword ```var``` pada loop nya.

```javascript
for (var i = 1; i < 5; i++) {
  console.log(i); 
}

console.log(i); // 5
```

terlihat bahwa nilai terakhir variable ```i``` adalah 5 dan masih bisa di akses di luar loop. Hal ini karena ketika menggunakan keyword ```var```, maka JavaScript di belakang layar akan melakukan variable _hoisting_ yaitu dengan mengangkat deklarasi ```var i``` ke atas seperti ini.

```javascript
var i; // default value undefined

for (i = 0; i < 5; i++) {
  console.log(i);
}

console.log(i); // 5
```

Pembahasan mengenal _hoisting_ dapat dilihat lebih lanjut di pembahasan **_Konsep Dasar > Mengenal Scope di JavaScript_**.

```for``` juga bisa digunakan untuk membuat infinite loop alias looping forever dengan cara seperti ini

```javascript
for(;;) { 
  console.log('looping forever');
}
```

**perhatian**: hati-hati jika ingin menjalankan contoh code looping forever di atas karena bisa membuat tab browser crash. 


### ```while``` loop

sintaks:

```javascript
while (condition) {
  // jalanin code di dalam sini
}
```

Iterasi dalam statement ```while``` akan terus _running_ selama ```condition``` nya  ```truthy``` dan akan _stop_ jika ```condition``` nya ```falsy```. Contoh:

```javascript
let i = 0;

while (i < 5) {
  console.log(i);
  i++;
}
```
output:

```javascript
0
1
2
3
4
```

Loop di atas akan melakukan 5x iterasi dan _stop_ saat nilai ```i``` menyentuh angka ```5``` karena ```5 < 5``` saat di evaluasi akan bernilai ```false```. 

Contoh berikutnya,

```javascript
let age = 30;

while (age != 90) {
  console.log('Masih hidup');
}
```
output:

```javascript
Masih hidup
Masih hidup
Masih hidup
...
...
Masih hidup
...
```
Loop di atas akan terus _running_ alias _looping forever_ sampai ada yang merubah nilai variable ```age``` menjadi ```90```. 

contoh lain:

```javascript
let age = 3;

while (age) {
  console.log(age);
  age--;
}
```
output:

```javascript
3
2
1
```

Pada contoh di atas iterasi akan terus _running_ hanya jika statement ```while (age) ``` masih bernilai _truthy_. Saat ```age``` bernilai ```0``` (ingat bahwa ```0``` termasuk salah satu value yang bersifat```falsy```), maka iterasi tidak akan dilanjutkan oleh karena itu pada bagian _output_ hanya angka 3, 2, dan 1 yang akan di print.

Dengan definisi dan contoh di atas kita simpulkan bahwa ```while``` lebih cocok digunakan saat jumlah iterasi (berapa kali-nya) tidak diketahui dengan pasti. Kita hanya tahu pokoknya selama kondisinya ```truthy```, ya lakukan terus iterasinya.


### ```do..while``` loop

Gunakan statement ```do...while``` saat kita ingin melakukan sebuah perulangan minimal satu kali dan iterasi akan terus _running_ sampai ```condition``` nya bernilai ```falsy```. Nah disini kata kuncinya, hanya gunakan ```do...while``` saat kita ingin loop nya _stop_
ketika ketemu ```condition``` false atau ```falsy```.

sintaks:

```javascript
do {
  // jalanin block code di dalam sini
} while (condition);
  // selama condition nya belum falsy
```

contoh:

```javascript
let i = 0;

do {
  i += 1;
  console.log(i);
} while (false);
```

output:
```javascript
1
```

Sebagaimana definisi di atas, block code di dalam ```do-while``` tetap akan di eksekusi (minimal) **satu kali** meskipun condition-nya **false**.

Perhatikan lagi contoh dibawah ini:

```javascript
let i = 0;

do {
  i += 1;
  console.log(i);
} while (i < 5);
```
output:

```javascript
1
2
3
4
5
```

Pertama JavaScript akan eksekusi block code di dalam ```do-while``` yakni dengan mem-_print_ angka ```1``` (hasil operasi dari 0 + 1 pada expression ```i += 1```). Setelah itu JavaScript akan cek apakah condition-nya belum ```false / falsy```. Selama belum ```false```, lakukan lagi iterasi **dan** eksekusi block code nya sampai ketemu _falsy_ yaitu saat nilai ```i``` menjadi 5.

Perhatikan bahwa angka **5** tetap diprint karena memang ```do-while``` tetap akan meng-eksekusi block code di dalamnya dahulu meskipun condition saat ini (yakni nilai ```i``` akan menjadi ```5```) bernilai ```false```. 


### Nested loop

Semua jenis loop bisa bersarang atau nested. Ini biasa terjadi ketika kita butuh ada operasi perulangan lagi di dalam perulangan.

contoh:

```javascript
let star = "";

for (let i = 1; i <= 4; i++) {  
  for (let j = 0; j < 2 * i - 1; j++) {
    star += "*";
  }
  star += "\n";
}

console.log(star);
```

output:

```javascript
*
***
*****
*******
```

Contoh nested loop dengan while untuk membuat segitiga yang sama

```javascript
let i = 1;

while (i <= 4) {
  let j = 1;
  let line = "";
  while (j < 2 * i) {
    line += "*";
    j++;
  }
  console.log(line);
  i++;
}
```

Contoh lain nested loop yang lebih konkret misalkan kita punya beberapa data user, dan masing-masing user punya akun media sosial.

```js
let users = [
  {
    name: "Budi Santoso",
    age: 28,
    social_media: [
      { platform: "Twitter", username: "@budi_s" },
      { platform: "Instagram", username: "@budigram" }
    ]
  },
  {
    name: "Sari Dewi",
    age: 25,
    social_media: [
      { platform: "LinkedIn", username: "sari-dewi" },
      { platform: "Instagram", username: "@saridewi" },
      { platform: "YouTube", username: "Sari Vlog" }
    ]
  }
];

for (let i = 0; i < users.length; i++) {
  let user = users[i];

  console.log("Nama:", user.name);
  console.log("Usia:", user.age);
  console.log("Akun Media Sosial:");

  let sosmed = user.social_media;

  for (let j = 0; j < sosmed.length; j++) {
    let account = sosmed[j];

    console.log(
      "- " + account.platform + ": " + account.username
    );
  }

  console.log("");
}
```

output:

```js
Nama: Budi Santoso
Usia: 28
Akun Media Sosial:
- Twitter: @budi_s
- Instagram: @budigram

Nama: Sari Dewi
Usia: 25
Akun Media Sosial:
- LinkedIn: sari-dewi
- Instagram: @saridewi
- YouTube: Sari Vlog
```

**Catatan**: Untuk operasi loop pada array object seperti di atas sebenarnya adalah cara yang biasa dan lebih umum dilakukan yaitu menggunakan _method_ bawaan dari **Array** seperti ```forEach```, ```map```, ```filter``` dan sebagainya. Namun kita akan bahas lebih lanjut tentang _method-method_ ini nanti di materi tentang Object dan Array.


### break dan continue

Pada operasi perulangan, tentu saja suatu waktu kita butuh untuk bisa _stop_ / exit perulangan pada kondisi tertentu. Untuk hal ini kita bisa pakai statement ```break``` pada loop.

contoh:

```javascript
for (let i = 1; i <= 4; i++) {  
  console.log(i);
  if (i === 2) {
    console.log('stop di angka: ' + i);
    break;
  }
}
```

output:

```javascript
1
2
stop di angka: 2
```

Terlihat bahwa perulangannya berhenti atau _exit_ ketika nilai ```i``` sama dengan 2.


Kemudian kita bisa pakai ```continue``` untuk _stop_ sejenak lalu lanjutkan iterasi-nya. Contoh:

```javascript
for (let i = 1; i <= 4; i++) {  
  console.log(i);

  if (i === 2) {
    console.log('stop dulu di angka: ' + i);
    console.log('ngopi dulu sejenak');
    continue;
  }
}
```

output:

```javascript
1
2
stop dulu di angka: 2
ngopi dulu sejenak
3
4
```

Sebelum lanjut ke materi berikutnya, baiknya coba latihan beberapa kali dulu yah masing-masing jenis loop-nya agar semakin paham dan menguasai sehingga nanti lebih mudah untuk menentukan jenis loop mana yang lebih cocok sesuai dengan kasusnya.