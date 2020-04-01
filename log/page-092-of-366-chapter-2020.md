# 复习菜鸟教程第三遍 
## Vue.js  
+ 是一套构建用户界面的渐进式框架。
+ Vue 的目标是通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件。


#### 实例
```
<!-- 展示模板 -->
<template>
  <div id="app">
    <img src="./assets/logo.png">
    <hello></hello>
  </div>
</template>
 
<script>
// 导入组件
import Hello from './components/Hello'
 
export default {
  name: 'app',
  components: {
    Hello
  }
}
</script>
<!-- 样式代码 -->
<!-- src/APP.vue -->
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<!-- src/components/Hello.vue -->
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>
 
<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: '欢迎来到菜鸟教程！'
    }
  }
}
</script>
```


```
<!-- 原来页面展示的model 是可以直接写函数，然后return 返回值的 -->
<div id="vue_det">
    <h1>site : {{site}}</h1>
    <h1>url : {{url}}</h1>
    <h1>{{details()}}</h1>
</div>
<script type="text/javascript">
    var vm = new Vue({
        el: '#vue_det',
        data: {
            site: "菜鸟教程",
            url: "www.runoob.com",
            alexa: "10000"
        },
        methods: {
            details: function() {
                return  this.site + " - 学的不仅是技术，更是梦想！";
            }
        }
    })
</script>

```


```
<!-- 原来还可以通过true、false判断css 是否使用 -->
<!-- 判断 use 的值，如果为 true 使用 class1 类的样式，否则不使用该类 -->
<div id="app">
<label for="r1">修改颜色</label><input type="checkbox" v-model="use" id="r1">
<br><br>
<div v-bind:class="{'class1': use}">
    v-bind:class 指令
</div>
</div>
    
<script>
new Vue({
    el: '#app',
data:{
    use: false
}
});
</script>
```

### 过滤器
#### Vue.js 允许你自定义过滤器，被用作一些常见的文本格式化。由"管道符"指示, 格式如下：
```
<!-- 在两个大括号中 -->
{{ message | capitalize }}

<!-- 在 v-bind 指令中 -->
<div v-bind:id="rawId | formatId"></div>

<!-- 过滤器可以串联： -->

{{ message | filterA | filterB }}

<!-- 过滤器是 JavaScript 函数，因此可以接受参数： -->
<!-- 这里，message 是第一个参数，字符串 'arg1' 将传给过滤器作为第二个参数， arg2 表达式的值将被求值然后传给过滤器作为第三个参数。 -->
{{ message | filterA('arg1', arg2) }}


<!-- 实例 ：对输入的字符串第一个字母转为大写-->

<div id="app">
  {{ message | capitalize }}
</div>
    
<script>
new Vue({
  el: '#app',
  data: {
    message: 'runoob'
  },
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
})
</script>

```

### 计算属性关键词: computed。
```
<div id="app">
  <p>原始字符串: {{ message }}</p>
  <p>计算后反转字符串: {{ reversedMessage }}</p>
</div>
 
<script>
var vm = new Vue({
  el: '#app',
  data: {
    message: 'Runoob!'
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
})
</script>

<!-- 实例中声明了一个计算属性 reversedMessage 。
提供的函数将用作属性 vm.reversedMessage 的 getter 。
vm.reversedMessage 依赖于 vm.message，在 vm.message 发生改变时，vm.reversedMessage 也会更新。 -->
```

### computed vs methods
- 我们可以使用 methods 来替代 computed，效果上两个都是一样的，但是 computed 是基于它的依赖缓存，只有相关依赖发生改变时才会重新取值。而使用 methods ，在重新渲染的时候，函数总会重新调用执行。
- 可以说使用 computed 性能会更好，但是如果你不希望缓存，你可以使用 methods 属性。

### Vue.js 监听属性  这块还是有点小疑虑
##### 
```
<div id = "computed_props">
    千米 : <input type = "text" v-model = "kilometers">
    米 : <input type = "text" v-model = "meters">
</div>
<p id="info"></p>
<script type = "text/javascript">
    var vm = new Vue({
    el: '#computed_props',
    data: {
        kilometers : 0,
        meters:0
    },
    methods: {
    },
    computed :{
    },
    watch : {
        kilometers:function(val) {
            this.kilometers = val;
            this.meters = this.kilometers * 1000
        },
        meters : function (val) {
            this.kilometers = val/ 1000;
            this.meters = val;
        }
    }
    });
    // $watch 是一个实例方法
    vm.$watch('kilometers', function (newValue, oldValue) {
    // 这个回调将在 vm.kilometers 改变后调用
    document.getElementById ("info").innerHTML = "修改前值为: " + oldValue + "，修改后值为: " + newValue;
})
</script>
```

### Vue.js 样式绑定
- Vue.js v-bind 在处理 class 和 style 时， 专门增强了它。表达式的结果类型除了字符串之外，还可以是对象或数组。
```
<!-- 实例中将 isActive 设置为 true 显示了一个绿色的 div 块，如果设置为 false 则不显示： -->

<div v-bind:class="{ active: isActive }"></div>
```

```
<!--  -->
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://cdn.staticfile.org/vue/2.2.2/vue.min.js"></script>
</head>
<body>
<div id="app">
	<div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }">菜鸟教程</div>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    activeColor: 'green',
	fontSize: 30
  }
})
</script>
</body>
</html>
```

### 事件处理器
##### 修饰符
- .lazy     在默认情况下， v-model 在 input 事件中同步输入框的值与数据，但你可以添加一个修饰符 lazy ，从而转变为在 change 事件中同步：
- .number   如果想自动将用户的输入值转为 Number 类型（如果原值的转换结果为 NaN 则返回原值），可以添加一个修饰符 number 给 v-model 来处理输入值
- .trim     如果要自动过滤用户输入的首尾空格，可以添加 trim 修饰符到 v-model 上过滤输入： eg：<input v-model.trim="msg">


[截止，有空在更](https://www.runoob.com/vue2/vue-component.html "Vue 组件")