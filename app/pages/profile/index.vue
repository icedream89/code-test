<template>
  <view class="page">
    <view class="profile-card">
      <view class="avatar">企</view>
      <view class="profile-info">
        <view class="name">当阳智造装备有限公司</view>
        <view class="meta">企业账号 · 已认证</view>
      </view>
      <button class="switch-btn" size="mini">切换账号</button>
    </view>

    <view class="section">
      <view class="section-title">账号权限</view>
      <view class="section-card">
        <view class="permission" v-for="item in permissions" :key="item.title">
          <view class="permission-title">{{ item.title }}</view>
          <view class="permission-desc">{{ item.desc }}</view>
        </view>
      </view>
    </view>

    <view class="section">
      <view class="section-title">快速操作</view>
      <view class="action-grid">
        <view class="action-card" v-for="action in actions" :key="action.title" @tap="go(action.path)">
          <view class="action-title">{{ action.title }}</view>
          <view class="action-desc">{{ action.desc }}</view>
        </view>
      </view>
    </view>

    <view class="section">
      <view class="section-title">企业信息</view>
      <view class="section-card">
        <view class="info-row" v-for="info in infos" :key="info.label">
          <view class="info-label">{{ info.label }}</view>
          <view class="info-value">{{ info.value }}</view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      permissions: [
        {
          title: '企业账号',
          desc: '可发布产品、提交需求、维护企业信息。'
        },
        {
          title: '非企业账号',
          desc: '可浏览政策、课堂与订阅消息。'
        }
      ],
      actions: [
        {
          title: '发布产品',
          desc: '快速提交产品信息',
          path: '/pages/gallery/index'
        },
        {
          title: '修改企业信息',
          desc: '更新企业简介与联系方式',
          path: '/pages/profile/index'
        },
        {
          title: '订阅消息',
          desc: '管理订阅提醒',
          path: '/pages/subscribe/index'
        }
      ],
      infos: [
        {
          label: '主营业务',
          value: '智能装备制造、系统集成'
        },
        {
          label: '联系人',
          value: '李经理 13800001234'
        },
        {
          label: '企业地址',
          value: '当阳市产业新区创新大道8号'
        }
      ]
    }
  },
  methods: {
    go(path) {
      uni.navigateTo({
        url: path
      })
    }
  }
}
</script>

<style scoped>
.page {
  padding: 24rpx;
}

.profile-card {
  background: #fff;
  border-radius: 24rpx;
  padding: 24rpx;
  display: flex;
  align-items: center;
  gap: 16rpx;
  box-shadow: 0 12rpx 32rpx rgba(15, 33, 64, 0.06);
}

.avatar {
  width: 88rpx;
  height: 88rpx;
  border-radius: 50%;
  background: #0b72f0;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 32rpx;
  font-weight: 600;
}

.profile-info {
  flex: 1;
}

.name {
  font-size: 30rpx;
  font-weight: 600;
}

.meta {
  margin-top: 6rpx;
  color: #6b7280;
  font-size: 24rpx;
}

.switch-btn {
  background: #e6f2ff;
  color: #0b72f0;
}

.section {
  margin-top: 24rpx;
}

.section-title {
  font-size: 28rpx;
  font-weight: 600;
  margin-bottom: 16rpx;
}

.section-card {
  background: #fff;
  border-radius: 18rpx;
  padding: 20rpx;
  box-shadow: 0 8rpx 24rpx rgba(15, 33, 64, 0.06);
}

.permission {
  padding: 12rpx 0;
  border-bottom: 1rpx solid #eef2f7;
}

.permission:last-child {
  border-bottom: none;
}

.permission-title {
  font-size: 26rpx;
  font-weight: 600;
}

.permission-desc {
  margin-top: 6rpx;
  font-size: 22rpx;
  color: #6b7280;
}

.action-grid {
  display: grid;
  gap: 16rpx;
}

.action-card {
  background: #fff;
  border-radius: 18rpx;
  padding: 20rpx;
  box-shadow: 0 8rpx 24rpx rgba(15, 33, 64, 0.06);
}

.action-title {
  font-size: 26rpx;
  font-weight: 600;
}

.action-desc {
  margin-top: 8rpx;
  color: #6b7280;
  font-size: 22rpx;
}

.info-row {
  display: flex;
  justify-content: space-between;
  padding: 12rpx 0;
  border-bottom: 1rpx solid #eef2f7;
}

.info-row:last-child {
  border-bottom: none;
}

.info-label {
  color: #6b7280;
  font-size: 24rpx;
}

.info-value {
  font-size: 24rpx;
  font-weight: 500;
}
</style>
