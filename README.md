# node-ratify

[![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url]

A library of string, array and javascript object validators.

### Server-side usage

```javascript
var ratify = require('node-ratify');

ratify.isBase64('bm9kZS1yYXRpZnk='); //=> true
```

The library can also be installed through [npm][npm]

```bash
$ npm install -g node-ratify
$ npm install --save node-ratify
```

### Client-side usage

```html
<script type="text/javascript" src="validate.min.js"></script>
<script type="text/javascript">
  validate.isBase64('bm9kZS1yYXRpZnk='); //=> true
</script>
```

The library can also be installed through [bower][bower]

```bash
$ bower install node-ratify
```

### Clone the repo

```bash
$ git clone https://github.com/luthraG/node-validate.git
```

### Validators

- **contains(str)** - check if the string contains another string(Case sensitive search).
- **containsDeepKey(obj)** - Safely reach into a 'nested' object and returns true if specified key is present.
- **containsIgnoreCase(str)** - check if the string contains another string(Case insensitive search).
- **containsKey(obj, key)** - Safely reach into a object and returns true if specified key is present. 
- **hasAnyMethod(obj)** - check if the object has any method present inside it.
- **isAlpha(str)** - check if the string contains only alphabets, both upper and lower case.
- **isAlphanumeric(str)** - check if the string contains alphabets and numbers.
- **isArray(value)** - check if the value passed is Array.
- **isAscii(value)** - check if the string contains only ascii characters.
- **isBase64(str)** - check if a string is base64 encoded.
- **isBlank(str)** - check if a string is blank.
- **isBoolean(str)** - check if the value is boolean value i.e. true, false, 1, or 0.
- **isEmpty(str)** - check if a string is empty. A string containing only whitespaces is blank string but not empty string.
- **isFalse(value)** - check if the value passed is false.
- **isFunction(value)** - check if the value is function or not.
- **isHexadecimal(str)** - Check if the string is a hexadecimal number.
- **isJSON(str)** - check if a string is a valid JSON string.
- **isLowerCase(str)** - check if a string is in lowercase.
- **isMACAddress(str)** - check if the string value is a valid MAC address.
- **isMD5(str)** - check if the string value is MD5 hash.
- **isMethodPresent(obj, methodName)** - check if the object has the specified method present inside it.
- **isNull(value)** - check if the value is null or undefined or Nan.
- **isNumber(value)** - check if the value passed is Number object.
- **isNumeric(str)** - check if a string is number(Integer/Floating point et al.).
- **isObject(value)** - check if the value passed is Object.
- **isPalindrome(str)** - check if input string is a palindrome or not.
- **isRegExp(value)** - check if the value is RegExp or not.
- **isStrictBoolean(value)** - check if the value is boolean object or not.
- **isStrictObject(value)** - check if the value is Object or not.
- **isString(value)** - check if the value passed is string.
- **isTitleCase(value)** - check is the string is title case i.e. first letter of each word in the string is capital case.
- **isTrue(value)** - check if the value passed is true.
- **isUpperCase(str)** - check if a string is in uppercase.
- **isURIEncoded(str)** - check if String is URI encoded.
- **isUUID(str)** - check if the specified string is uuid(of specified version).
- **isValidEmail(str)** - check if the string is a valid email address.
- **isWhiteSpace(str)** - check if a string contains only whitespaces.
- **objectEquals(obj1, obj2)** - check if two objects(String, Object, Number, Date, function, RegExp, Array) are equal or not.
- **startsWith(str, starts, position, strict)** - check if a string/number/array starts with another string/number/array.<br />
It accepts two optional parameters - position and strict. Client can specify the optional position value to tell where it will check for start.<br />
The optional parameters strict, which is set to false by default, indicates whether number values should be converted to string or not while comparing
- **endsWith(str, ends, position, strict)** - check if a string/number/array ends with another string/number/array.<br />
It accepts two optional parameters - position and strict. Client can specify the optional position value to tell where it will check for end.<br />
The optional parameters strict, which is set to false by default, indicates whether number values should be converted to string or not while comparing

### Examples

```javascript
var ratify = require('node-ratify');

// Check if the value is string or not
ratify.isString(new String('hello')); // returns true

// Check if the value is Number or not
ratify.isNumber(7); // returns true
ratify.isNumber(false); // returns false

// Check if the value is Array or not
ratify.isArray('7'); // returns false
ratify.isArray(['5', '7']); // returns true

// Check if the value is Object or not 
// (Value could be String object, Number Object, Array Object, Date object etc.)
ratify.isObject(new Array(7, 11)); // returns true
ratify.isObject(''); // returns false

// Check if the value is Object or not 
ratify.isStrictObject({}); // returns true
ratify.isStrictObject(new Array(7, 11)); // returns false

// Check if the value is RegExp or not
ratify.isRegExp('/abc/'); // returns false
ratify.isRegExp(/abc/); // returns true

// Check if the value is Boolean object or not
ratify.isStrictBoolean(false) // returns true

// Check if the value is Boolean or not
ratify.isBoolean() // returns false
ratify.isBoolean(1) // returns true
ratify.isBoolean(false) // returns true

// Check if the value is Function or not
function test() {return true;}
function test2() {};
var arr = ['Item1', 'Item2', 'Item3'];
var obj = {};

ratify.isFunction(test) // returns true
ratify.isFunction(test2) // returns true
ratify.isFunction(arr) // returns false
ratify.isFunction(obj) // returns false
ratify.isFunction(null) // returns false

// Check if the string is a lowercase string
ratify.isLowerCase('gaurav') // returns true
ratify.isLowerCase() // returns false

// Check if the string is a uppercase string
ratify.isUpperCase('GAURAV') // returns true
ratify.isUpperCase() // returns false

// Check is the string is title case 
// i.e. first letter of each word in the string is capital case
ratify.isTitleCase('hello World') // returns false
ratify.isTitleCase('HATs Off To YOU') // returns true

// Check if the string is a number
ratify.isNumeric('7') // returns true
ratify.isNumeric(-Infinity) // returns true

// Check if the string/object is valid JSON
var a = {a : 'a', b : 'b', c : 'c', d : 'd'};
var b = {a : 'a', b : 'b', c : { x : 'x', y : 'y', z : 
            { key1 : 'value1', key2 : 'value2'}}};
var c = {a : 'a', b : 'b', c : { x : 'x', y : 'y', z : 
            { key1 : 'value1', key2 : 'value2', }}};  // Extra comma

ratify.isJSON("\n{\"a\" : \"5\"}\n"); // returns true
ratify.isJSON(a); // returns true
ratify.isJSON(b); // returns true
ratify.isJSON(c); // returns true
ratify.isJSON('/abc/'); // returns false

// Check if the string is base64 encoded
ratify.isBase64('gaurav') // returns false
ratify.isBase64('Zm9vYg==') // returns true

// Check if the string contains only alphabets, both upper and lower case
ratify.isAlpha()  // returns false
ratify.isAlpha('asd')  // returns true
ratify.isAlpha('123')  // returns false

// Check if the string contains alphabets and numbers
ratify.isAlphanumeric('abc') // returns true
ratify.isAlphanumeric(new Object()) // returns false
ratify.isAlphanumeric('134766678') // returns true

// Check if the string is a hexadecimal number
ratify.isHexadecimal('1f') // returns true
ratify.isHexadecimal('0x1F') // returns false
ratify.isHexadecimal('efa0123') // returns true

// Check if the string contains only ascii characters
ratify.isAscii('ᴁᴪᴙݝۺ') // returns false
ratify.isAscii(undefined) // returns false

// Check if the value is null
ratify.isNull(false) // returns false
ratify.isNull(0/0) // returns true

// Check if the string is a valid email address
ratify.isValidEmail('luthra.zenith@google.com'); // returns true
ratify.isValidEmail('luthra.zenithgoogle.com'); // returns false

// Check if the specified string is uuid(of specified version)
ratify.isUUID('4925123f-85a1-46bd-bfef-14026fbd4800', 4); // returns true
ratify.isUUID('4956123f-89a1-36bd-cfef-14026fbd1270', 3); // returns true

// Check if String is URI encoded
ratify.isURIEncoded('gaurav'); // returns true

// Check if the string doesn't contain anything
ratify.isEmpty(null); // returns true
ratify.isEmpty(''); // returns true
ratify.isEmpty('    '); // returns false

// Check if the string contains only whitespaces
ratify.isWhiteSpace('    '); // returns true
ratify.isWhiteSpace(null); // returns false

// Check if the string is blank : i.e. 
// either it is empty or only contains whitespaces
ratify.isBlank(''); // returns true
ratify.isBlank('    '); // returns true

// Check if the string contains another string(Case sensitive search)
var baseStr = 'This is me and that is you';
var searchStr = 'this';

ratify.contains(baseStr, searchStr); // returns false
ratify.contains(baseStr, 'This'); // returns true

// Check if the string contains another string(Case insensitive search)
var baseStr = 'This is this and that is that';
var searchStr = 'this';

ratify.containsIgnoreCase(baseStr, searchStr); // returns true
ratify.containsIgnoreCase(baseStr, 'hello'); // returns false

// Safely search into a object and returns true if specified key is present. 
// Returns false if the intended target is not present.

var o = { qwe : { asd : { zxc : 123 } } };
ratify.containsKey(o, 'qwe'); // returns true
ratify.containsKey(o, 'zxc'); // returns false, as it is not present at top level

// Safely reach into a nested object and returns true if specified key is present. 
// Returns false if any of the intermediate subobjects or the intended target are not present.

var o = { qwe : { asd : { zxc : 123 } } };
ratify.containsDeepKey(o, 'qwe'); // returns true
ratify.containsDeepKey(o, 'zxc'); // returns true
ratify.containsDeepKey(o, 'qwe', 'asd'); // returns true

// Check if input string is a palindrome or not

var str1 = 'abcdefghijklmnopqrstuvwxyzzyxwvutsrqponmlkjihgfedcba';
var str2 = 'eye';
var str3 = 'Hello';

ratify.isPalindrome(str1); // returns true
ratify.isPalindrome(str2); // returns true
ratify.isPalindrome(str3); // returns false

// Check if two objects(String, Object, Number, Date, function, RegExp, Array)
// are equal

var o = { qwe : { asd : { zxc : 123 } } };
var m = { qwe : { asd : { zxc : 123 } } };

ratify.objectEquals(o, m); // returns true
ratify.objectEquals(new Number(5), 5); // returns true
ratify.objectEquals(['1', '2', '3'], ['3', '2', '1']); // returns false

// Check if the object has any method present inside it

var o = { qwe : { asd : { zxc : 123 } } };
var m = { qwe : 123, dummy : function() {console.log('Hello')} };

ratify.hasAnyMethod(o); // returns false
ratify.hasAnyMethod(m); // returns true

// Check if the object has the specified method present inside it

var o = { qwe : { asd : { zxc : 123 } } };
var m = { qwe : 123, dummy : function() {console.log('Hello')} };

ratify.isMethodPresent(o); // returns false
ratify.isMethodPresent(null); // returns false
ratify.isMethodPresent(m); // returns false
ratify.isMethodPresent(m, 'dummy'); // returns true

//
// Check if a string/number/array starts with another string/number/array at specified position.
// Returns boolean true or false
// Setting strict to true will not convert number to string while comparing
//
ratify.startsWith('Blue Whale, Killer Whale', 'Blue');          // returns true
ratify.startsWith('Blue Whale, Killer Whale', 'Blue', 10);      // returns false
ratify.startsWith('Brave new world', 'world');                  // returns false
ratify.startsWith('Brave new world', 'world', 10);              // returns true
ratify.startsWith('123456', '234', 1);                          // returns true
ratify.startsWith([1, 2, 3, 4], [1, 2, 3]);                     // returns true
ratify.startsWith([1, 2, 3, 4], 1);                             // returns true
ratify.startsWith([1, 2, 3, 4], '1', true);                     // returns false as strict mode = true


//
// Check if a string/number/array ends with another string/number/array at specified position.
// Returns boolean true or false
// Setting strict to true will not convert number to string while comparing
//
ratify.endsWith('Blue Whale, Killer Whale', 'Whale');             // returns true
ratify.endsWith('Blue Whale, Killer Whale', 'Killer Whale', 10);  // returns false
ratify.endsWith('Blue Whale, Killer Whale', 'Killer Whale', 12);  // returns true
ratify.endsWith('Brave new world', 'world');                      // returns true
ratify.endsWith('Brave new world', 'world', 11);                  // returns false
ratify.endsWith('123456', '23456', 1);                            // returns true
ratify.endsWith('123456', '2345', 1);                             // returns false
ratify.endsWith([1, 2, 3, 4], [2, 3, 4]);                         // returns true
ratify.endsWith([1, 2, 3, 4], 4);                                 // returns true
ratify.endsWith([1, 2, 3, 4], '4', true);                         // returns false as strict mode = true

//
// Check if the specified string is md5 hash or not
//
ratify.isMD5('');                                   // returns false
ratify.isMD5(null);                                 // returns false
ratify.isMD5('e4d909c290d0fb1ca068ffaddf22cbd0');   // returns true
ratify.isMD5('9e107d9d372bb6826bd81d3542a419d6');   // returns true
ratify.isMD5('hello world');                        // returns false

//
// Check if the specified string is valid MAC address or not
//
ratify.isMACAddress('');                    // returns false
ratify.isMACAddress(null);                  // returns false
ratify.isMACAddress('78:0C:B8:D8:ED:74');   // returns true
ratify.isMACAddress('78-0C-B8-D8-ED-74');   // returns true
ratify.isMACAddress('78:0K:B8:M8:DF:74');   // returns false

//
// Check if the specified string is valid hexadecimal color value or not
//
ratify.isHexaColor('');                 // returns false
ratify.isHexaColor(null);               // returns false
ratify.isHexaColor('#ffe4e1');          // returns true
ratify.isHexaColor('#ff4545');          // returns true
ratify.isHexaColor('#800080');          // returns true
ratify.isHexaColor('800080');           // returns true
ratify.isHexaColor('#8K0K8K');          // returns false
ratify.isHexaColor('#helloworld');      // returns false

//
// Check if the specified object is set or not
//
ratify.isSet('');                 // returns false
ratify.isSet(null);               // returns false
ratify.isSet(new Set());          // returns true
ratify.isSet(new Set(1, 2, 3));   // returns true
ratify.isSet(new WeakSet);        // returns false
ratify.isSet(new Set[1, 2, 3]);   // returns true

//
// Check if the specified object is weakset or not
//
ratify.isWeakSet('');               // returns false
ratify.isWeakSet(null);             // returns false
ratify.isWeakSet(new WeakSet());    // returns true
ratify.isWeakSet(new Set);          // returns false
ratify.isWeakSet(new WeakSet[{}]);  // returns true

//
// Check if passed value is undefined or not
//
ratify.isUndefined(undefined);      // returns true
ratify.isUndefined(null);           // returns false
ratify.isUndefined(void 0);         // returns true
ratify.isUndefined(new Object);     // returns false

```

### License(MIT)

```
Copyright (c) 2017 Gaurav Luthra(luthra.zenith@gmail.com)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

[npm-url]: https://www.npmjs.com/package/node-ratify
[npm-image]: https://img.shields.io/npm/v/node-ratify.svg

[npm]: https://www.npmjs.com/
[bower]: http://bower.io/

[travis-url]: https://travis-ci.org/luthraG/node-validate
[travis-image]: http://img.shields.io/travis/luthraG/node-validate.svg