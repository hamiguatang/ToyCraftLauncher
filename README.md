# ToyCraftLauncher

一个正在开发中的 Minecraft 启动器喵~

## 项目简介

本项目是一个基于 Tauri 2 + Vue 3 + Vite 开发的桌面应用程序喵~

## 技术栈

| 层级 | 技术 |
|------|------|
| 前端 | Vue 3 + TypeScript + Vite |
| 后端 | Rust + Tauri 2 |
| 构建工具 | npm |

## 项目结构

```
ToyCraftLauncher/
├── src/                    # 前端代码 (Vue 3)
│   ├── main.ts            # 前端入口
│   ├── App.vue            # 主组件
│   └── assets/            # 静态资源
├── src-tauri/             # 后端代码 (Rust)
│   ├── src/
│   │   ├── lib.rs         # Tauri 命令定义
│   │   └── main.rs        # 后端入口
│   ├── Cargo.toml         # Rust 依赖配置
│   └── tauri.conf.json    # Tauri 配置
├── package.json           # 前端依赖配置
├── vite.config.ts         # Vite 配置
└── tsconfig.json          # TypeScript 配置
```

## 快速开始

### 前置要求

- Node.js (LTS 版本)
- Rust (最新版)
- npm 或 pnpm

### 安装依赖

```bash
npm install
```

### 开发模式

```bash
# 启动前端开发服务器
npm run dev

# 启动 Tauri 开发模式
npm run tauri dev
```

### 构建发布

```bash
npm run tauri build
```

## 功能规划

- [ ] 启动器主界面
- [ ] 游戏版本管理
- [ ] 登录验证
- [ ] 配置文件管理
- [ ] Mod/整合包管理

## 技术架构

```
+-------------------------------------------------------------+
|                    前端 (Vue 3 + TS)                         |
|  +---------+  +---------+  +---------+  +---------+       |
|  | 版本管理 |  | 账户管理 |  | 启动游戏 |  | Mod管理 |       |
|  +----+----+  +----+----+  +----+----+  +----+----+       |
+-------+-----------+-----------+-----------+----------------+
        |           |           |           |
        +-----------+-----+-----+-----------+
                          |
              +-----------------------+
              |    Tauri 2 Commands    |
              +-----------+-----------+
                          |
+-------------------------------------------------------------+
|                    核心库 (Rust)                            |
|  +---------+  +---------+  +---------+  +---------+       |
|  |VersionMgr|  | AuthMgr |  |Launcher |  |ModMgr   |       |
|  +---------+  +---------+  +---------+  +---------+       |
|  +---------+  +---------+  +---------+                     |
|  |Download |  |Config   |  |FileIO   |                     |
|  +---------+  +---------+  +---------+                     |
+-------------------------------------------------------------+
        +-----------------+-----------------+
        |                 |                 |
        v                 v                 v
    Windows             Linux             Android
```

## 功能模块

| 模块 | 功能 | 关键技术 |
|------|------|----------|
| 版本管理 | 获取版本列表、下载版本、安装、删除 | Mojang API + BMCLAPI |
| 账户系统 | 正版登录、外置登录(Yggdrasil)、离线模式 | OAuth2 / 离线模式 |
| 游戏启动 | 构建参数、启动进程、进程监控 | std::process::Command |
| 资源管理 | Mod/整合包搜索、下载、安装 | CurseForge API + Modrinth API |
| 配置管理 | 启动器配置、游戏配置 | JSON 序列化 |

## 开发阶段

### 第一阶段：基础框架搭建
- 配置 Tauri 2 移动端支持 (Android)
- 搭建 Vue 3 前端项目结构
- 实现 Rust 核心库基础架构

### 第二阶段：核心功能
- 版本管理（官方源 + BMCLAPI 双源）
- 账户系统（正版 + 离线 + 外置）
- 游戏启动逻辑
- 基础 UI 界面

### 第三阶段：资源管理
- Mod 下载（CurseForge + Modrinth）
- 整合包支持
- 高级 UI（进度显示、设置面板）

### 第四阶段：三端适配
- Windows 端优化
- Linux 端适配
- Android 端适配

## API 对接

| 服务 | API | 用途 |
|------|-----|------|
| Mojang | launchermeta.mojang.com | 游戏版本元数据 |
| BMCLAPI | bmclapi2.bangbang93.com | 国内镜像源 |
| Yggdrasil | authserver.mojang.com | 三方登录 |
| CurseForge | api.curseforge.com | Mod 下载 |
| Modrinth | api.modrinth.com | Mod 下载 |

## 开发说明

- 前端代码位于 `src/` 目录，使用 Vue 3 编写喵~
- 后端代码位于 `src-tauri/src/` 目录，使用 Rust 编写喵~
- 前端与后端通过 Tauri 的 `invoke` 命令进行通信喵~

## 相关文档

- [Tauri 文档](https://tauri.app/zh-cn/v1/)
- [Vue 3 文档](https://vuejs.org/)
- [Vite 文档](https://vitejs.dev/)

