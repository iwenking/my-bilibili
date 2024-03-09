<script setup lang="ts">
import type { VideoItem } from "@/types/video";
// 获取频道列表
const { data: channelList } = await useFetch("/api/channel");
// 获取视频列表
const { data: videoList } = await useFetch("/api/video");

const list = ref<VideoItem[]>([]);
const loading = ref(false);
const finished = ref(false);
//页码
let page = 1;
let pageSize = 20;
const onLoad = () => {
  loading.value = false;
  //根据页码提取数据
  const data = videoList.value?.slice(
    (page - 1) * pageSize,
    page * pageSize
  ) as VideoItem[];
  //追加数据
  list.value.push(...data);
  //页码+1
  page++;
  //判断是否加载完毕
  if (list.value.length === videoList.value.length) {
    finished.value = true;
  }
};
//初始化加载-主动请求前20条数据，用于首屏渲染,方便SEO抓取到数据
onLoad();
</script>

<template>
  <!-- 头部 -->
  <AppHeader />
  <!-- 频道模块 -->
  <van-tabs>
    <van-tab v-for="item in channelList" :key="item.id" :title="item.name" />
  </van-tabs>
  <!-- 视频列表 -->

  <van-list
    v-model:loading="loading"
    :finished="finished"
    finished-text="去bilibili看更多视频"
    @load="onLoad"
  >
    <div class="video-list">
      <AppVideo v-for="item in list" :key="item.aid" :item="item" />
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
