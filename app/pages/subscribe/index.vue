<template>
  <view class="page">
    <view class="card">
      <view class="card-title">订阅消息设置</view>
      <view class="toggle-row" v-for="item in subscriptions" :key="item.title">
        <view>
          <view class="toggle-title">{{ item.title }}</view>
          <view class="toggle-desc">{{ item.desc }}</view>
        </view>
        <switch color="#0B72F0" :checked="item.enabled" @change="toggle(item)" />
      </view>
    </view>

    <view class="section">
      <view class="section-title">通知场景</view>
      <view class="scene-list">
        <view class="scene-card" v-for="scene in scenes" :key="scene.title">
          <view class="scene-title">{{ scene.title }}</view>
          <view class="scene-desc">{{ scene.desc }}</view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      subscriptions: [
        {
          title: '政策更新提醒',
          desc: '新政策发布或解读更新提醒。',
          enabled: true
        },
        {
          title: '求助进度通知',
          desc: '办理进度变化即时提醒。',
          enabled: true
        },
        {
          title: '采购对接通知',
          desc: '供应商反馈与对接结果提醒。',
          enabled: false
        }
      ],
      scenes: [
        {
          title: '微信订阅通知',
          desc: '在政策发布、服务办理关键节点推送订阅消息。'
        },
        {
          title: '服务事项提醒',
          desc: '求助、采购等事项进度实时提醒。'
        },
        {
          title: '活动与课堂提醒',
          desc: '培训与活动报名开始时提醒。'
        }
      ]
    }
  },
  methods: {
    toggle(item) {
      item.enabled = !item.enabled
    }
  }
}
</script>

<style scoped>
.page {
  padding: 24rpx;
}

.card {
  background: #fff;
  border-radius: 20rpx;
  padding: 24rpx;
  box-shadow: 0 12rpx 32rpx rgba(15, 33, 64, 0.06);
}

.card-title {
  font-size: 30rpx;
  font-weight: 600;
  margin-bottom: 16rpx;
}

.toggle-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16rpx 0;
  border-bottom: 1rpx solid #eef2f7;
}

.toggle-row:last-child {
  border-bottom: none;
}

.toggle-title {
  font-size: 26rpx;
  font-weight: 600;
}

.toggle-desc {
  margin-top: 6rpx;
  font-size: 22rpx;
  color: #6b7280;
}

.section {
  margin-top: 24rpx;
}

.section-title {
  font-size: 28rpx;
  font-weight: 600;
  margin-bottom: 16rpx;
}

.scene-list {
  display: flex;
  flex-direction: column;
  gap: 16rpx;
}

.scene-card {
  background: #fff;
  border-radius: 18rpx;
  padding: 20rpx;
  box-shadow: 0 8rpx 24rpx rgba(15, 33, 64, 0.06);
}

.scene-title {
  font-size: 26rpx;
  font-weight: 600;
}

.scene-desc {
  margin-top: 8rpx;
  font-size: 24rpx;
  color: #4b5563;
}
</style>
