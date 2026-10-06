# Multimodal RAG (OCR 方向)

> 基于 OCR + VLM 的多模态文档检索 RAG 系统，支持扫描版 PDF、图片文档的智能识别、检索与问答。

[![Python](https://img.shields.io/badge/Python-3.10+-blue)](https://www.python.org/)
[![React](https://img.shields.io/badge/React-18+-61dafb)](https://react.dev/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688)](https://fastapi.tiangolo.com/)
[![MinerU](https://img.shields.io/badge/MinerU-v2+-orange)](https://github.com/opendatalab/MinerU)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## ✨ 特性

- 📸 **OCR 文档解析**：基于 MinerU 的高精度文档解析，支持扫描件、图片
- 🖼️ **多模态理解**：结合 VLM 理解图表、公式、版式
- 🔍 **混合检索**：文本检索 + 图像检索 + 知识图谱
- 💬 **溯源问答**：每个回答都能追溯到原文位置
- 🎨 **现代前端**：React + Vite + TailwindCSS

---

## 🏗️ 技术架构

```
┌──────────────────────────────────────────────────────────┐
│                        Frontend                          │
│                     (React + Vite)                       │
└───────────────┬────────────────────────────┬─────────────┘
                │                            │
        ┌───────▼───────┐           ┌───────▼───────┐
        │   Chat API    │           │ Knowledge API │
        │  (对话服务)   │           │  (知识库服务) │
        └───────┬───────┘           └───────┬───────┘
                │                            │
┌───────────────▼────────────────────────────▼─────────────┐
│                    Backend Services                      │
│  ┌─────────┐ ┌──────────┐ ┌──────────┐ ┌─────────────┐ │
│  │ MinerU  │ │ 文本分段 │ │ 向量检索 │ │ 知识管理    │ │
│  │ (OCR)   │ │          │ │ (Milvus) │ │ (Milvus)    │ │
│  └─────────┘ └──────────┘ └──────────┘ └─────────────┘ │
└──────────────────────────────────────────────────────────┘
```

---

## 📁 项目结构

```
.
├── backend/                    # 后端服务
│   ├── chat/                   # 对话 API
│   ├── knowledge-base-api/     # 知识库 API
│   ├── knowledge-management/   # 知识管理
│   ├── Information-Extraction/ # 信息提取（OCR + VLM）
│   ├── Text_segmentation/      # 文本分段
│   ├── fastapi-document-retrieval/  # 文档检索
│   ├── Database/               # 数据库
│   ├── start_all_services.sh   # 一键启动
│   └── requirements.txt
├── frontend/                   # 前端
│   ├── src/
│   ├── package.json
│   └── vite.config.ts
└── README.md
```

> 💡 **数据/模型文件**：MinerU 模型、Milvus 数据、测试数据等位于 `../data/` 目录（约 7.6GB），不纳入 Git 仓库。

---

## 🚀 快速开始

### 环境要求

- Python 3.10+
- Node.js 18+
- Milvus 向量数据库
- MinerU（OCR 引擎，约 7GB 模型）
- VLM API Key

### 后端启动

```bash
cd backend

# 安装依赖
pip install -r requirements.txt

# 配置环境变量
cp knowledge-base-api/.env.example knowledge-base-api/.env
# 填入 API Key、MinerU 路径等

# 启动所有服务
chmod +x start_all_services.sh
./start_all_services.sh
```

### 前端启动

```bash
cd frontend
npm install
cp .env.example .env
npm run dev
```

访问 http://localhost:5173

---

## 📚 相关课程

- 📖 课程文档：[飞书知识库](https://scnxinvxtnbo.feishu.cn/wiki/SsUBwW4TZiyM72kHMbvc7auQnTe)
- 🎥 视频教程：[课程链接](#)（待补充）

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.
