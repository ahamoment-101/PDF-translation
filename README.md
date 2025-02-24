# PDF翻译工具 (PDF Translation Tool)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

这是一个强大的PDF文档翻译工具，能够将英文PDF文档翻译成中文，同时保持原始文档的布局、格式和样式。支持表格、列表、图片等复杂元素的处理，让翻译后的文档看起来与原文档保持一致。

## 特性

- 🚀 保持原始PDF的布局和格式
- 📊 支持表格、列表等复杂元素的翻译
- 🖼️ 保留原文档中的图片
- 🎯 智能识别文档结构
- 🔄 批量处理多个PDF文件
- 🖥️ 支持GPU加速（如果可用）
- 📝 输出为易于编辑的Word格式

## 安装

### 1. 克隆仓库

```bash
git clone https://github.com/yourusername/pdffanyi.git
cd pdffanyi
```

### 2. 安装依赖

```bash
pip install -r requirements.txt
```

### 3. 准备字体文件

本项目使用思源黑体(Source Han Sans)来确保中文显示的美观。

1. 从[Adobe Source Han Sans发布页](https://github.com/adobe-fonts/source-han-sans/releases)下载字体
2. 将字体文件(特别是`SourceHanSansSC-Regular.otf`)放入`fonts/`目录

## 使用方法

### 基本用法

1. 将需要翻译的PDF文件放入`file`目录
2. 运行程序：
   ```bash
   python translate_pdf.py
   ```
3. 翻译后的文件将保存为Word格式（`file/原文件名_translated.docx`）

### 高级配置

在`translate_pdf.py`中，您可以调整以下参数：

- 翻译质量参数（`translate_text`函数）：
  - `max_length`: 控制输出长度
  - `num_beams`: 控制搜索宽度
  - `temperature`: 控制输出多样性
  - `chinese_ratio`: 控制中文比例阈值（默认0.15）

## 工作原理

1. 使用PyMuPDF (fitz)解析PDF文档结构
2. 通过Helsinki-NLP的opus-mt-en-zh模型进行英译中
3. 使用python-docx重建文档布局
4. 智能处理表格、列表和图片等特殊元素

## 贡献指南

欢迎贡献代码！请遵循以下步骤：

1. Fork本仓库
2. 创建您的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交您的更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启一个Pull Request

## 注意事项

1. 首次运行时会自动下载翻译模型（约1GB），需要等待一段时间
2. 确保系统有足够的内存和存储空间
3. 如果有CUDA设备，会自动使用GPU加速翻译
4. 对于大型PDF文件，处理时间可能较长

## 许可证

本项目采用MIT许可证 - 查看[LICENSE](LICENSE)文件了解详情

## 致谢

- [PyMuPDF](https://github.com/pymupdf/PyMuPDF)
- [Hugging Face Transformers](https://github.com/huggingface/transformers)
- [python-docx](https://github.com/python-openxml/python-docx)
- [Source Han Sans](https://github.com/adobe-fonts/source-han-sans)