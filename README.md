h1JavaScript Style Guide

**1. Всегда используйте let или const для объявления переменных.**

íå íàäî òàê: 

SuperPower = new SuperPower();
 
íàäî òàê:

const superPower = new SuperPower();


2. Èñïîëüçóé ôèãóðíûå ñêîáêè äëÿ âñåõ ìíîãîñòðî÷íûõ áëîêîâ.

íå íàäî òàê:

if (test)
  return false;

function foo() { return false; }
 
íàäî òàê:

if (test) return false;

function bar() {
  return false;
}

3. Íå âûçûâàé âñòðîåííûå ìåòîäû Object.prototype (òàêèå êàê hasOwnProperty, propertyIsEnumerable, è isPrototypeOf) ó ñàìèõ îáúåêòîâ. Âìåñòî ýòîãî âûçûâàé èõ ñ ïîìîùüþ call ïåðåäàâàÿ â íåãî îáúåêò.

Òàêèå âñòðîåííûå ìåòîäû ìîãóò áûòü ïåðåîïðåäåëåíû â îáúåêòå è ìîãóò ðàáîòàòü íå òàê, êàê îíè îïèñàíû â Object.prototype

íå íàäî òàê:

object.hasOwnProperty(key);
 
íàäî òàê:

Object.prototype.hasOwnProperty.call(object, key);

// åùå ëó÷øå
const has = Object.prototype.hasOwnProperty;
console.log(has.call(object, key));
/* èëè*/
import has from 'has';
console.log(has(object, key));

4.Èñïîëüçóé êâàäðàòíûå ñêîáêè [ ] äëÿ îáúÿâëåíèÿ ìàññèâîâ.

íå íàäî òàê:

const items = new Array();
 
íàäî òàê: 

const items = [];

5. Ïðè èñïîëüçîâàíèè ïåðåáèðàþùèõ ìåòîäîâ ìàññèâîâ â êîëëáýêå âñåãäà èñïîëüçóé return äëÿ âîçâðàòà ðåçóëüòàòà êîëëáýêà. Åñëè òåáå íå íóæíî èñïîëüçîâàòü ðåçóëüòàò êîëëáýêà, èñïîëüçóé äëÿ ïåðåáîðà forEach.

íå íàäî òàê:

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
 

íàäî òàê:

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

6.Èñïîëüçóé function expressions (Ôóíêöèîíàëüíîå Âûðàæåíèå) è ïðèñâàèâàé åå ïåðåìåííîé âìåñòî function declarations (Îáúÿâëåíèå Ôóíêöèè). Ëó÷øå: èñïîëüçóé ñòðåëî÷íûå ôóíêöèè.

Ýòî ïîçâîëèò èçáåæàòü îøèáîê, åñëè ôóíêöèÿ áóäåò âûçâàíà äî åå îáúÿâëåíèÿ. 

íå íàäî òàê:

function foo() {
  // ...
}

const foo = function () {
  // ...
};
 

íàäî òàê:

const short = function longUniqueMoreDescriptiveLexicalFoo() {
  // ...
};

//ëó÷øå
const foo = () => {};

7.Íå îáúÿâëÿé ôóíêöèþ âíóòðè öèêëà.

íå íàäî òàê:

for (let i=10; i; i--) {
  (function() { return i; })();
}

while(i) {
  const a = function() { return i; };
  a();
}
 
íàäî òàê:

const a = function() {};

for (let i=10; i; i--) {
  a();
}

8.Âñåãäà ñòàâü îäèí ïðîáåë ïåðåä () è ïåðåä {} â ôóíêöèÿõ.

íå íàäî òàê:

const f = function(){};
const g = function (){};
const h = function() {};
 

íàäî òàê:

const x = function () {};
const y = function a() {};

9.Èñïîëüçóéòå ñòðåëî÷íûå ôóíêöèè äëÿ ïåðåäà÷è êîëëáåêîâ.

íå íàäî òàê:

[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});
 

íàäî òàê:

[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});

10.Íàçûâàé ôóíêöèè-êîíñòðóêòîðû ñ áîëüøîé áóêâû.

íå íàäî òàê:

const colleague = new person();
const friend = new person.acquaintance();
 

íàäî òàê:

const colleague = new Person();
const friend = new person.Acquaintance();
