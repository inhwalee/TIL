# Operators

## 🐇 연산자란?

{% hint style="info" %}
주어진 식을 계산하여 **값을 얻어내는 과정**
{% endhint %}

## 🐇 산술 연산자

{% hint style="info" %}
기본적으로 숫자를 조작하는 연산자로, 숫자로 변환할 수 없는 피연산자는 NaN로 변환된다.\
피연산자 중 하나라도 NaN면 연산 결과는 거의 항상 NaN이다. 자바스크립트에서는 모든 숫자가 부동 소수점이다.
{% endhint %}

### 2**항 산술 연산자**

> **거듭제곱 연산자 (\*\*)**
>
> 오른쪽에서 왼쪽으로 동작하며, Math.pow() 함수와 정확이 같은 동작을 수행한다.

```javascript
2**2**3  // 4**3이 아니라 2**8과 같다.
```

> **나누기 연산자 (/)**
>
> 자바스크립트에서는 모든 숫자가 부동 소수점이므로 나눗셈 결과 역시 항상 부동 소수점이다.

```javascript
5/2   // 2.5
5/0   // Infinity
-5/0  // -Infinity
0/0   // NaN
```

> **나머지 연산자 (%)**
>
> 결과의 부호는 첫번째 피연산자를 따른다.

```javascript
5%2   // 1
-5%2  // -1
```

> **더하기 연산자 (+)**
>
> 숫자 피연산자는 더하고 문자열 피연산자는 병합한다. 두 타입이 일치하지 않으면 문자열 병합에 우선순위가 있다.

```javascript
1+2          // 3
'1'+2        // 12
1+2+'0'      // 30
1+(2+'0')    // 120
1+{}         // 1[object object]: 객체를 문자열로 변환 후 병합
true + true  // 2: boolean 값을 숫자로 변환 후 덧
1+null       // 1: null을 0으로 변환 후 덧샘
1+undefined  // NaN: undefined를 NaN로 변환 후 덧샘
```

### 단항 산술 연산자

{% hint style="info" %}
자바스크립트에서 단항 연산자는 모두 우선순위가 높으며 전부 오른쪽에서 왼쪽으로 연산을 수행한다. 또한 필요하다면 피연산자를 숫자로 변환한다.
{% endhint %}

> **단항 플러스 (+피연산자), 단항 마이너스 (-피연산자)**
>
> 피연산자를 숫자로 변환한 값을 반환한다. 단항 마이너스를 사용하면 숫자로 변환한 뒤 부호를 바꿔준다.

```javascript
let text = '123'
typeof text   // string
typeof +text  // number
-text         // -123 
```

> **전위/후위 증가 연산자(++), 전위/후위 감소 연산(--)**
>
> 피연산자를 숫자로 변환하고, 1을 더하거나 뺀 다음 값을 피연산자에 할당한다. 문자열 우선으로 변환하는 2항 산술연산과 달리 문자열 병합 수행을 절대 하지 않는다. 반환값은 피연산자와 연산자의 위치 관계에 따라 다르다.

```javascript
// Some code
let x = '1';
let y = '1';
let z = '1';

let frontCount = ++x;  // x: 2, frontCount: 2
let backCount = y++;   // y: 2, backCount: 1
z = z+z                // z: '11'
```

## 🐇 관계 연산자

{% hint style="info" %}
두 값 사이의 관계를 나타내며, 관계에 따라 항상 값으로 평가된다.
{% endhint %}

> **일치 연산자 (===)**
>
> 타입 변환을 수행하지 않으며, 엄격한 정의에 따라 두 연산자가 완전히 일치하는지 체크한다. NaN은 자신을 포함에 어떤 값과도 같지 않다. (특정 값의 타입이 NaN인지 체크하려면 isNaN() 사용) 객체는 값이 아니라 참조로 비교하므로 같은 프로퍼티라 하더라도 참조가 다르면 둘은 다른 객체이다. 문자열의 경우 내부 표현인 16비트 값이 두 연산자 모두 같아야 일치한다고 판단한다.

```javascript
1 === '1'                          // false
null === null                      // true
undefined === undefined            // true
NaN === NaN                        // false
0 === -0                           // true
{color: black} === {color: black}  // false
```

> **동등 연산자 (==)**
>
> 두 피연산자가 같은 타입이 아니라면, 타입을 변환한 뒤 둘을 같다 볼 수 있는지 체크한다.

```javascript
null == undefined  // true
1 == '1'           // true
true == 1          // true
```

> **NOT 연산자 (!)** &#x20;
>
> 일치 또는 동등하지 않은지를 체크하여 일치/동등하지 않으면 true, 일치/동등하면 false를 반환한다.

```javascript
1 !== '1' // true
1 != '1'  // false
```

> **비교 연산자: 미만 (<), 초과 (>), 이하 (<=), 이상(>=)**
>
> 비교는 숫자와 문자열에 대해서만 가능하므로, 피연산자는 숫자나 문자열로 변환된다. 더하기 연산자가 문자열을 선호한다면, 비교 연산자는 숫자를 선호하므로 두 피연산자 모두 문자열일 때만 문자열 비교를 수행한다.

```javascript
'11' < '3'  // true: 문자열 비교
'11' < 3    // false: 숫자 비교
'one' < 3   // false: 'one'은 NaN로 변환된다.
```

{% hint style="info" %}
자바스크립트에서의 문자열 비교는 두 문자열을 구성하는 값(16비트 정수)의 비교이므로, 인코딩에 따라 순서가 다를 수 있다. 따라서 문자열 비교 알고리즘이 필요할 때는 해당 지역에 맞는 알파벳 순서를 판단 기준에 포함하는 String.localeCompare() 메서드를 사용하거나, String.toLowerCase()나 String.toUpperCase를 사용해 전부 소문자 또는 대문자로 통일하여비교하는 것이 좋다. 또한 Intl.Collator 클래스를 이용하면 좀 더 상식적인 문자열 비교 결과를 얻을 수 있다.
{% endhint %}

> **in 연산자**
>
> 왼쪽 피연산자가 오른쪽 객체의 프로퍼티 이름일 경우 true를 반환한다.

```javascript
const obj = {x: 1, y: 1}
x in obj           // true
z in obj           // false
'toString' in obj  // true: 객체는 toString 메서드를 상속한다. 

const list = [7, 8, 9]
'0' in list        // true: 배열 프로퍼티(인덱스) 0이 들어있다.
1 in list          // true: 숫자는 문자열로 변환되며, 인덱스 1이 들어있다.
3 in list          // false
```

> **instanceof 연산자**
>
> 프로토타입 체인을 통해 분석하경우 왼쪽에 있는 객체가 오른쪽에 있는 클래스의 인스턴스라면 true, 아니라면 false를 반환한다. 오른쪽 피연산자가 객체가 아니라면 TypeError가 발생한다.

```javascript
const today = new Date();
today instanceof Date    // true
today instanceof Object  // true
today instanceof RegExp  // false
```

## 🐇 논리 연산자

{% hint style="info" %}
불 값을 조합하거나 부정한다.
{% endhint %}

> **AND (&&)**
>
> boolean 피연산자와 사용시 양 피연산자가 모두 true일 때에만 true를 반환한다. 왼쪽 피연산자가 false면 오른쪽 표현식은 평가하지 않으며, 왼쪽 피연산자가 true면 전체적인 값은 오른쪽에 있는 값이 된다. 따라서 왼쪽에 있는 값이 true면 && 연산자는 오른쪽에 있는 값을 평가 후 반환한다. 이를 이용해서 코드를 조건부로 실행할 수 있다.

```javascript
(x === y) && add(x); // x가 y일 때 add 함수 실행
```

> **OR (||)**
>
> boolean 피연산자와 사용시 양쪽 피연산자 중 하나만 true여도 true를 반환한다. 왼쪽 피연산자 값이 true면, 오른쪽 표현식은 평가하지 않고 바로 왼쪽 값을 반환한다. 반면 왼쪽 피연산자 값이 false면 두번째 피연산자를 평가하고 그 값을 반환한다.

```javascript
let color = pointColor || color.pointColor || 'orange'
```

> **NOT (!)**
>
> 단일한 피연산자 앞에 사용하며, 해당 피연산자의 boolean 값을 부정하여 항상 true 또는 false를  반환한다.

```javascript
// NOT 연산자를 이용한 드모르간의 법칙
!(p && q) === (!p || !q) // true: p와 q의 값이 어떻든 관계 없음
```

## 🐇 할당 연산자

> **할당 연산**
>
> \= 오른쪽에 있는 값을 외쪽에 있는 변수나 프로퍼티에 할당한다.

```javascript
x = y = z = 0 // 세 변수 모두 0으로 초기화
```

> **할당과 연산**
>
> 할당 연산자를 다른 연산자와 결합하여 연산과 할당을 동시에 수행하는 단축 표현을 할 수 있다. 함수 호출이나 증가 연산자가 있을 경우 부수 효과가 있을 수 있다.

```javascript
const data = [1, 2, 3, 4, 5]
let i = 0;

data[i++] += 2;  // 3, i = 1
data[i++] = data[i++] + 2; // 5, i = 3
```

## 🐇 기타 연산자

> **3항 연산자 (?:)**
>
> 조건 ? '참일 때 반환하는 값' : '거짓일 때 반환하는 값'

```javascript
const age = 30
age > 20 ? '성인입니다.' : '학생입니다.' // '성인입니다.'
```

> **null 병합 연산자 (??)**
>
> 왼쪽 피연산자가 null 또는 undefined가 아니면 그 값을, 맞다면 오른쪽 피연산자 값을 반환한다.

```javascript
function message(text){
  return text ?? '안녕하세요.'
}
message('Hello')  // Hello
message(null)     // 안녕하세요.
```

* 참고) defalt parmeter는 값이 null인  경우 null로 출력한다.

```javascript
function message(text = '안녕하세요.'){
  return text
}
message(undefined) // 안녕하세요.
message(null)      // null
```

## 🐇 연산 우선순위

{% hint style="info" %}
연산의 우선순위는 아래와 같으며, 연산이 길어질 경우 가독성을 위해 괄호를 사용는 것이 좋다.&#x20;
{% endhint %}

1. `++` `--` `!`
2. `*` `/` `%`
3. `+` `-`
4. `>` `<` `<=` `>=`&#x20;
5. `==` `!=` `===` `!==`
6. `&&`
7. `||`
8. `??`
9. `?:`

