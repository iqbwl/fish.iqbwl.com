---
title: "Redirect menggunakan html"
date: 2022-09-22T09:59:56+07:00
draft: false # Set 'false' to publish
description: "URL redirection, also called URL forwarding, is a World Wide Web technique for making a web page available under more than one URL address. When a web browser attempts to open a URL that has been redirected, a page with a different URL is opened"
tags:
- html
layout: "simple"
---

Untuk redirect menggunakan html, cukup tambahkan parameter berikut pada header html:
```html
<meta http-equiv="Refresh" content="0; url='https://iqbal.id'" />
```

Agar ada jeda beberapa detik sebelum redirect, ganti value `content` menjadi angka yang diinginkan, misal 3 untuk 3 detik.
```html
<meta http-equiv="Refresh" content="3; url='https://iqbal.id'" />
```

Contoh html:
```html
<!DOCTYPE html>
<html>
  <head>
    <meta http-equiv="refresh" content="3; url='https://iqbal.id'" />
  </head>
  <body>
    <p>lanjut ke <a href="https://iqbal.id">iqbal.id</a>.</p>
  </body>
</html>
```

Selesai.