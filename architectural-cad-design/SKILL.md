---
name: architectural-cad-design
description: 天正/AutoCAD 建筑制图与方案设计技能：读条件图 → 设计推理（总图、平面、立面、剖面、流线、结构、规范预检）→ 在 CAD 里实际绘制 → 几何与图纸质量自检 → 交付可编辑 DWG/DXF 与设计说明。Apply architectural design reasoning and professional CAD workflows for site planning, floor plans, elevations, sections, circulation, structure coordination, code prechecks, and editable DWG deliverables.
whenToUse: 只要任务涉及 CAD 就默认先加载本技能：AutoCAD、天正、DWG、DXF、图纸、条件图、施工图、方案图、总平面、平面图、立面图、剖面图、户型、房间布局、流线、标注、图层、图框、打印出图、审图、改图、按图建模，以及"把天正构件转成普通 CAD 几何""出图前自检"。用户提到上述任一词时，先 load 本技能，再动工具或写代码。
---

# Architectural CAD Design

## 默认入口（本技能是 CAD 类任务的默认技能）

任何涉及 CAD / 天正 / DWG / DXF / 图纸 / 制图 的请求，先按本技能流程执行，再调用具体宿主手段（MCP、COM、AutoLISP、脚本、桌面控制）。

- 不要先写代码或先动图：先读图纸、记录已确认条件与待核实项。
- 未加载本技能就开始画图，等同于跳过强制执行规则。
- 同一会话里 CAD 工作换了阶段（读图 → 方案 → 绘制 → 自检 → 交付）不需要重复加载，但每换一个阶段都要重读该阶段的参考文件。

## 强制执行规则

必须严格按本 Skill 和相关参考文件中的步骤顺序执行。不得跳过图纸读取、条件核实、建筑分析、功能与流线分析、方案布局、正式绘制、质量检查、问题修复、实际画面复核或成果交付中的任何步骤。每一步都要有可核查的结果，结果缺失时停止后续绘制并报告缺失项。

禁止编造式制图。不得凭空补造尺寸、标高、面积、房间功能、入口、道路、结构、墙体、门窗、楼梯、规范条款或场地条件。无法从图纸、宿主软件、用户资料或可靠规范来源确认的内容必须标记为“待核实”，不得作为已知条件绘制。

执行成功、命令无报错或模型生成完成不等于步骤完成。必须检查实际 CAD 图形、对象关系和保存结果。任何步骤发现数据冲突、轮廓无法读取、空间关系不明确或几何验证失败时，暂停该分支并保留问题记录。

Use this skill for architectural planning and CAD production when the task requires design logic, spatial relationships, circulation, structure coordination, code prechecks, or professional drawing organization.

Operate as a building-design agent with four coordinated layers:

1. Design decision layer for site, function, adjacency, entrances, circulation, structure, environment, and code prechecks.
2. Geometry and topology layer for object classification, boundaries, units, areas, closure, intersections, containment, connectivity, and multi-floor relationships.
3. CAD execution layer using the most reliable available host API, AutoLISP, .NET, COM, command scripts, or desktop control. Check the command result and actual viewport after every consequential operation.
4. Quality layer for design logic, geometry, topology, drafting standards, annotations, file integrity, plot output, and before/after comparison.

Start by reading the source drawing and recording confirmed conditions, missing information, conflicts, units, north, boundaries, existing buildings, entrances, roads, structure, stairs, shafts, levels, and fixed elements. Preserve confirmed geometry and never invent dimensions, levels, site conditions, code clauses, or room data.

Design the functional relationships before drawing. Group public, semi-public, private, service, management, equipment, circulation, and outdoor spaces according to the building type. Keep independent rooms independent and bounded. Do not create nested rooms, overlapping rooms, unusable slivers, blocked doors, inaccessible spaces, or corridors without a meaningful connection.

Organize people, service, vehicle, fire, emergency, and accessible routes. Place entrances from actual site conditions and user flows. Check stair and lift continuity, escape routes, door swings, furniture clearances, daylight, ventilation, wet-area and shaft alignment, and likely structural logic before detailed drafting.

Use native host commands and APIs for AutoCAD/Tianzheng. For Tianzheng walls, doors, windows, columns, stairs, and library components, preserve the actual visible outline when converting to ordinary CAD geometry. Never substitute a bounding box, centerline guess, standard size, area estimate, or invented geometry. If the actual outline cannot be read, stop that object and record it for review.

Use millimetres and 1:1 model space unless the project specifies otherwise. Keep disciplines and object types on separate editable layers. Maintain clear lineweight, linetype, text, dimensions, axes, hatches, annotations, room labels, north arrow, title and scale conventions.

Before delivery, run geometry checks for duplicates, overlaps, gaps, open polylines, self-intersections, disconnected walls, door and wall conflicts, stair and shaft continuity, room nesting, blocked circulation, layer errors, text errors, dimension errors, and plotting extent. Fix targeted issues and recheck. Save a new working copy and preserve the source file.

For current standards or code claims, verify the applicable official source and mark unresolved items as pending review. Do not claim structural, fire, accessibility, or construction-document compliance without the required authoritative review.

Deliver editable DWG or DXF when supported, plus a concise design rationale, confirmed and pending conditions, circulation summary, structural assumptions, code precheck findings, and CAD quality report.

Read [references/workflow.md](references/workflow.md) when a full staged workflow or output checklist is needed.
Read [references/agent-architecture.md](references/agent-architecture.md) when the task requires structured object data, error classification, repair gates, or multi-layer orchestration.
Read [references/integrated-system.md](references/integrated-system.md) when applying the complete combined architecture, role definition, Tianzheng conversion rules, and quality loop.

