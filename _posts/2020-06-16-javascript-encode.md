---
layout: post
title:  "JavaScript文字轉碼"
date:   2020-06-16 00:00:00 +0800
categories: javascript
---

Keyword: `encodeURI`, `encodeURIComponent`.

Browser compatibility: Internet Explorer 5.5+, Edge, Chrome, Firefox and Safari.

---

# 中文字轉URI

`encodeURI`

```javascript
var str = "https://username:password@www.example.com:80/path/to/file.html?a=1&b=this+has+spaces#anchor&c=測試";
console.log( encodeURI( str ) ); // https://username:password@www.example.com:80/path/to/file.html?a=1&b=this+has+spaces#anchor&c=%E6%B8%AC%E8%A9%A6
```

---

# 中文字、符號轉URI

`encodeURIComponent`

```javascript
var str = "https://username:password@www.example.com:80/path/to/file.html?a=1&b=this+has+spaces#anchor&c=測試";
console.log( encodeURIComponent( str ) ); // https%3A%2F%2Fusername%3Apassword%40www.example.com%3A80%2Fpath%2Fto%2Ffile.html%3Fa%3D1%26b%3Dthis%2Bhas%2Bspaces%23anchor%26c%3D%E6%B8%AC%E8%A9%A6
```
