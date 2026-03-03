# CACTER邮件安全网关系统

## 项目简介
CACTER邮件安全网关系统是一个用于邮件安全检测和管理的前端应用程序，提供邮件信息概览、检测分析、邮件详情等功能。

## 技术栈
- 前端：HTML5, CSS3, JavaScript
- 服务器：Node.js
- 依赖管理：npm

## 部署步骤

### 1. 环境准备
- 安装 Node.js 14.0 或更高版本
- 安装 npm 6.0 或更高版本

### 2. 项目配置
1. 克隆项目到本地
   ```bash
   git clone https://github.com/wheeler3884/Cluster-Node-Display-Prototype.git
   ```
2. 进入项目目录
   ```bash
   cd Cluster-Node-Display-Prototype
   ```
3. 安装依赖：
   ```bash
   npm install
   ```

### 3. 启动开发服务器
```bash
npm start
```
服务器将在 http://localhost:3000 启动

### 4. 生产环境部署

#### 4.1 GitHub Pages 部署
1. 确保项目包含 `.nojekyll` 文件
2. 推送到 GitHub 仓库
3. 在 GitHub 仓库设置中启用 GitHub Pages
4. 选择 `main` 分支作为发布源

#### 4.2 服务器部署
- 推荐使用 Nginx 作为反向代理
- 配置 HTTPS 证书
- 配置域名解析

## 功能特性
- 邮件信息概览
- 检测分析
- 邮件详情查看
- 日志查看
- 响应式设计

## 项目结构
- index.html - 邮件详情页面
- delivery-log.html - 邮件投递日志页面
- script.js - 前端脚本
- style.css - 样式文件
- server.js - Node.js 服务器
- package.json - 项目配置

## 联系方式
如有问题，请联系系统管理员。