# fly-html
html/css

## 事件

```html
<div>
    <button></button>
</div>
```

冒泡处理：从触发的 dom ,向上冒泡处理。button->div->body->html

捕获处理：与冒泡处理相反。html->body->div->button

### 事件分类

```html
<button id="btn"></button>
```

- dom0 级事件添加
```js
// dom0 级事件添加，只能绑定一个事件
const btn = document.getElementById('btn');
btn.onclick = (e) => {
  console.log(e);
  alert(e.target.value);
};
```
- dom2 级事件添加

```js
// dom2 级事件添加，可以绑定多个
const btn2 = document.getElementById('btn2');
btn2.addEventListener('click', (e) => {
  alert(e.target.value + '11');
});
```

- ie 事件添加

### 事件处理

```html
<!DOCTYPE html>
<html lang="zh-CN">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta http-equiv="X - UA - Compatible " content="ie = edge ">
    <title>测试事件冒泡</title>
</head>

<body>
    <div id="div1">
        <button id="btn1">点击button</button>
    </div>

    <a id="a1" href="event.html" target="_blank">跳转 event.html</a>
    <script>
        const div1 = document.getElementById('div1');
        div1.onclick = (e) => {
            alert(`div 触发的事件`);
        };

        const btn1 = document.getElementById('btn1');
        btn1.addEventListener('click', (e) => {
            alert(`button 触发的事件：${e.target.innerText}`);
            // 阻止事件传播,不会触发 div->body->html 事件
            e.stopPropagation();
        });

        const a1 = document.getElementById('a1');
        a1.addEventListener('click', (e) => {
            alert(e.target.href);
            // 阻止事件的默认行为，a 标签将不会跳转到 event.html
            e.preventDefault();
        });
    </script>
</body>
</html>
```

e.target:获得触发事件的目标对象

e.type: 获取事件类型

e.preventDefault：阻止事件的默认行为

e.stopPropagation()：阻止事件传播