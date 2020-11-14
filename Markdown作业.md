<h1 align = "center">
    拼图小游戏
</h1>
[TOC]



## 内容

### 1、游戏介绍

拼图作为为一种广泛流传的智力小游戏，几百年来深受人们喜爱，而此拼图小游戏正是对人们所玩拼图实物的模拟。在这里你不  仅能体验拼图的乐趣，还能欣赏精美的图片，快点击进入你的旅程吧——→[游戏入口](小游戏1(1).html)

> > ***

### 2、游戏教程  

（1）进入网页后会弹出一个小窗口，点击“确定”或右上方即可关闭窗口。  

（2）在开始游戏前，你应该点击左上方“查看图片”查看图片按钮，查看完整的图片。  

（3）当你准备好后，即可点击左上方”开始“按钮，网页拼图左框会出现所有拼图，同时游戏开始计时，并会有时间显示出来。  

（4）你需要将拼图从左方拖放至在右框你所认为的位置，拼图一旦移入右框后，你可以再将它拖动回原来的框，或在右框框内继续拖动。  

（5）拼好了之后，可以点击左上方“提交”按钮，查看结果。  

（6）若你拼图成功，则停止计时，并可以看见你所用的时间

（7）若你拼图错误，可以继续拼图，多次提交，直至正确。  

> > ***

### 3、游戏代码

（1）绘制方框与放置图片，使用html与css渲染。 

 以下是右大方框的样式

![](C:\Users\86132\Desktop\作业\新建文件夹 (5)\代码1.png)    

以下是将图片放置到容器中

![](C:\Users\86132\Desktop\作业\新建文件夹 (5)\代码2.png)  

样式中也把图片的属性`display`设置为`none`，将其隐藏不可见

![](C:\Users\86132\Desktop\作业\新建文件夹 (5)\代码3.png)  

当点击开始时将会把图片`display`属性更改为`block`，图片可见  

![](C:\Users\86132\Desktop\作业\新建文件夹 (5)\代码4.png) 

（2）拖拽图片  

拖拽图片通过以下函数实现:  

~~~
  function allPrevent(event) {

​    event.preventDefault();

  }



  function allDrag(event) {

​    event.dataTransfer.setData("Text", event.target.id);



  }

  

  function allDrop(event) {

​    event.preventDefault();

​    if (event.target.nodeName !="DIV"||event.target.children.length>0){ 

​       return

​    }

​    var data = event.dataTransfer.getData("Text");

​    event.target.appendChild(document.getElementById(data));

  }
~~~

​    

该过程中涉及了属性`draggable`、`ondragstart`、`ondrop`、`ondragover`，方法`setData() `、`preventDefault()`、`getData()`、`getElementById()`、`appendChild()`  

图片的`draggable`设置为`true`后可拖动，而当开始拖动时，则调用了函数`allDrag(event)`设置被拖动图片的数据类型（text）和值（图片的id），当图片将拖动完成时，调用了函数`allDrag(event)`，阻止数据的浏览器默认处理方式（drop 事件的默认行为是以链接形式打开），当图片要放置在相应的框时，则调用了函数`allDrop(event)`，将之前的数据追加到父级标签的放置元素中。如果要放置图片的容器已经有了图片，则不能再将图片放置其中。  

（3）计时  

以下关于计时的代码  

```
int=setInterval(clock,1000)

​    clock()

  }

  

  function clock(){

​    if (second < 59){

​      second+=1

​    }

​    else{

​      second-=59

​      minute+=1

​    }

​    gametime=minute+"："+second

​    document.getElementById("clock").value=gametime

​    

  }
```

~~~
if (a ==1 && b==2 && c==3 && d==4 && e==5 && f==6 && g==7 && h==8 && i==9){

​      alert("恭喜，您拼对了")

​      clearInterval(int)
~~~

使用了方法`setInterval()`、`clearInterval()`，每过一秒则执行一次函数`clock()`，`gametime`即为使用时间。  

而当提交结果正确时，则调用方法`clearInterval()`，停止计时。