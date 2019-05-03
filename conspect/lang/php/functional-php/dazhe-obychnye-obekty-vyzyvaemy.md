---
layout: post.njk
tags: [post, postInConspect:functional-php]
conspect: functional-php
section: lang
subject: php
title: Даже обычные объекты вызываемы
seoDescription: Использование магического метода invoke() для запуска объекта как функции.
seoKeywords: php, __invoke(), __construct()
date: 2017-11-08 12:00:00
---
# Даже обычные объекты вызываемы

Синтаксис анонимной функции на самом деле компилируется в объект `Closure` с методом `__invoke()`. Данный метод позволяет объекту быть вызываемым. Рассмотрим следующий пример с точки зрения функционального программирования:

```php
class Counter {
  private $_value;
  public function __construct($init) {
    $this->_value = $init;
  }
  public function increment(): int {
    return $this->_value++;
  }
  public function __invoke() {
    return $this->increment()
  }
}
$c = new Counter(0);
$c(); //-> 1
$c(); //-> 2
$c(); //-> 3
```

С точки зрения функционального программирования, наличие внешней переменной по отношению к функции является сайд эффектом, такая функция не является чистой. Но на практике, эта переменная является приватной, она инкапсулирована в класс и ее можно безопасно использовать. Тем не менее, для функционального программирования предпочтительнее полностью избавиться от сайд эффекта, разделив поведение и состояние. Это можно достигнуть, декларируя переменную для каждых данных, которые мы желаем получить.

```php
class Counter {
  //...
  public static function increment(int $val): int {
    return $val + 1;
  }
}
Counter::increment(100); //-> 101
```