# Subclasses

## ๐ ์๋ธ ํด๋์ค

{% hint style="info" %}
๋ค๋ฅธ ํด๋์ค๋ฅผ ์์๋ฐ๋ ์๋ธํด๋์ค๋ฅผ ์ ์ํ  ๋๋ class ํค์๋์ ํจ๊ป extends ํค์๋๋ฅผ ์ฌ์ฉํ๋ค.
{% endhint %}

## ๐ ES6 ์ด์  ์๋ธํด๋์ค

{% hint style="info" %}
๋ค์๊ณผ ๊ฐ์ด Object.create()๋ฅผ ํตํด ์ง์  ์์๋ฐ๊ณ  ์ผ๋ถ๋ฅผ ๋ฎ์ด์ฐ๋ ์ฐ๋ ๋ฐฉ์์ผ๋ก ํ์ฅํ  ์ ์๋ค. ํ์ง๋ง ์ํผํด๋์ค๊ฐ ์ด๋ป๊ฒ ๋ง๋ค์ด์ก๋์ง ์์ธํ ์๊ณ  ์์ด์ผ ์๋ธํด๋์ค ๋ฉ์ปค๋์ฆ์ ๋นํ์์ด ๋ง๋ค ์ ์๋ค๋ ๋ฒ๊ฑฐ๋ก์์ด ์๋ค.
{% endhint %}

```
function Span(start, span) {
  if(span >= 0) {
    this.from = start;
    this.to = start + span;
  } else {
    this.to = start;
    this.from = start + span
  }
}

// Span ๊ฐ์ฒด Span.prototype๊ณผ Range.prototype์ ๋ชจ๋ ์์๋ฐ๋๋ค.
Span.prototype = Object.create(Range.prototype); 
Span.prototype.constructor = Span;
Span.prototype.toString = function() {
  return `(${this.from}~${thi.to = this.from})`
}
```



## ๐ ES6 ์ดํ ์๋ธํด๋์ค

{% hint style="info" %}
ES6์์๋ class ๋ฌธ๋ฒ์ super ํค์๋๋ฅผ ๋์ํด ํ์ฅ์ ๋จ์ํ๊ฒ ์ฒ๋ฆฌํ  ์ ์๋๋ก ํ์๋ค.ES6 ์ดํ์๋ ํด๋์ค ์ ์ธ์ extends ๋ฅผ ์ถ๊ฐํ๊ธฐ๋ง ํด๋ ์๋ธํด๋์ค๋ฅผ ๋ง๋ค ์ ์์ผ๋ฉฐ ๋ด์ฅ ํด๋์ค์๋ ์ด๋ฐ ๋์์ด ํ์ฉ๋๋ค.
{% endhint %}

```
// ํค์ ๊ฐ ํ์์ ์ฒดํฌํ๋ ๋งต์ ์๋ธํด๋
class TypeMap extends Map {
  cosntructor(keyType, valueType, entries) {
    if(entries) {
      for(let [k, v] of entries) {
        if(typeof k !== keyType || typeof v !== valueType) {
          throw new Error(`Wrong type form entry [${k}, ${v}]`);
        }
      }
    }
    super(entries);             // ํ์์ ์ฒดํฌํ entries๋ก ์ํผํด๋์ค ์ด๊ธฐํ
    this.#keyType = keyType;     // ํ์ ์ ์ฅํ๋ฉด์ ์๋ธํด๋์ค ์ด๊ธฐํ
    this.#valueType = valueType; // ํ์ ์ ์ฅํ๋ฉด์ ์๋ธํด๋์ค ์ด๊ธฐํ
  }
 
  set(key, value) {             // ์ถ๊ฐ๋๋ ์ ํญ๋ชฉ๋ง๋ค ํ์ ์ฒดํฌํ๋๋ก ์ฌ์ 
    if(this.#keyType && typeof key !== this.#keyType) {
      throw new TypeError(`${key} is not of type ${this.#keyType}`);
    }
    if(this.#valueType && typeof value !== this.#valueType) {
      throw new TypeError(`${value} is not of type ${this.#valueType}`);
    }
    return super.set(key, value); // ํ์์ด ์ผ์นํ๋ฉด ์ํผํด๋์ค์ set() ์ค
  }
  
}
```

## ๐ super() ์ฌ์ฉ ๊ท์น

* extends ํค์๋๋ก ํด๋์ค๋ฅผ ์ ์ํ๋ฉด ํด๋์ค ์์ฑ์๋ ์ํผํด๋์ค ์์ฑ์๋ฅผ ํธ์ถํ  ๋ ๋ฐ๋์ super()์ ์ฌ์ฉํด์ผ ํ๋ค.
* ์๋ธํด๋์ค์ ์์ฑ์๋ฅผ ์ ์ํ์ง ์์ผ๋ฉด ์๋์ผ๋ก ์์ฑ๋๋ฉฐ, ๋ฌต์์ ์ผ๋ก ์ ์๋ ์์ฑ์๋ ์ ๋ฌ๋ ๊ฐ์ ๊ทธ๋๋ก super()์ ์ ๋ฌํ๋ค.
* super()์ ์จ์ ์ํผํด๋์ค ์์ฑ์๋ฅผ ํธ์ถํ๊ธฐ ์ ์๋ ์์ฑ์ ์์์ this ํค์๋๋ฅผ ์ฌ์ฉํ์ง ๋ง์์ผ ํ๋ค.&#x20;
* new ํค์๋ ์์ด ํธ์ถํ ํจ์์์๋ ํํ์ new.target์ ๊ฐ์ด undefined์ด๋ค. ๋ฐ๋ฉด ์์ฑ์ ํจ์์์ new.target์ ํธ์ถ๋ ์์ฑ์๋ฅผ ์ฐธ์กฐํ๋ค. ์๋ธํด๋์ค ์์ฑ์๋ฅผ ํธ์ถํ๊ณ  super()๋ก ์ํผํด๋์ค ์์ฑ์๋ฅผ ํธ์ถํ๋ฉด ์ํผํด๋์ค ์์ฑ์๋ new.target()์ ํตํด ์๋ธํด๋์ค ์์ฑ์๋ฅผ ์ฐธ์กฐํ  ์ ์๋ค.

## ๐ ์์ ๋์  ์

{% hint style="info" %}
๋ค๋ฅธ ํด๋์ค์ ๋์์ ๊ณต์ ํ๋ ํด๋์ค๋ฅผ ์ํ๋ค๋ฉด ์๋ธํด๋์ค๋ฅผ ๋ง๋ค์ด ๋์์ ์์๋ฐ์ ์๋ ์์ง๋ง, ํด๋์ค์์ ๋ค๋ฅธ ํด๋์ค์ ์ธ์คํด์ค๋ฅผ ๋ง๋ค๊ณ  ๊ทธ ์ธ์คํด์ค์ ์ํ๋ ๋์์ ์์ํ๋ ๊ฒ์ด ๋ ์ฝ๊ณ  ์ ์ฐํ ๋ฐฉ๋ฒ์ผ ๋๋ ์๋ค. ์ด ๋ ๋ค๋ฅธ ํด๋์ค์ ๋ํผ๋ฅผ ๋ง๋ค๊ฑฐ๋ ํฉ์ฑ์ ํตํด์๋ ์ ํด๋์ค๋ฅผ ๋ง๋ค ์ ์์ผ๋ฉฐ, ๋์์ ์์ํ๋ ๋ฐฉ์์ ํฉ์ฑ์ด๋ผ๊ณ  ๋ถ๋ฅธ๋ค. ๊ฐ์ฒด ์งํฅ ํ๋ก๊ทธ๋๋ฐ์์๋ '์์๋ณด๋ค ํฉ์ฑ์ ์ฐ์ ํ๋ผ' ๋ผ๋ ๊ฒฉ์ธ์ด ์์ฃผ ์ธ์ฉ๋๋ค.
{% endhint %}

```
// ์ธํธ์ ๋น์ทํ์ง๋ง ๊ฐ ๊ฐ์ด ๋ช๋ฒ ์ถ๊ฐ๋์๋์ง ์ถ์ ํ๋ ๊ธฐ๋ฅ์ด ์ถ๊ฐ๋ ํด๋์ค
class Histogram {
  constructor() {this.map = new Map();}
  
  count(key) {return this.map.get(key) || 0;}
  has(key) {return this.count(key) > 0;}
  get size() {return this.map.size;}
  add(key) {this.map.set(key, this.count(key) + 1);}
  delete(key) {
    let count = this.count(key);
    if(count === 1) {
      this.map.delete(key);
    } else if(count > 1) {
      this.map.set(key, count -1);
    }
  }
  [Symbol.iterator]() {return this.map.keys();}
  key() {return this.map.keys();}
  value() {return this.map.values();}
  entries() {return this.map.entries();}
}
```
