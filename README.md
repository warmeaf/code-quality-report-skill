# code-quality-report-skill

基于 AI 的代码质量分析报告生成工具，通过三维度质量标准为项目源代码生成可视化质量报告。

## 功能概述

本 Skill 能够：

- 📁 自动扫描项目源代码目录结构
- 🤖 基于 AI 评估每个代码文件的质量得分（0-100）
- 📊 生成单页 HTML 可视化报告
- 💡 支持对低质量代码进行优化建议

## 质量评估标准

评估基于三个核心维度：

| 维度         | 说明                     | 关注点                           |
| ------------ | ------------------------ | -------------------------------- |
| **可理解性** | 代码是写给人看的         | 命名规范、复杂度控制、代码纯净度 |
| **可维护性** | 代码应对变化保持开放     | 开闭原则、DRY原则、依赖管理      |
| **健壮性**   | 代码在恶劣环境下保持正确 | 错误处理、边界情况、Fail Fast    |

详细标准参见：`skills/code-quality-report/reference/code-quality-standard.md`

## 项目结构

```
skills/code-quality-report/
├── SKILL.md                              # Skill 使用说明
├── reference/
│   └── code-quality-standard.md          # 代码质量评估标准
├── script/
│   └── generate-file-structure.js        # 文件结构扫描脚本
└── template/
    └── code-quality-report-template.html # 报告 HTML 模板
```

## 使用方法

当需要为项目生成代码质量报告时，使用此 Skill：

```
生成代码质量报告
分析项目 src 目录的代码质量
生成代码质量报告：{sourceDir}
```

## 生成流程

1. **确定路径** - 指定源码目录（通常为 `src/`）和输出目录（默认 `.cqm/code-quality-report/`）
2. **扫描结构** - 执行 Node.js 脚本生成 `code-quality-report.json`
3. **AI 评估** - 根据质量标准对每个代码文件进行评分
4. **生成报告** - 将评分数据注入 HTML 模板，生成可视化报告
5. **优化建议** - 对低于 90 分的文件提供优化选项

## 输出结果

生成的报告文件：`${outputDir}/code-quality-report.html`

报告包含：

- 项目文件树状结构
- 每个文件的质量得分（颜色标识）
- 质量分布统计
- 低质量文件列表

## 技术栈

- **Node.js** - 文件系统扫描
- **JSON** - 数据结构存储
- **HTML + CSS + JavaScript** - 可视化报告

## 许可证

详见 [LICENSE](./LICENSE) 文件
