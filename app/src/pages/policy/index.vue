<template>
  <view class="page">
    <view class="search-bar">
      <text class="search-icon">🔍</text>
      <input class="search-input" placeholder="搜索政策关键词" v-model="keyword" />
    </view>

    <view class="policy-group" v-for="group in filteredPolicies" :key="group.level">
      <view class="group-header">
        <view class="group-title">{{ group.level }}</view>
        <view class="group-desc">{{ group.desc }}</view>
      </view>
      <view class="policy-list">
        <view class="policy-card" v-for="policy in group.items" :key="policy.title">
          <view class="policy-title">{{ policy.title }}</view>
          <view class="policy-meta">{{ policy.department }} · {{ policy.date }}</view>
          <view class="policy-summary">{{ policy.summary }}</view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      keyword: '',
      policies: [
        {
          level: '国家级政策',
          desc: '高质量发展、创新与产业升级',
          items: [
            {
              title: '制造业数字化转型行动方案',
              department: '工信部',
              date: '2024-06-01',
              summary: '聚焦中小企业数字化改造，提供项目支持。'
            },
            {
              title: '专精特新企业培育计划',
              department: '国家工信部门',
              date: '2024-04-18',
              summary: '明确梯度培育路径和资金保障。'
            }
          ]
        },
        {
          level: '省级政策',
          desc: '湖北省产业链协同与招商支持',
          items: [
            {
              title: '湖北省企业技术改造补贴指引',
              department: '省经信厅',
              date: '2024-05-08',
              summary: '对智能化改造项目给予最高30%补贴。'
            },
            {
              title: '科技成果转化专项政策',
              department: '省科技厅',
              date: '2024-03-22',
              summary: '支持高校成果落地产业化。'
            }
          ]
        },
        {
          level: '当阳市政策',
          desc: '本地企业扶持与创新支持',
          items: [
            {
              title: '当阳市工业企业稳产增效措施',
              department: '当阳市科技经信商务局',
              date: '2024-07-02',
              summary: '针对重点企业实施一企一策服务。'
            },
            {
              title: '人才引育奖励实施细则',
              department: '当阳市委组织部',
              date: '2024-02-15',
              summary: '新增高层次人才奖励与住房补贴。'
            }
          ]
        }
      ]
    }
  },
  computed: {
    filteredPolicies() {
      if (!this.keyword) {
        return this.policies
      }
      const keyword = this.keyword.trim().toLowerCase()
      return this.policies
        .map((group) => {
          const items = group.items.filter((item) =>
            [item.title, item.department, item.summary].some((text) =>
              text.toLowerCase().includes(keyword)
            )
          )
          return {
            ...group,
            items
          }
        })
        .filter((group) => group.items.length)
    }
  }
}
</script>

<style scoped>
.page {
  padding: 24rpx;
}

.search-bar {
  background: #fff;
  border-radius: 20rpx;
  padding: 16rpx 20rpx;
  display: flex;
  align-items: center;
  margin-bottom: 24rpx;
  box-shadow: 0 12rpx 32rpx rgba(15, 33, 64, 0.06);
}

.search-icon {
  margin-right: 12rpx;
}

.search-input {
  flex: 1;
  font-size: 26rpx;
}

.policy-group {
  margin-bottom: 28rpx;
}

.group-header {
  margin-bottom: 12rpx;
}

.group-title {
  font-size: 30rpx;
  font-weight: 600;
}

.group-desc {
  font-size: 24rpx;
  color: #6b7280;
  margin-top: 6rpx;
}

.policy-list {
  display: flex;
  flex-direction: column;
  gap: 16rpx;
}

.policy-card {
  background: #fff;
  border-radius: 18rpx;
  padding: 20rpx;
  box-shadow: 0 8rpx 24rpx rgba(15, 33, 64, 0.06);
}

.policy-title {
  font-size: 28rpx;
  font-weight: 600;
}

.policy-meta {
  font-size: 22rpx;
  color: #6b7280;
  margin-top: 8rpx;
}

.policy-summary {
  margin-top: 10rpx;
  font-size: 24rpx;
  color: #374151;
}
</style>
