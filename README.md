# JS_CallBacks
Опа, вот мы и добрались до JavaScript callbacks — тема, которую все новички сначала недолюбливают, а потом обнимают, как старого друга 😄

### Что такое **callback** в JavaScript?
Callback — это **функция**, которая **передаётся как аргумент** другой функции и **выполняется позже**, после завершения какой-то операции.

То есть это как:  
> "Эй, функция А, когда закончишь своё дело — вызови функцию B, пожалуйста!"

### Простой пример:
```javascript
function greeting(name) {
  console.log(`Привет, ${name}!`);
}

function processUserInput(callback) {
  const name = "Иван";
  callback(name);
}

processUserInput(greeting);
```

👉 Здесь `greeting` — это **callback-функция**, которую мы передали в `processUserInput`.

---

### Зачем они вообще нужны?
Callbacks часто используются:
- при **работе с асинхронным кодом** (например, с задержками, запросами к серверу и т.д.),
- для **управления порядком выполнения функций**,
- в **обработчиках событий** (например, `button.onclick = callback`).

Пример с задержкой:
```javascript
setTimeout(function () {
  console.log("Прошло 2 секунды!");
}, 2000);
```

👆 Вот это тоже **callback**, который сработает через 2 секунды.

---

### Но! Есть подвох — **callback hell**:
Когда ты начинаешь вкладывать один callback в другой, и ещё один… и ещё… и получается такой лес кода, из которого сложно выбраться 🌲🌲🌲

Пример:
```javascript
doSomething(function(result1) {
  doSomethingElse(result1, function(result2) {
    doAnotherThing(result2, function(result3) {
      // и так далее...
    });
  });
});
```

🙈 Кошмар, да?

### Но не волнуйся! 🙌  
В будущем ты познакомишься с **Promises** и **async/await** — они пришли, чтобы сделать твою жизнь легче. Но начать нужно именно с **callbacks**, чтобы понимать, откуда всё это вообще взялось.

Хочешь — покажу тебе, как из callback сделать promise или как превратить адский вложенный код в красивый `async/await`? Или хочешь больше примеров с callback'ами? Скажи только слово! 💪😄
Ооо, **array callbacks** — это уже следующий уровень, и он прямо 🔥! Сейчас покажу, и тебе это понравится.

Когда говорят "array callbacks", обычно имеют в виду **методы массивов**, которые принимают **callback-функции**. Именно благодаря этому JavaScript становится таким выразительным и удобным.

Давай разберёмся, что это за методы и как они работают.

---

### 🔥 Топовые методы массивов с callbacks:

#### 1. **`.forEach()`** — просто пробежаться по каждому элементу
```javascript
const fruits = ['apple', 'banana', 'cherry'];

fruits.forEach(function(fruit, index) {
  console.log(`${index}: ${fruit}`);
});
```
➡ Callback принимает: `элемент`, `индекс`, `весь массив`.

---

#### 2. **`.map()`** — создать новый массив, преобразовав элементы
```javascript
const numbers = [1, 2, 3];

const doubled = numbers.map(function(num) {
  return num * 2;
});

console.log(doubled); // [2, 4, 6]
```
➡ Возвращает **новый массив**, ничего не меняя в старом — как настоящий джентльмен 🎩

---

#### 3. **`.filter()`** — отфильтровать элементы
```javascript
const numbers = [1, 2, 3, 4, 5];

const even = numbers.filter(function(num) {
  return num % 2 === 0;
});

console.log(even); // [2, 4]
```
➡ Возвращает **новый массив только с теми**, кто прошёл отбор (как на кастинге в Голливуде 😄).

---

#### 4. **`.reduce()`** — собрать всё в один результат
```javascript
const numbers = [1, 2, 3, 4];

const sum = numbers.reduce(function(total, current) {
  return total + current;
}, 0);

console.log(sum); // 10
```
➡ Это как снежный ком: берёт предыдущее значение (аккумулятор) и добавляет к нему новое.

---

#### 5. **`.find()`** — найти **первый подходящий элемент**
```javascript
const users = [
  { id: 1, name: 'Alice' },
  { id: 2, name: 'Bob' }
];

const user = users.find(function(u) {
  return u.id === 2;
});

console.log(user); // { id: 2, name: 'Bob' }
```

---

#### 6. **`.some()` и `.every()`**
- `.some()` — хотя бы один элемент проходит проверку?
- `.every()` — все проходят проверку?

```javascript
const scores = [80, 90, 100];

console.log(scores.some(score => score > 95)); // true
console.log(scores.every(score => score >= 80)); // true
```

---

### Всё это — **array callbacks** в действии 💥  
Ты передаёшь функцию, и массив говорит: "Окей, я вызову её для каждого своего элемента, без проблем!"

Хочешь, я тебе составлю мини-шпаргалку по этим методам? Или задачки на прокачку? 😉
