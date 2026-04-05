# CrossDesk Web 客户端

[![License: LGPL v3](https://img.shields.io/badge/License-LGPL%20v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0)
[![GitHub Pages Deploy Status](https://img.shields.io/github/deployments/13888285815/workbuddy-crossdesk/github-pages)]()

## 简介

CrossDesk Web 客户端是一个轻量级的跨平台远程桌面 Web 客户端，支持在浏览器中远程控制电脑。

### 功能特点

- 🌐 **跨平台访问** - 支持所有现代浏览器，无需安装任何软件
- 📱 **移动端适配** - 支持手机、平板等移动设备
- ⌨️ **虚拟控制** - 支持虚拟键盘和鼠标
- 🔒 **安全连接** - 使用 WebRTC 端到端加密传输
- 🔄 **自动重连** - 网络不稳定时自动重连
- 📺 **多屏支持** - 支持多显示器切换

## 快速开始

### 方式一：使用官方服务器（推荐）

直接访问 Web 客户端：

**https://13888285815.github.io/workbuddy-crossdesk/**

输入远程设备的 ID 和密码即可连接。

### 方式二：自托管部署

1. Fork 本仓库到你的 GitHub 账号
2. 进入仓库 Settings → Pages
3. 在 Source 中选择 `Deploy from a branch`，Branch 选择 `main`
4. 点击 Save，等待部署完成
5. 访问 `https://你的用户名.github.io/你的仓库名/`

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

## 配置说明

如需连接自建服务器，修改 `web_client.js` 中的配置：

```javascript
const DEFAULT_CONFIG = {
  signalingUrl: "wss://你的服务器地址:9099",
  iceServers: [
    { urls: ["stun:你的服务器地址:3478"] },
    { urls: ["turn:你的服务器地址:3478"], username: "crossdesk", credential: "crossdeskpw" },
  ],
  // ... 其他配置
};
```

## 许可证

[LGPL-3.0](LICENSE)

## 相关项目

- [CrossDesk 桌面客户端](https://github.com/kunkundi/crossdesk) - 跨平台远程桌面软件
- [CrossDesk Server](https://github.com/kunkundi/crossdesk-server) - 自托管服务器部署
