# Vue
根据官网学习如何使用Vue

官网地址https://cn.vuejs.org/v2/examples/grid-component.html

GitHub：https://github.com/vuejs/vue/releases

vue 是一套构建用户界面的渐进式框架，它采用自底向上增量开发设计，它的核心库只关注视图层。

一、指令带有前缀 v-，以表示它们是 Vue 提供的特殊属性。

v-bind：将这条指令绑定的元素节点的title属性和 Vue 实例的 message 属性保持一致，如下：

<table><tbody><tr><td ><pre><div class="line"><span>&lt;<span class="name">div</span> <span>id</span>=<span class="string">"app-2"</span>&gt;</span></div><div class="line">  <span>&lt;<span class="name">span</span> <span>v-bind:title</span>=<span class="string">"message"</span>&gt;</span></div><div class="line">    鼠标悬停几秒钟查看此处动态绑定的提示信息！</div><div class="line">  <span>&lt;/<span class="name">span</span>&gt;</span></div><div class="line"><span>&lt;/<span class="name">div</span>&gt;</span></div></pre></td></tr></tbody></table>

<table><tbody><tr><td><pre><div class="line"><span class="keyword">var</span> app2 = <span class="keyword">new</span> Vue({</div><div class="line">  <span>el</span>: <span class="string">'#app-2'</span>,</div><div class="line">  <span>data</span>: {</div><div class="line">    <span>message</span>: <span class="string">'页面加载于 '</span> + <span class="keyword">new</span> <span class="built_in">Date</span>()</div><div class="line">  }</div><div class="line">})</div></pre></td></tr></tbody></table>

v-if：条件 ，v-if=“true/false”

v-for：循环 ，v-for=“todo in todos” ，todos是list， .todos.push({ text:'XXX'})给list里添加一个新项。

v-on：可以用来绑定一个事件监听器，如下：

<table><tbody><tr><td><pre><div class="line"><span>&lt;<span class="name">div</span> <span>id</span>=<span class="string">"app-5"</span>&gt;</span></div><div class="line">  <span>&lt;<span class="name">p</span>&gt;</span>{{ message }}<span>&lt;/<span class="name">p</span>&gt;</span></div><div class="line">  <span>&lt;<span class="name">button</span> <span>v-on:click</span>=<span class="string">"reverseMessage"</span>&gt;</span>逆转消息<span >&lt;/<span class="name">button</span>&gt;</span></div><div class="line"><span >&lt;/<span class="name">div</span>&gt;</span></div></pre></td></tr></tbody></table>

<table><tbody><tr><td><pre><div class="line"><span class="keyword">var</span> app5 = <span class="keyword">new</span> Vue({</div><div class="line">  <span>el</span>: <span class="string">'#app-5'</span>,</div><div class="line">  <span>data</span>: {</div><div class="line">    <span>message</span>: <span class="string">'Hello Vue.js!'</span></div><div class="line">  },</div><div class="line">  <span>methods</span>: {</div><div class="line">    <span>reverseMessage</span>: <span class="function"><span class="keyword">function</span> (<span class="params"></span>) </span>{</div><div class="line">      <span class="keyword">this</span>.message = <span class="keyword">this</span>.message.split(<span class="string">''</span>).reverse().join(<span class="string">''</span>)</div><div class="line">    }</div><div class="line">  }</div><div class="line">})</div></pre></td></tr></tbody></table>

v-model：实现表单输入和应用状态之间的双向绑定。

v-once：一次性插入值，当数据改变时，插值处的内容不会更新。但请留心这会影响到该节点上所有的数据绑定。

v-html：双大括号会将数据解释为纯文本，而非 HTML 。为了输出真正的 HTML 需要此指令。被插入的内容都会被当做 HTML —— 数据绑定会被忽略。注意，你不能使用 v-html 来复合局部模板，因为 Vue 不是基于字符串的模板引擎。组件更适合担任 UI 重用与复合的基本单元。

二、组建系统是Vue的一个重要的概念，因为它是一种抽象，允许我们使用小型、自包含和通常可复用的组件构建大型应用。几乎任意类型的应用界面都可以抽象为一个组件树。

在Vue里，一个组件本质上是一个拥有预定义选项的一个Vue实例，在Vue中注册组件方式如下：

<table><tbody><tr><td><pre><div class="line"><span class="comment">// 定义名为 todo-item 的新组件</span></div><div class="line">Vue.component(<span class="string">'todo-item'</span>, {</div><div class="line">  <span>template</span>: <span class="string">'&lt;li&gt;这是个待办项&lt;/li&gt;'</span></div><div class="line">})</div></pre></td></tr></tbody></table>

如果想要将数据从父作用域传到子组件，需要修改一下组件定义，使之能够接受一个属性，写法如下：

<table><tbody><tr><td><pre><div class="line">Vue.component(<span class="string">'todo-item'</span>, {</div><div class="line">  <span class="comment">// todo-item 组件现在接受一个</span></div><div class="line">  <span class="comment">// "prop"，类似于一个自定义属性</span></div><div class="line">  <span class="comment">// 这个属性名为 todo。</span></div><div class="line">  props: [<span class="string">'todo'</span>],</div><div class="line">  <span>template</span>: <span class="string">'&lt;li&gt;{{ todo.text }}&lt;/li&gt;'</span></div><div class="line">})</div></pre></td></tr></tbody></table>

使用方式：

<table><tbody><tr><td><pre><div class="line"><span>&lt;<span class="name">ol</span>&gt;</span></div><div class="line">  <span class="comment">&lt;!-- 创建一个 todo-item 组件的实例 --&gt;</span></div><div class="line">  <span >&lt;<span class="name">todo-item</span>&gt;</span><span >&lt;/<span class="name">todo-item</span>&gt;</span></div><div class="line"><span >&lt;/<span class="name">ol</span>&gt;</span></div></pre></td></tr></tbody></table>

将数据从父作用域传到子组件的使用方式：

<table><tbody><tr><td><pre><div class="line"><span>&lt;<span class="name">div</span> <span>id</span>=<span class="string">"app-7"</span>&gt;</span></div><div class="line">  <span >&lt;<span class="name">ol</span>&gt;</span></div><div class="line">    <span class="comment">&lt;!-- 现在我们为每个todo-item提供待办项对象    --&gt;</span></div><div class="line">    <span class="comment">&lt;!-- 待办项对象是变量，即其内容可以是动态的 --&gt;</span></div><div class="line">    <span>&lt;<span class="name">todo-item</span> <span>v-for</span>=<span class="string">"item in groceryList"</span> <span>v-bind:todo</span>=<span class="string">"item"</span>&gt;</span><span>&lt;/<span class="name">todo-item</span>&gt;</span></div><div class="line">  <span >&lt;/<span class="name">ol</span>&gt;</span></div><div class="line"><span >&lt;/<span class="name">div</span>&gt;</span></div></pre></td></tr></tbody></table>

<table><tbody><tr><td class="code"><pre><div class="line"><span class="keyword">var</span> app7 = <span class="keyword">new</span> Vue({</div><div class="line">  <span class="attr">el</span>: <span class="string">'#app-7'</span>,</div><div class="line">  <span class="attr">data</span>: {</div><div class="line">    <span class="attr">groceryList</span>: [</div><div class="line">      { <span class="attr">text</span>: <span class="string">'蔬菜'</span> },</div><div class="line">      { <span class="attr">text</span>: <span class="string">'奶酪'</span> },</div><div class="line">      { <span class="attr">text</span>: <span class="string">'随便其他什么人吃的东西'</span> }</div><div class="line">    ]</div><div class="line">  }</div><div class="line">})</div></pre></td></tr></tbody></table>
