# 一、vue基础知识

    1、模板语法
        ```
        Mustache语法：{{12}}
        Html赋值：v-html
        绑定属性: v-bind:id=""  :id
        使用表达式:  {{ok?'yes':'no'}}
        文本赋值: v-text=""
        指令v-if
        过滤器:{{message | capitalize}} 和 v-bind:id="rawId | formatId"
        ```

      2、Class和Style绑定

        ```
          对象语法: v-bind:class="{ active: isActive, 'text-danger': hasError }">

          数组语法:<div v-bind:class="[activeClass, errorClass]"></div>
          data: {
            activeClass: 'active',
            errorClass: 'text-danger'
          }
          <div v-bind:class="[isActive ? activeClass : '', errorClass]"></div>

          style绑定对象语法：<div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
          data: {
            activeColor: 'red',
            fontSize: 30
          }
        ```

      3、条件渲染
        ```
          v-if
          v-else
          v-else-if
          v-show
          v-cloak
          [v-cloak] {
          display: none;
          }
          <div v-cloak>
            {{ message }}
          </div>
        ```

      4、vue事件处理器
        ```
          v-on:click="greet"或@click="greet"

          事件修饰符：
          v-on:click.stop 阻止冒泡
          v-on:click.stop.prevent 阻止默认事件（阻止按钮的默认事件，例如a标签让点击的打开新窗口或新页面失效）
          v-on:click.self 给对象本身绑定事件，如果元素中有子元素，点击子元素是没有作用的。
          v-on:click.once 只给事件绑定只生效一次

          v-on:keyup.enter
          enter/tab/delete(捕获删除和退格键)/esc/space/up/down/left/right

        ```

      5、Vue组件
        ```
          全局组件和局部组件
          SPA一般是局部组件，多页面会有全局组件。

          父子组件通讯-数据传递
          (组件单向流，只允许父组件传递给子组件数据不允许子组件修改父组件变量，因为组件之间嵌套很复杂，为了防止紊乱。但可以通过$emit变相更改)

          Slot
        ```


# 二、vue-router
      1、什么是前端路由?
          路由是根据不同的url地址展示不同的内容或页面
          前端路由就是把不同路由对应不同的内容或页面的任务交给前端来做，之前是通过服务端根据url的不同返回不同的页面实现的（后端直出渲染）。其实前端路由前端页面只有首页是存在的，其他的是虚拟出来的。SPA需要前端路由。
          vue-router实际上是对history的封装。
      2、前端路由由什么优点和缺点？
          优点:
              用户体验好，不需要每次都从服务器全部获取，快速展现给用户（只需首页获取）。
          缺点：
              不利于SEO（因为除了首页其他页面路径虚拟出来的）
              使用浏览器的前进，后退键的时候会重新发送请求，没有合理的利用缓存；
              单页面无法记住之前滚动的位置，无法在前进、后退的时候记住滚动的位置。

      3、vue-router用来构建SPA
            vue-router本质上是对history的封装。
            <router-link></router-link>或者this.$router.push({path:''})跳转
            <router-view></router-view>组件渲染  一个载体，专门承担组件选择，承载一级路由


      4.vue-router使用

              动态路由匹配

              模式                 		  |匹配路径											|$route.params

              --|:--|--:

              /user/:username | /user/evan | { username: 'evan' } 
              /user/:username/post/:post_id |/user/evan/post/123  |	{ username: 'evan', post_id: 123 }

            嵌套路由

            编程式路由
              $router.push({path:'name?a=123'})或者$router.push({path:'name',query:{a:123}})
              $router.go(1)
            命名路由和命名视图

            什么是命名路由和命名视图？
            给路由定义不同的名字，根据名字进行匹配。
            给不同的router-view定义名字，通过名字进行对应组件的渲染。
              例如
              ```
                <router-view></router-view>
                <router-view name="title"></router-view>
                <router-view name="img"></router-view>
                routes:[
                  {
                    path:'/',
                    name:'GoodsList',
                    components:{
                      default:GoodaList,
                      title:Title,
                      img:Image
                    }
                  }
                ]
              ```
    axios
      https://www.kancloud.cn/yunye/axios/234845
             ```
              axios直接暴露到全局
              成功.then() 失败.catch()。链式操作。
              axios.get()
              axios.post()
              http配置。get请求通过params:{}传递参数。post请求通过data:{}传递参数
              axios.all() 可同时请求多个接口

              全局拦截：
              request拦截
              axios.interceptors.request.use()
              请求之前可以做一些Loading处理或其他业务处理。
              response拦截
              axios.interceptors.response.use()
             ```
    箭头函数作用域和外面作用域是一样的，没有产生新的作用域。

# 三 ES6
      ECMAScript 6

      1、函数的Rest参数和扩展