# Lab Report Generator

面向《高级 Python 程序设计》课程的跨平台实验报告自动生成工具：从 Jupyter Notebook（`.ipynb`）与 `images/` 中的截图生成符合课程排版规范的 Word（`.docx`）报告。

本仓库供 Cursor、Claude Code、Windsurf 等工具使用；**完整操作流程、禁令与版式细则见 [`rules/SKILL.md`](rules/SKILL.md)**（根目录 `.cursorrules` / `.clauderules` / `.windsurfrules` 会引导助手读取该文件）。

## 依赖

- [python-docx](https://python-docx.readthedocs.io/) — 读写 Word  
- [nbformat](https://nbformat.readthedocs.io/) — 解析 `.ipynb`  
- [Pillow](https://python-pillow.org/) — 图像处理  

安装（任选镜像）：

```bash
pip install -r requirements.txt
# 或使用清华镜像：pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
```

> **说明：** 按 `rules/SKILL.md` 由 AI 自动执行生成任务时，应使用**当前终端已有环境**并直接运行 `python generate_report.py`，**不要**在自动化流程中新建虚拟环境（本地开发若自行使用 `venv` 仍可忽略提交，见 `.gitignore`）。

## 目录约定

| 目录 | 用途 |
|------|------|
| `inputs/` | 用户 `.ipynb` |
| `images/` | 截图（命名可杂乱，由 AI 按内容匹配题目） |
| `template/` | 带目录与占位符的 `template.docx`（勿覆盖源文件；脚本应 `Document(...)` 后另存到 `output/`） |
| `output/` | 生成的报告（如 `学号_姓名_实验报告.docx`） |
| `rules/` | 核心 SOP：`SKILL.md` |

## 用户输入
运行 lab report generator 技能。基于 template 里的模板生成报告。我的信息是：姓名：xxx，学号：xxx，学院：xx学院，专业：xxx，日期：2026-xx-xx。标题为：xxxxx。请开始工作。

## 生成物

由助手根据 `rules/SKILL.md` 在工作区生成并执行 `generate_report.py`。生成后请在 Word 中打开报告，**右键目录 →「更新域」→「更新整个目录」** 以刷新页码与目录。
