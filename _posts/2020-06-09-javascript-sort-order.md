---
layout: post
title:  "JavaScript陣列、物件和JSON排序"
date:   2020-06-09 00:00:00 +0800
categories: javascript
---

Keyword: `sort`, `reduce` and `Object.keys`.

Browser compatibility: Internet Explorer 9+, Edge, Chrome, Firefox and Safari.

---

# 陣列

## 小到大排序

		var arr = [ 1, 3, 2 ];
		arr.sort()
		console.log( arr ); // [ 1, 2, 3 ]

## 大到小排序

		var arr = [ 1, 3, 2 ];
		arr.sort( function ( a, b ) { return ( a > b ? -1 : 1 ) } )
		console.log( arr ); // [ 3, 2, 1 ]

---

# 物件

## 小到大排序

		var obj = { a: 1, c: 3, b: 2 };
		obj = Object.keys( obj ).sort()
		    .reduce( function ( accumulator, currentValue ) { 
		        accumulator[ currentValue ] = obj[ currentValue ] ;
		        return accumulator;
		}, {});
		console.log( obj ); // { a: 1, b: 2, c:3 }


## 大到小排序

		var obj = { a: 1, c: 3, b: 2 };
		obj = Object.keys( obj ).sort( ( a, b ) => ( a > b ? -1 : 1 ) )
		    .reduce( function ( accumulator, currentValue ) { 
		        accumulator[ currentValue ] = obj[ currentValue ] ;
		        return accumulator;
		}, {});
		console.log( obj ); // { c: 3, b: 2, a:1 }

---

# JSON

## 小到大排序

		var json = [{ name: "Tom", age: 20 }, { name: "Jack", age: 25 }, { name: "Mary", age: 23 }];
		json.sort( function( key, a, b ) { return a[ key ] - b[ key ]; }.bind( null, "age" ) );
		console.log( json ); // [{ name: "Tom", age: 20 }, { name: "Mary", age: 23 }, { name: "Jack", age: 25 }];


## 大到小排序

		var json = [{ name: "Tom", age: 20 }, { name: "Jack", age: 25 }, { name: "Mary", age: 23 }];
		json.sort( function( key, a, b ) { return b[ key ] - a[ key ]; }.bind( null, "age" ) );
		console.log( json ); // [{ name: "Jack", age: 25 }, { name: "Mary", age: 23 }, { name: "Tom", age: 20 }];
		