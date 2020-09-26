## css3学习

# backgroud
> 复合属性
```css
/*
图片路径 background-image: url();  或者渐变 linear-gradient()
图片大小 background-size
图片重复 background-repeat

复合属性写法
url  position/size no-repeat, cover
         

*/

div{
    background:
}

```

# box 
> box-sizing

> overflow

> flex 

```css
/*
父级设置display flex
其他设置在父级的属性
flex-direction

*/
div{
    display:flex
}



```


# text1
> text-shadow

# transition
> 过渡动画
```css
    /*transition  从某个状态过渡到某个状态 参数
    第一个过渡属性 
    第二个过渡时间
    第三个过渡方式(曲线)
    延迟时间*/
.div{
    transition:all 2s linear 1s
}
/*
状态过渡  鼠标移入
*/
    
```

# animation
> 动画 

```css
/*
参数   
    动画名称
    时间
    运动曲线
    延迟
    执行次数 2 数字 或者 infinity  
    执行方向 alternate


*/
@keyframes run{
    0%{
        left:0px;
        top:0px;
    }
    25%{

    }

}
/* 0%from to 100%*/

```
> 动画里面的  运动区县可以替换成 setp

```css
#app{
    animation: run 10s linear infinite alternate both;
}
/*替换成*/

#app{
    animation: run 10s steps(1,end) infinite alternate both;
}
/*
 steps(1,end); 每个步骤需要走几步
*/
```


# transform

> 具体属性  rotate 旋转

```css
div{
    transform:rotate(30deg)
}
/*
rotateX
rotateY
rotateZ
rotate3D
*/


```

> scale 伸缩
```css
div{
    transform:scale(2,3);
}
scalex
scaley
scalez
scale3d

```

> skew 倾斜

> translateX 