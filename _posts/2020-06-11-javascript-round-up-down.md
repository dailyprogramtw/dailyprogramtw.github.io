---
layout: post
title:  "JavaScript亂數、四捨五入、無條件進位、無條件捨去和小數點第2位"
date:   2020-06-11 00:00:00 +0800
categories: javascript
---

Keyword: `Math.round`, `Math.ceil`, `Math.floor`, `Math.random` and `Math.abs`.

Browser compatibility: Internet Explorer 5.5+, Edge, Chrome, Firefox and Safari.

---

# 亂數

		getRandom = function( min, max )
		{
			return Math.floor( Math.random() * ( max - min + 1 ) + min );
		}

		console.log( getRandom( 1, 2 ) ) // 1 or 2

---

# 四捨五入

		console.log( Math.round( 3.4 ) ); // 3
		console.log( Math.round( 3.45 ) ); // 3
		console.log( Math.round( 3.5 ) ); // 4

---

# 無條件進位

		console.log( Math.ceil( 3.4 ) ); // 4
		console.log( Math.ceil( 3.45 ) ); // 4
		console.log( Math.ceil( 3.5 ) ); // 4

---

# 無條件捨去

		console.log( Math.floor( 3.4 ) ); // 3
		console.log( Math.floor( 3.45 ) ); // 3
		console.log( Math.floor( 3.5 ) ); // 3

---

# 小數點第2位

## 四捨五入

		roundTo = function( num, decimal )
		{
			return Math.round( ( num + Number.EPSILON ) * Math.pow( 10, decimal ) ) / Math.pow( 10, decimal );
		}
		console.log( roundTo( 1.014, 2 ) ); // 1.01
		console.log( roundTo( 1.015, 2 ) ); // 1.02

## 無條件進位

		roundUp = function( num, decimal )
		{
			return Math.ceil( ( num + Number.EPSILON ) * Math.pow( 10, decimal ) ) / Math.pow( 10, decimal );
		}
		console.log( roundUp( 1.014, 2 ) ); // 1.02
		console.log( roundUp( 1.015, 2 ) ); // 1.02

## 無條件捨去

		roundDown = function( num, decimal )
		{
			return Math.floor( ( num + Number.EPSILON ) * Math.pow( 10, decimal ) ) / Math.pow( 10, decimal );
		}
		console.log( roundDown( 1.014, 2 ) ); // 1.01
		console.log( roundDown( 1.015, 2 ) ); // 1.01

---

# 絕對值

		console.log( Math.abs( 3 ) ); // 3
		console.log( Math.abs( -3 ) ); // 3