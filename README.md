# UEditor富文本编辑器

https://github.com/fex-team/ueditor

[文档](http://fex.baidu.com/ueditor/)

## iframe使用

``` 

<iframe class="ueditor" id="ueditor" src="index.html" frameborder="no" border="0" marginwidth="0" marginheight="0"
    scrolling="no" allowtransparency="yes"></iframe>
```

* 设置html内容、获取html内容、监听内容变化、初始化完成事件

``` 

var ueIframeWin = document.getElementById("editormd").contentWindow;
setTimeout(function () {
    //设置html内容
    ueIframeWin.postMessage({
        method: 'setContent',
        content: '<p>Hello UEditor</p>'
    }, "*");
    //获取html内容
    ueIframeWin.postMessage({
        method: 'getContent'
    }, "*");

    //监听子页面返回
    window.addEventListener("message", function (event) {
        let data = event.data;
        switch (data.method) {
            case 'setContent': //设置内容返回
                console.log(data.content);
                break;
            case 'getContent': //获取html内容返回
                console.log(data.content);
                break;
            case 'onload': //初始化完成
                console.log(data.content);
                break;
            case 'onchange': //内容改变事件
                console.log(data.content);
                break;
        }
    }, false);
}, 100);
```
