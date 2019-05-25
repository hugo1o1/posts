```javascript
<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">
    
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <meta http-equiv="X-UA-Compatible" content="ie=edge">

​    <title>hello world- react</title>

    <script src="../build/react.development.js"></script>
    
    <script src="../build/react-dom.development.js"></script>
    
    <script src="../build/babel.min.js"></script>

</head>

<body>

    <div id="example"></div>
    
    <script type= "text/babel">


​        ReactDOM.render(

​            <h1>hello,world</h1>,

​            document.getElementById('example')

​        );

​        

​        </script>

</body>

</html>
```

上面代码一共用了三个库： `react.js` 、`react-dom.js` 和 `Browser.js` ，它们必须首先加载。其中，`react.js` 是 React 的核心库，`react-dom.js` 是提供与 DOM 相关的功能，`Browser.js` 的作用是将 JSX 语法转为 JavaScript 语法，这一步很消耗时间，实际上线的时候，应该将它放到服务器完成。