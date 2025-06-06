## Mengenal ECMAScript (ES)

Pada tahun 1997, dikarenakan perkembangan dan popularitas JavaScript yang makin menanjak maka JavaScript sangat perlu untuk di _maintain_ dan distandarisasi dengan lebih baik. Oleh karena itu Netscape menyerahkan pengembangan standarisasi dan spesifikasi JavaScript kepada European Computer Manufacturers Association (ECMA), lembaga yang mengurusi standarisasi sistem/teknologi komputer. Dan dibentuklah _"divisi"_ [Technical Committee 39 (TC39)](https://github.com/tc39) yang bertugas untuk mengembangkan JavaScript lebih lanjut.

Setelah itu JavaScript mulai berkembang dengan spesifikasi dan standarisasi baru dengan kode ES. Kamu akan sering dengar istilah ES4, ES5, ES6, ES7 dst. Penamaan ini merepresentasikan versi spesifikasi atau **versi JavaScript** yang dikeluarkan oleh ECMA. Spesifikasi ini biasanya akan diikuti oleh pengembang browser atau JavaScript Engine (V8 dari Google, SpiderMonkey dari Mozilla, JavaScriptCore dari Apple dll).

Ketika pengembang browser dan JavaScript Engine sudah mengikuti spesifikasi terbaru, maka fitur-fitur terbaru JavaScript akan di support di berbagai browser populer. Namun tidak semua pengembang browser / JS Engine implementasi spesifikasi / versi terbaru secara bersamaan, oleh kerena itu kita sering lihat suatu fitur itu sudah tersedia di browser tertentu namun belum tersedia di browser lainnya.

## Daftar Edisi ECMAScript

| Versi         | Nama Resmi         | Keterangan    |
| ------------- |--------------------| --------------|
| ES1           | ECMAScript 1 (1997)| Edisi pertama |
| ES2           | ECMAScript 2 (1998)|               |
| ES3           | ECMAScript 3 (1999)| penambahan _regular expressions, try/catch, switch, do-while_|
| ES4           | ECMAScript 4       | tidak dirilis |
| ES5           | ECMAScript 5 (2009)| penambahan _strict mode_, JSON, method looping pada Array dll|
| ES6           | ECMAScript 2015    | penambahan _let dan const_, _Array.find()_, _Array.findIndex()_, value untuk paramater default di function|

Sejak 2016, perilisan ECMAScript secara resmi tidak menggunakan kode ES lagi, tapi langsung menggunakan nama resminya. Namun kebanyakan orang tetap melabeli dengan kode ES


| Versi (Unofficial) | Nama Resmi         | Keterangan    |
| -------------------|--------------------| --------------|
| ES7                | ECMAScript 2016    | penambahan operator exponensial (**), _Array.includes()_ |
| ES8                | ECMAScript 2017    | penambahan _Object.entries()_, _Object.values()_, _async functions_ dll |
| _dst..._           | ...                | ...

Selengkapnya bisa dibaca [https://www.w3schools.com/js/js_versions.asp](https://www.w3schools.com/js/js_versions.asp) 
