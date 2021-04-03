
**1. ������ ����������� let ��� const ��� ���������� ����������.**

�� ���� ���: 

SuperPower = new SuperPower();
 
���� ���:

const superPower = new SuperPower();


2. ��������� �������� ������ ��� ���� ������������� ������.

�� ���� ���:

if (test)
  return false;

function foo() { return false; }
 
���� ���:

if (test) return false;

function bar() {
  return false;
}

3. �� ������� ���������� ������ Object.prototype (����� ��� hasOwnProperty, propertyIsEnumerable, � isPrototypeOf) � ����� ��������. ������ ����� ������� �� � ������� call ��������� � ���� ������.

����� ���������� ������ ����� ���� �������������� � ������� � ����� �������� �� ���, ��� ��� ������� � Object.prototype

�� ���� ���:

object.hasOwnProperty(key);
 
���� ���:

Object.prototype.hasOwnProperty.call(object, key);

// ��� �����
const has = Object.prototype.hasOwnProperty;
console.log(has.call(object, key));
/* ���*/
import has from 'has';
console.log(has(object, key));

4.��������� ���������� ������ [ ] ��� ���������� ��������.

�� ���� ���:

const items = new Array();
 
���� ���: 

const items = [];

5. ��� ������������� ������������ ������� �������� � �������� ������ ��������� return ��� �������� ���������� ��������. ���� ���� �� ����� ������������ ��������� ��������, ��������� ��� �������� forEach.

�� ���� ���:

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
 

���� ���:

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

6.��������� function expressions (�������������� ���������) � ���������� �� ���������� ������ function declarations (���������� �������). �����: ��������� ���������� �������.

��� �������� �������� ������, ���� ������� ����� ������� �� �� ����������. 

�� ���� ���:

function foo() {
  // ...
}

const foo = function () {
  // ...
};
 

���� ���:

const short = function longUniqueMoreDescriptiveLexicalFoo() {
  // ...
};

//�����
const foo = () => {};

7.�� �������� ������� ������ �����.

�� ���� ���:

for (let i=10; i; i--) {
  (function() { return i; })();
}

while(i) {
  const a = function() { return i; };
  a();
}
 
���� ���:

const a = function() {};

for (let i=10; i; i--) {
  a();
}

8.������ ����� ���� ������ ����� () � ����� {} � ��������.

�� ���� ���:

const f = function(){};
const g = function (){};
const h = function() {};
 

���� ���:

const x = function () {};
const y = function a() {};

9.����������� ���������� ������� ��� �������� ���������.

�� ���� ���:

[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});
 

���� ���:

[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});

10.������� �������-������������ � ������� �����.

�� ���� ���:

const colleague = new person();
const friend = new person.acquaintance();
 

���� ���:

const colleague = new Person();
const friend = new person.Acquaintance();