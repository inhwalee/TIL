# Functional-Programming

## π ν¨μν νλ‘κ·Έλλ°μ΄λ?

{% hint style="info" %}
&#x20;μλ°μ€ν¬λ¦½νΈλ ν¨μν νλ‘κ·Έλλ° μΈμ΄λ μλμ§λ§ ν¨μλ₯Ό κ°μ²΄μ²λΌ μ‘°μν  μ μμΌλ―λ‘ ν¨μν νλ‘κ·Έλλ° κΈ°λ²μ μ¬μ©ν  μ μλ€.&#x20;
{% endhint %}

## π ν¨μλ‘ λ°°μ΄μ²λ¦¬

{% hint style="info" %}
&#x20;mapκ³Ό reduce κ°μ λ°°μ΄ λ©μλλ νΉν ν¨μν νλ‘κ·Έν΄λ° μ€νμΌμ μλ§λ€.
{% endhint %}

```
// νκ· κ³Ό νμ€ νΈμ°¨ κ΅¬ν
let data [1, 1, 3, 5, 5];

// νκ· μ μμμ ν©μ μμ κ°μλ‘ λλ κ°μ΄λ€.
let total = 0;
for(let i = 0; i < data.length; i+=) total == data[i];
let mean = total/data.length; // 3

// νμ€ νΈμ°¨λ κ° μμμ νκ·  κ° νΈμ°¨μ μ κ³±μ λͺ¨λ ν©ν κ°μ΄λ€.
total = 0;
for(let i = 0; i < data.length; i++) {
  let deviation = data[i] - mean;
  total += deviation * deviation;
}
let stddev = Math.sqrt(total/(data.length-1)); // 2
```

```
// ν¨μν νλ‘κ·Έλλ° μ
const map = function(a, ..args) {return a.map(...args);}
const reduce = function(a. ...args) {return a.reduce(...args);}
const sum = (x, y) => x + y;
const square = x => x * x;

let data [1, 1, 3, 5, 5];
let mean = reduce(data, sum)/data.length;
let deviations = map(data, x =< x - mean);
let stddev = Math.sqrt(reduce(map(deviations, square), sum)/(data.length - 1));
stddev; // 2
```

## π κ³ κ³ ν¨μ

{% hint style="info" %}
&#x20;κ³ κ³ ν¨μλ νλ μ΄μμ ν¨μλ₯Ό μΈμλ‘ λ°μ μ ν¨μλ₯Ό λ°ννλ ν¨μλ₯Ό λ§νλ€.&#x20;
{% endhint %}

```
function not(f) {
  return function(...args) {
    let result = f.apply(this, args);
    return !result;
  }
}
const even = x => x % 2 === 0;
const odd = not(even);
[1, 1, 3, 5, 5].every(odd); // true
```

```
const compose(f, g) {
  return runction(...args) {
    return f.call(this, g.apply(this, args));
  }
}

const sum = (x, y) => x + y;
const square = x => x * x;
compose(square, sum)(2, 3) // 25
```

## π ν¨μμ λΆλΆ μ μ©

{% hint style="info" %}
&#x20;bind() λ©μλλ μΌμͺ½μ μλ μΈμλ₯΄ λΆλΆμ μΌλ‘ μ μ©νλ€. bind()μ μ λ¬νλ μΈμλ μλ ν¨μμ μ λ¬λλ μΈμ λ¦¬μ€νΈμ μμ λΆλΆμ μμΉνλ€. λ°λλ‘ μ€λ₯Έμͺ½μ μλ μΈμλ₯Ό λΆλΆμ μΌλ‘ μ μ©νλ κ²λ κ°λ₯νλ€.&#x20;
{% endhint %}

```
// μ΄ ν¨μμ μΈμλ μΌμͺ½μ μ λ¬λλ€.
function partialLeft(f, ...outerArgs) {
  return function(...innerArgs) {
    let args = [...outerArgs, ...innerArgs];
    return f.apply(this, args);
  }
}
```

```
// μ΄ ν¨μμ μΈμλ μ€λ₯Έμͺ½μ μ λ¬λλ€.
function partialRight(f, ...outerArgs) {
  return function(...innerArgs) {
    let args = [...innerArgs, ...outerArgs];
    return f.apply(this, args);
  }
}
```

```
const f = function(x, y, z) {return x * (y - z);}
partialLeft(f, 2)(3, 4);        // -2
partialRight(f, 2)(3, 4);       // 6
partial(f, undefined, 2)(3, 4); // -6
```

{% hint style="info" %}
λΆλΆν¨μλ₯Ό μ¬μ©νλ©΄ μ΄λ―Έ μ μν ν¨μλ₯Ό νμ©ν΄μ λ ν₯λ―Έλ‘μ΄ ν¨μλ₯Ό μ½κ² μ μν  μμλ€.
{% endhint %}

```
// Some code
```

## π λ©λͺ¨μ΄μ μ΄μ

{% hint style="info" %}
μ΄μ μ κ³μ°ν κ²°κ³Όλ₯Ό μΊμνλ κ²μ ν¨μν νλ‘κ·Έλλ°μμλ λ©λͺ¨μ΄μ μ΄μμ΄λΌκ³  λΆλ₯Έλ€.
{% endhint %}

```
// fλ₯Ό μΊμλ₯Ό νμ©νλλ‘ μμ ν΄ λ°ννλ€.
// fμ μΈμκ° λͺ¨λ κ³ μ ν λ¬Έμμ΄ ννμΌ λλ§ λμνλ€.
function memoize(f) {
  const cache = new Map(); // κ° μΊμλ ν΄λ‘μ μ μ μ₯λλ€.
  return function(...args) {
    let key = args.length + args.join('+'); // μΈμλ₯Ό μΊμ ν€λ‘ μ¬μ©ν  λ¬Έμμ΄λ‘ λ³ν
    if(cache.has(key)) {
      return cache.get(key);
    }else {
      let result = f.apply(this, args);
      cache.set(key, result);
      return result;
    }
  }
  
}
```

memoize ν¨μλ μΊμλ‘ μ¬μ©ν  μ κ°μ²΄λ₯Ό μμ±νκ³  μ΄ κ°μ²΄λ₯Ό λ‘μ»¬ λ³μμ ν λΉνλ―λ‘, λ°νλ ν¨μ μΈμλ μ΄ κ°μ²΄λ₯Ό λ³Ό μ μλ€. λ°νλ ν¨μλ μΈμ λ°°μ΄μ λ¬Έμμ΄λ‘ λ³ννκ³  κ·Έ λ¬Έμμ΄μ μΊμ κ°μ²΄μ νλ‘νΌν° μ΄λ¦μΌλ‘ μ¬μ©νλ€. κ°μ΄ μΊμμ μ‘΄μ¬νλ©΄ λ°λ‘ λ°ννκ³ , κ·Έλ μ§ μλ€λ©΄ μΈμλ₯Ό λκΈ°λ©΄μ μ§μ λ ν¨μλ₯Ό νΈμΆν΄ κ°μ κ³μ°νλ μΊμμ μ μ₯ν λ€μ λ°ννλ€.

```
function gcd(a, b) {
  if(a < b) {          // aλ bλ³΄λ€ ν¬κ±°λ κ°μμΌ νλ€.
    [a, b] = [b, a];   // κ·Έλ μ§ μμΌλ©΄ λΆν΄ ν λΉμ ν΅ν΄ λ³μλ₯Ό μ€μνλ€.
  }
  while(b !== 0) {     // μ΅λ κ³΅μ½μλ₯Ό κ΅¬νλ μ ν΄λ¦¬λ μκ³ λ¦¬
    [a, b] = [b, a%b];
  }
  return a;
}

const gcdmemo = memoize(gcd);
gcdmemo(85, 187); // 17
```
