# FE-Interview-of-2018
个人2018年前端面试和心得汇总：一是为了总结，二是为了培养自己描述问题，及回答这些问题的能力

先整理部分吧
1. 了解ES6吗，对于数组，有哪些新的操作方法
- 数组的新方法有isArray, filter
- 还有一个新的类型Map，用来做数组去重

2. 对于数组排序了解吗
- sort方法，可以传参
- 现在需要定义一个通用方法，按照对象的某个属性对数组进行排序
```javascript
function comparison(propertyName) {
  return function(obj1, obj2) {
    var val1 = obj1[propertyName];
    var val2 = obj2[propertyName];
    return val1 - val2;
  }
}
```
然后调用如：
```js
var arr = [{id: 1, name: "test1"},
          {id: 3, name: "test3"},
          {id: 5, name: "test5"},
          {id: 2, name: "test2"}];
arr.sort(comparison("name"));
```

3. 查找一个字符串内部不重复的字符的数目，使用es6的写法
- 第一种es6的语法
```es6
let result = str => {
  const res = {};
  for(let s of str) {
    res[s] = (res[s] || 0) + 1;
  }
  return res;
}
```
  - 考查的点：
    - const定义的引用类型，是否可以改变
    - es6新语法使用的熟练程度

- 第二种使用reduce
```js
var names = ['Alice', 'Bob', 'Tiff', 'Bruce', 'Alice'];

var countedNames = names.reduce(function (allNames, name) { 
  if (name in allNames) {
    allNames[name]++;
  }
  else {
    allNames[name] = 1;
  }
  return allNames;
}, {});
```

4. 数组去重
- reduce
```
let arr = [1,2,1,2,3,5,4,5,3,4,4,4,4];
let result = arr.sort().reduce((init, current) => {
    if(init.length === 0 || init[init.length-1] !== current) {
        init.push(current);
    }
    return init;
}, []);
console.log(result); //[1,2,3,4,5]
```
- Set
```
let arr = [1,2,1,2,3,5,4,5,3,4,4,4,4];
let result = new Set(arr)
```
