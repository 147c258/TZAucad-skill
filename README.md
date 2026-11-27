# TZAucad skill

建筑与设计方向的 Agent 技能合集（天正 CAD 制图 + PPT 成稿）。每个技能一个目录，目录名即技能名，`SKILL.md` 在目录根部。

## 技能清单

| 技能 | 说明 |
|---|---|
| [`architectural-cad-design/`](architectural-cad-design/SKILL.md) | 天正 CAD / AutoCAD 建筑制图工作流：顺序化制图、不臆造图元、成图交付。 |
| [`ppt-master/`](ppt-master/SKILL.md) | 把文档、网页、图片或一句话主题做成**可编辑的原生 PPTX**：原生形状/图表/表格、转场与动画、按讲稿生成旁白、填充自带模板、美化既有 PPT。支持品牌/风格/版式/成品四类工作区。上游：[hugohe3/ppt-master](https://github.com/hugohe3/ppt-master)（MIT，v6.9.0）。 |

## 使用方式

### DeepSeek Harness（DSH）

把需要的技能目录整个复制到用户技能目录，重启会话后自动出现在技能列表里：

```powershell
Copy-Item -Recurse -Force .\ppt-master "$env:USERPROFILE\.dsh\skills\ppt-master"
```

### 其他 Agent（Codex / Claude Code 等）

直接把技能目录当作工作目录内的技能包使用，或按各自约定软链到技能搜索路径；`SKILL.md` 是唯一入口，正文里的路径都相对于技能目录自身。

## ppt-master 运行依赖

```powershell
python -m pip install -r ppt-master/requirements.txt
```

核心只需要 `python-pptx`、`XlsxWriter`、`skia-pathops`、`uharfbuzz`、`PyYAML`；PDF/docx/epub 转换、AI 配图、TTS 旁白等属于可选后端，按 `ppt-master/.env.example` 配置。
Windows 上把文档里的 `python3` 一律换成 `python`（`python3` 是 WindowsApps 存根，会以 9009 静默退出）。

## 目录结构

```
architectural-cad-design/   # 天正 CAD 制图技能
ppt-master/                 # 生成/美化 PPTX 技能
  SKILL.md                  # 入口
  workflows/                # 路由与分阶段流程
  references/               # 设计规范、版面、图示参考
  scripts/                  # SVG→PPTX、项目脚手架、质量检查等流水线
  templates/                # 版式/图表/品牌/音效等资源
```

## 许可

各技能保留其上游许可：`architectural-cad-design` 见仓库 `LICENSE`；`ppt-master` 为 MIT，见 `ppt-master/LICENSE` 与 `ppt-master/SPONSORS*.md`。