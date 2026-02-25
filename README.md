# DeepSeek 思维链对话客户端

本地桌面应用：与 DeepSeek 对话，并展示**思维链流程图**。支持两种模式：
- **DeepSeek API（云端）**：需联网，使用官方 API
- **Ollama 本地**：使用本机已部署的模型，无需 API Key

## 功能

- **双模式**：可切换 DeepSeek 云端 API 或 Ollama 本地模型
- **Ollama 模型选择**：选择「Ollama 本地」后，点击「刷新模型」获取已部署的模型列表，在下拉框中选取或自行输入模型名
- **对话**：在输入框提问，获取回答并显示
- **思维链流程图**：支持思维链的模型（如 deepseek-reasoner、deepseek-r1）会展示横向流程图

## 环境要求

- Python 3.8+
- 使用 DeepSeek API 模式时需联网
- 使用 Ollama 模式时需先安装并运行 [Ollama](https://ollama.com/download)

## 安装

```bash
pip install -r requirements.txt
```

## 模式一：DeepSeek API（云端）

### 如何获取 API Key

1. 打开 [DeepSeek 开放平台](https://platform.deepseek.com/)
2. 登录或注册
3. 进入 [API Keys](https://platform.deepseek.com/api_keys) 页面
4. 创建新 Key，格式通常为 `sk-` 开头
5. 复制 Key 并设置到环境变量（不要使用中文或占位符）

```bash
# Windows CMD（把 sk-xxxx 换成你的真实 Key）
set DEEPSEEK_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxx

# Windows PowerShell
$env:DEEPSEEK_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxx"

# Linux / macOS
export DEEPSEEK_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxx"
```

### 余额

调用 API 会消耗余额，需在 [充值页面](https://platform.deepseek.com/top_up) 为账户充值。

## 模式二：Ollama 本地

### 安装 Ollama

1. 下载并安装 [Ollama](https://ollama.com/download)
2. 启动 Ollama（安装后通常会自动运行，或运行 `ollama serve`）

### 拉取 DeepSeek 模型

```bash
# 推荐：DeepSeek-R1（支持思维链）
ollama pull deepseek-r1

# 其他可选
ollama pull deepseek-v3
ollama pull deepseek-coder
```

### 使用

1. 运行本应用，选择「Ollama 本地」
2. 点击「刷新模型」获取本机已部署的模型列表
3. 在下拉框中选择模型（如 deepseek-r1），或输入模型名（如 `deepseek-r1:8b`）
4. 开始对话

## 运行

```bash
cd /d "你的项目目录"
python deepseek_chat_app.py
```

## 界面说明

- **顶部**：模式切换（DeepSeek API / Ollama 本地）、Ollama 模型选择与刷新
- **思维链流程图**：支持思维链的模型会在此展示横向流程图
- **对话区**：消息记录
- **底部**：输入框 + 发送按钮
