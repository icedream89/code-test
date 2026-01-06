<template>
  <view class="page">
    <view class="form-card">
      <view class="form-title">采购需求提交</view>
      <view class="form-field">
        <text class="label">采购主题</text>
        <input class="input" v-model="form.title" placeholder="例如：设备采购" />
      </view>
      <view class="form-field">
        <text class="label">品类</text>
        <picker mode="selector" :range="categories" @change="onCategoryChange">
          <view class="picker">{{ form.category || '请选择品类' }}</view>
        </picker>
      </view>
      <view class="form-field">
        <text class="label">需求描述</text>
        <textarea class="textarea" v-model="form.detail" placeholder="填写采购规格、数量等" />
      </view>
      <view class="form-field">
        <text class="label">预算区间</text>
        <input class="input" v-model="form.budget" placeholder="请输入预算区间" />
      </view>
      <button class="submit" @tap="submit">提交采购</button>
    </view>

    <view class="section">
      <view class="section-title">回复进度</view>
      <view class="progress-list">
        <view class="progress-card" v-for="item in progress" :key="item.title">
          <view class="progress-title">{{ item.title }}</view>
          <view class="progress-meta">{{ item.date }} · {{ item.status }}</view>
          <view class="progress-desc">{{ item.desc }}</view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      categories: ['设备', '原材料', '技术服务', '物流仓储', '其他'],
      form: {
        title: '',
        category: '',
        detail: '',
        budget: ''
      },
      progress: [
        {
          title: '自动化设备采购对接',
          date: '2024-07-05',
          status: '已反馈',
          desc: '推荐3家供应商并完成初步报价。'
        },
        {
          title: '包装材料采购',
          date: '2024-06-18',
          status: '处理中',
          desc: '正在汇总本地供应商产能信息。'
        }
      ]
    }
  },
  methods: {
    onCategoryChange(event) {
      this.form.category = this.categories[event.detail.value]
    },
    submit() {
      uni.showToast({
        title: '已提交',
        icon: 'success'
      })
    }
  }
}
</script>

<style scoped>
.page {
  padding: 24rpx;
}

.form-card {
  background: #fff;
  border-radius: 20rpx;
  padding: 24rpx;
  box-shadow: 0 12rpx 32rpx rgba(15, 33, 64, 0.06);
}

.form-title {
  font-size: 30rpx;
  font-weight: 600;
  margin-bottom: 16rpx;
}

.form-field {
  margin-bottom: 16rpx;
}

.label {
  display: block;
  font-size: 24rpx;
  color: #6b7280;
  margin-bottom: 8rpx;
}

.input,
.textarea,
.picker {
  background: #f3f4f6;
  border-radius: 12rpx;
  padding: 16rpx;
  font-size: 26rpx;
}

.textarea {
  height: 140rpx;
}

.submit {
  background: #0b72f0;
  color: #fff;
  margin-top: 8rpx;
}

.section {
  margin-top: 24rpx;
}

.section-title {
  font-size: 28rpx;
  font-weight: 600;
  margin-bottom: 16rpx;
}

.progress-list {
  display: flex;
  flex-direction: column;
  gap: 16rpx;
}

.progress-card {
  background: #fff;
  border-radius: 18rpx;
  padding: 20rpx;
  box-shadow: 0 8rpx 24rpx rgba(15, 33, 64, 0.06);
}

.progress-title {
  font-weight: 600;
  font-size: 28rpx;
}

.progress-meta {
  margin-top: 8rpx;
  color: #6b7280;
  font-size: 22rpx;
}

.progress-desc {
  margin-top: 8rpx;
  font-size: 24rpx;
}
</style>
