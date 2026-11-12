#  DeepSeek Harness 下载与使用指南

## DeepSeek Harness 是什么？

**DeepSeek Harness**（命令行工具：`dsh`）是 DeepSeek 官方推出的 AI Agent 开发框架：把大模型装进一个工作台，让 AI 能直接**读写文件、执行命令、拆分任务**，而不只是聊天。基于 MIT 协议完全开源，目前为开发者预览版。

- GitHub：https://github.com/deepseek-ai/deepseek-harness
- 官方文档：https://api-docs.deepseek.com

<br>

## 一、下载安装（二选一）

### 方式 A：桌面版 —— 推荐新手

> ✅ 无需命令行 ✅ 无需 Node.js ✅ 5 分钟装好

**下载地址**：https://www.deepseekharness.online/download.html

1. 打开下载页，选择系统对应安装包：
   - Windows 10/11（64位）→ **EXE 安装包**
   - macOS 12+（M芯片）→ **DMG 安装包**
2. 双击安装包，按提示完成安装
3. 打开软件，进入下方「使用方法」

> 💡 Windows 首次打开若被 SmartScreen 拦截：点 **更多信息 → 仍要运行**

### 方式 B：网页版 —— 适合开发者

> ✅ 更新最快 ✅ 可进阶插件开发 ⚠️ 需先安装 Node.js



**前置条件**：Node.js `^20.19` 或 `>=22`（官网下载：https://nodejs.org）

1. 验证环境，输出版本号即成功：

```bash
node -v
```

2. 在终端执行一条命令启动：

```bash
npx @deepseek-ai/dsh web
```

3. 启动成功后，终端会打印访问地址，用浏览器打开即可：

```text
http://127.0.0.1:3080
```

> 💡 首次运行需下载，等待 1~2 分钟；长时间卡住先切换国内镜像，再重试：

```bash
npm config set registry https://registry.npmmirror.com
npx @deepseek-ai/dsh web
```

### 怎么选？

| | 桌面版 | 网页版 |
|---|:---:|:---:|
| 安装难度 | ★☆☆ | ★★☆ |
| 需要命令行 | ✕ | ✓ |
| 版本更新 | 稍慢 | 最快 |
| 适合 | **新手、普通用户** | **开发者** |

<br>

## 二、使用方法（两个版本通用）

### 第 1 步：申请 API Key

1. 打开 **https://platform.deepseek.com** → 注册登录
2. 左侧菜单 **API Keys** → **创建**
3. 立即复制保存（只显示一次）

### 第 2 步：配置模型

打开 **Settings → Models → DeepSeek**，粘贴 API Key，保存。

> 保存后立即生效，无需重启。

### 第 3 步：选择工作区

1. 点击 **Select workspace**
2. 添加你的项目文件夹，并**点击选中它**

> ⚠️ 易错点：文件夹只「添加」没「点选」，输入框会是灰色的。**输入框能打字 = 配置成功。**

### 第 4 步：开始使用

直接在输入框下达任务，例如让 AI 列出项目文件、修改代码、运行命令。

**验证示例**：新建空文件夹 `dsh-test` 并选中，发送——

```text
使用工具报告当前工作区的完整路径，并列出其中的文件。
不要创建、编辑或删除任何文件。
```

回复的路径、文件列表与磁盘一致，即环境正常 ✅

<br>

## 三、常见问题

| 问题 | 解决办法 |
|---|---|
| npx 卡住不动 | 等待 2 分钟，或切国内镜像后重试 |
| `node` 不是内部命令 | 重开终端，不行就重装 Node.js |
| 端口 3080 被占用 | `npx @deepseek-ai/dsh web --port 13080` |
| 输入框灰色不可用 | 工作区只添加了没点选，重新点选 |
| 报错 MISSING_CREDENTIAL | Settings → Models 重新保存 Key |

<br>

## 写在最后

跑通环境只是第一步，Harness 真正有意思的地方还在后面：

- **插件开发**：模型、工具、沙箱、会话全是插件，基于 Cordis 框架可以自己造轮子
- **接入本地模型**：通过 Settings → Models 添加自定义提供商（如 Ollama 的 `http://localhost:11434/v1`），数据不出本机
- **对比同类工具**：和 Claude Code 定位相似，但 Harness 开源免费、不绑定单一模型，值得玩一玩

> 目前还是预览版，版本变动快。如果你在安装或使用中踩了别的坑，欢迎评论区交流，我会持续更新这篇指南。
