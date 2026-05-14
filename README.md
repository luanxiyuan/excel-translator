# Excel 日英翻译工具

基于本地 Ollama 大模型的 Excel 日译英翻译工具，支持词库管理、多语言界面。

## 功能特性

- **Excel 解析** — 支持 `.xlsx` / `.xls`，多 Sheet 切换，列多选
- **本地翻译** — 通过 Ollama API 调用本地大模型，数据不出本机
- **两种翻译策略**
  - 智能批量：短文本自动合并批量翻译，长文本逐条翻译
  - 逐格翻译：每个单元格独立翻译
- **词库管理** — 日英术语 CRUD，日文自动查重，编辑锁定日文，JSON 导入导出（含去重）
- **词库注入** — 翻译时将词库术语注入 Prompt，约束 AI 按指定术语翻译
- **i18n 国际化** — 界面支持中文（默认）/ 日本語 / English 实时切换
- **Ollama 设置独立** — 连接地址、模型选择、超时、批量大小持久化保存，无需重复配置
- **格式保持** — 保留原文换行格式，翻译进度实时显示，支持取消

## 快速开始

### 前置条件

- [Ollama](https://ollama.ai) 已安装并运行，至少下载一个模型（推荐 `qwen2.5` 或 `llama3`）
- 现代浏览器（Chrome / Edge / Firefox）

### 运行

```bash
# 克隆仓库
git clone git@github.com:luanxiyuan/excel-translator.git
cd excel-translator

# 启动本地服务
python -m http.server 8765
```

浏览器打开 `http://localhost:8765`

### 使用流程

1. **设置** — 切换到「设置」Tab，填入 Ollama 地址，点击「检测连接」，选择模型后保存
2. **上传** — 在「翻译工作台」上传 Excel 文件
3. **选列** — 勾选需要翻译的列
4. **翻译** — 选择翻译策略，点击「开始翻译」
5. **下载** — 翻译完成后自动下载结果文件

## 技术栈

- **前端**：纯 HTML/CSS/JS，无框架依赖
- **Excel 解析**：[SheetJS](https://sheetjs.com/) (CDN)
- **翻译引擎**：[Ollama](https://ollama.ai) `/api/chat` 接口
- **数据持久化**：localStorage（设置 + 词库）

## 项目结构

```
excel-translator/
├── index.html        # 完整应用（HTML + CSS + JS）
├── dictionary.json   # 词库种子文件
└── README.md
```

## License

MIT
