[toc]
# webpack

## 入口 出口基本配置 

- webpack.config.js
```js 
module.exports={
    entry:{
        main:'./src/index.js'  /*主入口  */
        "a":'' /*配置多个chunk  filename 要动态 使用chunkhash  hash*/
    },
    output:{
        path:"", /*绝对路径*/
        filename:""
    }
} 

```
 entry 入口 配置的是 chunk,配置 webpack打包的时候解析的入口文件，  可以配置多个入口文件

## 出口,入口的最佳实践

- 每个页面都有一个js
    每个页面 出口一个js 
```js
module.exports={
    entry:{
        pageA:'pageA.js',
        pageB:'pageB.js'
    },
    output:{
        filename:'[name][chunhash].js'
    }
}


```
## loader
- 将源码通过函数进行转换  

```js
/* loader  配置*/
module.exports={
    module:{
        rules:[{
            test:`匹配模块路径`,
            use:[{
                loader:'规则1',
                options:{

                }
            }]
        }]

    }
}

```

- css样式处理 (练习 写一个css处理 loader)


## plugins

```js
var MyPlugin = require("./plugins/MyPlugin")

module.exports = {
    mode: "development",
    watch: true,
    plugins: [
        new MyPlugin()
    ]
}
```


## 其他配置

- context 
路径配置 绝对路径 配置 webpack中 entry跟laoder里面的path
- library libraryTarget 
配置webpack打包出来的 结果 变量定义
- target 目标环境 


## 常用配置

- clean-webpack-plugin 清除工作目录
- html-webpack-plugin  生成html目录
- copy-webpack-plugin 复制静态资源
- webpack-dev-server


## Postcss

- postcss-preset-env

- 添加 .browerlistrc 文件
```js
last 3 version
> 1%
not ie <= 8

```
- state

- postcss-apply

> webpack中使用postcss
    postcss postcss-loader