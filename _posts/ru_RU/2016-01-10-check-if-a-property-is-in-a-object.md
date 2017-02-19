---
layout: post

title: Проверяем есть ли свойство в объекте
tip-number: 10
tip-username: loverajoel
tip-username-profile: https://www.twitter.com/loverajoel
tip-tldr: Способы проверки если свойство есть в объекте.
tip-writer-support: https://www.coinbase.com/loverajoel

categories:
    - ru_RU
---

Когда вам надо проверить есть ли у [объекта](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects) свойство, вы вероятно пишете что-то вроде этого:

```javascript
var myObject = {
  name: '@tips_js'
};

if (myObject.name) { ... }

```

Это нормальный вариант, но вам также стоит знать, что есть 2 встроенных способа сделать подобное, [оператор `in`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/in) и [`Object.hasOwnProperty`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty). Этими способы есть у любого объект, который наследуемого от `Object`.

### Разница работы большая

```javascript
var myObject = {
  name: '@tips_js'
};

myObject.hasOwnProperty('name'); // true
'name' in myObject; // true

myObject.hasOwnProperty('valueOf'); // false, valueOf унаследован по цепочке прототипов
'valueOf' in myObject; // true

```

Both differ in the depth at which they check the properties. In other words, `hasOwnProperty` will only return true if key is available on that object directly. However, the `in` operator doesn't discriminate between properties created on an object and properties inherited from the prototype chain.

Here's another example:

```javascript
var myFunc = function() {
  this.name = '@tips_js';
};
myFunc.prototype.age = '10 days';

var user = new myFunc();

user.hasOwnProperty('name'); // true
user.hasOwnProperty('age'); // false, because age is from the prototype chain
```

Check the [live examples here](https://jsbin.com/tecoqa/edit?js,console)!

I also recommend reading [this discussion](https://github.com/loverajoel/jstips/issues/62) about common mistakes made when checking a property's existence in objects.
