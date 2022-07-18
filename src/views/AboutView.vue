<template>
  <div class="about">
    <h1>vue3 生命周期</h1>
    <div id="dom">{{msg}}--{{num}}</div>
  </div>
</template>
<script>
import { reactive, toRefs, onBeforeMount, onMounted, onBeforeUpdate, onUpdated } from 'vue'
export default {
  name: 'about',
  setup () {
    const data = reactive({
      msg: 'hello',
      num: 1
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
    return {
      ...toRefs(data)
    }
  }
}
</script>
