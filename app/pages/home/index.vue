<template>
  <view class="page">
    <swiper class="banner" circular autoplay interval="4000" indicator-dots indicator-active-color="#0B72F0">
      <swiper-item v-for="(item, index) in banners" :key="index">
        <view class="banner-item">
          <view class="banner-tag">{{ item.tag }}</view>
          <view class="banner-title">{{ item.title }}</view>
          <view class="banner-desc">{{ item.desc }}</view>
        </view>
      </swiper-item>
    </swiper>

    <view class="section">
      <view class="section-title">核心入口</view>
      <view class="entry-grid">
        <view class="entry-card" v-for="item in entries" :key="item.path" @tap="go(item.path)">
          <view class="entry-icon">{{ item.icon }}</view>
          <view class="entry-name">{{ item.name }}</view>
          <view class="entry-desc">{{ item.desc }}</view>
        </view>
      </view>
    </view>

    <view class="section">
      <view class="section-title">企业推荐</view>
      <view class="company-list">
        <view class="company-card" v-for="company in companies" :key="company.name">
          <view class="company-name">{{ company.name }}</view>
          <view class="company-meta">{{ company.industry }} · {{ company.scale }}</view>
          <view class="company-desc">{{ company.desc }}</view>
          <view class="company-tags">
            <text class="tag" v-for="tag in company.tags" :key="tag">{{ tag }}</text>
          </view>
        </view>
      </view>
    </view>

    <view class="section">
      <view class="section-title">服务直达</view>
      <view class="quick-actions">
        <view class="action-card" v-for="item in quickActions" :key="item.path" @tap="go(item.path)">
          <view class="action-title">{{ item.title }}</view>
          <view class="action-desc">{{ item.desc }}</view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      banners: [
        {
          tag: '产业风景',
          title: '项目建设一线实时展示',
          desc: '展示企业风貌与重点项目建设进展。'
        },
        {
          tag: '政策速递',
          title: '国家到当阳政策一站查询',
          desc: '分层级梳理政策，快速定位。'
        },
        {
          tag: '企业成长',
          title: '课程与资源持续更新',
          desc: '支撑企业学习与能力提升。'
        }
      ],
      entries: [
        {
          name: '政策查询',
          desc: '国家-市级政策一览',
          icon: '📄',
          path: '/pages/policy/index'
        },
        {
          name: '企业课堂',
          desc: '学习资料与培训资源',
          icon: '🎓',
          path: '/pages/classroom/index'
        },
        {
          name: '企业画册',
          desc: '企业展示与产品模块',
          icon: '🏭',
          path: '/pages/gallery/index'
        }
      ],
      companies: [
        {
          name: '当阳智造装备有限公司',
          industry: '智能装备',
          scale: '规上企业',
          desc: '提供智能装配线及数字化改造服务。',
          tags: ['专精特新', '智能制造']
        },
        {
          name: '丹阳新材料科技',
          industry: '新材料',
          scale: '高新技术企业',
          desc: '覆盖玻璃基材、工业涂层等产品。',
          tags: ['新材料', '绿色工艺']
        },
        {
          name: '宜昌山水农品',
          industry: '农产品加工',
          scale: '重点龙头',
          desc: '打造当阳特色农品供应链。',
          tags: ['乡村振兴', '供应链']
        }
      ],
      quickActions: [
        {
          title: '我要采购',
          desc: '快速提交采购需求',
          path: '/pages/procurement/index'
        },
        {
          title: '我要求助',
          desc: '提交企业问题与诉求',
          path: '/pages/help/index'
        },
        {
          title: '订阅消息',
          desc: '重要事项提醒通知',
          path: '/pages/subscribe/index'
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

.banner {
  height: 320rpx;
  border-radius: 24rpx;
  overflow: hidden;
  margin-bottom: 24rpx;
}

.banner-item {
  height: 100%;
  background: linear-gradient(135deg, #0b72f0, #47a4ff);
  color: #fff;
  padding: 32rpx;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.banner-tag {
  font-size: 24rpx;
  opacity: 0.85;
  margin-bottom: 12rpx;
}

.banner-title {
  font-size: 36rpx;
  font-weight: 600;
}

.banner-desc {
  font-size: 24rpx;
  margin-top: 12rpx;
  opacity: 0.9;
}

.section {
  margin-top: 24rpx;
}

.section-title {
  font-size: 30rpx;
  font-weight: 600;
  margin-bottom: 16rpx;
}

.entry-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16rpx;
}

.entry-card {
  background: #fff;
  border-radius: 20rpx;
  padding: 20rpx 16rpx;
  box-shadow: 0 12rpx 32rpx rgba(15, 33, 64, 0.08);
  text-align: center;
}

.entry-icon {
  font-size: 40rpx;
}

.entry-name {
  font-weight: 600;
  margin-top: 12rpx;
}

.entry-desc {
  font-size: 22rpx;
  color: #6b7280;
  margin-top: 8rpx;
}

.company-list {
  display: flex;
  flex-direction: column;
  gap: 16rpx;
}

.company-card {
  background: #fff;
  border-radius: 20rpx;
  padding: 20rpx;
  box-shadow: 0 10rpx 28rpx rgba(15, 33, 64, 0.06);
}

.company-name {
  font-size: 30rpx;
  font-weight: 600;
}

.company-meta {
  color: #6b7280;
  margin-top: 8rpx;
  font-size: 24rpx;
}

.company-desc {
  margin-top: 8rpx;
  font-size: 24rpx;
}

.company-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 12rpx;
  margin-top: 12rpx;
}

.tag {
  background: #e6f2ff;
  color: #0b72f0;
  padding: 6rpx 12rpx;
  border-radius: 999rpx;
  font-size: 22rpx;
}

.quick-actions {
  display: grid;
  gap: 16rpx;
}

.action-card {
  background: #fff;
  border-radius: 20rpx;
  padding: 20rpx;
  box-shadow: 0 10rpx 28rpx rgba(15, 33, 64, 0.06);
}

.action-title {
  font-size: 28rpx;
  font-weight: 600;
}

.action-desc {
  color: #6b7280;
  margin-top: 8rpx;
  font-size: 24rpx;
}
</style>
