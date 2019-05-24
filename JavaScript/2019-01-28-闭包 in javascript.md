#### 概念

闭包是一种特殊的对象。

由执行上下文（代号A）和在该上下文创建的函数（代号B)

当B 执行时，如果访问了A中变量对象的值，闭包产生。



```
<body>

    <div id="div1">

        这是div1

    </div>

</body>

<script>

  function foo() {

      var a= 20; 

      var b= 30;

      function add() {

          return a+b;

      }

      return add;

  }

  var res = foo();

  res();

</script>

</html>
```

![1545743814606](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\1545743814606.png)

#### 闭包阻止垃圾回收
 1. 当一个函数执行上下文运行完毕后，内部的所有内容都会失去引用被垃圾回收机制回收

 2. 而闭包的本质就是在函数外部保持内部变量的引用，因此闭包会阻止垃圾回收机制进行回收。

 3. 同时也要保持警惕，不能滥用闭包，需要回收这些变量时，手动地将这些变量设置成null。

 4. 使用闭包时极易形成循环引用。闭包的作用域链中保存着一些DOM 结点，而DOM，BOM 的对象在 IE 中是使用COM(C++)实现的，COM 中回收机制是引用计数策略。而在这个机制中，如果两个对象之间形成了循环引用，两个对象都无法回收。

#### 闭包封装变量

　使用闭包可以把一些不需要暴露在全局的变量封装成“私有变量”

　如有一个计算数组偶数乘积的方法：

```javascript
  let num = function(arr){
        let a = 1;
        for(let i = 0; i < arr.length; i++){
            if(arr[i] % 2 === 0){
                a *= arr[i];
            }
        }
        return a;
    }
   
    console.log( num([1,2,3,4]));//输出8
```

加入缓存机制提高函数性能,,把cache封装在num函数内部，减少页面中的全局变量，以免该变量在其他地方被修改而引发错误

封装后代码如下：

```javascript
let num = (function(){
        let cache = {};
        return function(arr){
           let args = Array.prototype.join.call(arr,',');//输出1,2,3,4
           console.log(cache[args])//第一次调用输出为undefined进行下一步计算 第二次调用输出8 直接返回
            //传入相同参数就比不必进行计算 直接返回缓存提高性能
            //判断cache缓存对象里面有args这个key值没
           if(args in cache){
                return cache[args];
            }
            //不是相同参数则进行计算
            let a = 1;
            for(let i = 0; i < arr.length; i++){
                if(arr[i] % 2 === 0){
                    a *= arr[i];
                }
            }
            return cache[args] = a;
        }
       
    })();
       
    console.log( num([1,2,3,4]));//8 进行计算
    console.log( num([1,2,3,4]));//8 返回缓存
```
#### 循环 setTimeout 与闭包
#### 闭包实现单例模式

#### 闭包实现命令模式

```

<body>
    <button id="start">打开冰箱</button>
    <button id="end">关闭冰箱</button>
    <script>
        //命令
        let Computer = {
            open(){
                alert('打开冰箱');
            },
            close(){
                alert('关闭冰箱');
            }
        }
        //创建命令执行中介
        let createCommand = function(receiver){
            //执行
            let execute = function(){
                return receiver.open();
            }
            //关闭
            let undo = function(){
                return receiver.close();
            }
            return {
                execute,
                undo
            }
        };
        //设置执行命令者
        let setCommand = function(command){
            document.querySelector('#start').onclick = function(){
                command.execute();//输出打开冰箱
            }
            document.querySelector('#end').onclick = function(){
                command.undo();//输出关闭冰箱
            }
        }
        //传入命令方法 传入执行中介 
    setCommand(createCommand(Computer));
    </script>
</body>

```
#### 闭包与模块化

模块化是建立在单例模式的基础之上的，每一个单例就是一个模块。
```
<body>

  

</body>

<script>

​    // 管理全局状态的模块，定义一个私有化成员保存所有状态，提供访问和设置这个私有变量的方法

 var module_status = (function  () {

​     var status = {

​         number:0,

​         color: null

​     }

​     var get = function (number) {

​         return status[number];

​     }

​     var set = function (number,value) {

​         status[number]= value;

​     }

​    return {

​        get: get,

​        set:set

​    }     

 })();

 // 负责背景颜色的改变

 var module_color=(function () {

​     var status= module_status;

​     var colors = ['orange','#ccc','pink'];

​     var render=function (params) {

​         var color = colors[status.get('number') % 3];

​        document.body.style.backgroundColor= color;

​        console.log(color);

​     }

​     return{

​         render:render

​     }})()

// 显示当前的number 值

var module_context = (function () {

​    var status= module_status;

​    function render(){

​        document.body.innerHTML ='this Number is'+ status.get ('number');

​            }

​    return{

​        render:render

​    }

​     

 })();

 var module_main = (function () {

   var status= module_status;

   var color= module_color;

  var context = module_context;

   setInterval(function () {

​       var newNumber = status.get('number')+1;

​       status.set('number',newNumber);

​       color.render();

​       context.render();

​       

​       

   },1000); 

 })();

</script>

```

