<template>
  <view class="page">
    <view class="intro">
      <view class="intro-title">企业画册</view>
      <view class="intro-desc">按行业分类展示企业信息、产品模块与销售联络方式。</view>
    </view>

    <view class="category" v-for="group in groups" :key="group.name">
      <view class="category-title">{{ group.name }}</view>
      <view class="company-grid">
        <view class="company-card" v-for="company in group.companies" :key="company.name">
          <view class="company-name">{{ company.name }}</view>
          <view class="company-info">{{ company.desc }}</view>
          <view class="product-title">产品模块</view>
          <view class="product-tags">
            <text class="tag" v-for="item in company.products" :key="item">{{ item }}</text>
          </view>
          <view class="contact">
            <view class="contact-label">销售联络：</view>
            <view class="contact-name">{{ company.contact }}</view>
            <button class="call-btn" size="mini" @tap="call(company.phone)">一键拨号</button>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      groups: [
        {
          name: '装备制造',
          companies: [
            {
              name: '当阳智造装备有限公司',
              desc: '专注智能装配线、工业机器人集成。',
              products: ['装配线', '智能机器人', '维保服务'],
              contact: '李经理',
              phone: '13800001234'
            },
            {
              name: '华中精工科技',
              desc: '提供精密零部件加工与定制。',
              products: ['精密加工', '定制模具'],
              contact: '周经理',
              phone: '13800005678'
            }
          ]
        },
        {
          name: '新材料',
          companies: [
            {
              name: '丹阳新材料科技',
              desc: '玻璃基材、工业涂层一体化供应。',
              products: ['玻璃基材', '工业涂层', '技术咨询'],
              contact: '王经理',
              phone: '13900001234'
            }
          ]
        }
      ]
    }
  },
  methods: {
    call(phone) {
      uni.makePhoneCall({
        phoneNumber: phone
      })
    }
  }
}
</script>

<style scoped>
.page {
  padding: 24rpx;
}

.intro {
  background: #fff;
  border-radius: 24rpx;
  padding: 24rpx;
  box-shadow: 0 12rpx 32rpx rgba(15, 33, 64, 0.06);
}

.intro-title {
  font-size: 32rpx;
  font-weight: 600;
}

.intro-desc {
  margin-top: 12rpx;
  font-size: 24rpx;
  color: #6b7280;
}

.category {
  margin-top: 24rpx;
}

.category-title {
  font-size: 28rpx;
  font-weight: 600;
  margin-bottom: 16rpx;
}

.company-grid {
  display: flex;
  flex-direction: column;
  gap: 16rpx;
}

.company-card {
  background: #fff;
  border-radius: 18rpx;
  padding: 20rpx;
  box-shadow: 0 8rpx 24rpx rgba(15, 33, 64, 0.06);
}

.company-name {
  font-size: 28rpx;
  font-weight: 600;
}

.company-info {
  margin-top: 8rpx;
  font-size: 24rpx;
  color: #4b5563;
}

.product-title {
  margin-top: 16rpx;
  font-size: 24rpx;
  font-weight: 600;
}

.product-tags {
  margin-top: 8rpx;
  display: flex;
  flex-wrap: wrap;
  gap: 12rpx;
}

.tag {
  background: #e6f2ff;
  color: #0b72f0;
  padding: 6rpx 12rpx;
  border-radius: 999rpx;
  font-size: 22rpx;
}

.contact {
  margin-top: 16rpx;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 12rpx;
}

.contact-label {
  color: #6b7280;
}

.contact-name {
  font-weight: 600;
}

.call-btn {
  margin-left: auto;
  background: #0b72f0;
  color: #fff;
}
</style>
