[toc]

# less

## less 学习

- 变量
```less
@height: 140px
@heighter: @heigher+20px;
body{
    height:@heighter
}

```
- 混入
```less
/*定义好一个样式，
其他选择器内可以直接引用 .color();
*/
.demo{
    position:absolute;
    left:50%;
    top:50%;
    transform:translate(-50%,-50%);
}

/*  其他样式表里面
*/

body{
    height:100px;
    .demo():
}


```

- 嵌套(可以嵌套子元素)
``` less
/*  嵌套意思等于  前面加上父级元素
    &和的意思
*/
div{
    background:red
    #app{
        background:green;
    }
    
    &::after(
        display:block;
        content:'',
        clear:both
    )


}


```
- 运算  

> 定义的变量可以进行 + - * /

- 函数 darken(颜色加深函数)

- 作用域
> 类似变量定义有作用域 。@name 定义在全局或者 局部

- 注释  /**/  //

- 导入 @import