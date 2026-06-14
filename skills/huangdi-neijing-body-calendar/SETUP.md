# 怎么用 · 三种方式

> 从最简单到最自动化，选适合你的。

---

## 方式1：复制粘贴（零门槛）

适合：想试试看、不想装任何东西的人。

打开 ChatGPT / Claude / 豆包 / Kimi，粘贴这段话：

```
请根据今天的日期和我所在的城市，生成一份「中医身体日历」。

要求：
1. 结合《黄帝内经》四时养生思想、现代运动科学（WHO/ACSM）和本地天气
2. 包含：今日主题、宜忌、作息、饮食、运动、情志、问诊自查、风险提醒、依据
3. 不做诊断、不开药方、不做吉凶判断，只给养生教育建议
4. 建议具体可执行，适合普通人照着做
5. 默认中低强度运动，保守安全

我的情况：[你的年龄、身体状况、所在城市]
```

每天打开对话，改一下日期和身体情况就行。

追加玩法：
- "我在北京，请按北京气候调整"
- "把今天的日历改写成小红书脚本，300字以内"
- "Generate today's body calendar in English"

---

## 方式2：安装到 Agent（自动化）

适合：已安装 Claude Code 或 Codex，想让 Agent 自动每天生成。

### 第1步：安装 Skill

**Claude Code**：
```bash
# 克隆仓库
git clone https://github.com/ShuyangLiu716/huangdi-neijing-body-calendar.git

# 在 Claude Code 中引用 skill
# 把 skills/huangdi-neijing-body-calendar/ 目录作为知识库加载
```

**Codex / ChatGPT**：
```
Use $skill-installer to install ShuyangLiu716/huangdi-neijing-body-calendar from path skills/huangdi-neijing-body-calendar.
```

### 第2步：填写你的信息

编辑 `assets/user-profile.md`：

```yaml
city: 北京          # 你的城市
age: 30             # 你的年龄
health_notes: 肩颈僵硬  # 身体情况，留空则生成通用日历
language: 中文
output_format: full  # full / concise / weibo
```

### 第3步：接你自己的自动化

Skill 安装好后，Agent 会按照 SKILL.md 的工作流运行。你可以：

- **Claude Code**：用 CronCreate / ScheduleWakeup 设置每日定时触发
- **Codex**：接 OpenAI 的 scheduled tasks 或外部 cron
- **自己写脚本**：调用 Agent API，传入 SKILL.md 的 prompt

具体怎么接，取决于你的 Agent 平台和工作流。Skill 本身只负责"输入上下文 → 生成日历"，触发和推送由你来配。

---

## 方式3：Agent + Obsidian（自动化 + 沉淀）

适合：想让日历自动出现在 Obsidian 笔记库里的人。

### 前提

- 已安装 Claude Code
- 已安装 Obsidian
- 已按方式2安装好 Skill

### 设置输出目录

编辑 `assets/user-profile.md`，把 `output_dir` 指向你的 Obsidian vault：

```yaml
output_dir: D:/MyObsidianVault/每日身体日历/
```

### 设置定时任务

在 Claude Code 中设置定时触发，prompt 示例：

```
读取 skills/huangdi-neijing-body-calendar/assets/user-profile.md，
按照 SKILL.md 的工作流生成今天的日历，
写入 output_dir 下的 YYYY-MM-DD.md 文件。
```

每天生成的日历会自动出现在 Obsidian 中，打开就能看。

### 进阶：日历 → 内容素材

在 Obsidian 中积累了一段时间的日历后，可以让 Agent：

- 把一周的日历汇总成公众号周报
- 挑出节气转换日的日历，扩展成深度文章
- 把日历中的"问诊自查"部分提炼成短视频脚本

---

## 输出格式

| 格式 | 内容 | 字数 |
|------|------|------|
| `full` | 完整10模块日历 | ~800字 |
| `concise` | 主题+宜忌+运动+饮食 | ~300字 |
| `weibo` | 小红书/微博短文案 | ~300字 |

---

## 安全边界

所有日历都遵循 `references/safety-boundary.md`：
- 不诊断疾病
- 不开药方
- 不推荐药物或补充剂
- 不做吉凶判断
- 不承诺治疗效果

身体有不舒服，去看医生。
