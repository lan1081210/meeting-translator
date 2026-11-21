# 实时会议翻译（Live Meeting Translator）

[English](README.en.md)

网页版实时会议翻译工具：麦克风收音 → 语音识别（俄语 / 英语）→ DeepSeek 流式翻译成简体中文，原文与译文分栏对照，支持语音播报与纪要导出。纯静态 HTML，无后端。

## 功能

- 实时收音转写：浏览器语音识别，支持俄语（ru-RU）、英语（en-US），以及自动识别（按文字自适应切换）
- 流式翻译：DeepSeek API（deepseek-chat / deepseek-reasoner），译文逐字上屏
- 展示模式：双栏对照 / 单栏对照 / 仅原文 / 仅译文，字号可调，支持全屏（投影友好）
- 语音播报：译文中文朗读（浏览器 TTS）
- 术语表与会议背景：自定义名词对齐与领域语境，提升翻译准确度
- 手动输入：不方便出声时可打字翻译
- 纪要导出：一键导出带时间戳的文本纪要，也可复制全文

## 快速开始

1. 用 Chrome 或 Edge 打开 `index.html`（语音识别需要 https 或 localhost；直接双击本地文件可用，若浏览器限制麦克风，起个本地服务即可）：

   ```bash
   python3 -m http.server 8000
   # 浏览器打开 http://localhost:8000
   ```

2. 点右上角「⚙ 设置」，填入 DeepSeek API Key（在 [platform.deepseek.com](https://platform.deepseek.com/) 申请）。
3. 选语言（俄语 / 英语 / 自动），点麦克风开始。发言实时出现在左栏，译文出现在右栏。

API Key 只保存在本机浏览器 localStorage，不经过任何第三方服务器——翻译请求由浏览器直连 DeepSeek API。

## 部署

静态文件，可直接部署 GitHub Pages 或任意静态托管。部署在公网时请自行在设置中填入你的 API Key。

## 浏览器支持

| 能力 | Chrome / Edge | Safari | Firefox |
|---|---|---|---|
| 语音识别 | ✅ | 部分版本 | ❌ |
| 手动输入翻译 | ✅ | ✅ | ✅ |

## 说明

- 语音识别由浏览器内置引擎完成，识别质量取决于浏览器与网络环境。
- 翻译质量取决于 DeepSeek 模型；善用术语表与会议背景配置。

---

©lan, cooperated with artificial intelligence
