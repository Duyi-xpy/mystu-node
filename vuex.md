[toc]
# Vuex

## vuex学习

```js
    import Vue from 'vue';
    import Vuex from 'vuex';

    Vue.use(Vues);

    const store = new Vuex.Store({
        state:{
            count:0,
        },
        getters:{

        },
        mutations:{

        }
    });

    new Vue({
        store
    })

```

## mapState函数

## mapGetters函数

## mutations
```js
注册mutations函数，
子组件修改状态的时候通过 提交mutation
    提交方法
    this.$store.commit('handler');

```

## mapMutations

## payload 额外参数


## Action 
 > store.dispatch
