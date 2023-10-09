<script setup lang="ts">
useSeoMeta({
  title: 'bilibili',
  description: '这是nuxt的访bilibili',
  keywords: 'bilibili, nuxt, vue',
  referrer:'no-referrer'
})
</script>
<template>
  <div>
    <NuxtPage />
  </div>
</template>

<style lang="scss">
// 基础样式
@import './assets/styles/base.scss';
// 字体图标
@import './assets/styles/iconfont.scss';
:root{
  --van-primary-color: #fb7299 !important;
  --van-back-top-background: #fbfbfb !important;
  --van-back-top-text-color: #666 !important;
}
</style>