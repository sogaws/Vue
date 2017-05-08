# Vue
根据官网学习如何使用Vue

官网地址https://cn.vuejs.org/v2/examples/grid-component.html

GitHub：https://github.com/vuejs/vue/releases

vue 是一套构建用户界面的渐进式框架，它采用自底向上增量开发设计，它的核心库只关注视图层。

指令带有前缀 v-，以表示它们是 Vue 提供的特殊属性。

v-bind：将这条指令绑定的元素节点的title属性和 Vue 实例的 message 属性保持一致

<div id="app-2">
  <span v-bind:title="message">
    鼠标悬停几秒钟查看此处动态绑定的提示信息！
  </span>
</div>

var app2 = new Vue({
  el: '#app-2',
  data: {
    message: '页面加载于 ' + new Date()
  }
})

