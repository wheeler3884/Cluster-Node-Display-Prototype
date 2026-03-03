<<<<<<< HEAD
# Cluster-Node-Display-Prototype
=======
# CACTER邮件安全网关系统部署指南

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
2. 进入项目目录
3. 安装依赖：
   ```bash
   npm install
   ```

### 3. 启动开发服务器
```bash
npm start
```
服务器将在 http://localhost:3001 启动

### 4. 生产环境部署

#### 4.1 构建优化
项目已经包含基本的静态文件，无需额外构建步骤。

#### 4.2 服务器配置
- 推荐使用 Nginx 作为反向代理
- 配置 HTTPS 证书
- 配置域名解析

#### 4.3 Nginx 配置示例
```nginx
server {
    listen 80;
    server_name your-domain.com;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name your-domain.com;
    
    ssl_certificate /path/to/your/certificate.crt;
    ssl_certificate_key /path/to/your/private.key;
    
    location / {
        proxy_pass http://localhost:3001;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

### 5. CI/CD 集成

#### 5.1 GitHub Actions 配置
创建 `.github/workflows/deploy.yml` 文件：

```yaml
name: Deploy

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Use Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '14.x'
    - run: npm install
    - run: npm test
    
  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Deploy to server
      uses: easingthemes/ssh-deploy@v2
      with:
        SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
        REMOTE_HOST: ${{ secrets.REMOTE_HOST }}
        REMOTE_USER: ${{ secrets.REMOTE_USER }}
        TARGET: ${{ secrets.REMOTE_TARGET }}
        SCRIPT_AFTER: |
          cd ${{ secrets.REMOTE_TARGET }}
          npm install
          pm2 restart server.js
```

### 6. 性能优化

#### 6.1 静态资源优化
- 使用 CDN 加速静态资源
- 启用浏览器缓存
- 压缩 CSS 和 JavaScript 文件

#### 6.2 服务器优化
- 使用 PM2 管理进程
- 配置适当的内存限制
- 启用 Gzip 压缩

### 7. 功能验证

#### 7.1 测试步骤
1. 访问应用首页，确认页面加载正常
2. 测试导航菜单功能
3. 测试各个模块的显示和交互
4. 验证响应式设计在不同设备上的表现

#### 7.2 性能测试
- 使用 Lighthouse 进行性能评估
- 测试页面加载速度
- 验证资源加载优化效果

### 8. 故障排查

#### 8.1 常见问题
- 端口占用：修改 server.js 中的 PORT 配置
- 依赖缺失：运行 npm install 安装依赖
- 静态资源加载失败：检查文件路径和权限

#### 8.2 日志查看
- 服务器日志：查看终端输出
- 浏览器控制台：检查 JavaScript 错误

## 维护指南

### 定期更新
- 定期更新依赖包
- 监控服务器性能
- 备份配置文件

### 安全措施
- 定期更新 SSL 证书
- 限制服务器访问权限
- 监控异常访问

## 联系方式
如有问题，请联系系统管理员。
>>>>>>> master
