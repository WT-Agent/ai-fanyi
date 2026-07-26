<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">实战案例与精译模板库 (Nomads Showcase)</h2>
        <p class="showcase-subtitle">精选多语种高频场景，点击“一键套用”快速获取地道翻译与润色</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个跨语言翻译模板</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次应用</span>
        </div>

        <div class="card-content">
          <h3 class="item-title">{{ item.title }}</h3>
          <p class="item-prompt">“{{ item.prompt }}”</p>
        </div>

        <div class="card-action">
          <button class="apply-btn" @click="applyTemplate(item)">
            <span>一键套用</span>
            <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  prompt: string;
  translationType?: string;
  targetLang?: string;
  toneStyle?: string;
  usageCount: string;
}

const emit = defineEmits<{
  (e: 'apply-template', payload: {
    prompt: string;
    translationType?: string;
    targetLang?: string;
    toneStyle?: string;
  }): void;
}>();

const showcaseItems = computed<ShowcaseItem[]>(() => [
  {
    id: 'fanyi-1',
    tag: '学术润色',
    title: 'SCI 论文摘要顶级学术表达润色',
    prompt: '针对人工智能领域 SCI 论文 Abstract，提升学术用词精准度，替换平淡口语化词汇为高端学术动词，优化被动语态与复合句型。',
    translationType: '学术论文与期刊地道润色',
    targetLang: '英语English',
    toneStyle: '专业严谨学术风',
    usageCount: '45.2k'
  },
  {
    id: 'fanyi-2',
    tag: '商务外贸',
    title: '外贸客户询盘与价格谈判邮件',
    prompt: '针对欧洲客户关于产品定制化报价与交货期的询盘，撰写礼貌得体、条理清晰且富有专业商务谈判技巧的回复邮件。',
    translationType: '商务邮件与外贸合同翻译',
    targetLang: '英语English',
    toneStyle: '正式商务公文风',
    usageCount: '39.8k'
  },
  {
    id: 'fanyi-3',
    tag: '软件本地化',
    title: 'SaaS 软件核心界面与错误提示本地化',
    prompt: '将云端协同软件的登录、配置、权限管理与异常提示语翻译为地道日文，确保简短精练且完全符合日本用户 UI 使用习惯。',
    translationType: '软件本地化与多语种互译',
    targetLang: '日语Japanese',
    toneStyle: '自然流畅口语风',
    usageCount: '31.4k'
  },
  {
    id: 'fanyi-4',
    tag: '法律合同',
    title: '跨国保密协议与补充条款严谨翻译',
    prompt: '将中英文 NDA 保密协议及补充违约赔偿条款精准翻译为德语，确保法律术语严谨且无歧义。',
    translationType: '商务邮件与外贸合同翻译',
    targetLang: '德语German',
    toneStyle: '专业严谨学术风',
    usageCount: '28.6k'
  },
  {
    id: 'fanyi-5',
    tag: '品牌意译',
    title: '企业品牌口号与文化故事意译润色',
    prompt: '将企业东方美学品牌的宣传语与品牌故事意译为优雅法语，保留诗意韵味并符合欧洲文化审美习惯。',
    translationType: '文学作品与口语地道意译',
    targetLang: '法语French',
    toneStyle: '优雅文学意译风',
    usageCount: '25.7k'
  },
  {
    id: 'fanyi-6',
    tag: '跨境说明书',
    title: '智能家电西语产品使用说明与 FAQ',
    prompt: '针对拉丁美洲西语市场，翻译智能扫地机的产品功能说明、常见故障排查与安全警告事项。',
    translationType: '软件本地化与多语种互译',
    targetLang: '西班牙语Spanish',
    toneStyle: '正式商务公文风',
    usageCount: '22.1k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt,
    translationType: item.translationType,
    targetLang: item.targetLang,
    toneStyle: item.toneStyle
  });
}
</script>

<style scoped>
.nomads-showcase-section {
  margin-top: 2rem;
  width: 100%;
}

.showcase-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1.25rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--card-border);
}

.showcase-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.showcase-subtitle {
  font-size: 0.825rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
}

.showcase-badge {
  font-size: 0.75rem;
  color: #a5b4fc;
  background: rgba(99, 102, 241, 0.12);
  border: 1px solid rgba(99, 102, 241, 0.25);
  padding: 4px 10px;
  border-radius: 20px;
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .showcase-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .showcase-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.showcase-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 1.25rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--card-border);
  border-radius: 14px;
  transition: all 0.25s ease;
}

.showcase-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.scenario-tag {
  font-size: 0.75rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 6px;
  background: rgba(168, 85, 247, 0.15);
  color: #c084fc;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

.usage-count {
  font-size: 0.75rem;
  color: var(--text-secondary);
}

.card-content {
  margin-bottom: 1rem;
  flex: 1;
}

.item-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.4rem;
}

.item-prompt {
  font-size: 0.825rem;
  color: var(--text-secondary);
  line-height: 1.45;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-style: italic;
}

.card-action {
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.04);
}

.apply-btn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 0.5rem 1rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  border-radius: 8px;
  color: #a5b4fc;
  font-size: 0.825rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.showcase-card:hover .apply-btn {
  background: var(--primary-gradient);
  border-color: transparent;
  color: white;
}

.arrow-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.2s ease;
}

.apply-btn:hover .arrow-icon {
  transform: translateX(3px);
}
</style>
