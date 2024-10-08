# Loop

Loop atau perulangan adalah salah satu konsep paling fundamental dalam sebuah bahasa pemrograman. Loop ini memungkinkan komputer untuk melakukan sebuah tugas yang sama berkali-kali secara otomatis atau sesuai dengan batasan yang kita tentukan tanpa kita menulis tugas itu satu per satu.

Misal kita diminta untuk mencetak bilangan ```1``` sampai ```100```. Dengan cara convensional, kita menulis dengan cara seperti dibawah satu persatu 100 kali.

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

Nah daripada menulis manual satu persatu, kita bisa pakai bantuan loop. Misal _case_ diatas kita selesaikan dengan ```for``` loop menjadi:

```javascript
for (let i = 1; i <= 100; i++) {
  console.log(i);
}
```

Di JavaScript ada beberapa cara untuk melakukan perulangan atau loop, yaitu menggunakan statement ```for``` loop, ```while``` loop dan ```do..while``` loop. Ada juga perulangan ```for-in``` loop dan ```for-of``` loop. Yang dua terakhir akan lebih khusus kita bahas di materi tentang Object dan Array.


### ```for``` loop

```for``` adalah loop yang paling umum digunakan terlebih jika kita tahu diawal berapa jumlah iterasi yang akan dilakukan.

sintaks:

```javascript
for(begin; condition; step) {
  // lakukan iterasi baris code didalam sini
}
```

contoh:

```javascript
for (let i = 1; i <= 100; i++) {
  console.log(i);
}
```

Code diatas sejatinya adalah memerintahkan JavaScript untuk mencetak bilangan ```1``` sampai ```100``` menggunakan ```for``` loop.


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
step #2 : Cek apakah nilai i < 5, Jika benar maka #3, Jika salah maka #5
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

Di internal JavaScript saat eksekusi Loop diatas nilai dari ```i``` sebenarnya sampai dengan angka ```5```. Tapi karena kondisi ```i < 5``` dan
jika dievaluasi menjadi ```5 < 5``` hasilnya adalah false, maka loop nya berhenti dan yang akan di print hanya sampai angka ```4``` saja.

Lalu kemana angka ```5``` nya?. Kita bisa lihat angka ```5``` nya jika memakai keyword ```var``` pada loop nya.

```javascript
for (var i = 1; i < 5; i++) {
  console.log(i); 
}

console.log(i); // 5
```

terlihat bahwa nilai terakhir variable ```i``` adalah 5 dan masih bisa di akses di luar loop. Hal ini karena ketika menggunakan keyword ```var```, maka JavaScript dibelakang layar akan melakukan variable _hoisting_ yaitu dengan mengangkat deklarasi ```var i``` ke atas seperti ini.

```javascript
var i; // dgn default value undefined
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

**perhatian**: hati-hati jika ingin menjalankan contoh code looping forever diatas karena bisa membuat tab browser crash. 


### ```while``` loop

sintaks:

```javascript
while (condition) {
  // jalanin code didalam sini
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

Loop diatas akan melakukan 5x iterasi dan _stop_ saat nilai ```i``` menyentuh angka ```5``` karena ```5 < 5``` saat di evaluasi akan bernilai ```false```. 

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
Loop diatas akan terus _running_ alias _looping forever_ sampai ada yang merubah nilai variable ```age``` menjadi ```90```. 

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

Pada contoh diatas iterasi akan terus _running_ hanya jika statement ```while (age) ``` masih bernilai _truthy_. Saat ```age``` bernilai ```0``` (ingat bahwa ```0``` termasuk salah satu value yang bersifat```falsy```), maka iterasi tidak akan dilanjutkan oleh karena itu pada bagian _output_ hanya angka 3, 2, dan 1 yang akan di print.

Dengan definisi dan contoh diatas kita simpulkan bahwa ```while``` lebih cocok digunakan saat jumlah iterasi (berapa kali-nya) tidak diketahui dengan pasti. Kita hanya tahu pokoknya selama kondisinya ```truthy``` ya lakukan terus iterasi-nya.


### ```do..while``` loop

Gunakan statement ```do...while``` saat kita ingin melakukan sebuah perulangan minimal satu kali dan iterasi akan terus _running_ sampai ```condition``` nya bernilai ```falsy```. Nah disini kata kuncinya, hanya gunakan ```do...while``` saat kita ingin loop nya _stop_
ketika ketemu ```condition``` false atau ```falsy```.

sintaks:

```javascript
do {
  // jalanin block-code didalam sini
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

Sebagaimana definisi diatas, block-code didalam ```do-while``` tetap akan di eksekusi (minimal) **satu kali** meskipun condition nya **false**.

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

Pertama JavaScript akan eksekusi block-code didalam ```do-while``` yakni dengan ngeprint angka ```1``` (hasil operasi dari 0 + 1 pada expression ```i += 1```). Setelah itu JavaScript akan cek apakah condition nya belum ```false / falsy```. Selama belum ```false```, lakukan lagi iterasi **dan** eksekusi block-code nya sampai ketemu _falsy_ yaitu saat nilai ```i``` menjadi 5.

Perhatikan bahwa angka *5* tetap di print karena memang ```do-while``` tetap akan meng-eksekusi block-code didalamnya dahulu meskipun condition saat ini (yakni nilai ```i``` akan menjadi ```5```) bernilai ```false```. 


### Nested loop

Semua jenis loop bisa bersarang atau nested. Ini biasa terjadi ketika kita butuh ada operasi perulangan lagi didalam perulangan.

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

Sebelum lanjut ke materi berikutnya, baiknya coba latihan beberapa kali dulu yah masing-masing jenis loop-nya agar semakin faham dan menguasasi sehingga nanti lebih mudah untuk menentukan jenis loop mana yang lebih cocok untuk _case_ yang kita punya.