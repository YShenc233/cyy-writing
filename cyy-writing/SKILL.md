---
name: cyy-writing
description: 微信公众号文章创作工作流。Use when user sends a reference article and requests to create a WeChat Official Account article, or when user explicitly mentions creating WeChat public account content,公众号文章, or WeChat article formatting.
---

# 微信公众号文章创作工作流

小陈哥（Siri小陈哥）的公众号文章创作完整流程。

## 触发条件

用户发送一篇参考文章并要求生成微信公众号文章

## 完整流程（5阶段）

```
1. 风格解构 → 分析参考文（骨架/血肉/气质）
2. 主题重构 → 生成 AB 双版本（用户确认）
3. humanize → 去 AI 痕迹 + 📤发送聊天框预览
4. 纯内联 HTML → 用 sessions_spawn 调用 Gemini 3.1 生成排版
5. 整理输出 → 保存文件夹 + 📤发送位置和复制指南
```

## 关键规则

- **阶段 3 完成后**：必须发送 humanize 后的完整文章到聊天框预览
- **阶段 4 模型调度**：用 `sessions_spawn` 调用 `github-copilot/gemini-3.1-pro-preview`，**子代理用 Gemini，主代理保持当前模型，无需切换**
- **阶段 5 完成后**：必须发送最终标题、HTML 保存位置、复制指南

## 文件夹结构

```
公众号文章/
└── YYYY-MM-DD_主题关键词/
    ├── markdown/
    │   ├── 01-原始草稿.md
    │   ├── 02-humanize版.md
    │   └── 03-最终版.md
    ├── html/
    │   └── 最终排版版.html
    └── README.md（可选）
```

## HTML 要求

- 必须**纯内联样式**（微信会过滤 class 和外部 CSS）
- 禁止使用 `<style>` 标签
- 禁止使用 Tailwind CSS 等类名

## 复制指南

浏览器打开 HTML 文件 → Ctrl+A 全选 → 粘贴到公众号编辑器

## 详细步骤

### 阶段 1：风格解构

分析参考文章的：
- **骨架**：结构、段落分布、标题层级
- **血肉**：语言风格、用词特点、案例类型
- **气质**：整体调性、情感色彩、目标受众

### 阶段 2：主题重构

生成 AB 两个版本供用户选择：
- A 版：偏保守，贴近参考文风格
- B 版：偏创新，加入新角度

### 阶段 3：Humanize

使用 humanize 技巧去除 AI 痕迹：
- 加入口语化表达
- 调整句式长短变化
- 添加个人观点或情感
- 使用更自然的过渡词

完成后发送完整文章到聊天框预览。

### 阶段 4：HTML 排版

调用子代理生成纯内联样式 HTML：

```
sessions_spawn:
  - runtime: acp
  - agentId: gemini
  - model: github-copilot/gemini-3.1-pro-preview
  - task: 将以下 markdown 转换为微信公众号可用的纯内联 HTML...
```

### 阶段 5：整理输出

1. 保存所有文件到对应文件夹
2. 发送给用户：
   - 最终标题
   - HTML 文件位置
   - 复制指南

## 参考文件

- 详细 workflow 示例：见 [references/workflow-examples.md](references/workflow-examples.md)
- HTML 模板：见 [assets/wechat-template.html](assets/wechat-template.html)
