# Третя лабораторна робота
## Завдання 1
Напишіть функцію, яка приймає будь-який тип масиву та асинхронний колбек, який викликається для кожного елемента масиву послідовно. Результатом виклику має бути масив результатів колбеку. Усі типи мають застосовуватися автоматично (функція шаблону). Приклад виклику:

    const array: Array<string> = ["one", "two", "three"];
    const results = await runSequent(array, (item, index) =>
        Promise.resolve({
            item,
            index,
        })
    );

IDE має розглядати змінні з прикладу так:
    item type = string
    index type = number
    results type = Array<{item: string, index: number}>

# Завдання 2
Напишіть функцію, яка приймає будь-який тип масиву та правило для видалення елементів масиву. Функція змінює переданий масив, а усі видалені елементи функція повертає окремим масивом такого ж типу. Усі типи мають застосовуватися автоматично (функція шаблону). Приклад виклику:
    const array = [1, 2, 3, 6, 7, 9];
    const deletedElements = arrayChangeDelete(array, (item) => item % 2 === 0);

IDE має розглядати змінні з прикладу так:
    item: number
    deletedElements: Array
Результат виклику:
    array = [1, 3, 7, 9]
    deletedElements = [2, 6]

# Завдання 3
Напишіть скрипт, який отримує з командного рядка рядковий параметр - шлях до JSON-файла із масивом рядків - посилань, читає та аналізує його вміст. Скрипт має створити папку «<JSON_filename>_pages» і для кожного посилання із <JSON-файла отримати його HTML-вміст і зберегти цей вміст у окремому файлі в новоствореній папці. Приклад JSON-файла (list.json) прикріплений до цього практичного завдання нижче.

# Завдання 4
Напишіть скрипт, який отримує з командного рядка числовий параметр – частоту в секундах. Скрипт має виводити на кожному тику (визначеному частотою) наступну системну інформацію:

- operating system;
- architecture;
- current user name;
- cpu cores models;
- cpu temperature;
- graphic controllers vendors and models;
- total memory, used memory, free memory в GB;
- дані про батарею (charging, percent, remaining time).

Знайдіть і використайте функціональність підходящих модулів.

# Завдання 5
Напишіть власну реалізацію класу EventEmitter (Publisher/Subscriber), який поводитиметься так:

    const emitter = new MyEventEmitter();
    emitter.registerHandler('userUpdated', () => console.log('Обліковий запис користувача оновлено'));
    emitter.emitEvent('userUpdated'); // Обліковий запис користувача оновлено

Результат у консолі
![](/lr_3/images/tg_image_2164673804.jpeg)
![](/lr_3/images/tg_image_4137631917.jpeg)