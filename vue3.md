# 拥抱ts   TypeScript

打包大小减少41%

初次渲染快了55%

内存减少54%

源码升级


# 指令  第二种创建vue cli
vite创建  新一代 不依赖 webpack

优势 无需打包操作 可以快速冷启动
真正的按需加载  不在等待整个应用的编译完成

1 npm init vite-app vue3_test_vite
 npm i
npm dev

启动特别快

# main.js 入口文件
# 引入的是  createApp 工厂函数 无需通过new来调用 直接写名字就行
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'
import store from './store'

createApp(App).use(store).use(router).mount('#app')

#  mount('#app') 页面App.vue的id

# 常用的Composition API  组合式API

1拉开序幕的setup 新的配置项 值是一个函数

数据 、方法 、均要在setup 中 
  setup(){
   let name = 'zs'

  //  方法
  function asty(){
    alert(`wode${name}`)
  }
  // 交出去 才能使用
  return {
    name,
    asty
  }
  }

# 支持 data  和 methods
vue2 函数可以读取 vue3 配置的变量函数
vue3 函数不可以读取 vue2配置的函数和方法 

# vue3 和vue2 数据和方法不能混用  容易出错

# 冲突的时候尽 vue3 为主

# async 不能修饰 seteup 

# vue3 ref 函数   （vue2 ref是标签  给元素打标识 获取 相当于id）
ref可以继续使用 
vue3 多了一个 ref函数

# import {ref} from 'vue'
export default {
  name: 'App',
#  setup(){
  <!-- ref 引用对象 -->
    // 不是响应式数据 需要加上ref  是RefImpl一个对象
    //  Ref reference 引用  impl implemenr  引用的实现
    // value
#   let name =ref('zs') 
   let object=ref({
    type:'html',
    style:'vue'
   })

  //  方法
  function asty(){
    // alert(`wode${name}`)
    // name.value 这样才能拿到值
    name.value="李斯"
    // 更改对象
#    object.value.type='html5'
     object.value.style='vue3'
     console.log(name.value)
  }
#   // 交出去 才能使用
  return {
    name,
    asty,
    object
  }
  },
}

# reactive 响应式
 let nm=reactive({
    type:'html',
    style:'vue'
   })

  nm.style='ppp' 直接修改
# 可以直接输出对象 proxy 对象
vue3 可以监视到数据变化就可以实现响应式
Proxy {type: 'html', style: 'ppp'}

# reactive 可以处理数组

# sutup 注意点
 $atters

# 插槽
子组件 <slot>
 $solts 虚拟节点 存放父组件的传递的容器

  具名插槽 
  <template solt="tex1">
  <slot></solt>
  </template>



# computed 计算属性


 let funname=computed({
    // 读
    get(){
      return obj.age + obj.name
    },
    // 写
    set(){
    }
   })

#    // watch
// 监视多个值
  watch([name,obj],(newValue,olderVallue)=>{
    console.log('gaiiban'+newValue+olderVallue)
  })

# 监视 reactive 数组和对象

# // 直接监视对象名，是不能拿到 olderValue
  // 强制开启深度检测是无效的
#  watch(person,(newValue,olderVallue)=>{
    console.log(newValue,olderVallue)
  }),{deep:false}


 # // 可以监视其中的某个属性
  // 这样写成函数就可以拿到olderValue
  watch(()=>person.job.school,(newValue,olderVallue)=>{
    console.log(newValue,olderVallue)
  })


 #  // 监视对象中的属性对象 对象里面的属性是对象
  // 深度检测是无效的 无法检测到
  // watch(()=>person.job,(newValue,olderVallue)=>{
  //   console.log(newValue,olderVallue)
  // }),{deep:false}

 #  // 对象属性是对象需要.属性  拿到对象里面是对象的属性值才可以检测到
  watch(()=>person.job.school,(newValue,olderVallue)=>{
    console.log(newValue,olderVallue)
  }),{deep:false}


# 生命周期  最后一组 挂载 和卸载
vue生命周期判断一次 不在判断两次



# github
 1 注册
 2 建立仓库


 3 了解两种访问方式
 https 访问的特点零配置 （默认）
 缺点每次都需要输入自己的账号和密码
 ssh 需要配置 但是配置成功之后不需要输入账号和密码

4 https  将本地项目上传到git
  