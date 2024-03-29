# Arrays

## 🐇 배열이란?

{% hint style="info" %}
배열은 **값의 순서있는 집합**으로, 각 값을 나타내는 요소에는 위치를 나타내는 숫자인 인덱스가 있다. 자바스크립트 실행 환경은 일반적으로 배열을 최적화하므로 **일반적인 객체 프로퍼티보다 빠르게 접근 가능**하다. 콤마를 연속해서 썼는데 그 사이에 값이 없으면 성긴 배열이 만들어지며, 생략한 위치에 실제 배열 요소가 존재하지는 않지만 검색하면 undefined가 반환된다. (배열 리터럴 문법은 마지막에 콤마를 허용하므로 \[,,]의 길이는 3이 아닌 2이다.)

배열의 요소는 어떤 타입이든 상관 없으며, 자바스크립트 배열은 0으로 시작하는 32비트 인덱스를 사용하므로 **최대 4,294,967,295개의 요소**까지 담을 수 있다.&#x20;
{% endhint %}

## 🐇 배열 생성

> **배열 리터럴**
>
> 배열을 만드는 가장 단순한 방법으로, 대괄호 안에서 콤마로 구분한 리스트 형태이다.

```javascript
[true, '2', 3, 2+2, [5], {six: 6}];
```

> **분해 연산자 (ES6)**
>
> 분해 연산자는 모든 이터러블 객체에 동작하며, ... 를 써서 배열 리터럴 안에 다른 배열 요소를 넣을 수 있다.

```javascript
const odd = [1, 3, 5];
const even = [2, 4, 6];
const number = [0, ...odd, ...even];        // [0, 1, 2, 3, 4, 5, 6]
const greeting = [...'안녕하세요'];           // ['안', '녕', '하', '세', '요']
const letters = [...new Set([...'hello'])]; // ['h', 'e', 'l', 'o']
```

> **Array() 생성자**
>
> Array() 생성자로 배열을 만들 수도 있으며, 생성자는 아래 3가지 방법으로 호출할 수 있다.

```javascript
new Array();       // []: 인자 없이 호출
new Array(3);      // [비어있음, 비어있음, 비어있음]: 길이를 가진 배열 생성
new Array(1, '2'); // [1, '2']: 인자가 요소가 되어 배열 생성 
```

> **Array.of() 팩토리 메서드 (ES6)**
>
> Array()는 생성자의 인자에 숫자 하나만 입력하면 그 숫자의 길이민큼 배열이 생성되므로, 숫자 요소 하나만 있는 배열은 생성할 수 없다. 인자의 갯수를 따지지 않고 각 인자를 새 배열의 요소로 사용하는 Array.of() 함수를 통해 이를 해결할 수 있다.

```javascript
Array.of();       // []
Array.of(10);     // [10]
Array.of(1,2,3);  // [1, 2, 3]
```

> **Array.from() 팩토리 메서드 (ES6)**
>
> 첫번째 인자로 이터러블 객체나 배열 비슷한 객체를 받으며, 해당 객체의 요소로 새 배열을 만들어 반환한다. 여기서 배열 비슷한 객체란 숫자인 length 프로퍼티가 있고, 이름이 정수인 프로퍼티에 값이 저장된 객체를 말하며, 웹 브라우저 메서드 일부가 배열 비슷한 객체를 반환하므로, 먼저 이들을 배열로 변환하면 작업이 간단해질 때가 많다.
>
> 선택사항인 두번째 인자로는 함수를 받으며, 새 배열을 생성할 때 소스 객체의 각 요소를 이 함수에 전달하고 반환값을 배열에 저장한다.

```javascript
Array.from(iterable);  // [...iterable]
Array.from([1, 2, 3], function(num){return num-1});  // [0, 1, 2]
```

## 🐇 배열 요소 읽기와 쓰기

{% hint style="info" %}
&#x20;배열 요소에 접근할 때는 \[] 연산자를 사용하며, **대괄호 안에는 양의 정수로 평가되는 표현식**이 있어야 한다. 배열은 특별하긴 하지만 결국 객체이며, 배열 요소에 접근할 때 사용하는 대괄호는 객체 프로퍼티에 접근할 대 사용하는 대괄호와 마찬가지로 동작한다. 즉 숫자인 배열 인덱스는 문자열로 변환되고, 이 문자열을 프로퍼티 이름으로 사용한다.
{% endhint %}

```javascript
a = ['hello'];
hello = a[0];
a[1] = 'world';
a[1+1] = '!';
```

{% hint style="info" %}
&#x20;배열 인덱스에는 음수도, 정수 아닌 숫자도 쓸 수 있다. 이런 프로퍼티는 이름이 양의 정수가 아니므로 배열 인덱스가 아니라 일반적인 객체 프로퍼티로 취급된다. 또한 배열 인덱스는 조금 특별한 타입의 객체 프로퍼티 이름일 뿐이므로 존재하지 않는 프로퍼티를 검색해도 undefined를 반환할 뿐 '경계 초과' 에러는 일어나지 않는다.
{% endhint %}

```javascript
a = [0, 1, 2];  // [0, 1, 2]
a[-1.1] = -1;       // [0, 1, 2, -1.1: -1]
a['3'] = 3;         // [0, 1, 2, 3, -1.1: -1]   
a[4.0] = 4;         // [0, 1, 2, 3, 4, -1.1: -1]  
a[-1.1];            // -1
a[5];               // undefined
```

## 🐇 성긴 배열

{% hint style="info" %}
성긴 배열은 인덱스가 연속적이지 않은 배열이다. Array() 생서자를 사용하거나 현재 배열의 길이보다 큰 인덱스에 요소를 할당하면 만들어진다. 성긴 배열은 일반적으로 빽빽한 배열에 비해 좀 느리지만 메모리를 효율적으로 사용하는 방법으로 구현되며, 이런 배열에서 요소를 검색하는 시간은 일반적인 객체 프로퍼티 검색에 필요한 시간과 비슷하다.
{% endhint %}

```javascript
a = new Array(5); // [비어있음 x5] 요소는 없지만 길이가 5인 배열
a[1000] = 1000;       // [비어있음 x 1000, 1000] 요소는 하나지만 길이는 1001인 배열
0 in a                // false: a에는 인덱스 0에 요소가 없다.
```

## 🐇 배열 길이

{% hint style="info" %}
&#x20;length 프로퍼티는 배열에 포함된 요소의 갯수와 같다. 모든 배열에는 length 프로퍼티가 있으며, 이 프로퍼티는 일반적인 자바스크립트 객체와 배열을 구분하는 특징이다. length 보다 크거나 같은 인덱스는 존재하지 않으며, length를 이용해서 요소를 추가하거나 삭제할 수 있다.
{% endhint %}

```javascript
a = [1, 2, 3, 4, 5];
a.length = 3;          // [1, 2, 3]: length를 이용한 요소 삭제
a.[a.length + 1] = 4;  // [1, 2, 3, 4]: length를 이용한 요소 추
```

## 🐇 배열 요소 추가와 삭제

{% hint style="info" %}
새 인덱스에 값을 할당하는 것 말고도 메서드를 활용해 값을 추가하고 삭제할 수 있다. push(), pop() 메서드는 배열 마지막에 값을 추가하거나 삭제한다. unshift(), shift() 메서드는 배열 맨 앞에 값을 추가하거나 삭제한다. 또한 delete 연산자로도 배열 요소를 삭제할 수 있는데, 이 delete 연산자는 pop(), shift()와 달리 빈 공간을 매우기 위해 요소를 이동시키 않으므로 length 프로퍼티는 변하지 않는다.
{% endhint %}

```javascript
a = [];
a.push(1, 2, 3, 3.5);  // [1, 2, 3, 3.5]
a.pop(1);              // [1, 2, 3]
a.unshift(-1, 0);      // [-1, 0, 1, 2, 3]
a.shift(1);            // [0, 1, 2, 3]
delete a[0];           // [비어있, 1, 2, 3]
```

## 🐇 배열 순회

{% hint style="info" %}
가장 기본적인 배열 순회 방법을 알아보자.
{% endhint %}

> **for/of 루프**
>
> 배열 요소나 이터러블 객체를 순회하는 가장 쉬운 방법은 for/of 루프이다. for/of 루프가 사용하는 내장 이터레이터는 오름차순으로 요소를 반환하는데, 성긴 배열도 마찬가지이며 존재하지 않는 배열 요소에 대해서는 undefined를 반환한다. for/of 루프를 이용할 때 인덱스가 필요하다면 entries() 메서드와 분해 할당을 이용하면 된다.

```javascript
const letters = [...'hello'];  // ['h', 'e', 'l', 'l', 'o']
let string = '';
for(let [index, letter] of letters) {
  if(index%2 === 0) string += letter;  // 짝수번째 인덱스 글자 추출
}
string  // 'hlo'
```

> **forEach()**
>
> 이 메서드는 for 루프의 변형이 아니라 배열 순회를 함수형으로 바꾼 배열 메서드이다. forEach()는 배열 요소를 순서대로 순회하면서 전달받은 함수를 호출한다. for/of 루프와 달리 **forEach() 는 성긴 배열을 인식하고 존재하지 않는 요소에 대해서 함수를 호출하지 않는다.**

```javascript
a = [0, 1, 2, 3, undefined];
delete a[0];                         // [비어있음, 1, 2, 3, undefined]
a.forEach(num => console.log(num));  // [1, 2, 3, undefined]
```

> **for 루프**
>
> for 루프는 배열이 빽빽하며 **모든 요소에 유효한 데이터가 있다고 가정**하므로 정의되지 않았거나 존재하지 않는 요소를 건너뛰려면 배열 요소를 사용하기 전에 아래와 같이 먼저 테스트를 해야한다.

```javascript
for(let i = 0; i < a.length; i++) {
  if(a[i] === undefined) continue;// 유효하지 않은 요소(비어있음, undefined)는 건너뛴다.
  // 루프 바
}
```

## 🐇 다차원 배열

{% hint style="info" %}
&#x20;자바스크립트에서 다차원 배열을 직접 지원하지는 않지만 배열의 배열을 만들어 대략적으로 흉내 낼 수는 있다. 내부 배열의 값에 접근할 때는 \[] 연산자를 이중으로 사용하면 된다.
{% endhint %}

```javascript
let table = new Array(10);
for(let i = 0; i < table.length; i++) {
  table[i] = new Array(10);
}

for(let row = 0; row < table.length; row++) {
  for(let col = 0; col < table[row].length; col++) {
    table[row][col] = rol*col;
  }
}

table[5][7];  // 35
```
