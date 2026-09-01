# 去 AI 味

这个 skill 能识别并去除 20 多种中文写作中的 AI 套话模式，也能帮你检测文章是否有 AI 味。

## 效果展示

以下是编辑草稿前后的 git diff 效果：

![编辑前后对比 — 第一部分](images/skill-diff-01.png)
*红色为 AI 套话原文，绿色为编辑后的版本。可以看到二元对立、废话开头、冒号揭示、伪洞察铺垫等模式被识别并改写。*

![编辑前后对比 — 第二部分](images/skill-diff-02.png)
*继续展示更多模式的修改效果，包括重要性吹捧、表面分析、虚假强动词、格式套话等。*

## 能识别什么

它检测的模式包括：

| 模式 | 典型表现 |
|------|----------|
| 二元对立 | "这不是X，而是Y。" |
| 废话开头 | "说到底……"、"不得不说……" |
| 伪洞察铺垫 | "很多人不知道的是……" |
| 冒号揭示 | "最关键的一点：它能自我学习。" |
| 表面分析 | "……彰显了团队的决心" |
| 重要性吹捧 | "标志着一个里程碑式的时刻" |
| 模糊引用 | "专家表示"、"研究表明" |
| 虚假强动词 | "充当了一个集中管理的枢纽" |
| 同义词轮换 | 先说"智能体"，再说"助手"，又说"工具" |
| 否定列举 | "不是X。不是Y。而是Z。" |
| 戏剧化碎片 | "就这样。就是这么简单。" |

它还会执行让写作变好的基本原则：该亮观点时直接亮观点、用主动语态、理清难懂的句子、用具体数字替代抽象表述。

## 安装

推荐用插件方式装，之后我更新模式和规则，你能自动拿到。在 Claude Code 里执行：

```
/plugin marketplace add shenxianpeng/no-ai-slop-zh
/plugin install no-ai-slop-zh@shenxianpeng-skills
```

也可以手动装：把 `skills/no-ai-slop-zh/` 整个目录复制到 `~/.claude/skills/` 下（只对当前项目生效就复制到项目的 `.claude/skills/`）。手动装的缺点是没法自动更新。

或者在 Claude Code、Codex 或你常用的 AI 工具中粘贴：

"全局安装这个 skill：[https://github.com/shenxianpeng/no-ai-slop-zh](https://github.com/shenxianpeng/no-ai-slop-zh)"

skill 名字是 `no-ai-slop-zh`，和英文原版的 `no-ai-slop` 错开，两个可以同时装。

## 使用

**1. 编辑草稿。** 粘贴草稿并调用 skill：

```
/no-ai-slop-zh

[你的草稿]
```

你会得到编辑后的草稿和一个简短的「改了什么」部分。这个 skill 只做最小有效修改，然后对照 [eval.md](skills/no-ai-slop-zh/eval.md) 自检。

**2. 检测 AI 味。** 让它判断一段文字是否有 AI 味：

```
/no-ai-slop-zh 这是 AI 写的吗？

[待检测文本]
```

你会得到它找到的每个模式以及对应的原文引用。

插件方式装的，显式调用要带插件前缀：`/no-ai-slop-zh:no-ai-slop-zh`。不显式调用也行，写中文草稿时它会自己判断要不要出来。

## 文件

1. `skills/no-ai-slop-zh/SKILL.md`：编辑规则和工作流程。
2. `skills/no-ai-slop-zh/eval.md`：skill 对自身编辑结果的通过/不通过检查清单。
3. `.claude-plugin/`：插件清单和 marketplace 配置，用于插件安装和自动更新。

## 谁做的

[shenxianpeng](https://github.com/shenxianpeng) 维护中文版。

原始英文版来自 [petergyang/no-ai-slop](https://github.com/petergyang/no-ai-slop)，本仓库在它的基础上重写了全部模式和规则，使其适用于中文写作。

## 许可证

MIT
