# Immutable-Primitive-Values

## π κΈ°λ³Έ νμ (λΆλ³)

{% hint style="info" %}
**μ«μ, λ¬Έμμ΄, λΆ, μ¬λ²(ES6), null, undefined** λ§μ΄ κΈ°λ³Έ νμμ΄λ€.

κΈ°λ³Έ νμμ κ° μμ²΄κ° λ©λͺ¨λ¦¬μ μ μ₯λλ©°, μλ ₯ν κ°μ΄ μ΄λ―Έ λ©λͺ¨λ¦¬μ μμΌλ©΄ μλ‘­κ² λ©λͺ¨λ¦¬λ₯Ό λ§λ€μ§ μκ³  ν΄λΉ λ©λͺ¨λ¦¬ μ£Όμλ§ μ§μ ν΄μ€λ€. λν κΈ°λ³Έ νμμ λΆλ³μ΄λ―λ‘ κ°μ λ°κΏ μ μλ€. (μλ‘ μ«μ 2λ₯Ό 3μΌλ‘ λ°κΎΈλ κ² λΆκ°λ₯ν κ²κ³Ό κ°λ€.) λ©μλ λν κ°μ μμ νλ κ²μ΄ μλ μ λ¬Έμμ΄μ λ°ννλ€. λ¬Έμμ κ²½μ° λ°°μ΄λ‘ μκ°νμ¬ λ°κΏ μ μλ€κ³  μ°©κ°ν  μ μλλ°, μλ°μ€ν¬λ¦½νΈμμ λ¬Έμμ΄μ μ½κΈ° μ μ© λ°°μ΄μ΄λ―λ‘ μΈλ±μ€λ₯Ό ν΅ν΄ λ¬Έμμ΄μ νΉμ  νμ€νΈμ μ κ·Όν  μλ μμ§λ§ κΈ°μ‘΄ λ¬Έμμ΄μ λ°κΏ μλ μλ€.&#x20;
{% endhint %}

## π μ«μ Number

{% hint style="info" %}
μλ°μ€ν¬λ¦½νΈλ IEEE 754 νμ€μμ μ μνλ 64λΉνΈ λΆλ μμμ  νμμ μ¬μ©ν΄ μ«μλ₯Ό νννλ€.&#x20;
{% endhint %}

> **μ μ λ¦¬ν°λ΄**
>
> μλ°μ€ν¬λ¦½νΈλ 10μ§ μ μ λ¦¬ν°λ΄ λΏ μλλΌ, 2μ§μ(0b), 8μ§μ(0o), 16μ§μ(0x) λ¦¬ν°λ΄λ μ§μνλ€.

```
0b10101  // 21: 2μ§μ 
0o377    // 255 8μ§μ
0xff     // 255: 16μ§μ
```

> **λΆλ μμμ  λ¦¬ν°λ΄**
>
> λΆλ μμμ  λ¦¬ν°λ΄μλ μμμ μ΄ ν¬ν¨λ  μ μμΌλ©°, μ§μ νκΈ°λ²μΌλ‘λ ννν  μ μλ€.

```
3.14
.333333
6.02e25
1.4E-32
```

> **μ«μ λ¦¬ν°λ΄μ κ΅¬λΆμ**
>
> λ€μκ³Ό κ°μ΄ μ«μ μ¬μ΄μ λ°μ€μ λ£μ΄ μ½κΈ° μ½κ² κ΅¬λΆν  μ μλ€.

```
const billion = 1_000_000_000  // μ² λ¨μ κ΅¬λΆμ
const bytes = 0x89_AB_CD_EF    // λ°μ΄νΈ κ΅¬λΆμ
const bits = 0b0001_1101_0111  // 4λΉνΈ κ΅¬λΆ
```

> **μλ°μ€ν¬λ¦½νΈμ μ°μ  μ°μ°**
>
> μλ°μ€ν¬λ¦½νΈλ μ°μ  μ°μ°μλ₯Ό ν΅ν΄ μ«μλ₯Ό μ‘°μνλ€. λνκΈ°, λΉΌκΈ°, λλκΈ°, λλ¨Έμ§, μ§μμ κ°μ κΈ°λ³Έ μ°μ  μ°μ°μ μΈμλ Math κ°μ²΄μ λ©μλλ₯Ό ν΅ν΄ λ³΅μ‘ν μν κ³μ°μ μ½κ² μ μ©ν  μ μλ€.

```
1/0                    // Infinity
Number.MAX_VALUE * 2   // Infinity
-1/0                   // -Infinity
-Number.MAX_VALUE * 2  // -Infinity
0/0                    // NaN
Infinity/Infinity      // NaN
Number.Min_VALUE       // 0
-1/Infinity            // -0
```

{% hint style="info" %}
NaNλ μκΈ° μμ μ ν¬ν¨ν΄ μ΄λ€ κ°κ³Όλ κ°μ§ μλ€. μ¦, λ³μ xμ κ°μ΄ NaNμΈμ§ μμλ³΄κΈ° μν΄ x === NaNλ₯Ό μ¬μ©ν  μ μλ€. x != x λλ Number.isNaN(x)λ₯Ό μ¬μ©ν΄μΌ νλ€.
{% endhint %}

> **μ΄μ§ λΆλ μμμ  μ«μμ λ°μ¬λ¦Ό μ€λ₯**
>
> μλ°μ€ν¬λ¦½νΈλ₯Ό λΉλ‘―ν΄ μ΅μ  νλ‘κ·Έλλ° μΈμ΄μμ μ¬μ©νλ IEEE 754 λΆλ μμμ  ννμ μ΄μ§ ννμ΄λ―λ‘ 1/2, 1/8, 1/1024κ°μ λΆμλ μ νν ννν  μ μμ§λ§ 0.1 κ°μ λ¨μν μ«μλ μ ννκ² νννμ§ λͺ»νλ λ¬Έμ κ° μλ€. κ·ΌμΏκ°μ΄ μμκ³Ό λ¬λΌ νλ‘κ·Έλ¨μ λ¬Έμ κ° μκΈ΄λ€λ©΄ μ μλ‘ λ³ννμ¬ ν΄κ²°ν  μ μλ€.

```
const x = 0.3-0.2  // 0.09999999999999998
const y = 0.2-0.1  // 0.1
x === y            // false
```

> **BigInt (ES2020)**
>
> 64λΉνΈ μ μλ₯Ό νννκΈ° μν΄ μλ‘ μΆκ°λ κΈ°λ₯μΌλ‘, μ°μλ μ«μ λ€μ μλ¬Έμ nμ λΆμΈ νμμ΄λ€. BigInt() ν¨μλ₯Ό μ¬μ©ν΄ μ«μλ λ¬Έμμ΄μ BigIntλ‘ λ³νν  μ μμΌλ©°, μΌλ°μ μΈ μ°μ μ μ«μμ μ μ¬νμ§λ§ λλμμ ν  λ λλ¨Έμ§λ₯Ό λ²λ¦°λ€λ νΉμ§μ΄ μλ€. BigIntμ μΌλ°μ μΈ μ«μλ λ²μκ° λ€λ₯΄λ―λ‘ μ΄ λμ μμ΄μ μ°μ  μ°μ°μ μ€νν  μ μλ€.&#x20;

```
1000n + 2000n // 3000n
2000n - 1000n  // 1000n
2000n * 3000n //6000000n
3000n / 977n  // 3n
3000n % 977n  // 9n
```

## π λ¬Έμμ΄ String

{% hint style="info" %}
μλ°μ€ν¬λ¦½νΈ λ¬Έμμ΄μ 16λΉνΈ κ°μ΄ μμμ λ°λΌ μ΄μ΄μ§ ννμ΄λ©°, κ° κ°μ μΌλ°μ μΌλ‘ μ λμ½λ λ¬Έμμ΄λ€. λ¬Έμμ΄ λ©μλλ λλΆλΆ λ¬Έμκ° μλλΌ 16λΉνΈ κ° λ¨μλ‘ λμνλ―λ‘ λ¬Έμμ΄μ κΈΈμ΄λ λ¬Έμμ κ°―μκ° μλλΌ ν΄λΉ λ¬Έμμ΄λ₯Ό κ΅¬μ±νλ 16λΉνΈ κ°μ κ°―μμ΄λ€.&#x20;
{% endhint %}

> **μ½λ ν¬μΈνΈ**
>
> μλ°μ€ν¬λ¦½νΈλ μ λμ½λ λ¬Έμμμ UTF-16 μΈμ½λ©μ μ¬μ©νλ€. μμ£Ό μ°μ΄λ μ λμ½λ λ¬Έμμ μ½λ ν¬μΈνΈλ λ³΄ν΅ 16λΉνΈ μ΄λ΄μ΄λ―λ‘ λ¬Έμμ΄ μμ νλλ‘ ννν  μ μλ€. λ°λ©΄ μμ£Ό μ°μ΄μ§ μλ μ λμ½λ λ¬Έμμ μ½λ ν¬μΈνΈλ 16λΉνΈλ₯Ό λμ μ μμΌλ©°, μ΄λ 16λΉνΈ λκ°λ₯Ό μ°μμΌλ‘ μ°λ UTF-16 κ·μΉ(μ¨λ‘κ²μ΄νΈ νμ΄)λ‘ μΈμ½λ λλ€. μ¦, μ λμ½λ λ¬Έμ νλμ length κ°μ΄ 2κ° λ  μλ μλ€.

```
const heart = 'π'
heart.length // 2: UTF-16 μΈμ½λ© \ud83d\udc99
```

> **λ¬Έμμ΄ μ΄μ€μΌμ΄ν μνμ€ (ES5)**
>
> μμ λ°μ΄νλ ν° λ°μ΄νλ‘ κ°μΌ λ¬Έμμ΄μμ μ­μ¬λμ(\\)λ λ¬Έμμ΄μ νμν  μ μλ ' λ " κ°μ λ¬Έμλ₯Ό ννν  μ μκ² νλ νΉλ³ν μ­ν μ νλ€. (λ°±ν± λ¬Έλ²μμλ μ¬μ©ν  μ μμ§λ§ μ€ λ λ¬Έμκ° λ¬Έμμ΄ λ¦¬ν°λ΄μ ν¬ν¨λλ€.)

```
'you\'re right, it can\'t be a quote'
```

```
\n      // λ΄λΌμΈ
\t      // ν­
\'      // μμ λ°μ΄ν
\"      // ν° λ°μ΄ν
\\      // μ­μ¬λμ
\xnn    // 16μ§μ μ«μ 2κ°λ‘ νννλ μ λμ½λ λ¬Έμ
\unnnn  // 16μ§μ μ«μ 4κ°λ‘ νννλ μ λμ½λ λ¬Έμ
\u{n}   // μ½λν¬μΈνΈ nμΌλ‘ νννλ μ λμ½λ λ¬Έμ 
```

> **νκ·Έλ ν¬νλ¦Ώ λ¦¬ν°λ΄**
>
> λ°±ν± λ°λ‘ μμ ν¨μ μ΄λ¦μ΄ μμΌλ©΄ ννλ¦Ώ λ¦¬ν°λ΄μ νμ€νΈμ ννμ κ°μ΄ ν¨μμ μ λ¬λλλ°, μ΄λ¬ν κ΅¬μ‘°λ₯Ό κ°μ§ μ½λλ₯Ό νκ·Έλ ννλ¦Ώ λ¦¬ν°λ΄μ΄λΌκ³  νλ€.

```
`\n`.length            // 1
String.raw`\n`.length  // 2: String.rawλ μ΄μ€μΌμ΄νλ₯Ό μ²λ¦¬νμ§ μκ³  λ¬Έμ κ·Έλλ‘ λ°ν 
```

## π λΆ Boolean

{% hint style="info" %}
μμ½μ΄μΈ true λλ fasle λκ°μ§ κ°λ§ μ‘΄μ¬νλ©°, μλ°μ€ν¬λ¦½νΈ κ°μ λͺ¨λ λΆ κ°μΌλ‘ λ³νλ  μ μλ€.
{% endhint %}

> **falsy(false κ°μ κ°), trusy(true κ°μ κ°)**
>
> falsyμ trusyλ₯Ό μ΄μ©ν΄ μ‘°κ±΄λ¬Έμ μμ±ν  μ μλ€. λ€λ§ μ΄λ€ μμΌλ‘ μμ±ν μ§λ μ΄λ€ κ°μ΄ ν λΉλλ€κ³  μμνλλμ λ°λΌ λ€λ₯΄λ€.&#x20;

```
if(num !== null) num + 1   // nullλ§ μλλ©΄ λ  
if(num) console.log(num)   // trusyν κ°μΌ λλ§ (0μ falsyν κ°μ΄λ― μ€ν X)
```

## π Null and Undefined

{% hint style="info" %}
λλ± μ°μ°μλ nullκ³Ό undefinedκ° κ°λ€κ³  κ°μ£Όνλ©°, μΌμΉ μ°μ°μλ λ κ°μ κ΅¬λΆνλ€. λ λ€ falsyν κ°μΌλ‘ μ·¨κΈλλ©°, μ μΌνκ² μ΄ λκ°μ§ νμλ§ νλ‘νΌν°λ λ©μλκ° μλ€.&#x20;
{% endhint %}

> **null**
>
> nullμ μλμ μΌλ‘ κ°μ΄ μμμ λνλΌ λ μ¬μ©νλ νΉλ³ν κ°μ΄λ€. typeof μ°μ°μλ₯Ό μ¬μ©νλ©΄ λ¬Έμμ΄ 'object'λ₯Ό λ°ννλ€.

> **undefined**
>
> undefinedλ μ΄κΈ°νλμ§ μλ κ°μ΄λ©°, μ‘΄μ¬νμ§ μλ κ°μ²΄ νλ‘νΌν°λ λ°°μ΄ μμμ μ κ·Όνμ λ λ°νλλ κ°μ΄λ€. λν κ°μ λͺμμ μΌλ‘ λ°ννμ§ μλ ν¨μμ λ°νκ°μ΄λ©° μ λ¬λμ§ μμ μΈμμ κ°μ΄κΈ°λ νλ€.

## π μ¬λ² Symbol (ES6)

{% hint style="info" %}
μ¬λ²μ λ¬Έμμ΄μ΄ μλ νλ‘νΌν° μ΄λ¦μΌλ‘, μ¬λ² κ°μ κ°μ Έμ¬ λλ Symbol() ν¨μλ₯Ό νΈμΆνλ©° μ΄ ν¨μλ κ°μ μΈμλ‘ νΈμΆνλλΌλ μ λ κ°μ κ°μ λ°ννμ§ μλλ€. λλ¬Έμ μ¬λ²μΈ νλ‘νΌν° μ΄λ¦μ μ¬μ©νκ³  κ·Έ μ¬λ²μ κ³΅μ νμ§ μμΌλ©΄ νλ‘κ·Έλ¨μ λ€λ₯Έ λͺ¨λμμ μ€μλ‘ ν΄λΉ νλ‘νΌν°λ₯Ό λ?μ΄μΈ μ μλ€.
{% endhint %}

> **Symbol()κ³Ό Symbol.for()**
>
> Symbol()μ μ΄λ€ μΈμλ₯Ό μλ ₯νλ  μΈμ λ κ³ μ ν μ κ°μ λ°ννλ λ°λ©΄, Symbol.for()μ μΈμλ‘ μλ ₯ν λ¬Έμμ΄κ³Ό μ°κ΄λ μ¬λ²μ΄ μ‘΄μ¬νλ©΄ κΈ°μ‘΄ μ¬λ²μ λ°ννκ³ , μ‘΄μ¬νμ§ μλ κ²½μ°μλ§ μ μ¬λ²μ μμ±ν΄ λ°ννλ€.

```js
const sym_1 = Symbol('apple')
const sym_2 = Symbol('apple')

const sym_3 = Symbol.for('banana')
const sym_4 = Symbol.for('banana')

symbol_1 === symbol_2   // false
symbol_3 === symbol_4   // true
```

> **Symbol.prototype.description**
>
> μ¬λ²μ μΆλ ₯ν  λλ descriptionμ ν΅ν΄ λ¬Έμμ΄λ‘ λ³νν΄μ£Όμ΄ μλ¬λ₯Ό λ°©μ§ν  μ μλ€.

```js
symbol_1.description  // 'apple'
symbol_3.description  // 'banana'
```
