<template>
  <div class="glass-card ticker-card">
    <div class="ticker-wrapper">
      <div v-for="(item, index) in tickerItems" :key="index" class="ticker-item">
        <span>{{ item.text }}</span>
        <span style="color: var(--success-color); font-weight: bold;">[翻译成功]</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tickerItems = ref([
  { text: '用户 138****9281 刚刚完成了 SCI 论文 Abstract 英语学术润色并导出' },
  { text: '用户 159****4012 成功将 20 页外贸商务合同精准翻译为德语' },
  { text: '用户 186****7739 刚刚使用软件 UI 本地化模块生成了日韩双语语言包' },
  { text: '用户 135****6188 刚刚完成跨国投融资路演 PPT 意译与术语矫正' },
  { text: '用户 177****5520 成功优化了海外客户退换货邮件的商务法语回复' },
]);
</script>

<style scoped>
.ticker-card {
  padding: 0.6rem 1rem;
  margin-bottom: 1.25rem;
  overflow: hidden;
}

.ticker-wrapper {
  display: flex;
  gap: 2rem;
  white-space: nowrap;
  animation: ticker 25s linear infinite;
}

.ticker-wrapper:hover {
  animation-play-state: paused;
}

.ticker-item {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.8rem;
  color: var(--text-secondary);
}

@keyframes ticker {
  0% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(-100%);
  }
}
</style>
