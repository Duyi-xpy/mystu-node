[toc]
# vue-router的使用学习笔记

## vue-router
- vue路由:方便于组件之间的切换
```js
    多个组件在同一个页面当中需要进行切换 腾讯课堂
```
- 具体实现
```js 
配置文件
 import Vuex from 'vuex';
 import Vue from 'vue';

 Vue.use(Vuex);
const routes=[{
    path:'/stu',
    component:()=> import('/cmp/stu'),
}]


 const router = new Vuex({
    routes,
    mode:'history'
 })

 export default router

Vue具体页面
import router from '配置文件'

new Vue({
    el:'#app',
    router
})

```
- 组件内使用
```js
    <router-link to="/stu"/>   /* 具体的链接地址*/
    <router-view /> /*内容显示*/
```
- 路由引出的其他便捷处理 
 >路由命名
    1、路由配置 新增name属性 给路由进行名称配置

 >嵌套路由
    多重路由嵌套，在原先的路由配置中 新增children属性继续配置

 >路由重定向
    redirect  访问a路由 重定向到b路由
 
 >路由元信息
    1、有时候并非使用router-link标签进行路由跳转
    可以使用 router route对象进行路由跳转 .pusu replace方法

 >动态路由：
    接收路由参数  /stu/:id id为路由源信息的params 参数列表 通过参数列表可以进行匹配路由

 >其中的css属性
    1、router-link-excact-active
    2、router-link-active

- vue-router 命名视图
  具体内容:
```js
    <router-view /> /* 可以配置多个路由视图 并且进行name匹配*/
    <router-view name="xpy"/>
    <router-view name="wzd"/>
    <router-view name="ysh" />

/*进行路由配置的过程中,将组件配置到对应的视图中去
说明到对应的视图才会显示对应的组件*/
    routes=[{
        path:"stu",
        components:{
            xpy:import('./cmp')
        }
    }]
 
```

## vue-router路由守卫  

- 在路由使用的过程中对 具体的是否要进行跳转
 
- 全局导航守卫
 > beforeEach

 ```js
    to from next 
    去哪里 ,来自哪里,是否跳转
 ```
 > beforeResolve

 > afertEach
 
- 单个路由独享的路由守卫

> beforeEnter

- 组件内部守卫
> beforeRoutedEnter

> beforeRouteUpdate

> beforeRouteLeave


# 路由守卫的过程
 > 路由信息匹配

 > 离开的路由调用beforeRoutedleave

 > beforeEach

 > 判断是否组件被复用 复用调用 beforeRouteUpdate

 > 调用单个路由的beforeEnter

 > 异步加载路由元
 
 > beofreRouteEnter

 > beforeResolve
 
 > 路由被确认

 > 确定之后加载全局的 afterEach

 > dom更新

 > 创建好的实力 调用beforeRouterEnter的回调函数
 

 
