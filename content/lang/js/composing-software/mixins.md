---
title: Композиция на миксинах
seoDescription: Композиция на миксинах в JavaScript.
seoKeywords: js, композиция, миксины
date: 2019-09-16 01:00:00
---
# Композиция на миксинах

Миксин &ndash; это подмешивание свойств одного объекта в другой объект.

Композицию на миксинах легко создать через синтаксис *деструктуризации*:

```js
const a = {
  a: 'a'
};

const b = {
  b: 'b'
};

const c = {foo: 'bar', ...a, ...b}; // {foo: 'bar', a: 'a', b: 'b'}
```
