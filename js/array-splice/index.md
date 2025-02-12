---
title: "`.splice()`"
description: "Изменяет массив, удаляя и/или добавляя новые элементы."
authors:
  - vitya-ne
related:
  - js/array-slice
  - js/array-push
  - js/array-to-spliced
tags:
  - doka
---

## Кратко

Метод `splice()` изменяет массив, удаляя определённое количество элементов и/или добавляя новые элементы, начиная с указанного индекса.

## Пример

Удалим из массива два элемента начиная с элемента с индексом 1:

```js
const tasks = ['Проверить тесты', 'Выполнить код-ревью', 'Подготовить доклад', 'Обновить бэклог']

tasks.splice(1, 2)

console.tasks(tasks)
// ['Проверить тесты', 'Обновить бэклог']
```

## Как пишется

`Array.splice` принимает аргументы:

- индекс — позиция начала изменений в массиве;
- количество удаляемых элементов в массиве;
- остальные аргументы — элементы, добавляемые к массиву.

При удалении, элемент с индексом соответствующим началу изменений включается в число удаляемых элементов

Если индекс отрицательный, то отсчёт позиции начала изменений ведется от конца массива.

Удалим из массива три последних элемента и добавим два других элемента:

```js
const items = ['HTML', 'CSS', 'JavaScript', 'recipes', 'accessibility', null]

items.splice(-3, 3, 'Рецепты', 'Доступность')

console.log(items)
// ['HTML', 'CSS', 'JavaScript', 'Рецепты', 'Доступность']
```

Если индекс не соответствует размеру массива, то позиция начала изменений определяется по знаку индекса:

- отрицательный индекс — элементы удаляются и/или добавляются, начиная с 0-ого элемента исходного массива;
- положительный индекс — элементы добавляются после последнего элемента исходного массива;

Если количество удаляемых элементов меньше или равно 0, элементы не удаляются.

Добавим в массив один элемент на позицию с индексом 2:

```js
const months = ['Июнь', 'Июль', 'Сентябрь']

months.splice(2, 0, 'Август')

console.log(newMonths)
// [Июнь', 'Июль', 'Июль', Сентябрь']
```

Если при вызове указать только индекс, то все элементы, начиная с элемента с этим индексом (включая сам элемент), будут удалены.

`Array.splice` возвращает массив удалённых элементов. Если ни один элемент удалён не был, возвращается пустой массив.

## Как понять

Метод `splice()` может применяться для изменения последовательной группы элементов массива: удаления, добавления или замены.

Метод `splice()` является изменяющим методом, он изменяет исходный массив, для которого был вызван. Если вместо изменения исходного массива нужно получить новый массив, содержащий изменения, воспользуйтесь методом `toSpliced()`.

Метод `splice()` удобно использовать когда необходимо извлечь элементы из массива, чтобы продолжить с ними работать:

```js
const languages = ['Java', 'JavaScript', 'Python', 'C++']

const scriptLanguages = languages.splice(1, 2)

console.log(languages)
// ['Java', 'C++']

console.log(scriptLanguages)
// ['JavaScript', 'Python']
```

## Подсказки

💡 Если массив имеет незаполненные элементы, то при выполнении `splice()` массив сохранит для таких элементов отсутствие значения и не изменит их на `undefined`. В этом ещё одно отличие от метода `toSpliced()`.

Создадим массив, который имеет незаполненные элементы:

```js
const chords = ['Em']
chords[3] = 'A7'
chords[4] = 'F'

console.log(chords)
// ['Em', <2 empty items>, 'A7', 'F']
```

Заменим предпоследний элемент. Незаполненные элементы сохранятся:

```js
chords.splice(-2, 1, 'Am7' )
console.log(chords)
// ['Em', <2 empty items>, 'Am7', 'F']
```
