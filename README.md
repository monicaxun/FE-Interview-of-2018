# FE-Interview-of-2018
个人2018年前端面试和心得汇总：一是为了总结，二是为了培养自己描述问题，及回答这些问题的能力

先按照公司来整理吧
### 掌门1加1
1. 了解ES6吗，对于数组，有哪些新的操作方法
- 数组的新方法有isArray, filter
- 还有一个新的类型Map，用来做数组去重

2. 对于数组排序了解吗
- sort方法，可以传参
- 现在需要定义一个通用方法，按照对象的某个属性对数组进行排序
```
function comparison(propertyName) {
  return function(obj1, obj2) {
    var val1 = obj1[propertyName];
    var val2 = obj2[propertyName];
    if(val1 < val2) {
      return -1;
    } else if(val1 > val2) {
      return 1;
    } else {
      return 0;
    }
  }
}
```
然后调用如：
```
var arr = [{id: 1, name: "test1"},
          {id: 3, name: "test3"},
          {id: 5, name: "test5"},
          {id: 2, name: "test2"}];
arr.sort(comparison("name"));
```
