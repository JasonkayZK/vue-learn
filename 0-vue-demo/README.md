# 指令

v-bind:property <=> :property

v-if、v-else: 惰性、删除后 dom 看不到

v-show：css display控制

v-for: `<div v-for="(item, idx) in items" :key="item.id|index"></div>`

v-on: <=> @

- @click
- ...

v-model: input, textarea, select 

- .lazy: change 事件之后（失去焦点或者回车之后）同步
- .trim: 过滤前后空白符


# 组件

单文件组件：

- template
- script
- style

scoped：当前样式只在当前样式中生效

加载组件：

- import 引入
- components 挂载
- `<MyComp />` 显示

数据传递：

- 父传子：props(type, default：数组和对象必须使用函数返回)
- 子传父（自定义事件）、兄弟互传：`this.$emit`


# 生命周期

> https://cn.vuejs.org/guide/essentials/lifecycle.html

- beforeCreate
- created
- beforeMount
- mounted：进行网络请求
- beforeUpdate
- updated
- beforeUnmount：卸载定时器等
- unmounted


# 第三方

- Swiper：轮播图
- Axios + querystring：
  - 组件引入、全局引入（`$axios`）
  - 网络请求封装：
    - `request.js`：网络配置、拦截器
    - `api/path.js`：请求地址
    - `api/index.js`：导出


# 解决跨越

修改配置：`devServer/proxy`


# 路由配置 vue-router

创建：

- createRouter：
  - history：访问方式 createWebHashHistory
  - routes：
    - path：访问url路径
    - name：路由名称
    - component：路径对应组件，异步加载：`() => import("AboutView.vue")`

引入：

- `createApp(App).use(router)`

显示：`<router-view />`

跳转：`<router-link to="/about" />`


createWebHashHistory 和 createWebHistory：

- createWebHistory（pushState）：需要后台配合重定向，否则出现404问题
- createWebHashHistory（a标签锚点）：不需要后台配置


传递参数：

- 路由配置指定参数 key
- 跳转时携带参数
- 详情页读取路由携带的参数


嵌套路由（多级导航）：

- 路由配置中增加 Children（二级导航路由不加斜杠）


默认路由显示（重定向）：

- 路由配置中增加 redirect 重定向；


# 状态管理 vuex

配置 Vuex：

- createStore：
  - state

引入 Vuex：

- `app.use(store)`

读取状态 State：

- `$store.state.xxx`
- `computed: ...mapState["xxx"]`

核心：

- State：存储状态，用来读取
- Getters：Vuex 中的数据进行过滤（类似于 computed）
  - `$store.getters.xxxFunc`
  - `computed: ...mapGetters["xxxFunc"]`
- Mutations：修改状态，提交 Mutation（仅允许同步操作）
  - 定义：`mutations: addXXX(state) {state.xxx++}`
  - 使用：
    - `$store.commit("addXXX")` （类似于 emit 事件）
    - `methods: ...mapMutations["addXXX"]`
- Action：类似于 Mutation，Action 可以异步提交 Mutation，而不是直接变更状态
  - 定义：`actions: asyncAddXXX({commit}) {...}`
  - 使用：
    - `$store.dispatch("asyncAddXXX")`
    - `methods: ...mapActions["asyncAddXXX"]`









# Vue3 新特性

- Composition 组合式API
- Fragment 碎片、Teleport 传送门、Suspense 悬念


ref 或者 reactive：



