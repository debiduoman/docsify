# 今日开发日志：Docsify 部署全记录

> 记录 Node.js 环境配置与 Docsify 部署完整过程

## 目录
- #检查nodejs
- #部署docsify
- #github-项目部署
- #启用并配置侧边栏
- #应对push错误
- #push成功

---

## 检查 Node.js 环境

全局环境变量配置：
```bash
系统环境变量 'C:\Program Files\nodejs\node_global'
```

## 部署 Docsify 开发环境

```bash
# 全局安装 docsify-cli
npm i docsify-cli -g
```

## 初始化项目结构

```bash
# 在项目目录执行初始化命令
npx docsify init ./docs
```

---

## GitHub 项目部署

### 完整操作流程

1. **本地仓库初始化**
```bash
git init
git status  # 检查当前Git状态
```

2. **首次代码提交**
```bash
git add .
git commit -m "Initial commit"
git branch -M main  # 分支命名标准化
```

3. **关联远程仓库**
```bash
git remote add origin https://github.com/debiduoman/docsify.git
```

4. **推送至 GitHub**
```bash
git push -u origin main
```

5. **GitHub Pages 配置**
```
GitHub 仓库 → Settings → Pages
├── Source: Deploy from a branch
├── Branch: main
└── Folder: /docs
```

---

## 启用并配置侧边栏

1. 修改 `docs/index.html`：
```javascript
window.$docsify = {
  loadSidebar: true,
  subMaxLevel: 2
}
```

2. 创建 `_sidebar.md` 文件实现自动目录生成

---

## 应对 push 错误

### HTTPS 443端口连接失败解决方案

```bash
# 切换至 SSH 协议
git remote set-url origin git@github.com:debiduoman/docsify.git
```

### SSH 密钥配置步骤
1. 获取公钥内容：
```
路径：C:\Users\SuoJie\.ssh\id_rsa.pub
```

2. GitHub 配置入口：
```
用户设置 → SSH and GPG keys → New SSH key
```

3. 密钥填写指南：
```
Title: My Windows PC
Key: [粘贴完整公钥内容]
```

---

## Push 成功验证

### 部署结果
```bash
✅ 代码成功推送至 GitHub 仓库
```

### 访问链接
👉 https://debiduoman.github.io/docsify/

### 后续更新流程
```bash
# 标准三步操作
git add .
git commit -m "更新说明"
git push origin main
```

> **注**：GitHub Pages 会自动构建更新，1-2分钟后刷新页面即可查看最新内容

---

> 本次部署耗时：120分钟  
> 关键技术点：Node环境配置·GitHub Pages·SSH密钥认证  
> 文档渲染效果：支持侧边栏导航 + 自动标题目录