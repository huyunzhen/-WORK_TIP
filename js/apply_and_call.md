# call and apply 

> 用途：
* [用於 Copy 被指定的人身上的所有屬性和方法](#copy)
* [覆用](#reuse)
* [用於繼承](#inherit)

> 打油詩
>
> `猫吃鱼，狗吃肉，奥特曼打小怪兽。`
>
> `有天狗想吃鱼了`
>
> `猫.吃鱼.call(狗，鱼)`
>
> `狗就吃到鱼了`
>
> `猫成精了，想打怪兽`
>
> `奥特曼.打小怪兽.call(猫，小怪兽)`
>
> `猫也可以打小怪兽了``


### 模擬 call
```js
Function.prototype.copyCall = function(context) {
  context = context || window;

  context.fn = this;
  
  var args = [];
  for (var i = 1; i < arguments.length; i++) {
    args.push('arguments[' + i + ']');
  }
  
  var result = eval('context.fn(' + args + ')');

  delete context.fn;
  return result;
}
```


```js

Obj.call(thisObj, arg1, arg2, ...) // thisObj 擁有 Obj 身上的東西

// ps.1
if (thisObj === null) {
  thisObj === window
}

Obj.call(thisObj, arg1, arg2, ...);
Obj.apply(thisObj, [arg1, arg2, ...]);

```

<a name="copy" id="copy">copy</a>

```js
// example1 

function add(r, k) {
  return r + k;
}

function sub(r, k) {
  return r - k;
}

const result = {
  one: add.call(sub, 10, 249),
  two: add.call(sub, 20, 19),
  three: sub.call(add, 30, 299),
  four: sub.call(add, 40, 219),
}

for (key in results) {
  console.log(results[key]);
}
```

<a name="reuse" id="reuse">reuse</a>

```js

const Lyonar = {
  hp: 25,
  attack: 2,
  range: 'melee',
}

const Songhai = {
  hp: 25,
  attack: 2,
  range: 'summon',
}

function Person() {
  const personInfo = {
    hp: this.hp,
    attack: this.attack,
    range: this.range,
  }
  
  return personInfo;
}

[Lyonar, Songhai].map(function(p){
    var _person = Person.call(p);
    // if _person is String/Function
    return Object.prototype.toString.call(_person) === "[obejct Function]" ? _person() : _person
});

```

<a name="inherit" id="inherit">inherit</a>

```js

function Parent() {
  this.habit = 'play games',
  this.skin = 'yellow',
}

const Child = {};

Parent.call(Child);
```
