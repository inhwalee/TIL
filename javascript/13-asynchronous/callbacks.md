# Callbacks

## ๐ ๋น๋๊ธฐ ํ๋ก๊ทธ๋๋ฐ๊ณผ ์ฝ๋ฐฑ

{% hint style="info" %}
๋น๋๊ธฐ์ ์ด๋ผ๋ ๋ง์ ๋ฐ์ดํฐ๊ฐ ๋ค์ด์ค๊ฑฐ๋ ์ด๋ค ์ด๋ฒคํธ๊ฐ ์ผ์ด๋  ๋๊น์ง ๊ณ์ฐ์ ๋ฉ์ถ๊ณ  ๋๊ธฐํ๋ ์ผ์ด ์ฆ๋ค๋ ์๋ฏธ์ด๋ค. ์๋ฐ์คํฌ๋ฆฝํธ์์๋ ๋น๋๊ธฐ ์ฝ๋๋ฅผ ๋ค๋ฃจ๋ ๊ธฐ๋ฅ๋ค์ ์ ๊ณตํ๋๋ฐ, ๊ฐ์ฅ ๊ธฐ๋ณธ์ ์ธ ๋น๋๊ธฐ ํ๋ก๊ทธ๋๋ฐ์ ์ฝ๋ฐฑ์ ํตํด ์ด๋ฃจ์ด์ง๋ค. ์ฝ๋ฐฑ์ ๋ค๋ฅธ ํจ์์ ์ ๋ฌํ๋ ํจ์๋ก, ์ฝ๋ฐฑ์ ์ ๋ฌ๋ฐ์ ํจ์๋ ์ด๋ค ์กฐ๊ฑด์ ๋ง์กฑํ๊ฑฐ๋ ๋น๋๊ธฐ ์ด๋ฒคํธ๊ฐ ์ผ์ด๋๋ฉด ์ ๋ฌ๋ฐ์ ์ฝ๋ฐฑ ํจ์๋ฅผ ํธ์ถํ๋ค.&#x20;
{% endhint %}

## ๐ ํ์ด๋จธ์ ์ฝ๋ฐฑ

{% hint style="info" %}
์ผ์  ์๊ฐ์ด ์ง๋๋ฉด ์ฝ๋๋ฅผ ์คํํ๋ ํ์ด๋จธ๋ ๋จ์ํ ๋น๋๊ธฐ ํ๋ก๊ทธ๋จ ์ค ํ๋์ด๋ค.&#x20;
{% endhint %}

```
setTimeout(checkForUpdates, 1000 * 60);  // 1๋ถ ๋ค ๋ฑ 1๋ฒ๋ง ํธ์ถ๋๋ ์ฝ๋ฐฑ ํจ์
setInterval(checkForUpdates, 1000 * 60); // 1๋ถ ๊ฐ๊ฒฉ์ผ๋ก ๊ณ์ ํธ์ถ๋๋ ์ฝ๋ฐฑ ํจ์
```

## ๐ ์ด๋ฒคํธ์ ์ฝ๋ฐฑ

{% hint style="info" %}
ํด๋ผ์ด์ธํธ ์ฌ์ด๋ ์๋ฐ์คํฌ๋ฆฝํธ๋ ๋ฏธ๋ฆฌ ์ง์ ๋ ๊ณ์ฐ์ ์คํํ๊ธฐ๋ณด๋ค๋ ์ฌ์ฉ์๊ฐ ๋ญ๊ฐ ํ๊ธธ ๊ธฐ๋ค๋ ธ๋ค๊ฐ ๊ทธ ํ๋์ ๋ฐ์ํ๋ ์ด๋ฒคํธ ์ฃผ๋์ ์ผ๋ก ์คํ๋๋ค. ์ง์ ๋ ์ปจํ์คํธ์ ์ด๋ฒคํธ ํ์๊ณผ ์ด๋ฒคํธ๋ฅผ ์ฒ๋ฆฌํ  ์ฝ๋ฐฑ ํจ์๋ฅผ ๋ฑ๋กํ๋ฉด ์น ๋ธ๋ผ์ฐ์ ๋ ํด๋น ์ด๋ฒคํธ๊ฐ ์ผ์ด๋  ๋๋ง๋ค ํจ์๋ฅผ ํธ์ถํ๋ค. ์ด๋ฐ ์ฝ๋ฐฑ ํจ์๋ฅผ ์ด๋ฒคํธ ํธ๋ค๋ฌ, ์ด๋ฒคํธ ๋ฆฌ์ค๋๋ผ๊ณ  ๋ถ๋ฅธ๋ค.
{% endhint %}

```
button.addEventListener('click', applyUpdate);
```

{% hint style="info" %}
๋๋ถ๋ถ์ ์น API๋ ์ ์์ ์ ๊ฐ์ด ์ด๋ฒคํธ๋ฅผ ๋ฐ์์ํค๋ ๊ฐ์ฒด์์ addEventListner()๋ฅผ ํธ์ถํ๋ ๋ฐฉ์์ผ๋ก ์ด๋ฒคํธ ํธ๋ค๋ฌ๋ฅผ ์ ์ํ์ง๋ง, ์ด๋ฒคํธ๋ฅผ ๋ฐ์์ํค๋ ๊ฐ์ฒด์ ํ๋กํผํฐ์ ์ด๋ฒคํธ ๋ฆฌ์ค๋๋ฅผ ์ง์  ํ ๋นํ๋ ๋ฐฉ์์ผ๋ก๋ ๋ฑ๋กํ  ์ ์๋ค. ์ด๋ฐ ํํ์ ์ด๋ฒคํธ ๋ฆฌ์คํฐ ํ๋กํผํฐ ์ด๋ฆ์ ๊ด์ต์ ์ผ๋ก on์ผ๋ก ์์ํ๋ค.
{% endhint %}

```
button.onclick = applyUpdate;
```

## ๐ ๋คํธ์ํฌ ์ด๋ฒคํธ์ ์ฝ๋ฐฑ

{% hint style="info" %}
๋คํธ์ํฌ ์์ฒญ ์ญ์ ์๋ฐ์คํฌ๋ฆฝํธ ํ๋ก๊ทธ๋๋ฐ์ ๋ํ์ ์ธ ๋น๋๊ธฐ ์ ํ ์ค ํ๋์ด๋ค. ๋ธ๋ผ์ฐ์ ์์ ์คํ๋๋ ์๋ฐ์คํฌ๋ฆฝํธ๋ ๋ค์๊ณผ ๊ฐ์ด ์น ์๋ฒ์์ ๋ฐ์ดํฐ๋ฅผ ๊ฐ์ ธ์ฌ ์ ์๋ค.&#x20;
{% endhint %}

```
function getCurrentVersionNumber(versionCallback) {
  // ๋ฐฑ์๋ ๋ฒ์  API์ HTTP ์์ฒญ 
  let request = new XMLHttpRequest();
  request.open('GET', 'http://www.example.com/api/version');
  request.send();
  
  // ์๋ต์ ๋ฐ์์ ๋ ํธ์ถํ  ์ฝ๋ฐฑ ๋ฑ๋ก 
  request.onload = function() {
    if(request.status === 200) {
      let currentVersion = parseFloat(request.responseText);
      versionCallback(null, currentVersion);
    } else {
      versionCallback(response.statusText, null);
    }
  };
  
  // ๋คํธ์ํฌ ์๋ฌ์ ํธ์ถํ  ๋ค๋ฅธ ์ฝ๋ฐฑ ๋ฑ๋ก 
  request.onerror = request.ontimeout = function(e) {
    versionCallback(e.type, null);
  }
}
```

## ๐ ๋ธ๋์ ์ฝ๋ฐฑ๊ณผ ์ด๋ฒคํธ

{% hint style="info" %}
๋ธ๋๋ ๋น๋๊ธฐ์ ์ผ๋ก ๋ง๋ค์ด์ ธ ์์ผ๋ฉฐ ๋ง์ API๊ฐ ์ฝ๋ฐฑ๊ณผ ์ด๋ฒคํธ๋ฅผ ์ฌ์ฉํ๋ค. ์๋ฅผ ๋ค์ด ํ์ผ ์ฝํ์ธ ๋ฅผ ์ฝ๋ ๊ธฐ๋ณธ API๋ ๋น๋๊ธฐ์ ์ด๋ฉฐ ํ์ผ ์ฝํ์ธ ๋ฅผ ์ฝ์ผ๋ฉด ์ฝ๋ฐฑ ํจ์๋ฅผ ํธ์ถํ๋ค.
{% endhint %}

```
const fs = require('fs');  // fs ๋ชจ๋์ ํ์ผ ์์คํ ๊ด๋ จ API์ด๋ค.
let options = {            // ํ๋ก๊ทธ๋จ์์ ์ฌ์ฉํ  ์ต์ ๊ฐ์ฒด
  // ๊ธฐ๋ณธ ์ต์
}

// fs.readFile์ ์ง์ ๋ ํ์ผ์ ๋น๋๊ธฐ์ ์ผ๋ก ์ฝ๊ณ  ์ฝ๋ฐฑ์ ํธ์ถํ๋ค.
fs.readFile('config.json', 'utf-8', (err, text) => {
  if(err) {
    // ์๋ฌ๊ฐ ์์ผ๋ฉด ๊ฒฝ๊ณ ๋ฅผ ํ์ํ๊ณ  ๊ณ์ ์งํํ๋ค.
    console.warn('config ํ์ผ์ ์ฝ์ ์ ์์ต๋๋ค.', err);
  } else {
    // ์๋ฌ๊ฐ ์์ผ๋ฉด ํ์ผ ์ปจํ์ธ ๋ฅผ ๋ถ์ํ๊ณ  options ๊ฐ์ฒด์ ํ ๋นํ๋ค.
    Object.assgin(options, JSON.parse(text));
  }
  
  startProgram(options);
})
```

{% hint style="info" %}
๋ธ๋์๋ ์ด๋ฒคํธ ๊ธฐ๋ฐ API๋ ๋ค์ํ๋ฐ, ๋ค์ ํจ์๋ ๋ธ๋์์ URL์ HTTP ์์ฒญ์ ๋ณด๋ด๋ ๋ฐฉ๋ฒ์ด๋ค. ๋ธ๋๋ addEventListener() ๋์  on() ๋ฉ์๋๋ฅผ ์ฌ์ฉํด ์ด๋ฒคํธ ๋ฆฌ์ค๋๋ฅผ ๋ฑ๋กํ๋ค.
{% endhint %}

```
const https = require('https');

function getText(url, callback) {
  // URL์ HTTP GET ์์ฒญ์ ์์ํ๋ค.
  request = https.get(url);
  
  // ์๋ต ์ด๋ฒคํธ๋ฅผ ์ฒ๋ฆฌํ  ํจ์๋ฅผ ๋ฑ๋กํ๋ค.
  request.on('response', response => {
    // ์๋ต ์ด๋ฒคํธ๊ฐ ์๋ค๋ ๊ฒ์ ์๋ต ํค๋๋ฅผ ๋ฐ์๋ค๋ ์๋ฏธ์ด๋ค.
    let httpStatus = response.statusCode;
    
    // HTTP ์๋ต ๋ฐ๋๋ ์์ง ๋ฐ์ง ๋ชปํ์ผ๋ฏ๋ก
    // ๋ฐ๋๋ฅผ ๋ฐ์์ ๋ ํธ์ถํ  ์ด๋ฒคํธ ํธ๋ค๋ฌ๋ฅผ ๋ฑ๋กํ๋ค.
    response.setEncoding('utf-8');
    let body = '';
    
    // ๋ฐ๋์ ํ์คํธ ๋ฉ์ด๋ฆฌ๋ฅผ ์ฌ์ฉํ  ์ ์๊ฒ ๋๋ฉด ์ด ์ด๋ฒคํธ ํธ๋ค๋ฌ๋ฅผ ํธ์ถํ๋ค.
    response.on('data', chunk => {body += chunk});
    
    // ์๋ต์ด ์๋ฃ๋๋ฉด ์ด ์ด๋ฒคํธ ํธ๋ค๋ฌ๋ฅผ ํธ์ถํ๋ค.
    response.on('end', () => {
      if(httpStatus === 200) {
        callback(null, body);
      } else {
        callback(httpStatus, null);
      }
    });
  });
  
  // ์ ์์ค ๋คํธ์ํฌ ์๋ฌ๋ฅผ ์ฒ๋ฆฌํ  ์ด๋ฒคํธ ํธ๋ค๋ฌ๋ ๋ฑ๋กํ๋ค.
  request.on('error', (err) => {
    callback(err, null);
  })
}
```

## ๐ ์ฝ๋ฐฑ์ง์ฅ ์์ 

{% hint style="info" %}
์ฝ๋ฐฑ์ ์ฌ๋ฌ๋ฒ ์ค์ฒฉํด์ ์ฌ์ฉํ๋ฉด ๊ฐ๋์ฑ, ๋ฌธ์ ๋ถ์, ์ ์ง๋ณด์, ์์  ๋ฑ์ด ์ด๋ ค์์ง๋ค.
{% endhint %}

```js
class UserStorage {
  loginUser(id, password, onSuccess, onError){
    setTimeout(() => {
      if(
        (id === 'ellie' && password === 'dream') ||
        (id === 'coder' && password === 'academy')
      ){
        onSuccess(id)
      } else{
        onError(new Error('not found'))
      }
    }, 2000)
  }
  
  getRoles(user, onSuccess, onError){
    setTimeout(() => { 
      if(user === 'ellie'){
        onSuccess({name: 'ellie', role: 'admin'})
      } else{
        onError(new Error('no access'))
      }
    }, 1000)
    
  }
}

const userStorage = new UserStorage();
const id = prompt('id๋ฅผ ์๋ ฅํ์ธ์.');
const password = prompt('password๋ฅผ ์๋ ฅํ์ธ์.');

userStorage.loginUser(id, password, (user) => {
  id,
  password,
  user => {
    userStorage.getRolse(
      user,
      userWithRole => {
        alert(`Hello ${userWithRole.name}, you hava a ${userWithRole.role} role`)
      },
      error => {}
    )
  },
  error => {
    console.log(error)
  }
})
```

## ๐ ์ฝ๋ฐฑ์ง์ฅ โ ํ๋ก๋ฏธ์ค

```js
class UserStorage {
  return new Promise((resoleve, reject) => {
  setTimeout(() => {
      if(
        (id === 'ellie' && password === 'dream') ||
        (id === 'coder' && password === 'academy')
      ){
        resolve(id)
      } else{
        reject(new Error('not found'))
      }
    }, 2000)
  })
}
  
getRoles(user){
  return new Promise((resolve, reject) => {
   setTimeout(() => { 
      if(user === 'ellie'){
        resolve({name: 'ellie', role: 'admin'})
      } else{
        reject(new Error('no access'))
      }
    }, 1000)
   })
  }
}

const userStorage = new UserStorage();
const id = prompt('id๋ฅผ ์๋ ฅํ์ธ์.');
const password = prompt('password๋ฅผ ์๋ ฅํ์ธ์.');

userStorage
  .loginUser(id, password)
  .then(userStorage.getRoles)
  .then(user => alert(`Hello ${userWithRole.name}, you hava a ${userWithRole.role} role`))
  .catch(console.log)
```
