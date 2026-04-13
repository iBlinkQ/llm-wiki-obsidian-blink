# LLM Wiki - 基于 Obsidian 的知识管理系统

一个基于 Andrej Karpathy 的 [LLM Wiki 模式](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) 实现的 Obsidian 知识库，利用 LLM 维护可复利的个人知识层。

## ✨ 核心理念

传统 Wiki 失败的原因是维护成本太高——人类不擅长处理繁琐的交叉引用、一致性检查和内容更新。而 LLM 恰好擅长这些"记账"工作。

本项目将知识管理分为三层：
- **原始资料层**（`raw/`）：不可变的事实来源
- **知识层**（`wiki/`）：LLM 维护的结构化知识网络
- **配置层**（`TheSchema.md`）：定义系统规则和工作流

## 🎯 核心特性

- **持久化知识积累**：Wiki 是可复利的资产，而非每次重新推导
- **自动化维护**：LLM 处理交叉引用、一致性检查、内容更新
- **结构化组织**：按来源、实体、概念、比较、总览分类管理
- **可追溯性**：完整的操作日志和来源引用
- **Obsidian 原生**：充分利用双向链接、标签、图谱等功能

## 📁 目录结构

```
.
├── raw/                    # 原始资料（只读）
│   ├── papers/            # 论文、文章
│   ├── books/             # 书籍摘录
│   └── media/             # 图片、视频等
│
├── wiki/                   # 知识层（LLM 维护）
│   ├── sources/           # 来源摘要页
│   ├── entities/          # 实体页（人物、项目等）
│   ├── concepts/          # 概念页（方法、理论等）
│   ├── comparisons/       # 比较分析页
│   ├── overview/          # 总览综合页
│   ├── index.md           # 内容索引
│   └── log.md             # 操作日志
│
├── Attachments/           # 图片资源
├── TheSchema.md           # 系统配置文档
└── README.md              # 本文档
```

## 🎨 框架总览

![Pasted image 20260410195644.png](Attachments/Pasted%20image%2020260410195644.png)

系统通过三层架构实现知识的持续积累和复利增长。

## 🏗️ Architecture · 三种文件类型

![Pasted image 20260410195715.png](Attachments/Pasted%20image%2020260410195715.png)

- **Raw Sources**：原始资料，不可变的事实来源
- **Wiki Pages**：LLM 生成和维护的结构化知识页面
- **Schema**：系统配置，定义工作流和规则

## 🔄 Operations · 三个日常操作

![Pasted image 20260410195804.png](Attachments/Pasted%20image%2020260410195804.png)

### 1. Ingest（导入）
添加新资料到 `raw/`，LLM 阅读并：
- 创建来源摘要页
- 更新相关实体/概念页
- 维护交叉引用
- 记录到操作日志

### 2. Query（查询）
向 Wiki 提问，LLM：
- 搜索相关页面
- 综合回答并附上引用
- 可选：将有价值的回答写回为新页面

### 3. Lint（检查）
定期审计 Wiki 健康度：
- 发现矛盾和过时内容
- 识别孤立页面
- 建议合并/拆分
- 补充缺失的交叉引用

## 🛠️ 辅助工具

![Pasted image 20260410195828.png](Attachments/Pasted%20image%2020260410195828.png)

- **index.md**：按类别组织的内容目录，帮助 LLM 快速定位
- **log.md**：时间序列的操作记录，追溯知识演化
- **Search**：Obsidian 的全文搜索和标签系统

## 💡 使用建议

![Pasted image 20260410195907.png](Attachments/Pasted%20image%2020260410195907.png)

1. **保持原始资料不变**：`raw/` 目录只添加不修改
2. **让 LLM 处理繁琐工作**：交叉引用、格式统一、一致性检查
3. **定期 Lint**：保持 Wiki 健康，防止知识腐化

## 🚀 快速开始

1. **下载最新版本**
   - 前往 [Releases](../../releases) 页面
   - 下载最新版本的 .zip 文件

2. **解压文件**
   - 将下载的 .zip 文件解压到你的 Obsidian 仓库所在文件夹

3. **在 Obsidian 中打开**
   - 打开 Obsidian
   - 选择"打开文件夹作为仓库"
   - 选择解压后的文件夹

4. **配置 AI Agent**
   - 阅读 [[TheSchema.md]] 了解系统规则
   - 将 Schema 内容提供给你的 AI Agent（Claude Code、OpenClaw、Trae 等）

5. **开始使用**

<a href="https://www.bilibili.com/video/BV1mgQPBXEZp/">
  <img src="https://github.com/user-attachments/assets/f30b7441-310c-400f-b930-2aa081931756" alt="▶️ 查看视频演示" width="400">
</a>

👆 查看视频演示



   ```
   # 导入新资料
   "请基于 raw/xxx.pdf 进行 Ingest"
   
   # 查询知识
   "XXX 和 YYY 有什么区别？"
   
   # 健康检查
   "请对 wiki 做一次 Lint"
   ```

   更多可见视频演示：

## 📖 页面类型说明

| 类型 | 路径 | 用途 |
|------|------|------|
| Source Summary | `wiki/sources/` | 单个来源的摘要和要点 |
| Entity Page | `wiki/entities/` | 人物、书籍、项目等实体 |
| Concept Page | `wiki/concepts/` | 方法、理论、模型等概念 |
| Comparison | `wiki/comparisons/` | 对比分析 |
| Overview | `wiki/overview/` | 主题综述和总览 |

## 🙏 致谢

本项目基于 [Andrej Karpathy](https://github.com/karpathy) 的 [LLM Wiki 模式](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) 实现。

核心思想：
> "The wiki is a persistent, compounding artifact" — 让 LLM 处理人类不擅长的记账工作，让知识真正复利增长。

## 👤 关于作者

**Blink**
- 18 年笔记软件老玩家
- AI + 知识管理实践者
- 10 年互联网产品经理

<img src="Attachments/539.jpg" width="224" alt="539.jpg">

## 📄 许可证

MIT License

---

**相关链接**
- Karpathy 原文：https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- Obsidian：https://obsidian.md
