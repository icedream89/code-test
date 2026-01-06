<template>
  <view class="page">
    <view class="form-card">
      <view class="form-title">快速求助</view>
      <view class="form-field">
        <text class="label">企业名称</text>
        <input class="input" v-model="form.company" placeholder="请输入企业名称" />
      </view>
      <view class="form-field">
        <text class="label">问题类型</text>
        <picker mode="selector" :range="types" @change="onTypeChange">
          <view class="picker">{{ form.type || '请选择问题类型' }}</view>
        </picker>
      </view>
      <view class="form-field">
        <text class="label">问题描述</text>
        <textarea class="textarea" v-model="form.detail" placeholder="描述问题与诉求" />
      </view>
      <view class="form-field">
        <text class="label">联系方式</text>
        <input class="input" v-model="form.contact" placeholder="手机号/微信" />
      </view>
      <button class="submit" @tap="submit">提交求助</button>
    </view>

    <view class="section">
      <view class="section-title">求助进度</view>
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
      types: ['融资需求', '技术难题', '政策咨询', '用工需求', '其他'],
      form: {
        company: '',
        type: '',
        detail: '',
        contact: ''
      },
      progress: [
        {
          title: '设备升级资金协调',
          date: '2024-07-08',
          status: '处理中',
          desc: '已安排对接金融机构，预计2个工作日内反馈。'
        },
        {
          title: '节能审查咨询',
          date: '2024-06-25',
          status: '已完成',
          desc: '提供审查流程与材料清单。'
        }
      ]
    }
  },
  methods: {
    onTypeChange(event) {
      this.form.type = this.types[event.detail.value]
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
