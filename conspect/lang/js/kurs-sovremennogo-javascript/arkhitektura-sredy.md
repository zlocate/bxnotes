---
layout: post.njk
tags: [post, postInConspect:kurs_sovremennogo_javascript]
conspect: kurs_sovremennogo_javascript
section: lang
subject: js
title: Архитектура среды
seoDescription: Рассмотрим такие понятия как Heap, Call Stack, Event Table, Event Queue и Event Loop и их роль в выполнении JavaScript программ.
seoKeywords: js, heap, call, stack, event loop
date: 2018-09-22 12:00:00
---
# Архитектура среды

Рассмотрим из каких архитектурных частей состоит среда выполнения js программ на примере движка V8, который используется в Chrome и Node.

**Heap**
Область памяти, содержит объекты, на которые ссылаются переменные программы.

**Call Stack**
Стек вызовов это LIFO структура (последний вошедший выходит первым). В данный стек помещаются и удаляются функции по мере выполнения программы. Синхронные функции помещаются в стек вызова сразу. Асинхронные откладываются в специальную таблицу - Event Table, где ожидают дальнейшей обработки, чтобы не блокировать процесс выполнения программы.

**Event Table**
Таблица в которой находится информация о том, по какому событию необходимо поместить функцию в Event Queue (очередь событий).

**Event Queue**
Очередь событий - это FIFO структура (раньше выходят элементы, которые раньше были помещены). В ней находятся асинхронные функции, для которых наступило время запуска

**Event Loop**
Цикл событий - это цикл, который непрерывно проверяет есть ли функции в очереди событий и помещает их в стек вызова. Срабатывает когда стек вызовов пуст.

*Event Table* и *Event Queue* являются частью Web Api, который реализуют браузеры для того, чтобы использовать такие возможности, как асинхронные запросы, таймеры, обрабатывать DOM события и другое асинхронное поведение. **Web Api не является стандартной функциональностью JavaScript** и в различных средах данное API может быть реализовано по разному.