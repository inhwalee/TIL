# Properties-Methods

{% hint style="info" %}
자바스크립트 함수에 typeof 연산자를 적용하면 문자열 'function' 을 반환하지만, 사실 함수는특별한 종류의 자바스크립트 객체이다. 함수는 객체이므로 다른 객체와 마찬가지로 프로퍼티와 메서드를 가질 수 있다. 심지어 새 함수 객체를 생성하는 Function() 생성자까지 있다.&#x20;
{% endhint %}

## 🐇  함수 프로퍼티

> **length 프로퍼티**
>
> 읽기 전용인 length 프로퍼티는 함수에 정의된 매개변수 개수이며 보통 함수가 예상하는 인수의 개수이기도 하다. 나머지 매개변수가 있다면 그 매개변수는 length 프로퍼티에 포함되지 않는다.

> **name 프로퍼티**
>
> 읽기 전용인 name 프로퍼티는 함수가 정의될 때 이름이 있었다면 그 이름을, 익명 함수 표현식이라면 처음 생성되었을 대 할당된 변수나 프로퍼티 이름이다. 이 프로퍼티는 디버깅이나 에러 메세지에 유용하게 사용된다.

> **prototype 프로퍼티**
>
> 화살표 함수를 제외하면 모든 함수에는 프로토타입 객체를 참조하는 prototype 프로퍼티가 있다. 함수의 프로토타입 객체는 모두 다르며, 함수를 생성자로 사용하면 새로 생성된 객체는 프로토타입 객체에서 프로퍼티를 상속받는다.

## 🐇 함수 메서드

> **call()과 apply()메서드**
>
> call()과 apply()는 함수를 마치 다른 객체의 메서드인 것 처럼 간접적으로 호출한다. 첫번째 인자는 함수를 호출할 객체이며 이 인자가 호출 컨텍스트가 되어 함수 바디 안에서 this 키워드의 값이 된다.&#x20;

```javascript
f.call(obj);   // obj.m = f;
f.apply(obj);  // obj.m = f;
```

> 화살표 함수는 자신이 정의된 컨텍스트의 this 값을 상속받으며, 이 값은 call()과 apply() 메서드로 덮어쓸 수 없다. 때문에 화살표 함수에서 이들 메서드를 호출하면 첫번째 인자는 무시된다.

> call()을 사용할 때 두번째 인자는 호출될 함수에 전달된다. 이 인자는 화살표함수에서도 무시되지 않는다. apply() 메서드도 call()과 비슷하지만, 함수에 전달할 인자가 배열로 제공된다는 점이 다르다. ES6 이후라면 그냥 분해 연산자를 써도 되지만 ES5 코드에서는 함수가 받는 인자 개수에 제한이 없다면 apply() 메서드를 써서 임의의 길이를 가진 배열을 전달해 함수를 호출했다.&#x20;

```javascript
f.call(obj, 1, 2);
f.apply(obj, [1, 2]);
```

> 다음 trace()함수는 timed() 함수와 비슷하지만 함수가 아니라 메서드를 대상으로 동작한다.&#x20;

```javascript
functin trace(obj, m) {
  let original = obj[m];
  obj[m] = function(...args) {
    console.log(`시작시간: ${new Date}`)
    let result = original.apply(this, args);
    console.log(`종료시간: ${new Date()}`);
    return result;
  }
}
```

> &#x20;**bind() 메서드**
>
> &#x20;bind()의 주요 목적은 함수를 객체에 결합시키는 것이다. 함수 func 에서 bind() 메서드를 호출하면서 객체 obj를 전달하면 새 함수를 반환한다. 새 함수를 함수로 호출하면 원래 함수 func이 obj의 메서드로 호출된다.

```javascript
function func(y) {return this.x = y};
let obj = {x: 1};
let m = func.bind(obj);
m(2); // 3

let newObj = {x: 10, m};
newObj.m(2); // 3: m는 여전히 obj에 결합되어 있다.
```

> bind() 함수를 호출하는 목적은 대개 화살표 함수가 아닌 함수를 화살표 함수처럼 사용하는 것이므로 화살표 함수에서 결합이 이루어지지 않는다는 것은 문제가 되지 않는다. bind() 메서드는 단순히 함수를 객체에 결합하는 것으로 끝나지 않는다. bind()에 전달하는 인자 중 첫번째를 제외한 나머지는 this 값과 함께 결합된다. 이러한 부분 적용은 화살표 함수에서도 동작한다. 부분 적용은 함수형 프로그래밍에서 널리 쓰이는 기법이며 커링이라고 부르기도 한다.

```javascript
let sum = (x, y) => x + y;
let succ = sum.bind(null, 1); // sum의 첫번째 인자 x와 1을 결합
succ(2); // 3: x는 1이고 y는 2이다.
```

```javascript
function f(y, z) {return this.x + y + z;}
let a = f.bind({x: 1}, 2); // this와 y를 결합
a(3); // 6: this.x는 1, y는 2, z는 3
```

> &#x20;**toString() 메서드**
>
> &#x20;자른 자바스크립트 객체와 마찬가지로 함수에도 toString() 메서드가 있다. 이 메서드는 함수ㅇ 선언문의 문법을 지키는 문자열을 반환해야한다고 규정하나 현실에서는 대부분의 환경에서 함수의 toString 메서드가 소스 코드 전체를 반환한다. 내장 함수는 일반적으로 '\[native code]' 같은 문자열을 함수 바디로 반환한다.
