Конечно! Давайте рассмотрим основы синтаксиса JavaScript, включая переменные, типы данных, операторы и управляющие конструкции.

### 1. **Переменные**
В JavaScript можно объявлять переменные с помощью ключевых слов `var`, `let` и `const`.

- **`var`**: используется для объявления переменных, которые могут быть переопределены. Имеет функциональную или глобальную область видимости.
  
  ```javascript
  var name = "John";
  ```

- **`let`**: используется для объявления переменных с блочной областью видимости. Можно переопределять.
  
  ```javascript
  let age = 25;
  ```

- **`const`**: используется для объявления констант, которые не могут быть переопределены. Также имеет блочную область видимости.
  
  ```javascript
  const pi = 3.14;
  ```

### 2. **Типы данных**
JavaScript имеет несколько основных типов данных:

- **Примитивные типы**:
  - **String**: строки текста.
    ```javascript
    let greeting = "Hello, World!";
    ```
  - **Number**: числовые значения (целые и дробные).
    ```javascript
    let score = 95.5;
    ```
  - **Boolean**: логические значения `true` или `false`.
    ```javascript
    let isActive = true;
    ```
  - **Null**: специальный тип, представляющий отсутствие значения.
    ```javascript
    let emptyValue = null;
    ```
  - **Undefined**: переменная, которая была объявлена, но не инициализирована.
    ```javascript
    let notAssigned;
    ```
  - **Symbol**: уникальные и неизменяемые значения, используемые в качестве идентификаторов.
  
- **Сложные типы**:
  - **Object**: коллекция свойств и значений.
    ```javascript
    let person = {
      name: "Alice",
      age: 30
    };
    ```
  - **Array**: упорядоченная коллекция значений.
    ```javascript
    let colors = ["red", "green", "blue"];
    ```

### 3. **Операторы**
JavaScript поддерживает различные операторы:

- **Арифметические операторы**:
  - `+` (сложение)
  - `-` (вычитание)
  - `*` (умножение)
  - `/` (деление)
  - `%` (остаток от деления)

  ```javascript
  let sum = 5 + 10; // 15
  ```

- **Сравнительные операторы**:
  - `==` (равенство)
  - `===` (строгое равенство)
  - `!=` (неравенство)
  - `!==` (строгое неравенство)
  - `>` (больше)
  - `<` (меньше)
  - `>=` (больше или равно)
  - `<=` (меньше или равно)

  ```javascript
  let isEqual = (5 === 5); // true
  ```

- **Логические операторы**:
  - `&&` (логическое И)
  - `||` (логическое ИЛИ)
  - `!` (логическое НЕ)

  ```javascript
  let isTrue = (true && false); // false
  ```

### 4. **Управляющие конструкции**
JavaScript поддерживает различные управляющие конструкции:

- **Условные операторы**:
  
  ```javascript
  let score = 85;
  
  if (score >= 90) {
      console.log("Отлично!");
  } else if (score >= 75) {
      console.log("Хорошо!");
  } else {
      console.log("Нужно подтянуться!");
  }
  ```

- **Циклы**:
  - **`for`**:
  
    ```javascript
    for (let i = 0; i < 5; i++) {
        console.log(i); // 0, 1, 2, 3, 4
    }
    ```

  - **`while`**:
  
    ```javascript
    let count = 0;
    while (count < 5) {
        console.log(count);
        count++;
    }
    ```

  - **`do...while`**:
  
    ```javascript
    let number = 0;
    do {
        console.log(number);
        number++;
    } while (number < 5);
    ```


### 5. **Комментарии**
Комментарии помогают документировать код и делают его более читаемым. В JavaScript есть два типа комментариев:

- **Однострочные комментарии**: начинаются с `//`. Все, что находится после `//`, игнорируется интерпретатором.
  
  ```javascript
  // Это однострочный комментарий
  let x = 10; // Переменная x равна 10
  ```

- **Многострочные комментарии**: заключаются между `/*` и `*/`. Они могут занимать несколько строк.
  
  ```javascript
  /*
  Это многострочный комментарий.
  Он может занимать несколько строк.
  */
  let y = 20;
  ```

### 6. **Функции**
Функции позволяют группировать код и повторно использовать его. В JavaScript есть несколько способов определения функций:

- **Функция-объявление**:
  
  ```javascript
  function greet(name) {
      return "Привет, " + name + "!";
  }
  
  console.log(greet("Алекс")); // Привет, Алекс!
  ```

- **Функция-выражение**:
  
  ```javascript
  const add = function(a, b) {
      return a + b;
  };
  
  console.log(add(5, 3)); // 8
  ```

- **Стрелочные функции** (ES6):
  
  ```javascript
  const multiply = (a, b) => a * b;
  
  console.log(multiply(4, 2)); // 8
  ```

### 7. **Объекты**
Объекты - это коллекции пар "ключ-значение". Они позволяют организовывать данные и функции.

- **Создание объекта**:
  
  ```javascript
  const car = {
      make: "Toyota",
      model: "Camry",
      year: 2020,
      start: function() {
          console.log("Машина заведена!");
      }
  };
  
  console.log(car.make); // Toyota
  car.start(); // Машина заведена!
  ```

### 8. **Массивы**
Массивы - это упорядоченные коллекции элементов. Они могут содержать любые типы данных.

- **Создание массива**:
  
  ```javascript
  const fruits = ["яблоко", "банан", "апельсин"];
  
  console.log(fruits[0]); // яблоко
  ```

- **Методы массивов**:
  
  ```javascript
  fruits.push("груша"); // Добавляет элемент в конец массива
  console.log(fruits.length); // 4
  ```

### 9. **Циклы по массивам**
JavaScript предоставляет несколько способов перебора массивов.

- **Цикл `for`**:
  
  ```javascript
  for (let i = 0; i < fruits.length; i++) {
      console.log(fruits[i]);
  }
  ```

- **Метод `forEach`**:
  
  ```javascript
  fruits.forEach(function(fruit) {
      console.log(fruit);
  });
  ```

### 10. **Управляющие конструкции**
JavaScript также поддерживает более сложные управляющие конструкции, такие как `switch`:

- **`switch`**:
  
  ```javascript
  const day = 2;
  
  switch (day) {
      case 1:
          console.log("Понедельник");
          break;
      case 2:
          console.log("Вторник");
          break;
      case 3:
          console.log("Среда");
          break;
      default:
          console.log("Неизвестный день");
  }
  ```

### 11. **Обработка ошибок**
JavaScript предоставляет механизм для обработки ошибок с помощью конструкции `try...catch`.

```javascript
try {
    let result = riskyFunction(); // Функция, которая может вызвать ошибку
} catch (error) {
    console.error("Произошла ошибка:", error);
}
```

### 12. **Шаблонные строки**
Шаблонные строки (ES6) позволяют удобно работать со строками и вставлять переменные с помощью обратных кавычек (`` ` ``).

```javascript
const name = "Иван";
const message = `Привет, ${name}!`;
console.log(message); // Привет, Иван!
```


### 13. **Модули (продолжение)**

- **Экспорт**:
  
  В файле модуля вы можете экспортировать переменные, функции или классы, чтобы они были доступны в других модулях.

  ```javascript
  // myModule.js
  export const pi = 3.14;

  export function add(a, b) {
      return a + b;
  }
  ```

- **Импорт**:
  
  В другом файле вы можете импортировать экспортированные элементы.

  ```javascript
  // main.js
  import { pi, add } from './myModule.js';

  console.log(pi); // 3.14
  console.log(add(5, 3)); // 8
  ```

### 14. **Асинхронное программирование**

JavaScript поддерживает асинхронное программирование, что позволяет выполнять операции, такие как запросы к серверу, без блокировки основного потока.

- **Обещания (Promises)**:
  
  Обещания представляют собой объект, который может находиться в одном из трех состояний: ожидание (pending), выполнено (fulfilled) или отклонено (rejected).

  ```javascript
  const fetchData = new Promise((resolve, reject) => {
      setTimeout(() => {
          const data = { name: "Алекс", age: 30 };
          resolve(data); // Успешное выполнение
      }, 2000);
  });

  fetchData
      .then(data => console.log(data)) // { name: "Алекс", age: 30 }
      .catch(error => console.error("Ошибка:", error));
  ```

- **Асинхронные функции (async/await)**:
  
  Асинхронные функции позволяют использовать синтаксис, похожий на синхронный код.

  ```javascript
  async function getData() {
      try {
          const data = await fetchData; // Ожидание выполнения обещания
          console.log(data);
      } catch (error) {
          console.error("Ошибка:", error);
      }
  }

  getData(); // { name: "Алекс", age: 30 }
  ```

### 15. **Объект `this`**

Ключевое слово `this` ссылается на контекст выполнения функции. Его значение может изменяться в зависимости от того, как вызывается функция.

- **В глобальной области**:
  
  ```javascript
  console.log(this); // В браузере: window
  ```

- **В методе объекта**:
  
  ```javascript
  const person = {
      name: "Иван",
      greet: function() {
          console.log("Привет, " + this.name);
      }
  };
  
  person.greet(); // Привет, Иван
  ```

- **В стрелочной функции**:
  
  Стрелочные функции не имеют собственного контекста `this`, они наследуют его от родительской функции.

  ```javascript
  const person = {
      name: "Иван",
      greet: function() {
          const inner = () => {
              console.log("Привет, " + this.name);
          };
          inner();
      }
  };
  
  person.greet(); // Привет, Иван
  ```

### 16. **События**

JavaScript позволяет взаимодействовать с пользователем через события, такие как клики, наведение мыши и нажатия клавиш.

- **Добавление обработчиков событий**:

  ```javascript
  const button = document.getElementById("myButton");
  
  button.addEventListener("click", function() {
      alert("Кнопка нажата!");
  });
  ```

### 17. **DOM (Document Object Model)**

JavaScript позволяет взаимодействовать с HTML-документом через объектную модель документа (DOM).

- **Изменение содержимого элемента**:

  ```javascript
  const heading = document.getElementById("myHeading");
  heading.textContent = "Новый заголовок!";
  ```

- **Создание и добавление новых элементов**:

  ```javascript
  const newElement = document.createElement("p");
  newElement.textContent = "Это новый параграф.";
  document.body.appendChild(newElement);
  ```

Конечно! Давайте продолжим с работы с JSON и другими аспектами JavaScript.

### 18. **JSON (продолжение)**

- **Преобразование объекта в JSON**:

  ```javascript
  const person = {
      name: "Иван",
      age: 30
  };
  
  const jsonString = JSON.stringify(person);
  console.log(jsonString); // {"name":"Иван","age":30}
  ```

- **Преобразование JSON в объект**:

  ```javascript
  const jsonString = '{"name":"Иван","age":30}';
  const parsedObject = JSON.parse(jsonString);
  console.log(parsedObject.name); // Иван
  ```

### 19. **Работа с локальным хранилищем (Local Storage)**

Local Storage позволяет сохранять данные в браузере, которые могут быть доступны даже после перезагрузки страницы.

- **Сохранение данных**:

  ```javascript
  localStorage.setItem("username", "Иван");
  ```

- **Получение данных**:

  ```javascript
  const username = localStorage.getItem("username");
  console.log(username); // Иван
  ```

- **Удаление данных**:

  ```javascript
  localStorage.removeItem("username");
  ```

### 20. **Fetch API**

Fetch API предоставляет интерфейс для работы с HTTP-запросами. Он позволяет выполнять асинхронные запросы к серверу.

- **Пример использования Fetch**:

  ```javascript
  fetch('https://api.example.com/data')
      .then(response => {
          if (!response.ok) {
              throw new Error('Сеть не в порядке!');
          }
          return response.json();
      })
      .then(data => console.log(data))
      .catch(error => console.error('Ошибка:', error));
  ```

### 21. **Классы и наследование**

JavaScript поддерживает объектно-ориентированное программирование с использованием классов.

- **Определение класса**:

  ```javascript
  class Animal {
      constructor(name) {
          this.name = name;
      }
      
      speak() {
          console.log(`${this.name} издает звук.`);
      }
  }
  
  const dog = new Animal("Собака");
  dog.speak(); // Собака издает звук.
  ```

- **Наследование**:

  ```javascript
  class Dog extends Animal {
      speak() {
          console.log(`${this.name} гавкает.`);
      }
  }
  
  const myDog = new Dog("Бобик");
  myDog.speak(); // Бобик гавкает.
  ```

### 22. **Модули ES6**

С помощью ES6 можно разделять код на модули, что упрощает организацию и повторное использование кода.

- **Экспорт**:

  ```javascript
  // myModule.js
  export const greet = (name) => `Привет, ${name}!`;
  ```

- **Импорт**:

  ```javascript
  // main.js
  import { greet } from './myModule.js';

  console.log(greet("Иван")); // Привет, Иван!
  ```

### 23. **Тестирование**

JavaScript поддерживает различные фреймворки для тестирования, такие как Jest и Mocha. Тестирование помогает убедиться, что ваш код работает правильно.

- **Пример простого теста с использованием Jest**:

  ```javascript
  function sum(a, b) {
      return a + b;
  }

  test('Сложение 1 + 2 равно 3', () => {
      expect(sum(1, 2)).toBe(3);
  });
  ```

### 24. **Советы по производительности**

- **Избегайте глобальных переменных**: Они могут привести к конфликтам и ухудшению производительности.
- **Используйте делегирование событий**: Это позволяет уменьшить количество обработчиков событий, улучшая производительность.
- **Оптимизируйте работу с DOM**: Минимизируйте количество операций с DOM, так как они могут быть медленными.

### 25. **Заключение**

JavaScript — это мощный язык программирования, который используется для создания интерактивных веб-приложений. Он поддерживает объектно-ориентированное программирование, асинхронное выполнение, работу с API и многое другое. Понимание основных концепций JavaScript поможет вам стать успешным разработчиком и создавать качественные веб-приложения.

Есть множество других аспектов и возможностей JavaScript, которые могут быть интересны. Давайте рассмотрим некоторые из них:

### 26. **Обработка ошибок**

JavaScript предоставляет механизмы для обработки ошибок, что позволяет избежать сбоев в работе приложения.

- **Использование `try...catch`**:

  ```javascript
  try {
      // Код, который может вызвать ошибку
      let result = riskyFunction();
  } catch (error) {
      console.error("Произошла ошибка:", error);
  } finally {
      console.log("Этот код выполнится в любом случае.");
  }
  ```

### 27. **Регулярные выражения**

Регулярные выражения позволяют выполнять сложные операции поиска и замены строк.

- **Пример использования регулярных выражений**:

  ```javascript
  const regex = /ab+c/; // Находит строки, содержащие "a", затем одну или более "b", затем "c"
  console.log(regex.test("abc")); // true
  console.log(regex.test("ac")); // false
  ```

### 28. **Объекты и массивы**

Объекты и массивы — это основные структуры данных в JavaScript.

- **Создание объекта**:

  ```javascript
  const person = {
      name: "Иван",
      age: 30,
      greet() {
          console.log(`Привет, я ${this.name}`);
      }
  };
  
  person.greet(); // Привет, я Иван
  ```

- **Создание массива**:

  ```javascript
  const fruits = ["яблоко", "банан", "апельсин"];
  console.log(fruits[1]); // банан
  ```

### 29. **Методы массивов**

JavaScript предоставляет множество встроенных методов для работы с массивами.

- **`map`, `filter`, `reduce`**:

  ```javascript
  const numbers = [1, 2, 3, 4, 5];

  const doubled = numbers.map(num => num * 2); // [2, 4, 6, 8, 10]
  const evens = numbers.filter(num => num % 2 === 0); // [2, 4]
  const sum = numbers.reduce((acc, num) => acc + num, 0); // 15
  ```

### 30. **Замыкания**

Замыкания позволяют создавать функции с доступом к переменным из внешней функции, даже после ее завершения.

- **Пример замыкания**:

  ```javascript
  function makeCounter() {
      let count = 0;
      return function() {
          count += 1;
          return count;
      };
  }

  const counter = makeCounter();
  console.log(counter()); // 1
  console.log(counter()); // 2
  ```

### 31. **Декораторы и функции высшего порядка**

JavaScript поддерживает функции высшего порядка, которые могут принимать другие функции в качестве аргументов или возвращать их.

- **Пример функции высшего порядка**:

  ```javascript
  function greet(name) {
      return function() {
          console.log(`Привет, ${name}!`);
      };
  }

  const greetIvan = greet("Иван");
  greetIvan(); // Привет, Иван!
  ```

### 32. **Событийный цикл и асинхронность**

JavaScript использует событийный цикл для обработки асинхронных операций, таких как запросы к серверу или таймеры.

- **Пример работы с таймерами**:

  ```javascript
  console.log("Начало");

  setTimeout(() => {
      console.log("Это сообщение появится позже");
  }, 2000);

  console.log("Конец");
  ```

### 33. **Web APIs**

JavaScript предоставляет доступ к различным Web API, которые позволяют взаимодействовать с браузером и его функциональностью, например, работа с геолокацией, локальным хранилищем, анимацией и многим другим.

- **Пример использования Geolocation API**:

  ```javascript
  if ("geolocation" in navigator) {
      navigator.geolocation.getCurrentPosition(position => {
          console.log(`Широта: ${position.coords.latitude}, Долгота: ${position.coords.longitude}`);
      });
  } else {
      console.log("Геолокация не поддерживается этим браузером.");
  }
  ```


### 34. **Фреймворки и библиотеки (продолжение)**

- **Angular**: Полноценный фреймворк для создания веб-приложений, который предлагает мощные инструменты для разработки, такие как двухсторонняя привязка данных, маршрутизация и управление состоянием.
  
- **jQuery**: Библиотека, которая упрощает работу с DOM, обработку событий и AJAX-запросы. Хотя её популярность снизилась с появлением современных фреймворков, она все еще используется в некоторых проектах.

- **D3.js**: Библиотека для визуализации данных с использованием HTML, SVG и CSS. Она позволяет создавать динамичные и интерактивные графики.

### 35. **Состояние приложения**

Современные приложения часто требуют управления состоянием. Для этого используются различные библиотеки и подходы:

- **Redux**: Широко используемая библиотека для управления состоянием в приложениях, основанных на React. Она предоставляет единую хранилище состояния и предсказуемый способ изменения состояния через действия.

- **MobX**: Альтернатива Redux, которая использует реактивное программирование для управления состоянием. MobX позволяет более просто управлять состоянием и реакцией на изменения.

### 36. **Тестирование JavaScript**

Тестирование — важная часть разработки, которая помогает поддерживать качество кода. Вот некоторые популярные инструменты:

- **Jest**: Фреймворк для тестирования, который позволяет писать юнит-тесты и интеграционные тесты. Он поддерживает мокирование и имеет встроенную поддержку для тестирования React-приложений.

- **Mocha**: Гибкий фреймворк для тестирования, который позволяет использовать различные библиотеки для утверждений, такие как Chai.

- **Cypress**: Инструмент для тестирования, который позволяет проводить end-to-end тестирование веб-приложений с удобным интерфейсом.

### 37. **Оптимизация производительности**

Оптимизация производительности вашего приложения важна для обеспечения быстрого отклика и хорошего пользовательского опыта. Вот несколько советов:

- **Минификация и сжатие**: Используйте инструменты, такие как Webpack или Gulp, для минификации JavaScript и CSS файлов, чтобы уменьшить их размер и ускорить загрузку.

- **Ленивая загрузка**: Загружайте ресурсы только тогда, когда они действительно нужны, например, изображения и компоненты. Это помогает уменьшить время загрузки страницы.

- **Кэширование**: Используйте кэширование на стороне клиента и сервера для уменьшения числа запросов к серверу.

### 38. **Безопасность**

Безопасность веб-приложений — важный аспект, который нельзя игнорировать. Вот несколько рекомендаций:

- **Защита от XSS (Cross-Site Scripting)**: Используйте механизмы экранирования и валидации пользовательского ввода, чтобы избежать внедрения вредоносного кода.

- **Защита от CSRF (Cross-Site Request Forgery)**: Используйте токены CSRF для защиты от подделки запросов.

- **HTTPS**: Всегда используйте HTTPS для защиты данных, передаваемых между клиентом и сервером.

### 39. **Прогрессивные веб-приложения (PWA)**

PWA — это веб-приложения, которые используют современные технологии для обеспечения функциональности, схожей с нативными приложениями. Они могут работать офлайн, отправлять уведомления и быть установлены на устройствах.

- **Ключевые особенности PWA**:
  - **Манифест**: Файл, который определяет, как приложение будет выглядеть и как оно будет вести себя на устройстве.
  - **Сервис-воркеры**: Скрипты, которые работают в фоновом режиме и позволяют кэшировать ресурсы для работы в офлайн-режиме.

### 40. **Заключение**

JavaScript — это мощный и гибкий язык программирования, который продолжает развиваться. С его помощью можно создавать интерактивные веб-приложения, работать с серверной частью (Node.js), а также разрабатывать мобильные и настольные приложения. Понимание современных инструментов и подходов поможет вам стать успешным разработчиком.
# 🎯 Специальные возможности JavaScript: Drag & Drop и другие интерактивные функции

## 1. Drag & Drop (Перетаскивание)

### 1.1. Нативный Drag & Drop API

```javascript
// Базовый пример с нативным Drag & Drop
class DraggablePost {
    constructor(element) {
        this.element = element;
        this.init();
    }
    
    init() {
        // Делаем элемент перетаскиваемым
        this.element.setAttribute('draggable', 'true');
        
        // Обработчики событий
        this.element.addEventListener('dragstart', this.handleDragStart.bind(this));
        this.element.addEventListener('dragend', this.handleDragEnd.bind(this));
        this.element.addEventListener('dragenter', this.handleDragEnter.bind(this));
        this.element.addEventListener('dragleave', this.handleDragLeave.bind(this));
        this.element.addEventListener('dragover', this.handleDragOver.bind(this));
        this.element.addEventListener('drop', this.handleDrop.bind(this));
    }
    
    handleDragStart(event) {
        // Сохраняем данные о перетаскиваемом элементе
        event.dataTransfer.setData('text/plain', this.element.id);
        event.dataTransfer.effectAllowed = 'move';
        
        // Создаем кастомное изображение для drag
        const dragImage = this.element.cloneNode(true);
        dragImage.style.position = 'absolute';
        dragImage.style.top = '-1000px';
        document.body.appendChild(dragImage);
        event.dataTransfer.setDragImage(dragImage, 0, 0);
        
        // Добавляем класс для визуального эффекта
        this.element.classList.add('dragging');
        
        // Удаляем временное изображение после начала drag
        setTimeout(() => document.body.removeChild(dragImage), 0);
    }
    
    handleDragEnd(event) {
        this.element.classList.remove('dragging');
        this.element.classList.remove('drag-over');
        
        // Очищаем данные
        event.dataTransfer.clearData();
    }
    
    handleDragEnter(event) {
        event.preventDefault();
        this.element.classList.add('drag-over');
    }
    
    handleDragLeave(event) {
        this.element.classList.remove('drag-over');
    }
    
    handleDragOver(event) {
        event.preventDefault();
        event.dataTransfer.dropEffect = 'move';
    }
    
    handleDrop(event) {
        event.preventDefault();
        this.element.classList.remove('drag-over');
        
        const draggedId = event.dataTransfer.getData('text/plain');
        const draggedElement = document.getElementById(draggedId);
        
        if (draggedElement && draggedElement !== this.element) {
            // Меняем элементы местами
            const parent = this.element.parentNode;
            const draggedIndex = Array.from(parent.children).indexOf(draggedElement);
            const targetIndex = Array.from(parent.children).indexOf(this.element);
            
            if (draggedIndex < targetIndex) {
                parent.insertBefore(draggedElement, this.element.nextSibling);
            } else {
                parent.insertBefore(draggedElement, this.element);
            }
        }
    }
}
```

### 1.2. Кастомная реализация Drag & Drop (без нативного API)

```javascript
class CustomDragDrop {
    constructor(container) {
        this.container = container;
        this.draggedItem = null;
        this.dragOverItem = null;
        this.dragOffset = { x: 0, y: 0 };
        this.isDragging = false;
        
        this.init();
    }
    
    init() {
        // Используем mouse события для кастомного drag & drop
        this.container.addEventListener('mousedown', this.onMouseDown.bind(this));
        document.addEventListener('mousemove', this.onMouseMove.bind(this));
        document.addEventListener('mouseup', this.onMouseUp.bind(this));
    }
    
    onMouseDown(event) {
        // Находим элемент поста
        const postElement = event.target.closest('.post');
        if (!postElement) return;
        
        event.preventDefault();
        
        this.draggedItem = postElement;
        this.isDragging = true;
        
        // Вычисляем смещение от курсора до края элемента
        const rect = this.draggedItem.getBoundingClientRect();
        this.dragOffset = {
            x: event.clientX - rect.left,
            y: event.clientY - rect.top
        };
        
        // Создаем клон для перетаскивания
        this.clone = this.draggedItem.cloneNode(true);
        this.clone.style.position = 'fixed';
        this.clone.style.left = `${rect.left}px`;
        this.clone.style.top = `${rect.top}px`;
        this.clone.style.width = `${rect.width}px`;
        this.clone.style.opacity = '0.8';
        this.clone.style.pointerEvents = 'none';
        this.clone.style.zIndex = '1000';
        this.clone.classList.add('dragging-clone');
        
        document.body.appendChild(this.clone);
        
        // Скрываем оригинал
        this.draggedItem.style.opacity = '0.4';
        
        // Добавляем класс для курсора
        document.body.style.cursor = 'grabbing';
    }
    
    onMouseMove(event) {
        if (!this.isDragging) return;
        
        // Перемещаем клон
        if (this.clone) {
            this.clone.style.left = `${event.clientX - this.dragOffset.x}px`;
            this.clone.style.top = `${event.clientY - this.dragOffset.y}px`;
        }
        
        // Находим элемент под курсором
        const elementBelow = document.elementsFromPoint(event.clientX, event.clientY);
        const dropTarget = elementBelow.find(el => el.classList && el.classList.contains('post') && el !== this.draggedItem);
        
        // Убираем подсветку с предыдущего
        if (this.dragOverItem) {
            this.dragOverItem.classList.remove('drag-over');
        }
        
        // Подсвечиваем новый
        if (dropTarget) {
            this.dragOverItem = dropTarget;
            this.dragOverItem.classList.add('drag-over');
        } else {
            this.dragOverItem = null;
        }
    }
    
    onMouseUp(event) {
        if (!this.isDragging) return;
        
        // Удаляем клон
        if (this.clone) {
            this.clone.remove();
        }
        
        // Восстанавливаем оригинал
        if (this.draggedItem) {
            this.draggedItem.style.opacity = '1';
            this.draggedItem.classList.remove('dragging');
            
            // Если есть цель для drop
            if (this.dragOverItem) {
                this.swapItems(this.draggedItem, this.dragOverItem);
                this.dragOverItem.classList.remove('drag-over');
            }
        }
        
        // Сбрасываем состояние
        this.isDragging = false;
        this.draggedItem = null;
        this.dragOverItem = null;
        document.body.style.cursor = '';
    }
    
    swapItems(item1, item2) {
        const parent = this.container;
        const index1 = Array.from(parent.children).indexOf(item1);
        const index2 = Array.from(parent.children).indexOf(item2);
        
        if (index1 < index2) {
            parent.insertBefore(item1, item2.nextSibling);
        } else {
            parent.insertBefore(item1, item2);
        }
        
        // Диспатчим событие изменения порядка
        const event = new CustomEvent('orderChanged', {
            detail: { from: index1, to: index2 }
        });
        this.container.dispatchEvent(event);
    }
}
```

### 1.3. Drag & Drop для загрузки файлов

```javascript
class FileDragDropZone {
    constructor(element, options = {}) {
        this.element = element;
        this.onDrop = options.onDrop || (() => {});
        this.onDragOver = options.onDragOver || (() => {});
        this.allowedTypes = options.allowedTypes || ['image/*', 'video/*'];
        
        this.init();
    }
    
    init() {
        // Предотвращаем стандартное поведение браузера
        ['dragenter', 'dragover', 'dragleave', 'drop'].forEach(eventName => {
            this.element.addEventListener(eventName, this.preventDefaults.bind(this));
        });
        
        // Подсветка при перетаскивании
        this.element.addEventListener('dragenter', this.highlight.bind(this));
        this.element.addEventListener('dragleave', this.unhighlight.bind(this));
        this.element.addEventListener('drop', this.handleDrop.bind(this));
        
        // Клик для выбора файлов
        this.element.addEventListener('click', () => {
            this.createFileInput();
        });
    }
    
    preventDefaults(event) {
        event.preventDefault();
        event.stopPropagation();
    }
    
    highlight() {
        this.element.classList.add('drag-over');
    }
    
    unhighlight() {
        this.element.classList.remove('drag-over');
    }
    
    handleDrop(event) {
        this.unhighlight();
        
        const files = Array.from(event.dataTransfer.files);
        const validFiles = this.validateFiles(files);
        
        if (validFiles.length > 0) {
            this.onDrop(validFiles);
        }
    }
    
    validateFiles(files) {
        return files.filter(file => {
            return this.allowedTypes.some(type => {
                if (type.endsWith('/*')) {
                    const baseType = type.slice(0, -2);
                    return file.type.startsWith(baseType);
                }
                return file.type === type;
            });
        });
    }
    
    createFileInput() {
        const input = document.createElement('input');
        input.type = 'file';
        input.multiple = true;
        input.accept = this.allowedTypes.join(',');
        
        input.addEventListener('change', (event) => {
            const files = Array.from(event.target.files);
            const validFiles = this.validateFiles(files);
            if (validFiles.length > 0) {
                this.onDrop(validFiles);
            }
        });
        
        input.click();
    }
}

// Пример использования
const dropZone = new FileDragDropZone(document.getElementById('drop-zone'), {
    allowedTypes: ['image/*', 'video/*', 'application/pdf'],
    onDrop: (files) => {
        console.log('Загружено файлов:', files.length);
        files.forEach(file => {
            const reader = new FileReader();
            reader.onload = (e) => {
                // Создаем превью
                const preview = document.createElement('img');
                preview.src = e.target.result;
                document.body.appendChild(preview);
            };
            reader.readAsDataURL(file);
        });
    }
});
```

## 2. Clipboard API (Буфер обмена)

```javascript
class ClipboardManager {
    // Копирование текста
    static async copyText(text) {
        try {
            await navigator.clipboard.writeText(text);
            return { success: true, message: 'Текст скопирован' };
        } catch (error) {
            console.error('Ошибка копирования:', error);
            return { success: false, error: error.message };
        }
    }
    
    // Вставка текста
    static async pasteText() {
        try {
            const text = await navigator.clipboard.readText();
            return { success: true, text };
        } catch (error) {
            console.error('Ошибка вставки:', error);
            return { success: false, error: error.message };
        }
    }
    
    // Копирование изображения
    static async copyImage(imageElement) {
        try {
            // Создаем canvas и рисуем изображение
            const canvas = document.createElement('canvas');
            canvas.width = imageElement.naturalWidth;
            canvas.height = imageElement.naturalHeight;
            const ctx = canvas.getContext('2d');
            ctx.drawImage(imageElement, 0, 0);
            
            // Конвертируем canvas в blob
            const blob = await new Promise(resolve => canvas.toBlob(resolve));
            
            // Копируем в буфер
            await navigator.clipboard.write([
                new ClipboardItem({
                    [blob.type]: blob
                })
            ]);
            
            return { success: true, message: 'Изображение скопировано' };
        } catch (error) {
            console.error('Ошибка копирования изображения:', error);
            return { success: false, error: error.message };
        }
    }
    
    // Копирование сложных данных
    static async copyComplexData(data) {
        const html = this.formatAsHTML(data);
        const text = this.formatAsText(data);
        
        try {
            await navigator.clipboard.write([
                new ClipboardItem({
                    'text/html': new Blob([html], { type: 'text/html' }),
                    'text/plain': new Blob([text], { type: 'text/plain' })
                })
            ]);
            return { success: true };
        } catch (error) {
            console.error('Ошибка копирования данных:', error);
            return { success: false, error: error.message };
        }
    }
    
    static formatAsHTML(data) {
        return `<div class="copied-data">
            <h3>${data.title}</h3>
            <p>${data.content}</p>
            <time>${new Date().toLocaleString()}</time>
        </div>`;
    }
    
    static formatAsText(data) {
        return `${data.title}\n${data.content}\n${new Date().toLocaleString()}`;
    }
    
    // Обработка события вставки
    static handlePaste(event, callback) {
        event.preventDefault();
        
        const items = event.clipboardData.items;
        
        for (let item of items) {
            if (item.type.indexOf('text') !== -1) {
                item.getAsString(text => {
                    callback({ type: 'text', data: text });
                });
            } else if (item.type.indexOf('image') !== -1) {
                const file = item.getAsFile();
                const reader = new FileReader();
                reader.onload = (e) => {
                    callback({ type: 'image', data: e.target.result });
                };
                reader.readAsDataURL(file);
            }
        }
    }
}

// Пример использования
document.getElementById('copy-btn').addEventListener('click', async () => {
    const result = await ClipboardManager.copyText('Hello World');
    if (result.success) {
        showNotification(result.message);
    }
});

document.addEventListener('paste', (event) => {
    ClipboardManager.handlePaste(event, (data) => {
        console.log('Вставленные данные:', data);
        if (data.type === 'image') {
            // Отображаем вставленное изображение
            const img = document.createElement('img');
            img.src = data.data;
            document.body.appendChild(img);
        }
    });
});
```

## 3. Touch Events (Сенсорные события для мобильных устройств)

```javascript
class TouchGestures {
    constructor(element) {
        this.element = element;
        this.startX = 0;
        this.startY = 0;
        this.currentX = 0;
        this.currentY = 0;
        this.isSwiping = false;
        
        this.init();
    }
    
    init() {
        this.element.addEventListener('touchstart', this.onTouchStart.bind(this));
        this.element.addEventListener('touchmove', this.onTouchMove.bind(this));
        this.element.addEventListener('touchend', this.onTouchEnd.bind(this));
    }
    
    onTouchStart(event) {
        const touch = event.touches[0];
        this.startX = touch.clientX;
        this.startY = touch.clientY;
        this.isSwiping = true;
        
        // Диспатчим событие начала свайпа
        this.dispatchGestureEvent('swipeStart', {
            startX: this.startX,
            startY: this.startY
        });
    }
    
    onTouchMove(event) {
        if (!this.isSwiping) return;
        
        const touch = event.touches[0];
        this.currentX = touch.clientX;
        this.currentY = touch.clientY;
        
        const deltaX = this.currentX - this.startX;
        const deltaY = this.currentY - this.startY;
        
        // Предотвращаем скролл при горизонтальном свайпе
        if (Math.abs(deltaX) > Math.abs(deltaY) && Math.abs(deltaX) > 10) {
            event.preventDefault();
        }
        
        // Обновляем позицию элемента
        this.element.style.transform = `translateX(${deltaX}px)`;
        
        // Меняем прозрачность в зависимости от расстояния
        const opacity = 1 - Math.min(Math.abs(deltaX) / 200, 1);
        this.element.style.opacity = opacity;
        
        this.dispatchGestureEvent('swipeMove', {
            deltaX,
            deltaY,
            progress: Math.min(Math.abs(deltaX) / 200, 1)
        });
    }
    
    onTouchEnd(event) {
        if (!this.isSwiping) return;
        
        const deltaX = this.currentX - this.startX;
        const threshold = 100; // Минимальное расстояние для свайпа
        
        if (Math.abs(deltaX) > threshold) {
            // Определяем направление свайпа
            const direction = deltaX > 0 ? 'right' : 'left';
            
            this.dispatchGestureEvent('swipe', {
                direction,
                distance: Math.abs(deltaX),
                velocity: this.calculateVelocity()
            });
            
            // Анимация удаления
            this.element.style.transition = 'transform 0.3s ease';
            this.element.style.transform = `translateX(${deltaX > 0 ? '100%' : '-100%'})`;
            
            setTimeout(() => {
                this.element.remove();
            }, 300);
        } else {
            // Возвращаем элемент на место
            this.element.style.transition = 'transform 0.3s ease';
            this.element.style.transform = '';
            this.element.style.opacity = '';
            
            setTimeout(() => {
                this.element.style.transition = '';
            }, 300);
        }
        
        this.isSwiping = false;
        
        this.dispatchGestureEvent('swipeEnd', {
            deltaX,
            threshold
        });
    }
    
    calculateVelocity() {
        // Расчет скорости (упрощенная версия)
        return Math.abs(this.currentX - this.startX) / 100;
    }
    
    dispatchGestureEvent(type, detail) {
        const event = new CustomEvent(type, { detail });
        this.element.dispatchEvent(event);
    }
}

// Пример использования для постов
class SwipeablePost {
    constructor(element) {
        this.element = element;
        this.gestures = new TouchGestures(element);
        
        this.element.addEventListener('swipe', (event) => {
            if (event.detail.direction === 'left') {
                this.archivePost();
            } else if (event.detail.direction === 'right') {
                this.sharePost();
            }
        });
    }
    
    archivePost() {
        console.log('Пост архивирован');
        // Логика архивации
    }
    
    sharePost() {
        console.log('Открыть меню шаринга');
        // Логика шаринга
    }
}
```

## 4. Intersection Observer (Отслеживание видимости)

```javascript
class VisibilityTracker {
    constructor(options = {}) {
        this.callbacks = new Map();
        this.threshold = options.threshold || 0.5;
        this.rootMargin = options.rootMargin || '0px';
        
        this.observer = new IntersectionObserver(
            this.handleIntersection.bind(this),
            {
                threshold: this.threshold,
                rootMargin: this.rootMargin
            }
        );
    }
    
    observe(element, callback, context = {}) {
        this.callbacks.set(element, { callback, context });
        this.observer.observe(element);
    }
    
    unobserve(element) {
        this.callbacks.delete(element);
        this.observer.unobserve(element);
    }
    
    handleIntersection(entries) {
        entries.forEach(entry => {
            const callbackData = this.callbacks.get(entry.target);
            if (callbackData) {
                callbackData.callback({
                    isIntersecting: entry.isIntersecting,
                    intersectionRatio: entry.intersectionRatio,
                    boundingClientRect: entry.boundingClientRect,
                    target: entry.target,
                    ...callbackData.context
                });
            }
        });
    }
    
    destroy() {
        this.observer.disconnect();
        this.callbacks.clear();
    }
}

// Расширенные возможности Intersection Observer
class AdvancedVisibilityTracker extends VisibilityTracker {
    constructor(options = {}) {
        super(options);
        this.viewedItems = new Set();
    }
    
    // Отслеживание с подсчетом времени просмотра
    observeWithTimer(element, callback, options = {}) {
        let startTime = null;
        let timer = null;
        
        const visibilityCallback = (data) => {
            if (data.isIntersecting) {
                // Элемент стал видимым
                startTime = Date.now();
                
                if (options.onViewStart) {
                    options.onViewStart(data);
                }
                
                // Таймер для длительного просмотра
                if (options.viewDuration) {
                    timer = setTimeout(() => {
                        if (startTime) {
                            const duration = Date.now() - startTime;
                            callback({
                                type: 'duration',
                                duration,
                                element: data.target
                            });
                        }
                    }, options.viewDuration);
                }
            } else {
                // Элемент стал невидимым
                if (startTime) {
                    const viewDuration = Date.now() - startTime;
                    
                    if (viewDuration > 1000) { // Минимальная длительность просмотра
                        callback({
                            type: 'view',
                            duration: viewDuration,
                            element: data.target
                        });
                        
                        // Отмечаем как просмотренный
                        if (options.trackViews && !this.viewedItems.has(data.target)) {
                            this.viewedItems.add(data.target);
                            callback({
                                type: 'firstView',
                                duration: viewDuration,
                                element: data.target
                            });
                        }
                    }
                    
                    startTime = null;
                }
                
                if (timer) {
                    clearTimeout(timer);
                    timer = null;
                }
                
                if (options.onViewEnd) {
                    options.onViewEnd(data);
                }
            }
        };
        
        this.observe(element, visibilityCallback);
    }
}

// Пример использования для постов
const visibilityTracker = new AdvancedVisibilityTracker({
    threshold: 0.5,
    rootMargin: '50px'
});

document.querySelectorAll('.post').forEach(post => {
    visibilityTracker.observeWithTimer(post, (data) => {
        if (data.type === 'firstView') {
            console.log(`Пост просмотрен впервые: ${data.duration}ms`);
            // Отправляем аналитику
            sendAnalytics('post_viewed', {
                postId: post.dataset.id,
                duration: data.duration
            });
        }
    }, {
        viewDuration: 3000, // Считаем просмотром, если пост виден 3+ секунды
        trackViews: true,
        onViewStart: (data) => {
            post.classList.add('visible');
        },
        onViewEnd: (data) => {
            post.classList.remove('visible');
        }
    });
});
```

## 5. Web Workers (Многопоточность)

```javascript
// worker.js - отдельный файл
class FeedWorker {
    constructor() {
        this.posts = [];
        
        self.addEventListener('message', this.handleMessage.bind(this));
    }
    
    handleMessage(event) {
        const { type, data } = event.data;
        
        switch(type) {
            case 'PROCESS_POSTS':
                this.processPosts(data);
                break;
            case 'FILTER_POSTS':
                this.filterPosts(data);
                break;
            case 'ANALYZE_ENGAGEMENT':
                this.analyzeEngagement(data);
                break;
        }
    }
    
    processPosts(posts) {
        // Тяжелые вычисления в фоне
        const processed = posts.map(post => ({
            ...post,
            processedAt: Date.now(),
            engagementScore: this.calculateEngagement(post),
            tags: this.extractTags(post.content)
        }));
        
        self.postMessage({
            type: 'POSTS_PROCESSED',
            data: processed
        });
    }
    
    calculateEngagement(post) {
        // Вычисление метрики вовлеченности
        return (post.likes * 1 + post.comments * 3 + post.reposts * 5) / 
               (post.views || 1);
    }
    
    extractTags(content) {
        // Извлечение хэштегов
        const hashtags = content.match(/#[\w\u0400-\u04FF]+/g) || [];
        return [...new Set(hashtags)];
    }
    
    filterPosts(data) {
        const { posts, filters } = data;
        let filtered = [...posts];
        
        if (filters.hashtags) {
            filtered = filtered.filter(post => 
                filters.hashtags.some(tag => post.tags?.includes(tag))
            );
        }
        
        if (filters.minEngagement) {
            filtered = filtered.filter(post => 
                post.engagementScore >= filters.minEngagement
            );
        }
        
        self.postMessage({
            type: 'POSTS_FILTERED',
            data: filtered
        });
    }
    
    analyzeEngagement(data) {
        const { posts } = data;
        
        const analytics = {
            totalLikes: 0,
            totalComments: 0,
            totalReposts: 0,
            averageEngagement: 0,
            topPosts: [],
            hourlyDistribution: {}
        };
        
        posts.forEach(post => {
            analytics.totalLikes += post.likes;
            analytics.totalComments += post.comments;
            analytics.totalReposts += post.reposts;
            
            // Определяем лучшие посты
            if (post.engagementScore > 10) {
                analytics.topPosts.push(post);
            }
            
            // Распределение по часам
            const hour = new Date(post.createdAt).getHours();
            analytics.hourlyDistribution[hour] = 
                (analytics.hourlyDistribution[hour] || 0) + 1;
        });
        
        analytics.averageEngagement = 
            analytics.totalLikes + analytics.totalComments + analytics.totalReposts;
        
        self.postMessage({
            type: 'ENGAGEMENT_ANALYZED',
            data: analytics
        });
    }
}

// Инициализация воркера
new FeedWorker();

// main.js - использование воркера
class FeedProcessor {
    constructor() {
        this.worker = new Worker('worker.js');
        this.setupWorkerListeners();
    }
    
    setupWorkerListeners() {
        this.worker.addEventListener('message', (event) => {
            const { type, data } = event.data;
            
            switch(type) {
                case 'POSTS_PROCESSED':
                    this.onPostsProcessed(data);
                    break;
                case 'POSTS_FILTERED':
                    this.onPostsFiltered(data);
                    break;
                case 'ENGAGEMENT_ANALYZED':
                    this.onEngagementAnalyzed(data);
                    break;
            }
        });
        
        this.worker.addEventListener('error', (error) => {
            console.error('Worker error:', error);
        });
    }
    
    processPosts(posts) {
        this.worker.postMessage({
            type: 'PROCESS_POSTS',
            data: posts
        });
    }
    
    filterPosts(posts, filters) {
        this.worker.postMessage({
            type: 'FILTER_POSTS',
            data: { posts, filters }
        });
    }
    
    analyzeEngagement(posts) {
        this.worker.postMessage({
            type: 'ANALYZE_ENGAGEMENT',
            data: { posts }
        });
    }
    
    onPostsProcessed(processedPosts) {
        console.log('Посты обработаны:', processedPosts.length);
        // Обновляем UI
        this.updateFeed(processedPosts);
    }
    
    onPostsFiltered(filteredPosts) {
        console.log('Посты отфильтрованы:', filteredPosts.length);
        this.renderFilteredFeed(filteredPosts);
    }
    
    onEngagementAnalyzed(analytics) {
        console.log('Аналитика вовлеченности:', analytics);
        this.displayAnalytics(analytics);
    }
    
    updateFeed(posts) {
        // Обновление ленты
    }
    
    renderFilteredFeed(posts) {
        // Рендер отфильтрованных постов
    }
    
    displayAnalytics(analytics) {
        // Отображение аналитики
    }
}
```

## 6. Media Queries и Responsive Design

```javascript
class ResponsiveManager {
    constructor() {
        this.breakpoints = {
            mobile: '(max-width: 768px)',
            tablet: '(min-width: 769px) and (max-width: 1024px)',
            desktop: '(min-width: 1025px)',
            darkMode: '(prefers-color-scheme: dark)',
            reducedMotion: '(prefers-reduced-motion: reduce)',
            highContrast: '(prefers-contrast: high)'
        };
        
        this.mediaQueries = {};
        this.listeners = new Map();
        
        this.init();
    }
    
    init() {
        // Создаем MediaQueryList для каждого брейкпоинта
        Object.entries(this.breakpoints).forEach(([name, query]) => {
            this.mediaQueries[name] = window.matchMedia(query);
            
            // Добавляем слушатель изменений
            this.mediaQueries[name].addEventListener('change', (event) => {
                this.handleBreakpointChange(name, event.matches);
            });
        });
    }
    
    handleBreakpointChange(breakpoint, matches) {
        const listeners = this.listeners.get(breakpoint) || [];
        listeners.forEach(callback => callback(matches));
        
        // Диспатчим глобальное событие
        const event = new CustomEvent('breakpointChange', {
            detail: { breakpoint, matches }
        });
        window.dispatchEvent(event);
    }
    
    on(breakpoint, callback) {
        if (!this.listeners.has(breakpoint)) {
            this.listeners.set(breakpoint, []);
        }
        this.listeners.get(breakpoint).push(callback);
        
        // Вызываем сразу с текущим состоянием
        callback(this.mediaQueries[breakpoint]?.matches || false);
        
        return () => this.off(breakpoint, callback);
    }
    
    off(breakpoint, callback) {
        const listeners = this.listeners.get(breakpoint);
        if (listeners) {
            const index = listeners.indexOf(callback);
            if (index !== -1) {
                listeners.splice(index, 1);
            }
        }
    }
    
    isMobile() {
        return this.mediaQueries.mobile?.matches || false;
    }
    
    isTablet() {
        return this.mediaQueries.tablet?.matches || false;
    }
    
    isDesktop() {
        return this.mediaQueries.desktop?.matches || false;
    }
    
    isDarkMode() {
        return this.mediaQueries.darkMode?.matches || false;
    }
    
    shouldReduceMotion() {
        return this.mediaQueries.reducedMotion?.matches || false;
    }
}

// Адаптивный компонент для ленты
class AdaptiveFeed {
    constructor(container) {
        this.container = container;
        this.responsive = new ResponsiveManager();
        this.currentLayout = 'desktop';
        
        this.init();
    }
    
    init() {
        // Слушаем изменения брейкпоинтов
        this.responsive.on('mobile', (isMobile) => {
            if (isMobile) {
                this.switchToMobileLayout();
            }
        });
        
        this.responsive.on('tablet', (isTablet) => {
            if (isTablet) {
                this.switchToTabletLayout();
            }
        });
        
        this.responsive.on('desktop', (isDesktop) => {
            if (isDesktop) {
                this.switchToDesktopLayout();
            }
        });
        
        // Учитываем предпочтения пользователя
        if (this.responsive.shouldReduceMotion()) {
            this.disableAnimations();
        }
        
        if (this.responsive.isDarkMode()) {
            this.applyDarkTheme();
        }
    }
    
    switchToMobileLayout() {
        this.currentLayout = 'mobile';
        this.container.classList.add('mobile-layout');
        this.container.classList.remove('tablet-layout', 'desktop-layout');
        
        // Адаптируем отображение постов
        document.querySelectorAll('.post').forEach(post => {
            post.classList.add('mobile-post');
            // Скрываем некоторые элементы для мобильной версии
            const extraActions = post.querySelector('.extra-actions');
            if (extraActions) extraActions.style.display = 'none';
        });
    }
    
    switchToTabletLayout() {
        this.currentLayout = 'tablet';
        this.container.classList.add('tablet-layout');
        this.container.classList.remove('mobile-layout', 'desktop-layout');
        
        // 2 колонки для планшета
        this.container.style.display = 'grid';
        this.container.style.gridTemplateColumns = 'repeat(2, 1fr)';
        this.container.style.gap = '20px';
    }
    
    switchToDesktopLayout() {
        this.currentLayout = 'desktop';
        this.container.classList.add('desktop-layout');
        this.container.classList.remove('mobile-layout', 'tablet-layout');
        
        // 3 колонки для десктопа
        this.container.style.display = 'grid';
        this.container.style.gridTemplateColumns = 'repeat(3, 1fr)';
        this.container.style.gap = '24px';
    }
    
    disableAnimations() {
        this.container.style.setProperty('--animation-duration', '0s');
        const style = document.createElement('style');
        style.textContent = `
            * {
                animation-duration: 0s !important;
                transition-duration: 0s !important;
            }
        `;
        document.head.appendChild(style);
    }
    
    applyDarkTheme() {
        document.body.classList.add('dark-theme');
        
        // Настраиваем цвета для темной темы
        const darkThemeStyles = `
            .dark-theme {
                background-color: #1a1a1a;
                color: #ffffff;
            }
            .dark-theme .post {
                background-color: #2d2d2d;
                border-color: #404040;
            }
            .dark-theme .post-actions button {
                color: #e0e0e0;
            }
        `;
        
        const style = document.createElement('style');
        style.textContent = darkThemeStyles;
        document.head.appendChild(style);
    }
}
```

## 7. Fullscreen API

```javascript
class FullscreenManager {
    constructor(element) {
        this.element = element || document.documentElement;
        this.isFullscreen = false;
        
        this.init();
    }
    
    init() {
        // Слушаем изменения fullscreen
        document.addEventListener('fullscreenchange', this.onFullscreenChange.bind(this));
        document.addEventListener('webkitfullscreenchange', this.onFullscreenChange.bind(this));
        document.addEventListener('mozfullscreenchange', this.onFullscreenChange.bind(this));
        document.addEventListener('MSFullscreenChange', this.onFullscreenChange.bind(this));
    }
    
    onFullscreenChange() {
        this.isFullscreen = !!this.getFullscreenElement();
        
        const event = new CustomEvent('fullscreenChange', {
            detail: { isFullscreen: this.isFullscreen }
        });
        this.element.dispatchEvent(event);
    }
    
    getFullscreenElement() {
        return document.fullscreenElement ||
               document.webkitFullscreenElement ||
               document.mozFullScreenElement ||
               document.msFullscreenElement;
    }
    
    async enter() {
        try {
            if (this.element.requestFullscreen) {
                await this.element.requestFullscreen();
            } else if (this.element.webkitRequestFullscreen) {
                await this.element.webkitRequestFullscreen();
            } else if (this.element.mozRequestFullScreen) {
                await this.element.mozRequestFullScreen();
            } else if (this.element.msRequestFullscreen) {
                await this.element.msRequestFullscreen();
            }
            return true;
        } catch (error) {
            console.error('Error entering fullscreen:', error);
            return false;
        }
    }
    
    async exit() {
        try {
            if (document.exitFullscreen) {
                await document.exitFullscreen();
            } else if (document.webkitExitFullscreen) {
                await document.webkitExitFullscreen();
            } else if (document.mozCancelFullScreen) {
                await document.mozCancelFullScreen();
            } else if (document.msExitFullscreen) {
                await document.msExitFullscreen();
            }
            return true;
        } catch (error) {
            console.error('Error exiting fullscreen:', error);
            return false;
        }
    }
    
    toggle() {
        if (this.isFullscreen) {
            return this.exit();
        } else {
            return this.enter();
        }
    }
}

// Компонент для просмотра медиа в полноэкранном режиме
class MediaFullscreenViewer {
    constructor(mediaElement) {
        this.media = mediaElement;
        this.fullscreen = new FullscreenManager(mediaElement);
        
        this.setupControls();
    }
    
    setupControls() {
        // Создаем кнопку полноэкранного режима
        const button = document.createElement('button');
        button.innerHTML = '⛶';
        button.className = 'fullscreen-btn';
        button.addEventListener('click', () => this.fullscreen.toggle());
        
        this.media.parentElement.style.position = 'relative';
        this.media.parentElement.appendChild(button);
        
        // Двойной клик для переключения
        this.media.addEventListener('dblclick', () => this.fullscreen.toggle());
        
        // Изменяем стили при переходе в полноэкранный режим
        this.media.addEventListener('fullscreenChange', (event) => {
            if (event.detail.isFullscreen) {
                this.media.classList.add('fullscreen');
                button.innerHTML = '✕';
            } else {
                this.media.classList.remove('fullscreen');
                button.innerHTML = '⛶';
            }
        });
    }
}
```

## 8. Network Information API

```javascript
class NetworkMonitor {
    constructor() {
        this.connection = navigator.connection || 
                          navigator.mozConnection || 
                          navigator.webkitConnection;
        
        this.listeners = new Map();
        
        if (this.connection) {
            this.init();
        }
    }
    
    init() {
        this.connection.addEventListener('change', this.handleConnectionChange.bind(this));
    }
    
    handleConnectionChange() {
        const info = this.getConnectionInfo();
        
        // Уведомляем всех слушателей
        const listeners = this.listeners.get('change') || [];
        listeners.forEach(callback => callback(info));
        
        // Диспатчим событие
        const event = new CustomEvent('networkChange', { detail: info });
        window.dispatchEvent(event);
    }
    
    getConnectionInfo() {
        if (!this.connection) return null;
        
        return {
            type: this.connection.type,
            effectiveType: this.connection.effectiveType,
            downlink: this.connection.downlink,
            rtt: this.connection.rtt,
            saveData: this.connection.saveData
        };
    }
    
    on(event, callback) {
        if (!this.listeners.has(event)) {
            this.listeners.set(event, []);
        }
        this.listeners.get(event).push(callback);
    }
    
    off(event, callback) {
        const listeners = this.listeners.get(event);
        if (listeners) {
            const index = listeners.indexOf(callback);
            if (index !== -1) {
                listeners.splice(index, 1);
            }
        }
    }
    
    isSlowConnection() {
        const info = this.getConnectionInfo();
        if (!info) return false;
        
        return info.effectiveType === '2g' || 
               info.effectiveType === 'slow-2g' ||
               info.downlink < 1;
    }
    
    shouldReduceQuality() {
        const info = this.getConnectionInfo();
        if (!info) return false;
        
        return this.isSlowConnection() || info.saveData;
    }
}

// Адаптивная загрузка контента
class AdaptiveLoader {
    constructor() {
        this.network = new NetworkMonitor();
        this.quality = 'high';
        
        this.init();
    }
    
    init() {
        this.network.on('change', (info) => {
            this.adjustQuality(info);
        });
        
        // Устанавливаем начальное качество
        const info = this.network.getConnectionInfo();
        this.adjustQuality(info);
    }
    
    adjustQuality(info) {
        if (this.network.shouldReduceQuality()) {
            this.quality = 'low';
            this.loadLowQualityContent();
        } else {
            this.quality = 'high';
            this.loadHighQualityContent();
        }
    }
    
    loadLowQualityContent() {
        // Загружаем изображения низкого качества
        document.querySelectorAll('img[data-src-high]').forEach(img => {
            const lowSrc = img.dataset.srcLow;
            if (lowSrc) {
                img.src = lowSrc;
            }
        });
        
        // Отключаем автовоспроизведение видео
        document.querySelectorAll('video[autoplay]').forEach(video => {
            video.pause();
            video.removeAttribute('autoplay');
        });
        
        // Уменьшаем количество постов на странице
        this.reducePageSize();
    }
    
    loadHighQualityContent() {
        // Загружаем изображения высокого качества
        document.querySelectorAll('img[data-src-high]').forEach(img => {
            const highSrc = img.dataset.srcHigh;
            if (highSrc) {
                img.src = highSrc;
            }
        });
        
        // Восстанавливаем автовоспроизведение
        document.querySelectorAll('video[data-autoplay]').forEach(video => {
            video.setAttribute('autoplay', '');
            video.play();
        });
        
        // Восстанавливаем размер страницы
        this.restorePageSize();
    }
    
    reducePageSize() {
        // Уменьшаем количество загружаемых постов
        const postsPerPage = 10;
        // Логика уменьшения пагинации
    }
    
    restorePageSize() {
        const postsPerPage = 20;
        // Логика восстановления пагинации
    }
}
```

## 9. Vibration API (Вибрация)

```javascript
class VibrationManager {
    static vibrate(pattern) {
        if (!window.navigator.vibrate) {
            console.warn('Vibration API not supported');
            return false;
        }
        
        return window.navigator.vibrate(pattern);
    }
    
    static vibratePattern(pattern) {
        return this.vibrate(pattern);
    }
    
    static vibrateClick() {
        return this.vibrate(50);
    }
    
    static vibrateSuccess() {
        return this.vibrate([100, 50, 100]);
    }
    
    static vibrateError() {
        return this.vibrate([200, 100, 200]);
    }
    
    static vibrateLong() {
        return this.vibrate(500);
    }
    
    static vibrateCustom(patterns) {
        return this.vibrate(patterns);
    }
    
    static cancel() {
        if (!window.navigator.vibrate) return false;
        return window.navigator.vibrate(0);
    }
}

// Использование в UI
class HapticFeedback {
    constructor() {
        this.setupListeners();
    }
    
    setupListeners() {
        // Вибрация при нажатии на кнопки
        document.addEventListener('click', (event) => {
            const button = event.target.closest('button');
            if (button && button.dataset.haptic !== 'false') {
                VibrationManager.vibrateClick();
            }
        });
        
        // Вибрация при лайке
        document.addEventListener('like', () => {
            VibrationManager.vibratePattern([50, 30, 50]);
        });
        
        // Вибрация при успешной загрузке
        window.addEventListener('feedLoaded', () => {
            VibrationManager.vibrateSuccess();
        });
        
        // Вибрация при ошибке
        window.addEventListener('feedError', () => {
            VibrationManager.vibrateError();
        });
        
        // Вибрация при свайпе
        document.addEventListener('swipe', (event) => {
            if (event.detail.direction === 'left') {
                VibrationManager.vibratePattern([30, 20, 30]);
            }
        });
    }
}
```

## 10. Device Orientation API

```javascript
class DeviceOrientation {
    constructor() {
        this.alpha = 0; // Z-axis rotation
        this.beta = 0;  // X-axis rotation
        this.gamma = 0; // Y-axis rotation
        this.isSupported = false;
        
        this.init();
    }
    
    init() {
        if (window.DeviceOrientationEvent) {
            window.addEventListener('deviceorientation', this.handleOrientation.bind(this));
            this.isSupported = true;
        } else {
            console.warn('Device Orientation API not supported');
        }
    }
    
    handleOrientation(event) {
        this.alpha = event.alpha;
        this.beta = event.beta;
        this.gamma = event.gamma;
        
        const eventData = {
            alpha: this.alpha,
            beta: this.beta,
            gamma: this.gamma
        };
        
        const customEvent = new CustomEvent('orientationChange', {
            detail: eventData
        });
        window.dispatchEvent(customEvent);
    }
    
    getOrientation() {
        return {
            alpha: this.alpha,
            beta: this.beta,
            gamma: this.gamma
        };
    }
}

// Использование для параллакс-эффекта
class ParallaxFeed {
    constructor() {
        this.orientation = new DeviceOrientation();
        this.sensitivity = 20;
        
        window.addEventListener('orientationChange', this.handleOrientation.bind(this));
    }
    
    handleOrientation(event) {
        const { beta, gamma } = event.detail;
        
        // Применяем параллакс к постам
        document.querySelectorAll('.post').forEach((post, index) => {
            const offsetX = gamma * this.sensitivity * (index % 3) / 10;
            const offsetY = beta * this.sensitivity * (index % 2) / 10;
            
            post.style.transform = `translate(${offsetX}px, ${offsetY}px)`;
        });
    }
}
```

## Заключение

JavaScript предоставляет множество специальных возможностей для создания интерактивных и отзывчивых приложений:

1. **Drag & Drop** - для перетаскивания элементов
2. **Clipboard API** - для работы с буфером обмена
3. **Touch Events** - для мобильных взаимодействий
4. **Intersection Observer** - для отслеживания видимости
5. **Web Workers** - для многопоточности
6. **Media Queries** - для адаптивного дизайна
7. **Fullscreen API** - для полноэкранного режима
8. **Network Information** - для адаптации к скорости соединения
9. **Vibration API** - для тактильной обратной связи
10. **Device Orientation** - для использования гироскопа

Эти API позволяют создавать более богатые и интерактивные веб-приложения, приближая их к нативному опыту использования.
