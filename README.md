# gshop

> A Vue.js project

## 项目开发准备
``` bash

# 项目描述

前后端分离SPA应用，外卖，功能模块，主要技术，开发模式：模块化，组件化，工程化，
此项目为外卖 Web App (SPA)
2) 包括商家, 商品, 购物车, 用户等多个子模块
3) 使用 Vue 全家桶+ES6+Webpack 等前端最新最热的技术
4) 采用模块化、组件化、工程化的模式开

# 技术选型（技术架构）

1. 前台应用的一些数据展示，交互用了VUE全家桶（vue技术站），2. 前后台交互ajax请求promise，测试接口postman，3. es6等模块化 4. 工程化用到了脚手架

# API接口
url，请求方式，请求参数的格式，响应书籍的格式的集合


```
### 开启项目开发

``` bash
# 脚手架开发
npm install -g vue-cli
npm install -g vue-c
cd gshop
npm install
npm run de
# install dependicies

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```
### 搭建项目整体界面结构
``` bash
# stylus理解和使用
结构化，变量，函数/minxin

# vue-router的理解和使用
$router:路由器对象，包含一些操作路由的功能函数，，来实现编程式导航（跳转路由）
$route:当前路由对象，一些当前路由信息数据的容器，path/meta/query/params
项目路由拆分
底部导航组件：FooterGuide
导航路由组件：Msite/Search/Order/Profile

```
### 抽取组件
头部组件：HeadTop，通过slot来实现组件通信标签结构
商家列表组件： ShopList

### 登陆路由组件
静态组件
FooterGuide的显示/隐藏：通过路由的meta

### 后台项目
启动后台项目：
后台之前vagrantfile设置了private network，所有的localhost都要统一改地址

### 前后台交互
ajax请求库：axios
ajax请求函数封装：axios + promise
接口请求函数封装： 每个后台接口

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

git init
 git add *
  git commit -m "init gshop"  
   git remote add origin https://github.com/RileyCode-hash/2105_gshop.git
    git push origin master

### http://eslint.org/docs/rules/comma-dangle  Unexpected trailing comma， 分号， 双引号号等与eslint格式冲突
首页-》 setting --》 vetur里面打开setting.json
 "prettier": {
            "semi": false, // 取消分号
            "singleQuote": true, // 单引号
            "trailingComma": "none" // 取消最后的逗号
        }


----



# vue学习笔记

## el 選項
````bash
<div id = "app></div>
var app = new Vue({
  el: '#app'
})
````
连接在一起，存取<div id = “app></div>的元素， 可以通过app.$e1来进行存取

## data 

在Vue中建立data的選項，將可能會用到的資料全部放到data之中，方便我們維護。
````bash
var app = new Vue({
  el:'#app',
  data: {
    name: 'andy'
  }
})
console.log(app.name); // andy
// 修改資料
app.name = 'alex';
console.log(app.name); // alex
````
## data中定義一個名為car的資料，只要在視圖中使用{{car}} 就能顯示出car的資料內容
````bash
<body>
    <div id="app">
        {{ car }}
    </div>
</body>
<script>
var app = new Vue({
       el: '#app',
       data: {
           car: 'toyota';
       }
   })
````

## html而非將資料解釋後的純文字，可以使用v-html
````bash
<body>
    <div id="app">
        <span v-html="link"></span>
    </div>
</body>
<script>
var app = new Vue({
       el: '#app',
       data: {
           link: '<a href="#"> html webpage </a>'
       }
   })
</script>
````
## 侦听属性watch：
不支持缓存，数据变，直接会触发相应的操作；
watch支持异步；
监听的函数接收两个参数，第一个参数是最新的值；第二个参数是输入之前的值；
当一个属性发生变化时，需要执行对应的操作；一对多；
监听数据必须是data中声明过或者父组件传递过来的props中的数据，当数据变化时，触发其他操作，函数有两个参数：
immediate：组件加载立即触发回调函数执行

````bash
watch: {
  firstName: {
    handler(newName, oldName) {
      this.fullName = newName + ' ' + this.lastName;
    },
    // 代表在wacth里声明了firstName这个方法之后立即执行handler方法
    immediate: true
  }
}
````
## 格式化文本，我們可以添加” | ”對資料進行過濾
````bash
<body>
    <div id="app">
       {{name | toUpper}}
    </div>
</body>
<script>
var app = new Vue({
       el: '#app',
       data: {
           name: 'Andy'
       },
       filters:{
           toUpper:function(obj){
               return obj.toUpperCase();
           }
       }
   })
</script>
````
## v-bind v-on
````bash
<a v-bind:href="url"></a>
：
<a :href="url"></a>

<button v-on:click="handleClick"></button>
：
<button @click="handleClick"></button>
````
##  v-text / v-html
````bash

<body>
    <div id="app">
        <p v-html="note"></p><br>
        <p v-text="note"><i></i></p>
        <p><i>{{note}}</i></p>
    </div>
</body>
<script>
var app = new Vue({
       el: '#app',
       data: {
        note: '<a href="#">连接网页</a>'
       }
   })
</script>
````
结果1： 蓝字：连接网页

结果2：a href="#">连接网页</a

结果3：i>a href="#">连接网页/a></i (斜体)

v-html將note的內容直接渲染出來
v-text將note的內容原封不動顯示出來，並直接忽略<i>標籤
{{}}與v-text不同的是，他有保留<i>標籤，因此字體為斜體

##  v-cloak 网速慢时DOM中的{{}}会显示出来，用v-cloak + css能幫助在Vue实例化之前先給元素新增一個样式，常常會使用none這個样式。
````bash

<div id="app" v-cloak>
{{ message }}
</div>
<script>
var app = new Vue({
 el:'#app',
 data:{
   message: 'HelloWorld'
 }

</scrip
````

CSS STYLE:
````bash
[v-cloak]{
 display: none;
}
````

##  v-once 只会被渲染一次，后面变静态
````bash

<div id="app" v-once>
{{ message }}
</div>
<script>
var app = new Vue({
 el:'#app',
 data:{
   message: 'HelloWorld'
 }
</script>
````

##  v-if , v-else-if, v-else
````bash

<div id="app">
<p v-if="status === 1">xxx此行</p>
<p v-else-if="status === 2">oooo此行</p>
<p v-else>ssss</p>
</div>
<script>
var app = new Vue({
 el:'#app',
 data:{
   status: 1
 }
</script>
````

##  v-show 改變元素的CSS的display屬性，當v-show的值為false，元素則會隱藏，檢視DOM結構會看到元素上嵌入了display:none;
````bash
<div id="app">
  <p v-show="status === 1">當status為1時顯示此行</p>
</div>
<script>
var app = new Vue({
 el:'#app',
 data:{
   status: 2
 }
</script>
````
````bash
<p style="display: none;"> 當status為1時顯示此行</p>
````
v-if vs v-show
雖然這兩者的功能類似，但v-if才是真正的條件繪製，它會真的去銷毀或重建元素及綁定的事件，如果運算式為false，一開始元素就不會被繪製，但v-show都會將元素編譯，只是加了CSS的屬性。
使用時機：
如果元件會頻繁被切換-> v-show
不經常變換的場景-> v-if （負擔較大）

## v-for 循环
在进行数据传递之前，我们要了解下key属性，它和v-for使用，用来帮助Vue标识列表中的元素，这样Vue就不需要在列表变化时重新创建它们。但是Vue需要一个唯一的标识，即key来识别哪些元素是被复用的。
````bash
<div id="app">
  <ul>
    <li v-for="(val,key) in arr">{{val}}---{{key}}</li>
  </ul>
</div>
<script>
var app = new Vue({
 el:'#app',
 data:{
   arr: ['a', 'b', 'c']
 }});
</script>
````
结果：
a --- 0
b --- 1
c --- 2

````bash
<div id="app">
  <ul>
    <li v-for="(val,key) in ">{{val}}---{{key}}</li>
  </ul>
</div>
<script>
var app = new Vue({
 el:'#app',
 data:{
    obj: { id: 1, name: 'Jessica', sex: 'F' }
 }});
</script>
````
结果：
1 --- id
Jessica --- name
F --- sex

````bash
<div id="app">
  <ul>
    <li v-for="(brand,key) in brands">{{brand.name}}---{{key}}</li>
  </ul>
</div>
<script>
var app = new Vue({
 el:'#app',
 data:{
    brands:[ { name: 'addidas'},
             { name: 'nike'},
             { name: 'nubalance' }]
}
});
</script>
````
结果：
addidas --- 0
nike --- 1
nubalance --- 2

## 现实一个todolist
````bash
export default {
  name: 'app',
  components: {
    ToDoItem
  },
  data() {
    return {
      ToDoItems: [
        { label: 'Learn Vue', done: false },
        { label: 'Create a Vue project with the CLI', done: true },
        { label: 'Have fun', done: true },
        { label: 'Create a to-do list', done: false }
      ]
    };
  }
};
````
添加 id 字段到 ToDoItems 数组的每一个元素中, 并且将他们赋值为 uniqueId('todo-')。

````bash
import ToDoItem from './components/ToDoItem.vue';
import uniqueId from 'lodash.uniqueid'

export default {
  name: 'app',
  components: {
    ToDoItem
  },
  data() {
    return {
      ToDoItems: [
        { id: uniqueId('todo-'), label: 'Learn Vue', done: false },
        { id: uniqueId('todo-'), label: 'Create a Vue project with the CLI', done: true },
        { id: uniqueId('todo-'), label: 'Have fun', done: true },
        { id: uniqueId('todo-'), label: 'Create a to-do list', done: false }
      ]
    };
  }
};
````
````bash
<ul>
  <li v-for="item in ToDoItems" :key="item.id">
    <to-do-item label="My ToDo Item" :done="true"></to-do-item>
  </li>
</ul>
````
这样改后，<cli>标签中的js脚本就可以访问item了，这意味着我们可以使用v-bind来传递item对象的字段给ToDoItem组件了。这非常有用，我们想让列表中的待办事项的label值展示到它的label中，而不是显示一个静态的"My Todo Item"。此外，我们想让它们的checked状态反应它们的done字段，而不是默认的done="false"。

把 label="My ToDo Item" 改成 :label="item.label", :done="false" 改成 :done="item.done" ：
![](https://media.prod.mdn.mozit.cloud/attachments/2020/05/13/17244/0f2b3e70ddec91d18ab9f7bdd0846646/rendered-todo-items.png)

````bash
<ul>
  <li v-for="item in ToDoItems" :key="item.id">
     <to-do-item :label="item.label" :done="item.done"></to-do-item>
  </li>
</ul>
````
我们可以做一点代码重构。 因为我们已经要为每一个待办事项创建一个唯一id，所以不妨把id作为ToDoItem的一个prop，而不是在每个checkbox里生成它。

添加一个新的prop id 到 ToDoItem 组件。

标记它为required，类型是 String 。
为防止命名冲突，删除掉data属性中的id字段。
删除掉 import uniqueId from 'lodash.uniqueid'; 这行。

````bash
export default {
    props: {
        label: {required: true, type: String},
        done: {default: false, type: Boolean},
        id: {required: true, type: String}
    },
    data() {
        return {
           isDone : this.done,
        }
    },
}
````
现在，在 App.vue 组件中将 item.id 作为一个prop传递给 ToDoItem 组件。你的 App.vue template如下所示：
````bash
<template>
  <div id="app">
    <h1>My To-Do List</h1>
    <ul>
      <li v-for="item in ToDoItems" :key="item.id">
        <to-do-item :label="item.label" :done="item.done" :id="item.id"></to-do-item>
      </li>
    </ul>
  </div>
</template>
````
## v-bind 属性绑定
````bash
<div id = '#app'>
   <div v-bind:class = "color"> </div>
</div>
<script>
  var app = new Vue({
    el:'#app',
    data: {
      color: 'red',   
    }
})
</script>
````
````bash
<div id = '#app'>
   <img v-bind:src = "imgSrc" />
</div>
<script>
  var app = new Vue({
    el:'#app',
    data: {
      imgSrc: 'images/1.jpg',   
    }
})
</script>
````
img的src綁定的是data中的imgSrc屬性，如此一來以後當data中的imgSrc變化時，src就會重新繪製。通常動態網站的圖片位址會是動態刷新的，因此使用v-bind就能輕鬆掌握。

````bash
<div id = '#app'>
   <div v-bind:class="{active: isActive}"></div>
</div>
<script>
  var app = new Vue({
    el:'#app',
    data: {
      isActive: true
    }
})
</script>
````
上述程式碼中，active這個class是否綁定由isActive決定，當isActive為true，則
````bash
<div class = "active"> </div>
````
如果是false，
````bash
<div class = ""> </div>
````


## v-bind 陣列語法
````bash
<div id = '#app'>
   <div v-bind:class="[ac,color]"></div>
<script>
  var app = new Vue({
    el:'#app',
    data: {
      ac: 'active'   
      color: 'red'
    }
})
</script>
````
Vue渲染後為：
````bash
<div class = "active red"> </div>
````

## v-bind 对比陈列和物件{}的表达方式：
````bash
<div id = '#app' v-bind:style="{color: redColor，fontSize: font + 'px'}">
</div>
<script>
  var app = new Vue({
    el:'#app',
    data: {
      redColor: 'red',
      font: 40
    }
})
</script>
````
````bash
<div id = '#app' v-bind:style="[color，fontSize]">
</div>
<script>
  var app = new Vue({
    el:'#app',
    data: {
      color: {
        color: 'red',
      },
      fontSize: {
          'font-size':'40px'
      }
    }
})
</script>
````


## v-model 双向绑定：互动性功能
````bash

<body>
    <div id="app">
        <input type="text" v-model="input_val" >
        <div>{{input_val}}</div>
    </div>
</body>
<script>
var app = new Vue({
       el: '#app',
       data: {
        input_val: 'hello world '
       }
   })
</script>
````

## v-model 双向绑定textarea：互动性功能
````bash
<body>
    <div id="app">
        <textarea v-model="input_val"></textarea>
        <div>{{ input_val }}</div>
    </div>
</body>


<script>
    var app = new Vue({
        el: '#app',
        data: {
            input_val: ''
        }
    })
</script>
````

## v-model 单项选择题
````bash

<body>
    <div id="app">
        男<input type="radio" name="sex" value="男" v-model="sex">
        女<input type="radio" name="sex" value="女" v-model="sex"> 
        <br>
        {{sex}}
    </div>
</body>


<script>
    var vm = new Vue({
        el: '#app',
        data: {
            sex: ''
        }
    });
</script>
````

## v-on 单项选择题
一般不會把方法寫在data裡，原因是data就是拿來放資料的，把方法也寫進去不就太雜亂了，因此我們要使用Vue的一個叫做「methods」的選項，裡面專門存放方法

````bash

var app = new Vue({
  el: '#app',
  data: {
    
    name: "app"  
},
  methods:{
    handleClick: function(){
        alert("点击");
    }
  }
})
````
## v-on 传入参数运算

````bash
<body>
    <div id="app">
        <input type="button" value= "點我拜託" v-on:click = "handleClick(1,2)" >
    </div>
</body>
<script>
var app = new Vue({
       el: '#app',
       data: {
       },
       methods:{
           handleClick: function(num1,num2){
                alert(num1 + num2);
           }
       }
   })
</script>
````
## v-on 传入event

````bash
<body>
    <div id="app">
        <input type="button" value= "點我拜託" v-on:click = "handleClick" >
    </div>
</body>
<script>
var app = new Vue({
       el: '#app',
       data: {
       },
       methods:{
           handleClick: function(event){
                console.log(event);
           }
       }
   })
</script>
````
## v-on 传入参数和event

````bash
<body>
    <div id="app">
        <input type="button" value= "點我拜託" v-on:click = "handleClick(1,2)" >
    </div>
</body>
<script>
var app = new Vue({
       el: '#app',
       data: {
       },
       methods:{
          // 多加一個參數去接受事件物件
           handleClick: function(num1,num2,event){
                console.log(num1+num2);
                console.log(event);
           }
       }
   })
</script>
````
会出现错误，event undefined

若我們在參數後直接再傳一個參數，它並不會是事件物件，而是一個undefine的參數，那解決方法就是在函數中傳遞 $event 這個Vue內建的特殊變數來傳遞，這一個參數的名字是不可變的，所以我們將程式改成
````bash

<body>
    <div id="app">
        <!-- 加入$event -->
        <input type="button" value= "點我拜託" v-on:click = "handleClick(1,2,$event)" >
    </div>
</body>
<script>
var app = new Vue({
       el: '#app',
       data: {
       },
       methods:{
           handleClick: function(num1,num2,event){
                console.log(num1+num2);
                console.log(event);
           }
       }
   })
</script>
````
## v-on preventDefault
為click事件加入一個修飾符 prevent 它就等同於執行了event.preventDefault()的意思，所以點擊後，也不會跳轉到google。
````bash

<body>
    <div id="app">
        <!-- 為click事件加入修飾符 -->
        <a href="https://www.google.com" v-on:click.prevent="handleClick">點我</a>
    </div>
</body>
<script>
var app = new Vue({
       el: '#app',
       data: {
       },
       methods:{
          handleClick: function(){
                console.log("啥事也不會發生");
           }
       }
   })
</script>
````
推荐里面的实战教程[https://medium.com/andy%E7%9A%84%E8%B6%A3%E5%91%B3%E7%A8%8B%E5%BC%8F%E7%B7%B4%E5%8A%9F%E5%9D%8A/vue%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98-%E5%85%AD-%E5%AF%A6%E6%88%B0-%E7%B0%A1%E6%98%93%E8%B3%BC%E7%89%A9%E8%BB%8A-4882cdde269f]

````bash
var app = new Vue({
    el:'#app',
    data:{

    },
    methods:{

    },
    computed:{
        
    }
})
````
main.js的data中放置我們的商品清單，因為有多個物品，所以我們要用一個叫做itemList的陣列去包住多個物件，一個商品中含有特殊的編號（id）、名稱、價格、數量、圖片位址
````bash
var app = new Vue({
    el:'#app',
    data:{
        data:{
    itemList:[
      {
        id:'1',
        itemName:'優質短袖白T',
        imgUrl:'https://images.unsplash.com/photo-1534961880437-ce5ae2033053?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=668&q=80',
        price:'500',
        count:'1'
      },
      {
        id:'2',
        itemName:'骷髏手短黑T',
        imgUrl:'https://images.unsplash.com/photo-1503342217505-b0a15ec3261c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80',
        price:'790',
        count:'1'
      },
      {
        id:'3',
        itemName:'超時尚牛仔庫',
        imgUrl:'https://images.unsplash.com/photo-1529391409740-59f2cea08bc6?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1124&q=80',
        price:'1200',
        count:'1'
      },
      {
        id:'4',
        itemName:'質感褐色系大衣服',
        imgUrl:'https://images.unsplash.com/photo-1491998664548-0063bef7856c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80',
        price:'2300',
        count:'1'
      },
]

    },
    methods:{

    },
    computed:{
        
    }
})
````
HTML的部分
![图片](‪F:\1_QDNKgmyCXQZNT4PrqlxzcQ.png)
````bash
<div id="app">
    <div class="container">
        <div class="item_header">
            <div class="item_detail">商品</div>
            <div class="price">單價</div>
            <div class="count">數量</div> 
            <div class="amount">總計</div>
            <div class="operate">操作</div>
        </div>
        <div class="item_header item_body">
            <div class="item_detail">
                <img src="https://images.unsplash.com/photo-1534961880437-ce5ae2033053?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=668&q=80" alt="">
                <div class="name">優質短袖白T</div>
            </div>

            <div class="price"><span>$</span>300</div>
            <div class="count">
                <button>-</button>
                1
                <button>+</button>
            </div> 
            <div class="amount">300</div>
            <div class="operate">
                <button>刪除</button>
            </div>
        </div>
    </div>
</div>
````
目前的html結構是靜態的，可以看到裡面的文字都是自己加上去的，還未使用到Vue的功用，button也還沒有功能，現在看來，因為只有一個item，所以Html的程式量不多，當item有上百上千個的時候，程式就是好幾百行，但使用Vue我們可以輕鬆避免，只要寫好架構，一切交給data與vue。
````bash
# <!DOCTYPE html>
# <html lang="en">
# <head>
#     <meta charset="UTF-8">
#     <title>Vue購物車</title>
#     <script src="https://unpkg.com/vue/dist/vue.min.js"></script>
#     <link rel="stylesheet" href="style.css">
    
# </head>
# <body>
# <div id="app">
#     <div class="container">
#         <div class="item_header">
#             <div class="item_detail">商品</div>
#             <div class="price">單價</div>
#             <div class="count">數量</div> 
#             <div class="amount">總計</div>
#             <div class="operate">操作</div>
#         </div>

  
        <div class="item_container" v-for="(item, index) in itemList" :key="item.id" >
       

        <div class="item_header item_body">
            <div class="item_detail">
                # <img src="https://images.unsplash.com/photo-1534961880437-ce5ae2033053?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=668&q=80" alt="">
                # <div class="name">優質短袖白T
                 <img v-bind:src="item.imgUrl" alt="">
                <div class="name">{{item.itemName}}</div>
            </div>

            # <div class="price"><span>$</span>300</div>
            <div class="price"><span>$</span>{{item.price}}</div>

            # <div class="count">
            #     <button>-</button>
            #     1
            #     <button>+</button>
            # </div> 
            <div class="count">
            <button @click="handleSub(item)">-</button>
            {{item.count}}
            <button @click="handlePlus(item)">+</button>
        </div> 
            # <div class="amount">300</div>
            <div class="amount">{{item.price * item.count}}</div>
            # <div class="operate">
            #     <button>刪除</button>
            # </div>
            <div class="operate">
            <button @click="handledelete(index)">刪除</button>
        </div>
        </div>
    </div>
</div>
</body>
<script src="main.js"></script>
</html>
````
這時就會用到內插表示item的內容，

名稱： {{item.name}}

價格： {{item.price}}

圖片：使用v-bind綁定src，綁定為item的imgUrl

總價： 我們可以在內差法直接計算價格，所以可以直接寫

添加按鈕功能
現在當我們點擊按鈕時，要觸發一個事件去對item的個數做加減，所以我們先在button加及減各自加上一個v-on事件

````bash
<button @click=”handleSub(item)”>-</button>
{{item.count}}
<button @click=”handlePlus(item)”>+</button>
````
當按下+這個按鈕時，則會執行methods中的handlePlus函式， — 按鈕則是handleSub，這邊我們把「item」傳進去，這個item就是我們點到哪一個商品時，會將這個商品的item傳進去，而item中都有一個count的屬性，所以我們只要讓count值++或減減就可以了，這邊要注意的是，count>1才能讓count--否則值會變成負的
````bash
methods:{
  handlePlus: function(item){
    console.log(item);
    item.count++;
  },
  handleSub: function(item){
    console.log(item);
    if(item.count>1){
      item.count--;
    }
   },
}
````
處理完加減按鈕後，還有一個刪除的按鈕功能需要完成，這邊按鈕傳入的會是index（索引）因為我們要對整個itemList做操作，而不是只對單一個item，所以要傳入我們想要刪除掉的索引內容。
````bash
 <button @click=”handledelete(index)”>刪除</button>
 ````
 methods中則添加，handledelete()，this是整個Vue物件，裡面包含著所有data與methods等，所以我們可以找到itemList，並使用splice這個方法將index這個位置的元素刪除。
 ````bash
 handledelete: function(index){
   this.itemList.splice(index,1);
}
````