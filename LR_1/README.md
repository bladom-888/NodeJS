## Функція add()

Функція add() - це функція на NodeJS, яка приймає будь-яку кількість числових параметрів і повертає нову функцію, яка також приймає будь-яку кількість числових параметрів. Кожен наступний виклик цієї нової функції додає його аргументи до аргументів попереднього виклику і повертає нову функцію, поки останній виклик не закінчиться порожнім списком параметрів, після чого буде повернуто суму всіх переданих параметрів.

### Приклад використання:
    console.log(add(2)(5)(7)(1)(6)(5)(11)()); // 37
### Параметри:
Функція не має явно визначених параметрів. Вона приймає довільну кількість числових параметрів, які додаються до попередніх параметрів у кожному виклику.

### Повертає:
Функція повертає нову функцію, яка також приймає довільну кількість числових параметрів. Коли виклик з порожнім списком параметрів, функція повертає суму всіх переданих параметрів в попередніх викликах.

### Приклад:
    console.log(add(2)(5)(7)(1)(6)(5)(11)()); // 37
Цей приклад додає числа 2, 5, 7, 1, 6, 5 та 11. Кожен наступний виклик додає його аргументи до аргументів попереднього виклику. Коли останній виклик є порожнім, функція повертає суму всіх переданих параметрів - 37.

### Помилки:
Функція призначена для додавання лише числових параметрів. Передавати недопустимі параметри може призвести до помилок під час виконання функції.

## Функція deepClone()

Функція deepClone() - це функція на NodeJS, яка приймає об'єкт та повертає його глибоку копію. Глибоке копіювання означає, що повертається новий об'єкт, що містить всі поля та значення об'єкта, переданого параметром, та всі поля та значення об'єктів, які містяться всередині цього об'єкта. Якщо об'єкт містить посилання на інші об'єкти, ці посилання також будуть глибоко скопійовані, щоб не впливати на оригінальний об'єкт.

### Приклад використання:
    const obj = {a: 1, b: {c: 2}};
    const clone = deepClone(obj);
    console.log(clone); // {a: 1, b: {c: 2}}

### Параметри:
obj - об'єкт, який потрібно скопіювати. Об'єкт може містити будь-які поля та значення, включаючи інші об'єкти.

### Повертає:
Функція повертає новий об'єкт, який містить глибоку копію переданого об'єкта.

### Приклад:
    const obj = {a: 1, b: {c: 2}};
    const clone = deepClone(obj);
    console.log(clone); // {a: 1, b: {c: 2}}
Цей приклад створює об'єкт obj з полями a та b. Поле b містить об'єкт з полем c. Функція deepClone() повертає глибоку копію цього об'єкта, що містить всі його поля та значення, а також всі поля та значення об'єктів, які містяться всередині цього об'єкта. Результат виводу в консоль буде {a: 1, b: {c: 2}}.

### Помилки:
Якщо переданий параметр не є об'єктом, функція поверне помилку. Також можуть виникати помилки під час глибокого копіювання, які можуть виникнути, якщо переданий об'єкт містить циклічні посилання. В такому випадку функція може зациклитись і не завершити свою роботу.

## Функція-обгортка для кешування результатів іншої функції

Дана функція призначена для кешування результатів іншої функції з довільною кількістю числових параметрів. При виклику функції-обгортки з аргументами, вона перевіряє, чи були вже розраховані результати з такими ж аргументами, та повертає їх з кешу, якщо такі є. Якщо результатів з такими аргументами немає в кеші, функція-обгортка викликає задану функцію з цими аргументами, розраховує результат, зберігає його в кеші та повертає його.

### Параметри

func - функція, результат якої потрібно кешувати. Може мати будь-яку кількість числових параметрів.
cachedFunc - функція, яка повертається з функції-обгортки і призначена для виклику з тими ж аргументами, що й func.
args - масив числових параметрів, переданих у функцію-обгортку.
Повертає

cachedFunc - функція, яка повертається з функції-обгортки і призначена для виклику з тими ж аргументами, що й func.

### Приклад використання
    const cachedCalc = wrapper(calc);
    cachedCalc(2, 2, 3); // Calulated result: 7
    cachedCalc(5, 8, 1); // Calulated result: 14
    cachedCalc(2, 2, 3); // Cached result: 7
У цьому прикладі функція calc обчислює суму трьох чисел. Задана функція-обгортка wrapper приймає функцію calc і повертає нову функцію cachedCalc, яка має той самий інтерфейс, що й функція calc, але з кешуванням результатів.

Функція wrapper створює змінну cache, яка є об'єктом типу Map і слугує для зберігання ключів та значень кешу. Кожен ключ кешу є рядком, який містить JSON-подібну строку, що містить аргументи, передані до функції-обгортки.

Функція-обгортка cachedCalc приймає аргументи ...args (зібрані в масив) та перевіряє, чи є в кеші результат з такими самими аргументами. Якщо такий результат є, функція повертає його з кешу. Якщо ні, функція викликає функцію func з цими аргументами, обчислює результат та зберігає його в кеші, використовуючи ключ key. Функція також повертає обчислений результат.

Приклад використання функції-обгортки демонструє, що результати з аргументами (2, 2, 3) та (5, 8, 1) є новими та обчислювалися, а результат з аргументами (2, 2, 3) повторюється, тому повертається з кешу. В консолі виводиться інформація про те, чи був результат обчислений, чи повернутий з кешу.

## Функція isAnagram()
Ця функція isAnagram перевіряє, чи є два рядки анаграмами (тобто, чи можна один рядок переставити, щоб утворити другий рядок). Функція приймає два рядки як аргументи, str1 та str2.

Спочатку функція розбиває кожен рядок на масив окремих символів за допомогою методу split(""). Потім вона сортує кожен масив за допомогою методу sort(). Це дозволяє порівняти два масиви для визначення того, чи є вони анаграмами.

Функція використовує цикл for, щоб перевірити, чи кожен символ в arr1 дорівнює відповідному символу в arr2. Якщо хоча б один символ не збігається, функція повертає false. Якщо всі символи збігаються, то функція повертає true.

Ця функція може бути корисною для перевірки, чи є два рядки, наприклад, перестановкою символів один від одного, як, наприклад, "listen" та "silent".

## Результат виконання роботи
![result](/images/result.jpg)