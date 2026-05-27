# Huangdi Neijing Body Calendar

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Skill](https://img.shields.io/badge/Codex%20Skill-ready-2F6B4F.svg)
![Region](https://img.shields.io/badge/Default%20Region-Chengdu%2C%20Sichuan-blue.svg)

一个会看天气、懂《黄帝内经》、又守现代运动科学边界的「每日身体黄历」：每天告诉你在当地气候下该怎么睡、怎么吃、怎么动、哪里要小心。

## Skill 介绍

`huangdi-neijing-body-calendar` 是一个面向 Codex / ChatGPT 技能系统的「中医身体日历」skill。

它把《黄帝内经》的四时养生思想、现代运动科学和本地气候信息结合起来，生成每天可执行的作息、饮食、运动、情志调节和问诊自查建议。它更像一个“身体版日历”：每天提醒你今天适合怎样起居、怎么吃、怎么动、哪些情况需要谨慎，而不是给出玄学吉凶或医疗诊断。

初始版本以 **四川成都** 为默认地区，会考虑四川盆地常见的湿度大、多云雾、少日照、雨热同季等气候特点。用户可以根据自己所在城市替换本地气象依据，把它定制成杭州版、北京版、广州版、海外城市版等地区化身体日历。

> 重要边界：本 skill 只做养生教育和非诊断性自查，不诊断疾病、不开中药方、不推荐针灸/艾灸/拔罐/刮痧操作，不替代医生诊疗。

## What It Generates

| 模块 | 内容 |
| --- | --- |
| 今日主题 | 节气、季节、昼夜节律、本地气候和《黄帝内经》养生思想 |
| 今日宜 / 不宜 | 行为提醒，不做吉凶判断 |
| 作息 | 睡眠、晨间光照、久坐打断、晚间收心 |
| 饮食 | 食物类别、进食节制、饮水和晚餐时间 |
| 运动 | 强度、时长、方式、雨天/湿热/少日照替代方案 |
| 情志 | 简短的情绪调节和呼吸放松建议 |
| 问诊自查 | 非诊断性问题，帮助用户观察睡眠、消化、疼痛、疲劳和压力 |
| 风险提醒 | 红旗症状、运动降级和就医提示 |
| 依据 | 经典来源、官方规范、运动科学、气象资料 |

## Why It Is Different

- **不是玄学黄历**：保留“每日提醒”的趣味，但不输出吉凶、宜嫁娶、开运等内容。
- **不是医疗问诊机器人**：不诊断、不处方、不承诺治疗，始终保持养生教育边界。
- **不是通用健康鸡汤**：把建议放回日期、季节、城市气候和个人状态里。
- **可迁移到任何地区**：成都只是初始版本，你可以替换成自己的城市和官方气象来源。

## Repository Structure

```text
.
├── README.md
├── LICENSE
└── skills/
    └── huangdi-neijing-body-calendar/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── daily-calendar-template.md
            ├── safety-boundary.md
            └── source-policy.md
```

The repo-level `README.md` explains usage for humans. The actual skill lives under `skills/huangdi-neijing-body-calendar/` so the skill folder stays lean.

## Install

Clone the repository, then copy the skill folder into your Codex skills directory:

```powershell
git clone https://github.com/ShuyangLiu716/huangdi-neijing-body-calendar.git
Copy-Item -Recurse .\huangdi-neijing-body-calendar\skills\huangdi-neijing-body-calendar $env:CODEX_HOME\skills\
```

If `CODEX_HOME` is not set, use your local Codex skills directory directly, for example:

```text
D:/AI_OS/codex-home/skills/huangdi-neijing-body-calendar
```

## Usage

In a Codex / ChatGPT environment that supports skills:

```text
Use $huangdi-neijing-body-calendar 给我生成今天的中医身体日历。
```

With personal context:

```text
Use $huangdi-neijing-body-calendar 我最近睡不好，今天在成都怎么安排作息、饮食和运动？
```

With exercise risk:

```text
Use $huangdi-neijing-body-calendar 我今天膝盖疼，还能运动吗？请按养生筛查边界回答。
```

Switch location:

```text
Use $huangdi-neijing-body-calendar 我这周在杭州，请按杭州气候给我今天的身体日历。
```

## Customize Your Region

初始版本默认地点是成都。要改成你的城市，建议做三处修改：

1. 在 `skills/huangdi-neijing-body-calendar/SKILL.md` 中替换默认地点和本地气候描述。
2. 在 `skills/huangdi-neijing-body-calendar/references/daily-calendar-template.md` 中替换 `位置：成都，四川` 和相关气候提示。
3. 在 `skills/huangdi-neijing-body-calendar/references/source-policy.md` 中加入你所在城市的官方气象来源。

地区定制只应改变气候和生活方式建议，例如：

- 日照多或少：调整晨间光照、户外活动窗口。
- 湿热或干燥：调整补水、饮食清淡程度、运动出汗提醒。
- 高寒或炎热：调整户外运动时段、强度和室内替代。
- 雨季或雾霾：调整室内活动、通风和天气核对提醒。

不要因为地区习俗加入未经证实的治疗、偏方、药方或疾病判断。

## Evidence Model

本 skill 要求每次完整日历都包含「依据」：

- 《黄帝内经》：用于四时养生、起居有常、情志调摄等思想框架。
- 国家中医药管理局《中医养生保健服务规范（试行）》：用于限定养生服务边界。
- WHO 身体活动与久坐行为指南、ACSM 运动筛查/处方思路：用于运动强度、时长、久坐打断和风险筛查。
- 中国气象局、四川省政府、中国天气网、中央气象台：用于成都本地气候和实时天气核对。

## What This Skill Will Not Do

- 不根据症状下疾病诊断。
- 不开中药方、药膳方或治疗方案。
- 不指导针灸、艾灸、拔罐、刮痧等操作。
- 不承诺治疗、预防或治愈疾病。
- 不输出黄历式吉凶、迷信化判断。

## Example Output Shape

```markdown
# 中医身体日历｜2026-05-27

位置：成都，四川

## 今日主题
小满之后、芒种之前，成都湿热渐起，今日以清淡有节、微动微汗、晚间收心为主。

## 今日宜
- 上午见自然光。
- 饭后慢走 10-20 分钟。
- 晚间减少屏幕刺激。

## 今日不宜
- 不宜熬夜后再高强度运动。
- 不宜空腹训练。
- 不宜贪凉猛喝冰饮。

...

## 依据
- 《黄帝内经》四时养生思想。
- 国家中医药管理局养生保健服务规范。
- WHO/ACSM 身体活动和运动筛查建议。
- 成都本地气候参考：中国气象局/四川省政府资料。
```

## License

MIT License. See `LICENSE`.
