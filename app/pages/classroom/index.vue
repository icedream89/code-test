<template>
  <view class="page">
    <view class="hero">
      <view class="hero-title">企业学习课堂</view>
      <view class="hero-desc">按行业与主题分层展示学习资料、培训与实战案例。</view>
    </view>

    <view class="category" v-for="category in categories" :key="category.name">
      <view class="category-title">{{ category.name }}</view>
      <view class="category-list">
        <view class="course-card" v-for="course in category.courses" :key="course.title">
          <view class="course-title">{{ course.title }}</view>
          <view class="course-meta">{{ course.duration }} · {{ course.level }}</view>
          <view class="course-desc">{{ course.desc }}</view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      categories: [
        {
          name: '政策与合规',
          courses: [
            {
              title: '惠企政策申报流程与材料准备',
              duration: '45分钟',
              level: '入门',
              desc: '掌握企业申报必备材料与时间节点。'
            },
            {
              title: '节能降碳审查与绿色认证',
              duration: '60分钟',
              level: '进阶',
              desc: '解析绿色制造体系与认证流程。'
            }
          ]
        },
        {
          name: '数字化转型',
          courses: [
            {
              title: '中小企业数字化转型路线图',
              duration: '50分钟',
              level: '入门',
              desc: '从现状诊断到系统选型一站指导。'
            },
            {
              title: '数据驱动的生产管理实践',
              duration: '70分钟',
              level: '提升',
              desc: 'MES与设备数据采集的落地案例。'
            }
          ]
        },
        {
          name: '市场与供应链',
          courses: [
            {
              title: '产业链协同供需对接',
              duration: '40分钟',
              level: '入门',
              desc: '构建上下游协同机制与对接要点。'
            },
            {
              title: '外贸订单执行与风险控制',
              duration: '55分钟',
              level: '提升',
              desc: '国际订单履约重点与风险应对。'
            }
          ]
        }
      ]
    }
  }
}
</script>

<style scoped>
.page {
  padding: 24rpx;
}

.hero {
  background: #fff;
  border-radius: 24rpx;
  padding: 24rpx;
  box-shadow: 0 12rpx 32rpx rgba(15, 33, 64, 0.06);
}

.hero-title {
  font-size: 32rpx;
  font-weight: 600;
}

.hero-desc {
  margin-top: 12rpx;
  color: #6b7280;
  font-size: 24rpx;
}

.category {
  margin-top: 24rpx;
}

.category-title {
  font-size: 28rpx;
  font-weight: 600;
  margin-bottom: 16rpx;
}

.category-list {
  display: flex;
  flex-direction: column;
  gap: 16rpx;
}

.course-card {
  background: #fff;
  border-radius: 18rpx;
  padding: 20rpx;
  box-shadow: 0 8rpx 24rpx rgba(15, 33, 64, 0.06);
}

.course-title {
  font-size: 28rpx;
  font-weight: 600;
}

.course-meta {
  margin-top: 8rpx;
  color: #6b7280;
  font-size: 22rpx;
}

.course-desc {
  margin-top: 8rpx;
  font-size: 24rpx;
}
</style>
