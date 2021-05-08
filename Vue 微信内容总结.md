## Vue 微信内容总结

#### 1. $event

```vue
<div id="app">
  <!-- <button @click='foo'></button> -->
  
  <!-- 当传递参数时，若要同时拿到事件对象可以传入$event -->
  <button @click='foo(a,$event)'></button>
</div>

```

```javascript
const app = new Vue({
  el:"#app",
  methods:{
    // 函数没有传递实参时传递参数，默认传递事件对象
    //foo(e){
    //  console.log(e)
    //}
    
    foo(a,event){
      console(a,event)
    }
  }
})
```

> - $event 对象是当 某个元素执行事件时既有实参也要有事件对象，可以通过$event

#### v-for中key

Vue: v-for的键值key

 https://blog.csdn.net/qq_41609404/article/details/84064064?utm_source=app&app_version=4.5.2

> v-for中的key是标记dom节点的唯一标识符，不推荐使用index当做key
>
> 通常拿元素的独一无二的值当做标识符，这样可以提高渲染效果，提高性能

