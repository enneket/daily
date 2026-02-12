---
title: 总体统计
---

# 总体统计

::: info 数据说明
统计数据每次构建时自动生成，显示您的日报写作情况。
:::

<script setup>
import { data as stats } from './.vitepress/stats.data';

// 安全获取数据
const total = stats?.total || 0;
const thisYear = stats?.thisYear || 0;
const thisMonth = stats?.thisMonth || 0;
const totalWords = stats?.totalWords || 0;
const avgWords = stats?.avgWords || 0;
const firstDate = stats?.firstDate || '';
const lastDate = stats?.lastDate || '';
const byYear = stats?.byYear || {};
const byMonth = stats?.byMonth || {};
</script>

## 📊 核心数据

<div class="stats-grid">
  <div class="stat-card large">
    <div class="stat-icon">📝</div>
    <div class="stat-value">{{ total }}</div>
    <div class="stat-label">总日报数</div>
  </div>
  
  <div class="stat-card">
    <div class="stat-value">{{ thisYear }}</div>
    <div class="stat-label">今年日报</div>
  </div>
  
  <div class="stat-card">
    <div class="stat-value">{{ thisMonth }}</div>
    <div class="stat-label">本月日报</div>
  </div>
  
  <div class="stat-card">
    <div class="stat-value">{{ totalWords.toLocaleString() }}</div>
    <div class="stat-label">总字数</div>
  </div>
  
  <div class="stat-card">
    <div class="stat-value">{{ avgWords }}</div>
    <div class="stat-label">平均字数</div>
  </div>
</div>

<div v-if="firstDate && lastDate">

## ⏱️ 时间跨度

<div class="time-range">
  <div class="range-item">
    <div class="range-label">第一篇</div>
    <div class="range-value">{{ firstDate }}</div>
  </div>
  <div class="range-divider">→</div>
  <div class="range-item">
    <div class="range-label">最新一篇</div>
    <div class="range-value">{{ lastDate }}</div>
  </div>
</div>

</div>

<div v-if="Object.keys(byYear).length > 0">

## 📅 按年统计

<div class="year-stats">
  <div 
    v-for="(count, year) in byYear" 
    :key="year"
    class="year-item"
  >
    <div class="year-label">{{ year }} 年</div>
    <div class="year-bar">
      <div 
        class="year-bar-fill" 
        :style="{ width: (count / total * 100) + '%' }"
      ></div>
    </div>
    <div class="year-count">{{ count }} 篇</div>
  </div>
</div>

</div>

<div v-if="Object.keys(byMonth).length > 0">

## 📆 按月统计

<div class="month-stats">
  <div 
    v-for="(count, month) in byMonth" 
    :key="month"
    class="month-item"
  >
    <div class="month-label">{{ month }}</div>
    <div class="month-count">{{ count }} 篇</div>
  </div>
</div>

</div>

<style scoped>
.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
  margin: 2rem 0;
}

.stat-card {
  padding: 2rem;
  background: var(--vp-c-bg-soft);
  border-radius: 12px;
  text-align: center;
  transition: transform 0.2s, box-shadow 0.2s;
}

.stat-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.stat-card.large {
  grid-column: span 2;
}

.stat-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.stat-value {
  font-size: 2.5rem;
  font-weight: bold;
  color: var(--vp-c-brand-1);
  line-height: 1;
}

.stat-label {
  margin-top: 0.75rem;
  font-size: 0.875rem;
  color: var(--vp-c-text-2);
}

.time-range {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 2rem;
  padding: 2rem;
  background: var(--vp-c-bg-soft);
  border-radius: 12px;
  margin: 2rem 0;
}

.range-item {
  text-align: center;
}

.range-label {
  font-size: 0.875rem;
  color: var(--vp-c-text-2);
  margin-bottom: 0.5rem;
}

.range-value {
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--vp-c-brand-1);
}

.range-divider {
  font-size: 2rem;
  color: var(--vp-c-text-3);
}

.year-stats {
  margin: 2rem 0;
}

.year-item {
  display: grid;
  grid-template-columns: 100px 1fr 80px;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
  background: var(--vp-c-bg-soft);
  border-radius: 8px;
  margin-bottom: 0.75rem;
}

.year-label {
  font-weight: 600;
  color: var(--vp-c-text-1);
}

.year-bar {
  height: 24px;
  background: var(--vp-c-default-soft);
  border-radius: 12px;
  overflow: hidden;
}

.year-bar-fill {
  height: 100%;
  background: var(--vp-c-brand-1);
  transition: width 0.3s;
}

.year-count {
  text-align: right;
  font-weight: 600;
  color: var(--vp-c-brand-1);
}

.month-stats {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 1rem;
  margin: 2rem 0;
}

.month-item {
  padding: 1rem;
  background: var(--vp-c-bg-soft);
  border-radius: 8px;
  text-align: center;
}

.month-label {
  font-size: 0.875rem;
  color: var(--vp-c-text-2);
  margin-bottom: 0.5rem;
}

.month-count {
  font-size: 1.5rem;
  font-weight: bold;
  color: var(--vp-c-brand-1);
}

@media (max-width: 768px) {
  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }
  
  .stat-card.large {
    grid-column: span 2;
  }
  
  .time-range {
    flex-direction: column;
    gap: 1rem;
  }
  
  .range-divider {
    transform: rotate(90deg);
  }
  
  .year-item {
    grid-template-columns: 80px 1fr 60px;
    gap: 0.5rem;
  }
  
  .month-stats {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
