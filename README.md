# Markdown Multi-Platform Publisher

一款基于 Markdown 的写作与发布工具，支持一键导出/发布到微信公众号、小红书、知乎等平台，并集成 AI 智能优化功能（自定义 Prompt 模板）。

[![Vue 3](https://img.shields.io/badge/Vue-3.3-brightgreen)](https://vuejs.org/)
[![Vite](https://img.shields.io/badge/Vite-4.4-646CFF)](https://vitejs.dev/)
[![Element Plus](https://img.shields.io/badge/Element%20Plus-2.3-409EFF)](https://element-plus.org/)
[![Vditor](https://img.shields.io/badge/Vditor-3.9-blue)](https://github.com/Vanessa219/vditor)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15+-4169E1)](https://www.postgresql.org/)
[![Redis](https://img.shields.io/badge/Redis-7+-DC382D)](https://redis.io/)

---

## ✨ 功能特点

### 📝 Markdown 编辑器
- 基于 Vditor 的即时渲染编辑器，支持代码高亮、表格、图表、Emoji 等扩展语法。
- 实时预览，可切换不同平台样式（微信公众号、小红书、知乎）。

### 🔄 多平台转换与发布
- **微信公众号**：生成兼容的富文本 HTML，支持图片自动上传至微信素材库，通过 API 直接发布草稿。
- **小红书**：转换为适合小红书的纯文本/富文本格式，支持一键复制。
- **知乎**：生成兼容格式，支持复制或 API 发布（需权限）。
- 扩展架构，可轻松接入更多平台。

### 🤖 AI 智能助手
- **标题生成**：根据文章内容自动生成多个吸睛标题。
- **内容润色/扩写/缩写**：优化文章表达，调整篇幅。
- **敏感词检测**：识别并替换违规词，保障内容安全。
- **智能配图推荐**：基于语义分析推荐无版权图片（规划中）。
- **自定义 Prompt 模板**：用户可创建、编辑、共享自己的 Prompt 模板，灵活控制 AI 输出。

### 🖼️ 图片处理
- 支持拖拽/粘贴上传本地图片。
- 自动上传至用户指定的图床（如七牛云、阿里云 OSS）或微信素材库。
- 图片链接自动替换，发布无忧。

### 📂 草稿与团队协作
- 云端保存草稿，支持版本历史。
- 团队协作：共享草稿、评论、协作编辑（企业版）。

### 📊 数据看板
- 整合各平台公开数据，集中展示阅读、粉丝、互动趋势。
- 支持数据导出，辅助运营决策。

### 🔒 企业级安全架构
- **密钥安全**：所有第三方 API 密钥加密存储于后端，前端零暴露。
- **限流与防滥用**：用户级/接口级限流，异常行为检测，对爬虫返回空白信息。
- **备份与恢复**：每日全量 + 每小时增量备份，加密存储至异地云，支持一键恢复。
- **WAF 防护**：集成 ModSecurity 或 Cloudflare，拦截 SQL 注入、XSS 等攻击。
- **审计日志**：所有操作留痕，便于追溯。

---

## 🛠️ 技术栈

### 前端
- **框架**：Vue 3 + TypeScript
- **构建工具**：Vite
- **UI 组件库**：Element Plus
- **Markdown 编辑器**：Vditor
- **状态管理**：Pinia
- **路由**：Vue Router
- **HTTP 客户端**：Axios
- **图表**：ECharts
- **工具库**：Lodash、Day.js

### 后端
- **运行环境**：Node.js 18+
- **框架**：NestJS（模块化、守卫、拦截器）
- **数据库**：PostgreSQL 15+（支持 JSON、加密扩展）
- **缓存/限流**：Redis 7+
- **AI 集成**：OpenAI / 智谱 AI / 文心一言（通过统一 AI 网关）
- **备份工具**：pg_dump、WAL-G
- **密钥管理**：环境变量 / HashiCorp Vault / 云 KMS
- **监控**：Prometheus + Grafana
- **日志**：ELK Stack（Elasticsearch, Logstash, Kibana）
- **容器化**：Docker + Kubernetes
- **反向代理/WAF**：Nginx + ModSecurity 或 Cloudflare

---

## 🏗️ 项目结构（前端部分）

```
src/
├── assets/                # 静态资源
├── components/            # 公共组件
│   ├── Editor/            # 编辑器相关组件
│   │   ├── MarkdownEditor.vue
│   │   ├── AIPanel.vue
│   │   └── TemplateSelector.vue
│   ├── Layout/            # 布局组件
│   └── Common/            # 通用组件
├── views/                  # 页面视图
│   ├── Dashboard.vue       # 数据看板
│   ├── Editor.vue          # 编辑器主页面
│   ├── Templates.vue       # Prompt 模板管理
│   ├── Settings.vue        # 平台配置与个人设置
│   └── Login.vue           # 登录/注册
├── router/                 # 路由配置
├── stores/                 # Pinia 状态模块
├── api/                    # API 请求封装
├── utils/                  # 工具函数
├── types/                  # TypeScript 类型定义
├── App.vue
└── main.ts
```

后端结构（NestJS 风格）请参考 `/server` 目录。

---

## 🚀 快速开始

### 前置要求
- Node.js 18+
- PostgreSQL 15+
- Redis 7+
- （可选）Docker 与 Docker Compose

### 安装步骤

1. **克隆仓库**
   ```bash
   git clone https://github.com/yourname/markdown-publisher.git
   cd markdown-publisher
   ```

2. **安装前端依赖**
   ```bash
   cd frontend
   npm install
   ```

3. **安装后端依赖**
   ```bash
   cd ../server
   npm install
   ```

4. **配置环境变量**
   - 复制 `.env.example` 为 `.env`，填写必要的配置（数据库连接、Redis、第三方 API 密钥等）。
   - 前端 `.env` 文件配置后端 API 地址。

5. **启动开发服务**
   - 前端：`npm run dev`
   - 后端：`npm run start:dev`

6. **访问应用**
   打开浏览器访问 `http://localhost:5173`

### 使用 Docker Compose 一键启动（推荐）
```bash
docker-compose up -d
```
此命令会启动前端、后端、PostgreSQL、Redis 服务。

---

## 📚 使用指南

- **注册/登录**：首次使用需注册账号。
- **新建文章**：进入编辑器，使用 Markdown 写作。
- **调用 AI**：选中文字或点击 AI 助手图标，选择模板（可自定义）生成优化内容。
- **选择平台**：在右侧预览栏切换平台，查看渲染效果。
- **发布/复制**：点击“复制内容”将格式化的文章复制到剪贴板，直接粘贴到平台后台；微信公众号支持 API 直接发布。
- **管理模板**：在“模板管理”页面创建自己的 Prompt 模板，支持变量（如 `{{content}}`）。

---

## 🤝 贡献指南

欢迎贡献代码、报告问题或提出新功能建议！但请注意，本项目采用商业许可证，任何商业使用需获得授权。

1. Fork 本仓库。
2. 创建您的特性分支 (`git checkout -b feature/AmazingFeature`)。
3. 提交您的修改 (`git commit -m 'Add some AmazingFeature'`)。
4. 推送到分支 (`git push origin feature/AmazingFeature`)。
5. 打开一个 Pull Request。

请确保代码风格符合 ESLint 规则，并编写必要的单元测试。

---

## 📄 许可证与商业使用

本项目为**专有软件**，版权归作者所有。**未经作者书面许可，任何个人或组织不得将本软件用于商业用途**。

商业使用（包括但不限于企业内部部署、作为服务提供给第三方、集成到商业产品中）需与作者联系，获得商业授权并支付相应费用。

**个人学习、非营利性使用可免费试用，但不得分发或用于商业目的。**

如需商业授权或咨询，请联系：14778671462@sina.cn

---

## 📧 联系我们

如有问题或合作意向，请发送邮件至：14778671462@sina.cn

---

> 项目正在积极开发中，欢迎关注和参与！每日进度将更新在 GitHub 的 [Projects](https://github.com/yourname/markdown-publisher/projects) 看板中。
