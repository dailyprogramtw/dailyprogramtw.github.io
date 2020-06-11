---
layout: post
title:  "JavaScript陣列、物件和JSON移除重覆資料"
date:   2020-06-10 00:00:00 +0800
categories: javascript
---

Keyword: `filter`, `some` and `Object.keys`.

Browser compatibility: Internet Explorer 9+, Edge, Chrome, Firefox and Safari.

---

# 陣列

		var arr = [ 1, 2, 1, 2, 3 ];
		arr = arr.filter( function ( a, b ) { return arr.indexOf(a) === b } );
		console.log( arr ); // [ 1, 2, 3 ]
		
---

# 物件

		var obj = {  a: 1, b: 2, a: 1, b: 2, c: 3 };
		obj = Object.keys( obj ).reduce( function ( accumulator, currentValue ) { 
		    accumulator[ currentValue ] = obj[ currentValue ] ;
		    return accumulator;
		}, {});
		console.log( obj ); // { a: 1, b: 2, c:3 }

---

# JSON

		var json = [{ name: "Tom", age: 20 }, { name: "Jack", age: 25 }, { name: "Tom", age: 20 }, { name: "Jack", age: 25 }, { name: "Mary", age: 23 }];
		json = json.filter( function ( element, index, arr ) {
			var i = -1;
			arr.some( function( currentValue, index2 ) { if ( JSON.stringify( currentValue ) === JSON.stringify( element ) ) { i = index2; } }) 
			return ( i === index  )
		} )
		console.log( json ); // [{ name: "Tom", age: 20 }, { name: "Jack", age: 25 },  { name: "Mary", age: 23 }]

**recommend(not support Internet Explorer):**

		let json = [{ name: "Tom", age: 20 }, { name: "Jack", age: 25 }, { name: "Tom", age: 20 }, { name: "Jack", age: 25 }, { name: "Mary", age: 23 }];
		json = json.filter( ( element, index, arr ) => arr.findIndex( element2 => ( JSON.stringify( element2 ) === JSON.stringify( element ) ) ) === index )
		console.log( json ); // [{ name: "Tom", age: 20 }, { name: "Jack", age: 25 },  { name: "Mary", age: 23 }]






