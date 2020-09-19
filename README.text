对Vue的总结

一、Vue的构造函数
    通过  new Vue()其中的el属性配置 或者 产生的实例的$mount方法进行注册。
二、插值表达式
    {{}}  被vue所绑定的区域块内 使用插值语法
    js运算、基本的数据类型 数据、对象  不可以是js逻辑语句 
三、vue的响应式原理
    Object.defineProperty
    (1)、将每个vue中data的属性值挂载到 vue的实例上称谓实例的成员属性
    对成员属性进行数据劫持 数据监控。
    (2)、具体细节：
        深度劫持(类似深度克隆) ， 对每个key跟  value进行数据判断
        判断该属性对应的值是否为基本数据类型 typeof  为 object的时候继续循环绑定
        对typeof object的数据 进一步判断是否 继承自arrary  如果值所属类型为数组，
        对数组将不进行深度绑定，而是给该数据的__proto__  赋予 新创建出来并改写 的Array.prototype
        数组的变异方法。
        const arr  = Array.prototype.
        const obj = Object.create(arr);新创建一个对象 该对象的原型为 arr
        改写obj中的方法
            obj.push = function(){
                arr.push.apply(this,...arguments);
                //执行原先克隆出来的数组方法 在执行属性方法之后 进行数据渲染 响应式
                render();
            }
        key value, data
        var temp=value;
        Objcet.definePropertye(data,key,{
            set(newVal){
                temp = newVal;
                render();
                return temp;
            },
            get(){
                render()
                return temp;
            }
        })
        衍生出来的vue的设置对象的方法 vm.$deleted vm.$set 对象 key  设置的内容
    (3)、补充:
        数据更新机制.
            数据更新是异步更新 通过$nextTick(){} 监控数据完成之后的回调函数 
            new Promise((res,rej)=>{
                res(1);
            }).then(data=>{
                执行回调方法
            })
            setimmediately
            或者 setTimeout

四、vue的指令  写在html行间的特性
    1、内容相关的:v-html  v-text
    显示相关的:v-if v-else-if v-else v-show
    绑定属性相关的:v-bind : v-on @
    v-once 渲染一次  v-cloak防止闪烁 v-pre 数据不进行vue编译
    v-for 循环
    v-model 数据的双向绑定
    v-slot #
    指令的修饰符
        v-bind :  .camel 大小写 .sync 
        v-on @ .once .lazy  prevent stop self 
    
    2、指令的一些特殊使用 v-if v-else-if v-else 可以使用 template模板  具体是元素的重新生成与删除
        v-show元素已经生成 display属性进行更改
五、vue实例中的其他配置属性
    1、data
        data属性挂载了 在 vue创建过程中已经绑定的成员属性
    2、computed 计算属性
        数据响应式 对应计算属性劫持的key的值发生了 变化 computed中的方法也将对应进行改变
    3、watch 数据监控
        监控数据发生了变化后执行的步骤 可以异步
    4、methods:方法 vue实例中需要执行的一些具体方法

六、生命周期
    beforeCreate 实例创建之前。 什么都没做 数据劫持 watch都没进行 监控
    created 实例已经创建好了  此时有this 属性并且可以 数据劫持 watch 此时的this.$el属性为undefined
    beforeMount 挂载之前  this.$el 有值 但是是未渲染编译的旧模板 {{}}仍看得见  这时候可以进行异步处理
    mounted已经挂载 this.$el 是新模板 且替换html中el的innerHtml 异步处理
    beforeUpdate 数据更新的前一步
    updated 数据更新后
    beforeDestory 组件销毁之前
    Destoryed  组件销毁之后



七、组件component
    1、新建组件  Vue.component 或者实例中的components属性
    Vue.componet('cmp',{
        template:``,
        data(){
            return{

            }
        }
    }
    2、组件跟vue实例的主要区别
        data属性 vue实例是对象 组件是函数执行产生对象。 避免组件重复使用引用出现问题。
    3、组件间的通信
        (1)、prop  非prop特性
            父组件中模板中使用了 子组件。并且在子组件注册了属性特性 ，值用的是自身的data 属性或者prop传递过来的属性
            子组件通过props注册 props:['mynma'],就能直接使用
            传递过来的属性特性没有进行props注册的即为非props特性 。可以通过this.$attrs 获取得到。 inheritProps 属性设置为false 
        (2)、$emit  父组件注册时间，子组件触发父组件注册的事件  
            父:<cmp @click="changeData"/>
            子组件: cpm中  <button @click="@emit("changeData",$event,'2')"></button> 其中第一个参数为事件名，第二个会事件源对象
            通过事件注册引出第三个v-model,
            注册事件存在情况， 不是注册在根元素，需要在组件内的后代元素中。 $listeners访问
        (3)、v-model 绑定了 v-model="5" 等价于 :value="5"  并且监听 onInput事件 使得 value=事件传递过来的参数
             子组件中  props注册value值,使用value值 <input :value="5", @input="@emit('onIput',$event.target.value)">

            .sync 跟v-model相同的语法糖。 其中v-model是绑定了value属性
            如果使用.sycn绑定的数据 等价于 :name.sync="xpy"  v-model中的被绑定的属性为 name。 绑定方法 update:name
        (4)、$children $parent $root  边界情况
        (5)、provide inject 父组件注册 后代元素可以跨组件
        (6)、事件总线 eventBus  vm.$eventBus = new Vue();
        (7)、vuex
        (8)、slot插槽  #忘记点#
        (9)、ref引用  $refs  #忘记点#
    4、mixin混入 配置混合
    5、filter 过滤 {{ name | demo }} demo为过滤方法
八、自定义指令  directive 
        事件函数 钩子函数
    Vue.directive('指令名',{

    });

九、














