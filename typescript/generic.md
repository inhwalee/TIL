# ✅ Generics Basic
* 인풋과 아웃풋 타입이 고정되어 있지는 않지만, 일정한 규칙을 가지고 있는 함수에서 사용할 수 있다.
* 함수를 호출할 때 타입을 직접 지정해줄 수도 있고, 지정 없이 호출하여 추론하게 할 수도 있다. 
* 일반적으로 `T`로 표기하며, 이 `T`는 타입을 담는 변수처럼 사용된다.
```ts
function helloGeneric<T, U>(message:T, comment:U):T {
  return message;
}

helloGeneric<string, number>('Mark', 30) // 타입을 직접 지정해주는 경우
helloGeneric(30, 36) // 인자값에 따라 타입이 추론되는 경우 => T의 타입은 36, U의 타입은 39가 된다.
```

# ✅ Generics Array&Tuple
```ts
function helloArray<T>(message: T[]):T {
  return message[0];
}

helloArray(['Hello', 'World']) // 리턴 타입은 string
helloArray(['Hello', 5]) // 리턴 타입은 string | number => hello는 string이기 때문에 기대한 타입과 다름 
```
```ts
function helloTuple<T, K>(message: [T, K]):T {
  return message[0];
}

helloTuple(['Hello', 'World']) // 리턴 타입은 string
helloTuple(['Hello', 5]) // 리턴 타입은 string
```

# ✅ Generics Function
* Type Alias 방법
```ts
type HelloFunctionGeneric1 = <T>(message: T) => T  

const helloFunction1: HelloFunctionGeneric1 = <T>(message: T): T => {
  return message;
}
```
* Interface 방법
```ts
interface HelloFunctionGeneric2 {
  <T>(message: T): T
}

const helloFunction2: HelloFunctionGeneric2 = <T>(message: T): T => {
  return message;
}
```

# ✅ Generics Class
```ts
class Person<T, K> {
  private _name: T;
  private _age: K;
  
  constuctor(name: T, age: K) {
    this._name = name;
    this._age = age;
  }
}

new Person<string, number>('Mark' ,30) // 타입을 직접 지정해주는 경우
new Person('Mark', 30)  // 인자값에 따라 타입이 추론되는 경우 => T의 타입은 string, U의 타입은 number가 된다.
```

# ✅ Generics Class with extends
* 타입은 항상 제일 작은 범위로 제약을 걸어주는 것이 좋으므로, `extends`를 활용 할 것
```ts
class PersonExtends<T extends string | number> { // T의 타입은 string 또는 number만 가능
  pravate _name: T;
  
  constructor(name: T){
    this._name = name
  }
}

new PersonExtends('Mark');
new PersonExtends(30);
//  new PersonExtends(true) 에러
```

# ✅ Keyof & Type Lookup System
* `keyof`와 `extends`를 통해 컴파일 타임에 타입을 정확하게 찾아낼 수 있다.
```ts
interface IPerson {
  name: string;
  age: number;
}

const person: IPerson = {
  name: 'Mark',
  age: 30,
} 
```
```ts
function getProp<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

getProp(person, 'name') // T는 IPerson, K는 'name' => 리턴 타입은 string
getProp(person, 'age') // T는 IPerson, K는 'age' => 리턴 타입은 number 
```
```ts
function setProp<T, K extensds keyof T>(obj: T, key: K, value: T[K]): void {
  obj[key] = value;
}

setProps(person, 'name', 'Anna') // T는 IPerson, K는 'name' => value 타입은 string
setProps(person, 'age', 31) // T는 IPerson, K는 'age' => value 타입은 number
```
