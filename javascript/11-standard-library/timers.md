# Timers

## π νμ΄λ¨Έ ν¨μ

* `setTimeout(ν¨μ, μκ°)` : μΌμ  μκ° ν ν¨μ μ€ν
* `setInterval(ν¨μ, μκ°)` : μκ° κ°κ²©λ§λ€ ν¨μ μ€ν
* `clearTimeout()` : μ€μ λ timeout ν¨μλ₯Ό μ’λ£
* `clearInterval()` : μ€μ λ interval ν¨μλ₯Ό μ’λ£

```js
const timer = setTimeout (() => {
 console.log ('Heropy');
}, 3000) // 3μ΄ λ€ μ½μ μ€ν

const h1El = document.querySelector('h1');
h1El.addEventListener('click', () => {
 clearTimeout(timer); // h1μ ν΄λ¦­νλ©΄ νμμμ μ’λ£
})
```
