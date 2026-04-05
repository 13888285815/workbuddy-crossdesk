# CrossDesk Web 客户端

[![License: LGPL v3](https://img.shields.io/badge/License-LGPL%20v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0)

## 简介

CrossDesk Web 客户端是一个轻量级的跨平台远程桌面 Web 客户端，支持在浏览器中远程控制电脑。

### 功能特点

- 🌐 **跨平台访问** - 支持所有现代浏览器，无需安装任何软件
- 📱 **移动端适配** - 支持手机、平板等移动设备
- ⌨️ **虚拟控制** - 支持虚拟键盘和鼠标
- 🔒 **安全连接** - 使用 WebRTC 端到端加密传输
- 🔄 **自动重连** - 网络不稳定时自动重连
- 📺 **多屏支持** - 支持多显示器切换

## 部署说明

### 第一步：部署 CrossDesk Server

在使用 Web 客户端之前，您需要先部署 CrossDesk Server。请参考：
- [CrossDesk Server 部署指南](https://github.com/kunkundi/crossdesk-server)

### 第二步：修改配置

部署服务器后，修改 `web_client.js` 中的服务器地址：

```javascript
// 将 YOUR_SERVER 替换为您的服务器 IP 或域名
const DEFAULT_CONFIG = {
  signalingUrl: "wss://YOUR_SERVER:9099",
  iceServers: [
    { urls: ["stun:YOUR_SERVER:3478"] },
    { urls: ["turn:YOUR_SERVER:3478"], username: "crossdesk", credential: "crossdeskpw" },
  ],
  // ... 其他配置
};
```

### 第三步：部署 Web 客户端

#### 方式一：GitHub Pages（推荐）

1. Fork 本仓库
2. 进入仓库 Settings → Pages
3. 在 Source 中选择 `Deploy from a branch`，Branch 选择 `main`
4. 点击 Save，等待部署完成
5. 访问 `https://你的用户名.github.io/你的仓库名/`

#### 方式二：自建服务器

将所有文件部署到任何静态文件服务器（如 Nginx、Apache）即可。

## 使用说明

### 连接远程设备

1. 打开 Web 客户端页面
2. 在"远程设备 ID"输入框中输入对方设备的 ID
3. 如果对方设置了密码，输入密码
4. 点击"连接"按钮

### 连接状态说明

| 状态 | 说明 |
|------|------|
| 🟢 已连接 | 与服务器的连接正常 |
| 🟡 连接中 | 正在建立连接 |
| 🔴 断开连接 | 连接已断开，尝试重连 |

### 移动端操作

- **精准模式**：直接点击屏幕对应位置
- **增量模式**：通过方向按钮移动鼠标
- **虚拟键盘**：点击键盘图标打开虚拟键盘

## 技术架构

| 组件 | 技术 |
|------|------|
| 前端框架 | 原生 HTML/CSS/JavaScript |
| 实时通信 | WebRTC |
| 信令服务 | WebSocket |
| NAT穿透 | STUN/TURN |

## 许可证

[LGPL-3.0](LICENSE)

## 相关项目

- [CrossDesk 桌面客户端](https://github.com/kunkundi/crossdesk) - 跨平台远程桌面软件
- [CrossDesk Server](https://github.com/kunkundi/crossdesk-server) - 自托管服务器部署
