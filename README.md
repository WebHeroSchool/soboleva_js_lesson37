
**1. Всегда используйте let или const для объявления переменных.**

не надо так: 

SuperPower = new SuperPower();
 
надо так:

const superPower = new SuperPower();


2. Используй фигурные скобки для всех многострочных блоков.

не надо так:

if (test)
  return false;

function foo() { return false; }
 
надо так:

if (test) return false;

function bar() {
  return false;
}

3. Не вызывай встроенные методы Object.prototype (такие как hasOwnProperty, propertyIsEnumerable, и isPrototypeOf) у самих объектов. Вместо этого вызывай их с помощью call передавая в него объект.

Такие встроенные методы могут быть переопределены в объекте и могут работать не так, как они описаны в Object.prototype

не надо так:

object.hasOwnProperty(key);
 
надо так:

Object.prototype.hasOwnProperty.call(object, key);

// еще лучше
const has = Object.prototype.hasOwnProperty;
console.log(has.call(object, key));
/* или*/
import has from 'has';
console.log(has(object, key));

4.Используй квадратные скобки [ ] для объявления массивов.

не надо так:

const items = new Array();
 
надо так: 

const items = [];

5. При использовании перебирающих методов массивов в коллбэке всегда используй return для возврата результата коллбэка. Если тебе не нужно использовать результат коллбэка, используй для перебора forEach.

не надо так:

inbox.filter((msg) => {
  const { subject, author } = msg;
  if (subject === 'Mockingbird') {
    return author === 'Harper Lee';
  } else {
    return false;
  }
});

[[0, 1], [2, 3], [4, 5]].reduce((acc, item, index) => {
  const flatten = acc.concat(item);
});
 

надо так:

[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});


[1, 2, 3].map((x) => x + 1);

[[0, 1], [2, 3], [4, 5]].reduce((acc, item, index) => {
  const flatten = acc.concat(item);
  return flatten;
});



inbox.filter((msg) => {
  const { subject, author } = msg;
  if (subject === 'Mockingbird') {
    return author === 'Harper Lee';
  }

  return false;
});

6.Используй function expressions (Функциональное Выражение) и присваивай ее переменной вместо function declarations (Объявление Функции). Лучше: используй стрелочные функции.

Это позволит избежать ошибок, если функция будет вызвана до ее объявления. 

не надо так:

function foo() {
  // ...
}

const foo = function () {
  // ...
};
 

надо так:

const short = function longUniqueMoreDescriptiveLexicalFoo() {
  // ...
};

//лучше
const foo = () => {};

7.Не объявляй функцию внутри цикла.

не надо так:

for (let i=10; i; i--) {
  (function() { return i; })();
}

while(i) {
  const a = function() { return i; };
  a();
}
 
надо так:

const a = function() {};

for (let i=10; i; i--) {
  a();
}

8.Всегда ставь один пробел перед () и перед {} в функциях.

не надо так:

const f = function(){};
const g = function (){};
const h = function() {};
 

надо так:

const x = function () {};
const y = function a() {};

9.Используйте стрелочные функции для передачи коллбеков.

не надо так:

[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});
 

надо так:

[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});

10.Называй функции-конструкторы с большой буквы.

не надо так:

const colleague = new person();
const friend = new person.acquaintance();
 

надо так:

const colleague = new Person();
const friend = new person.Acquaintance();