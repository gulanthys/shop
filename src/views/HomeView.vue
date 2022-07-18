<template>
  <div class="home">
    <h1>hello world!</h1>
    <p v-text="name"></p>
    <!-- v-text 简写 -->
    <p>{{age}}</p>
    <!-- v-html 网页标签 -->
    <p v-html="info"></p>
    <!-- v-bind:属性名:"变量名" 绑定动态的标签属性 简写： :属性名 -->
    <p v-bind:data="dataVal">我有属性data</p>
    <!-- class类名绑定 可以叠加使用 -->
    <p class="text" :class="{'red':isRed}">我是红色的</p>
    <!-- v-if 判断语句-->
    <!-- v-show false的时候是样式上的隐藏 -->
    <p v-if="!isTrue">v-if</p>
    <p v-show="isTrue">v-show</p>
     <!-- v-if v-else-->
    <p v-if="!isTrue">if</p>
    <p v-else>else</p>
    <!-- for 循环 -->
    <!-- 循环userList -->
    <!-- 语法：v-for="(每一个对象的变量,下标) in 数组" -->
    <ul>
      <li v-for="(value,index) in userList" :key="index">
        学生姓名：{{ value.username}}
        学生年龄：{{ value.userage}}
      </li>
    </ul>
 <p></p>
  </div>
</template>

<script>
import { reactive, toRefs } from 'vue'
export default {
  name: 'home',
  setup () {
  // beforCreate和created这两个生命周期
    const data = reactive({
      name: '小红',
      age: 20,
      info: '<i>我是斜体字</i>',
      dataVal: 20,
      isRed: true,
      isTrue: true,
      isFalse: false,
      userList: [
        {
          username: '胡',
          userage: 20
        },
        {
          username: '红',
          userage: 18
        }
      ]
    })
    return {
      ...toRefs(data)
    }
  }
}
</script>
<style>
.red{
  color: red;
}
</style>
