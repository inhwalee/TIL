# Like-Arrays

## ๐ ํน๋ณํ ๊ฐ์ฒด์ธ ๋ฐฐ์ด

{% hint style="info" %}
์๋ฐ์คํฌ๋ฆฝํธ ๋ฐฐ์ด์๋ ๋ค์๊ณผ ๊ฐ์ด ๋ค๋ฅธ ๊ฐ์ฒด์๋ ์๋ ํน๋ณํ ๊ธฐ๋ฅ์ด ์์ผ๋ฉฐ, ์ด๋ค์ ์๋ฐ์คํฌ๋ฆฝํธ ๋ฐฐ์ด์ ์ผ๋ฐ์ ์ธ ๊ฐ์ฒด์ ๊ตฌ๋ถํ๋ ํน์ง์ด๋ค.
{% endhint %}

* ๋ฐฐ์ด์ ์ ์์๋ฅผ ์ถ๊ฐํ  ๋๋ง๋ค length ํ๋กํผํฐ๊ฐ ์๋์ผ๋ก ์๋ฐ์ดํธ ๋๋ค.
* length๋ฅผ ๋ ์์ ๊ฐ์ผ๋ก ๋ณ๊ฒฝํ๋ฉด ๋ฐฐ์ด ์์๋ฅผ ๊ทธ์ ๋ง๊ฒ ๋ฒ๋ฆฐ๋ค.
* ๋ฐฐ์ด์ Array.prototype์์ ์ ์ฉํ ๋ฉ์๋๋ค์ ์์๋ฐ๋๋ค.
* Array.isArray()๋ ๋ฐฐ์ด์ ๋ฐ์ผ๋ฉด true๋ฅผ ๋ฐํํ๋ค.

## ๐ ๋ฐฐ์ด ๋น์ทํ ๊ฐ์ฒด

{% hint style="info" %}
ํ์ง๋ง ์ด๋ค์ด ๋ฐฐ์ด์ ์ ์ํ๋ ํต์ฌ ํน์ง์ ์๋๋ฉฐ, **์ซ์๊ฐ ๊ฐ์ธ length ํ๋กํผํฐ๊ฐ ์๊ณ  ์์ด ์๋ ์ ์ ํ๋กํผํฐ๊ฐ ์๋ ๊ฐ์ฒด๋ผ๋ฉด ๋ชจ๋ ์ผ์ข์ ๋ฐฐ์ด๋ก ๊ฐ์ฃผํ**๋๋ผ๋ ์ ํ ๋ฌธ์ ๊ฐ ์๋ค. ์ด๋ฅผ '๋ฐฐ์ด ๋น์ทํ ๊ฐ์ฒด'๋ผ๊ณ  ๋ถ๋ฅด๋ฉฐ, ๋น๋ก ๋ฐฐ์ด ๋ฉ์๋๋ฅผ ์ง์ ์ ์ผ๋ก ํธ์ถํ๊ฑฐ๋ length ํ๋กํผํฐ๊ฐ ํน๋ณํ๊ฒ ๋์ํ์ง ์์ง๋ง ์ค์  ๋ฐฐ์ด์ ์ ์ฉํ๋ ์๊ณ ๋ฆฌ์ฆ์ ๋ฐฐ์ด ๋น์ทํ ๊ฐ์ฒด์๋ ์ ์ฉํ  ์ ์๋ค.&#x20;

ํนํ ์๊ณ ๋ฆฌ์ฆ์ด ๋ฐฐ์ด์ ์ฝ๊ธฐ ์ ์ฉ์ธ ๊ฒ ์ฒ๋ผ ๋ค๋ฃจ๊ฑฐ๋, ์ต์ํ ๋ฐฐ์ด ๊ธธ์ด๋ ๊ฑด๋๋ฆฌ์ง ์๋๋ค๋ฉด ๋์ฑ ๋ฐฐ์ด๊ณผ์ ์ฐจ์ด๊ฐ ์๋ ๊ฒ ์ฒ๋ผ ๋ณด์ผ ์ ์์ผ๋ฉฐ ์๋ฐ์คํฌ๋ฆฝํธ ๋ฐฐ์ด ๋ฉ์๋๋ ๋๋ถ๋ถ ๋ฐฐ์ด ๋น์ทํ ๊ฐ์ฒด์์๋ ์ ํํ ๋์ํ  ์ ์๋๋ก ๋ฒ์ฉ์ผ๋ก ์ค๊ณ๋์๋ค.
{% endhint %}

```
let likeArray = {};
let i = 0;
while(i < 10) {
 likeArray[i] = i * i;
 i++;
}
a.length = i;

// ์์์ ๋ง๋  ๊ฐ์ฒด๋ ์ค์  ๋ฐฐ์ด์ธ ๊ฒ ์ฒ๋ผ ์ํํ๋ค.
let total = 0;
for(let j = 0; j < likeArray.length; j++) {
  total += likeArray[j];
}
```

{% hint style="info" %}
์ค์  ํด๋ผ์ด์ธํธ ์ฌ์ด๋ ์๋ฐ์คํฌ๋ฆฝํธ์๋ document.querySelectorAll() ์ฒ๋ผ HTML ๋ฌธ์์์ ๋ฐฐ์ด ๋น์ทํ ๊ฐ์ฒด๋ฅผ ๋ฐํํ๋ ๋ฉ์๋๊ฐ ๋ง์ด ์๋๋ฐ, ๋ค์ ํจ์๋ฅผ ํตํด ํด๋น ๊ฐ์ฒด๋ฅผ ๋ฐฐ์ด์ฒ๋ผ ์ธ ์ ์๋์ง ์ฒดํฌํ  ์ ์๋ค.
{% endhint %}

```
function isArrayLike(obj) {
  if(obj &&                         // obj๊ฐ null, undefined ๋ฑ์ด ์๋๊ณ  
    typeof obj === 'object' &&      // ๊ฐ์ฒด์ด๋ฉฐ
    Number.isFinite(obj.length) &&  // o.length๊ฐ ์ ํํ ์ซ์์ด๊ณ 
    obj.length >= 0 &&              // ์์ด ์๋๋ฉฐ,
    Number.isInteger(obj.length) && // ์ ์์ด๊ณ  
    obj.length < 4294967295) {      // 2์ 32์น -1 ๋ฏธ๋ง์ด๋ฉด
    return true;                    // obj๋ ๋ฐฐ์ด ๋น์ทํ ๊ฐ์ฒด์ด๋ค.
  } else {
    return false;
  }
}

isArrayLike({0: 'zero' 'length': 1}); // true
isArrayLike('hello world');           // false: ๋ฌธ์์ด์ ๋ฐ์ผ๋ฉด false๋ฅผ ๋ฐํํ๋ค.  
```

{% hint style="info" %}
&#x20;๋ฐฐ์ด ๋น์ทํ ๊ฐ์ฒด์๋ Array.prototype์ ์์๋ฐ์ง ์์ผ๋ฏ๋ก ๋ฐฐ์ด ๋ฉ์๋๋ฅผ ์ง์  ํธ์ถํ  ์๋ ์๋ค. ํ์ง๋ง Function.call ๋ฉ์๋๋ฅผ ํตํด ๊ฐ์ ์ ์ผ๋ก ํธ์ถํ  ์๋ ์๋ค.
{% endhint %}

```
let a = {
  0: 'zero',
  1: 'one',
  2: 'two',
  length: 3,
}

Array.prototype.join.call(a, '+');                 // zero + one + two
Array.prototype.map.call(a, x => x.toUpperCase()); // ['ZERO', 'ONE', 'TWO']
Array.prototype.slice.call(a, 0); // ['zero', 'one', 'two']: ์ ํํ ๋ฐฐ์ด ๋ณต์ฌ
Array.from(a);                    // ['zero', 'one', 'two']: ๋ ์ฌ์ด ๋ณต์ฌ
```

## ๐ ๋ฐฐ์ด์ธ ๋ฌธ์์ด

{% hint style="info" %}
&#x20;์๋ฐ์คํฌ๋ฆฝํธ **๋ฌธ์์ด์ UTF-16 ์ ๋์ฝ๋ ๋ฌธ์๋ก ๊ตฌ์ฑ๋ ์ฝ๊ธฐ ์ ์ฉ ๋ฐฐ์ด์ฒ๋ผ ๋์**ํ๋ค. ๋๋ฌธ์ charAt() ๋ฉ์๋ ๋์  ๋๊ดํธ๋ฅผ ์์ ๊ฐ๋ณ ๋ฌธ์์ ์ ๊ทผํ  ์ ์๋ค. ๋ค๋ง typeof ์ฐ์ฐ์๋ ๋ฌธ์์ด์ ๋ํด 'string'์ ๋ฐํํ๋ฉฐ Array.isArray() ๋ฉ์๋๋ ๋ฌธ์์ด์ ๋ฐ์ผ๋ฉด false๋ฅผ ๋ฐํํ๋ค.
{% endhint %}

```
const string = 'hello world';
string.charAt(0); // 'h'
string[0];        // 'h'
```

{% hint style="info" %}
&#x20;๋ฌธ์์ด์ด ๋ฐฐ์ด์ฒ๋ผ ๋์ํ๋ค๋ ๊ฒ์ ๋ฒ์ฉ ๋ฐฐ์ด ๋ฉ์๋๋ ์ ์ฉํ  ์ ์๋ค๋ ๋ป์ด๋ค. ํ์ง๋ง ๋ฌธ์์ด์ ๋ถ๋ณ์ธ ๊ฐ์ด๋ฏ๋ก ๋ฐฐ์ด์ฒ๋ผ ์ทจ๊ธํ๋ค ํด๋ ์ฝ๊ธฐ ์ ์ฉ์ด๋ผ๋ ์ ์ ๋ช์ฌํด์ผ ํ๋ค.

push(), sort(), reverse(), splice() ์ฒ๋ผ ์๋ ๋ฐฐ์ด์ ์ ํ๋ ๋ฐฐ์ด ๋ฉ์๋๋ ๋ฌธ์์ด์์ ๋์ํ์ง ์์ผ๋ฉฐ, ์๋ฌ ์์ด ์กฐ์ฉํ ์คํจํ๋ค.
{% endhint %}

```
Array.prototype.join.call('์๋ํ์ธ์', '.'); // '์.๋.ํ.์ธ.์.'
```
