## 1.apply和call的区别

 	 apply:方法能劫持另外一个对象的方法，继承另外一个对象的属性.

Function.apply(obj,args)方法能接收两个参数
obj：这个对象将代替Function类里this对象
args：这个是数组，它将作为参数传给Function（args-->arguments）

 	 call:和apply的意思一样,只不过是参数列表不一样.

```javascript
Function.call(obj,[param1[,param2[,…[,paramN]]]])
obj：这个对象将代替Function类里this对象
params：这个是一个参数列表
```
## 2.使用场景

​	在给对象参数的情况下,如果参数的形式是数组的时候,比如apply示例里面传递了参数	arguments,这个参数是数组类型,并且在调用Person的时候参数的列表是对应一致的(	也就是Person和Student的参数列表前两位是一致的) 就可以采用 apply , 如果我的	Person的参数列表是这样的(age,name),而Student的参数列表是(name,age,grade),	这样就可以用call来实现了,也就是直接指定参数列表对应值的位置(Person.call	(this,age,name,grade));

## 3.妙用

​	a)        Math.max 可以实现得到数组中最大的一项，因为Math.max 参数里面不支持Math.max([param1,param2]) 也就是数组，但是它支持Math.max(param1,param2,param3…),所以可以根据刚才apply的那个特点来解决 var max=Math.max.apply(null,array),这样轻易的可以得到一个数组中最大的一项(apply会将一个数组装换为一个参数接一个参数的传递给方法)， 这块在调用的时候第一个参数给了一个null,这个是因为没有对象去调用这个方法,我只需要用这个方法帮我运算,得到返回的结果就行,.所以直接传递了一个null过去。
​	