<template>
  <view class="app">
    <slot />
  </view>
</template>

<script>
export default {
  onLaunch() {}
}
</script>

<style>
page {
  background-color: #f5f7fb;
  color: #1f2937;
  font-size: 28rpx;
}

.app {
  min-height: 100%;
}
</style>
