# RegExp (Regular Expressions)

### 

When String is called as part of a new expression, it is a constructor: 
it initialises the newly created object.

意謂著當String 出現的時候，同時也會產生RegExp 這個物件，表示String 也同時帶有RegExp 屬性。因此可以瞭解為何javascript String 可以match, exec, replace 等function 當中使用正規表示法。

## exec

## test

## match

## search

## replace

```js
// Q:
const str = '-xx____x-x__x-x_-'
let arr = []
```

```js
// A:
str.replace(/(-)|(x_*)/g, function(match, p1, p2) {
    p1 ? arr.push({on: true}) : null
    p2 ? arr.push({on: false}) : null
})
```



## split


[Regular_Expressions](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Regular_Expressions)

# 元字符