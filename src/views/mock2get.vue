<script setup>
import comments from '@/mocks/comments'
import settings from '@/mocks/settings'
import posts from '@/mocks/posts'
import pages from '@/mocks/pages'
import { useStore } from 'vuex'

const $store = useStore()

if ($store.state.model === 'production') {
  console.log('You are in production mode!')
}
if ($store.state.model === 'mocks') {
  console.log('You can use this mock data write in a json file and then deploy into a static file server and then you can use a static blog~')
  console.log('Enjoy it ;)')
  console.log(JSON.stringify({ status: 200, data: { posts, settings, comments, pages } }))
}
</script>
<template>
  <div>
    <img src="@/assets/404.png" title="七七-暗中观察"/>
    <h2>啊哦，看起来你好像迷路了呢......</h2>
    <h2><router-link to="/">点我返回</router-link></h2>
  </div>
</template>
<style scoped>
a:link,a:visited {
  color: black;
  text-decoration: none;
}
a:hover,a:active {
  color: cyan;
}
</style>
<style lang="less">

</style>
