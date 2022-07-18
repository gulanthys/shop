<template>
  <div class="about">
    <h1>vue3 生命周期</h1>
    <div id="dom">{{msg}}--{{num}}</div>
    <!-- v-on:事件名="事件方法" 绑定事件 简写：@:事件名="事件方法" 绑定事件 -->
    <!-- 事件及方法直接申明在 setup内 -->
    <button v-on:click="handleClick">Click me</button><br>
    <!-- v-model:双向绑定 -->
    <!-- input：输入事件 ； blur：失去焦点 ； focus：获取焦点 ； change：内容更改 -->
    <input type="text" placeholder="请输入姓名" v-model="userName">
    <textarea placeholder="请输入你的建议" cols="30" rows="10" v-model="userinput"></textarea>
    <p>{{userName}}---{{userinput}}</p>
    <button v-on:click="submit" >提交</button>
  </div>
</template>
<script>
import { reactive, toRefs, onBeforeMount, onMounted, onBeforeUpdate, onUpdated } from 'vue'
export default {
  name: 'about',
  setup () {
    const data = reactive({
      msg: 'hello',
      num: 1,
      userName: '',
      userinput: ''
    })
    // 数据渲染前
    onBeforeMount(() => {
      console.log('onBeforeMount', document.querySelector('#dom'))
    })
    // 数据渲染后
    onMounted(() => {
      console.log('onMount', document.querySelector('#dom'))
      setTimeout(() => {
        data.msg = 'world'
      }, 2000)
    })
    // dom更新前
    onBeforeUpdate(() => {
      console.log('onBeforUpdate')
    })
    // dom更新后
    onUpdated(() => {
      console.log('onUpdated')
      // data.num++ 触发死循环
    })
    // 事件及方法
    const handleClick = () => {
      alert('你好！')
    }
    const submit = () => {
      alert(`${data.userName}的建议是${data.userinput}`)
    }
    return {
      ...toRefs(data),
      handleClick,
      submit
    }
  }
}
</script>
