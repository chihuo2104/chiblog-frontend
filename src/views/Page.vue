<script setup>
import mockpages from '@/mocks/pages'

import { marked } from 'marked'
import { defineProps, ref } from 'vue'
import { useRouter } from 'vue-router'
import { useStore } from 'vuex'
import mocksettings from '../mocks/settings'

const $store = useStore()
const props = defineProps({
  path: String
})
let page = {}
const settings = ref({})
const pages = ref({})
if ($store.state.model === 'production') {
  pages.value = $store.state.all.pages
  settings.value = $store.state.all.settings
} else {
  pages.value = mockpages
  settings.value = mocksettings
}
const $router = useRouter()
if (pages.value.find((page) => page.name === props.path) === undefined) {
  $router.push('/error/404.html')
} else {
  page = pages.value.find((page) => page.name === props.path)
  document.title = page.title + ' - ' + settings.value.site.title
}
</script>
<template>
  <div>
    <h1>{{page.title}}</h1>
    <div id="page-content" v-html="marked.parse(page.content)"></div>
  </div>
</template>
<style lang="less" scoped>
</style>
<style lang="less">

</style>
