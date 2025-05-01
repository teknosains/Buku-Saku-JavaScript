# Konsep Dasar DOM (Document Object Model)
Di pembahasan sebelumnya kita sudah banyak berbicara mengenai fundamental JavaScript beserta teorinya. Sekarang waktunya kita _refreshment_ dengan mengenal lebih dekat apa itu DOM dan bagaimana cara kerjanya.

DOM adalah cara browser merepresentasikan halaman web dalam bentuk pohon (tree). Setiap elemen atau _tag_ HTML dianggap sebagai _object_ yang bisa kita akses dan modifikasi menggunakan JavaScript. Ketika kita menulis kode HTML misal seperti berikut:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Belajar JavaScript</title>
  </head>
  <body>
    <h1>Selamat datang!</h1>
  </body>
</html>
```
