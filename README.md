# 我的日报

这是我的个人日报仓库，使用 [日报桌面应用](https://github.com/enneket/daily-app) 记录每天的工作和学习。

## 📝 在线查看

访问日报展示网站：[https://你的用户名.github.io/daily-reports/](https://你的用户名.github.io/daily-reports/)

## 🗂️ 目录结构

```
.
├── docs/           # 日报目录
│   └── 2026/       # 按年份组织
│       ├── 01/     # 按月份组织
│       │   ├── 01.md   # 每日日报
│       │   ├── 02.md
│       │   └── ...
│       └── 02/
│           └── ...
└── site/           # 网站源码
```

## 🚀 功能特性

- ✅ 自动按日期组织日报
- ✅ 支持同一天多次提交
- ✅ 自动生成展示网站
- ✅ 日历视图
- ✅ 归档浏览
- ✅ 统计分析
- ✅ 全文搜索

## 📱 如何使用

### 方式 1：使用桌面应用（推荐）

1. 下载并安装[日报桌面应用](https://github.com/enneket/daily-app/releases)
2. 配置 GitHub 信息
3. 开始写日报

### 方式 2：手动提交

直接在对应日期的文件中编辑，例如 `docs/2026/02/11.md`。

## 🔧 本地开发

```bash
# 安装依赖
npm install

# 生成索引
node scripts/generate-index.js

# 启动开发服务器
npm run dev:site

# 构建网站
npm run build:site
```

## 📊 统计

- 总日报数：自动统计
- 连续天数：自动计算
- 最长连续：自动记录

## 📄 许可

MIT License

---

使用 [日报桌面应用](https://github.com/enneket/daily-app) 构建
