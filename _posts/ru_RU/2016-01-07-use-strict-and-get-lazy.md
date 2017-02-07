---
layout: post

title: Включите строгий режим и расслабьтесь
tip-number: 07
tip-username: nainslie
tip-username-profile: https://twitter.com/nat5an
tip-tldr: Strict-mode JavaScript makes it easier for the developer to write "secure" JavaScript.

categories:
    - ru_RU
---

Строгий режим в JavaScript упрощает задачу для разработчика писать "безопасный" JavaScript.

По умолчанию JavaScript позволяет программисту быть более беспечным. Например, он не требует нас объявлять переменные с `var`, когда мы первый раз вводим их. Для неопытного программиста это может показаться удобным, но это источник многих проблема, когда мы опечатываемся в названии перменной или случайно ссылаемся на нее вне ее контекста.

Программисты любят заставлять компьютер делать скучную работу за нас и автоматически проверять нашу работу на ошибки. Это и позволяет нам cделать директива "use strict" , превращая наши ошибки в ошибки JavaScript.

Чтобы включить эту директиву, мы можем добавить ее в начало js файла:

```javascript
// Строгий режим на весь скрипт
"use strict";
var v = "Hi!  I'm a strict mode script!";
```

или внутрь функции:

```javascript
function f()
{
  // Строгий режим на уровне функции
  'use strict';
  function nested() { return "And so am I!"; }
  return "Hi!  I'm a strict mode function!  " + nested();
}
function f2() { return "I'm not strict."; }
```

Добавляя эту директиву в JavaScript файл или функцию, мы побуждаем JavaScript движек работать в строгом режиме, что выключает многое поведение, которое обычно нежелательно в больших JS проэктах. Кроме многих других вещей, строгий режим поведение следующих вещей:

* Variables can only be introduced when they are preceded with "var"
* Attempting to write to read-only properties generates a noisy error
* You have to call constructors with the "new" keyword
* "this" is not implicitly bound to the global object
* Very limited use of eval() allowed
* Protects you from using reserved words or future reserved words as variable names

Strict mode is great for new projects, but can be challenging to introduce into older projects that don't already use it in most places.  It also can be problematic if your build chain concatenates all your js files into one big file, as this may cause all files to execute in strict mode.

It is not a statement, but a literal expression, ignored by earlier versions of JavaScript.
Strict mode is supported in:

* Internet Explorer from version 10.
* Firefox from version 4.
* Chrome from version 13.
* Safari from version 5.1.
* Opera from version 12.

[See MDN for a fuller description of strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode).
