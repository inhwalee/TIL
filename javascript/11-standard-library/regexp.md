# RegExp



정규표현식이란, 문자열을 검색하고 대체하는데 사용하는 일종의 형식입니다.\
이메일, 패스워드 유효성 검사와 같이 원하는 문자 형태를 빠르게 확인할 수 있습니다.

js 뿐만 아니라 다른 프로그래밍 언어에서도 사용되는 방식이지만, 각 언어에서 지원되는 문법이 다를 수 있으므로\
내가 작업하는 환경에서 해당 문법이 적용되는지 확인 후 작업해야합니다.

[연습 사이트](https://regexr.com/)\
[정규표현식 퀴즈](https://regexone.com/)

## JS 정규식 생성

* 생성자 함수 방식

```js
new RegExp('표현', '옵션');
new RegExp('[a-z]', 'gi');
```

* 리터럴 방식

```js
/표현/옵션
/[a-z]/gi
```

## 메서드

| 메서드     | 문법                       | 설명                     |
| ------- | ------------------------ | ---------------------- |
| test    | `정규식.test(문자열)`          | 일치 여부 반환 (Boolean)     |
| match   | `문자열.match(정규식)`         | 일치하는 문자의 배열 반환 (Array) |
| replace | `문자열.replace(정규식, 대체문자)` | 일치하는 문자를 대체            |

## 플래그(옵션)

| 플래그 | 뜻           | 설명                  |
| --- | ----------- | ------------------- |
| `g` | global      | 모든 문자 일치            |
| `i` | ignore case | 영어 대소문자를 구분하지 않고 일치 |
| `m` | multi line  | (줄바꿈이 된) 여러 줄 일치    |

## 문법(표현)

### 그룹/범위

| 문법             | 설명                         |
| -------------- | -------------------------- |
| `a &verbar; b` | a 또는 b                     |
| `()`           | 그룹                         |
| `[]`           | 괄호 안의 어떤 문자든               |
| `[abc]`        | a 또는 b 또는 c                |
| `[a-z]`        | a 부터 z 사이의 문자 구간에 일치 (소문자) |
| `[A-Z]`        | A 부터 Z 사이의 문자 구간에 일치 (대문자) |
| `[0-9]`        | 0 부터 9 사이의 문자 구간에 일치 (숫자)  |
| `[가-힣]`        | 가 부터 힣 사이의 문자 구간에 일치 (한글)  |
| `[^]`          | 괄호 안의 어떤 문자를 제외            |
| `(?:)`         | 찾지만 기억하지는 않음 (그룹을 생성하지 않음) |

### 수량

| 문법           | 설명                                  |
| ------------ | ----------------------------------- |
| `?`          | '있거나 없거나 (zero or one)              |
| `*`          | 없거나 있거나 많거나 (zero or more)          |
| `+`          | 하나 또는 많이 (one or more)              |
| `퐁{n}`       | '퐁'이 n번 반복                          |
| `퐁{min,}`    | '퐁'이 min번 이상 반복                     |
| `퐁{min,max}` | '퐁'이 min번 이상 max번 이하 (min\~max개) 반복 |

### 바운더리 타입

| 문법            | 설명                                 |
| ------------- | ---------------------------------- |
| `\b단어` `단어\b` | 단어 경계 (앞 또는 뒤에서 쓰이고 있는 단어)         |
| `\B단어` `단어\B` | 단어 경계가 아님 (앞 또는 뒤에서 쓰이고 있지 않는 단어)  |
| `^단어`         | 문장의 시작에 있는 단어                      |
| `단어$`         | 문장의 끝에 있는 단어 (여러줄에서 찾으려면 m 플래그 설정) |
| `(?=@)`       | @ 기호 기준 앞쪽 일치                      |
| `(?<=@)`      | @ 기호 기준 뒤쪽 일치                      |

### 문자 종류

| 문법   | 설명                                            |
| ---- | --------------------------------------------- |
| `\`  | 정규표현식에서 명령어로 쓰이는 특수문자가 아닌 특수문자 그 자체를 찾고 싶은 경우 |
| `.`  | 어떤 문자(줄바꿈 문자 제외)                              |
| `\w` | 문자 (world) // 대소문자 52개, 숫자 10개, \_            |
| `\W` | 문자 아님 (world)                                 |
| `\b` | 63개 문자에 일치하지 않는 문자 경계 (boundary)              |
| `\d` | 숫자 (digit)                                    |
| `\D` | 숫자 아님 (digit)                                 |
| `\s` | 공백 (space, tab)                               |
| `\S` | 공백 아님 (space, tab)                            |

## 예제 문자

```js
const str = `
  010-1234-5678
  010 1234 5678
  010.1234.5678
  
  the_email@naver.com
  the.email@naver.com
  theemail@naver.com
  
  https://www.omdbapi.com/?apikey=7035c60c&s=frozen
  https://youtu.be/-ZClicWm0zM
  youtu.be/-ZClicWm0zM
  
  The quick brown fox jumps over the lazy dog.
  abbcccddd
  `;
```

#### 전화번호만 찾고 싶은 경우

* `/\d\d\d-\d\d\d\d-\d\d\d\d/gm`
* `/\d{2,3}[- .]\d{4}[- .]\d{4}/gm`

#### 이메일만 찾고 싶은 경우

* `/[a-zA-Z0-9._+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9.]/gm`

#### 유튜브 주소에서 아이디만을 가져오고 싶은 경우

* `/(?:https?:\/\/)?(?:www\.)?youtu.be\/([a-zA-Z0-9]{11})/gm`

``

```
// Some code
 <h1>Hello world</h1>
  <script>
    let str = `
      010-1234-5678
      theemail@naver.com
      https://www.omdbapi.com/?apikey=7035c60c&s=frozen
      The quick brown fox jumps over the lazy dog.
      a_bb_ccc_dddd
    `
    /* 생성자 함수 방식
    const regexp = new RegExp('the', 'gi')
    */

    /* 리터럴 방식
    const regexp = /the/gi
    console.log(str.match(regexp)) // 일치하는 문자의 배열 반환*/

    /* 문자 수저 후 재할당
    const regexp = /fox/gi
    console.log(regexp.test(str)) // true
    str = console.log(str.replace(regexp, 'CAT')) */

    // const regexp = /the/g
    // console.log(str.match(/\.$/gim))

    console.log(str.match(/\bf\w{1,}\b/g))
  </script>
```

``
