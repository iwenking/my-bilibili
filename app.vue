<template>
  <!-- 首页 index/index.vue -->
  <!-- Nuxt 页面路由 相当于RouterView -->
  <!-- <NuxtLink to="/">首页</NuxtLink>
  <NuxtLink to="/video">视频</NuxtLink> -->

  <NuxtPage />
</template>
<script setup lang="ts">
//SEO 优化信息
useSeoMeta({
  title: "哔哩哔哩 (゜-゜)つロ 干杯~-bilibili",
  description:
    "哔哩哔哩（bilibili.com)是国内知名的视频弹幕网站，这里有及时的动漫新番，活跃的ACG氛围，有创意的Up主。大家可以在这里找到许多欢乐。",
  keywords:
    "B站,弹幕,字幕,AMV,MAD,MTV,ANIME,动漫,动漫音乐,游戏,游戏直播,ACG,galgame,动画,番组,新番,初音,洛天依,vocaloid",
  referrer: "no-referrer", //不发送referrer
});
</script>
<style lang="scss">
@import "./assets/styles/base.scss";
// 字体图标
@import "./assets/styles/iconfont.scss";
:root {
  --van-primary-color: #fb7299 !important;
  --van-back-top-background: #fbfbfb !important;
  --van-back-top-text-color: #666 !important;
}
</style>
