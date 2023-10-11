<script setup lang="ts">
import type {  VideoItem } from '~/types/video'
// 获取频道列表
const { data: channelList } = await useFetch('/api/channel', { method: 'GET' })
// 获取视频列表
const { data: videoList } = await useFetch('/api/video')

const list = ref<VideoItem[]>([]);
const loading = ref(false);
const finished = ref(false);
// 页码
let page = 1
const pageSize = 10
// 滚动触底触发
function onLoad() {
  loading.value = false;
  const data = videoList.value?.slice(
    (page - 1) * pageSize,
    page * pageSize
  ) as VideoItem[]
  list.value.push(...data)
  // 页码累加
  page++
  // 加载结束
  if (videoList.value?.length === list.value.length)
    finished.value = true
}

onLoad()
</script>

<template>
  <!-- 公共头部 -->
  <AppHeader />
  <!-- 频道模块 -->
  <van-tabs>
    <van-tab v-for="item in channelList" :key="item.id" :title="item.name" />
  </van-tabs>
  <!-- 视频列表 -->
  <van-list v-model:loading="loading" :finished="finished" finished-text="没有更多了" @load="onLoad">
    <div class="video-list">
      <AppVideo v-for="item in list" :key="item.bvid" :item="item"  />
    </div>
  </van-list>
</template>

<style lang="scss">
// 视频列表
.video-list {
  display: flex;
  flex-wrap: wrap;
  padding: 10px 5px;
}


</style>