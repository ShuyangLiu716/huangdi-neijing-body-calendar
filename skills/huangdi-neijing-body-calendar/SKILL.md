---
name: huangdi-neijing-body-calendar
description: Use this skill when creating a Chinese "中医身体日历" daily wellness guide, Huangdi Neijing inspired lifestyle guidance, Chengdu/Sichuan climate-aware seasonal TCM self-check prompts, or conservative non-diagnostic wellness screening that combines classical Chinese medicine sources with modern physical activity guidance.
---

# Huangdi Neijing Body Calendar

Use this skill to create a daily "中医身体日历": conservative lifestyle guidance inspired by the Huangdi Neijing, grounded in traceable sources, and cross-checked against modern physical activity guidance.

This skill is for wellness education and self-checking only. It must not diagnose disease, prescribe herbs, replace clinicians, or claim treatment effects.

## Core Defaults

- Write in Chinese unless the user asks otherwise.
- Assume a general adult audience in Chengdu, Sichuan unless the user gives another location.
- For Chengdu defaults, account for Sichuan Basin climate: humid, cloudy/foggy, relatively low sunshine, low wind, rainy-season heat and dampness, and indoor/outdoor activity constraints.
- Ask or infer a different location only when the user explicitly says they are outside Chengdu or travel today.
- Assume a general adult audience unless the user provides age, pregnancy status, medical conditions, pain, sleep problems, medications, or exercise history.
- Treat "黄历" as a metaphor for daily rhythm, not fortune telling. Do not produce auspicious/inauspicious claims.
- Prefer conservative advice: regular sleep, moderate meals, daylight exposure, walking, mobility, breathing, and reduced sedentary time.
- Every substantive daily guide must include an "依据" section with source categories.
- If medical risk appears, reduce intensity, avoid specific therapeutic claims, and recommend professional evaluation.

## Workflow

1. **Identify the calendar context**
   - Use the user's stated date and location if provided.
   - If no location is provided, default to Chengdu, Sichuan.
   - If no date is provided, use today's date from the environment.
   - If precise solar term data is unavailable, say "节气需按当地历法核对" and use season-level guidance.
   - For exact weather, air quality, rainfall, temperature, or humidity, use current official weather data when available; otherwise label the local climate guidance as climate-level rather than live weather.

2. **Screen for safety**
   - Check whether the user mentions pain, chest symptoms, fainting, fever, acute injury, pregnancy, chronic disease, recent surgery, or medication changes.
   - Read `references/safety-boundary.md` before answering medical-risk or pain-related prompts.
   - Ask only the minimum necessary follow-up if a red flag would change whether movement is appropriate.

3. **Select the evidence layer**
   - Read `references/source-policy.md` when adding or checking citations.
   - Use Huangdi Neijing concepts for rhythm, season, moderation, emotion, and daily conduct.
   - Use official TCM wellness service rules for scope boundaries.
   - Use WHO and ACSM-style exercise guidance for intensity, duration, sedentary breaks, and risk screening.
   - Use official meteorological sources for Chengdu climate context before making location-specific claims.

4. **Generate the daily guide**
   - Follow `references/daily-calendar-template.md` for structure.
   - Include: 今日主题, 今日宜, 今日不宜, 作息, 饮食, 运动, 情志, 问诊自查, 风险提醒, 依据.
   - Keep recommendations specific enough to act on but not clinical enough to become diagnosis or prescription.

5. **Adapt to personal context**
   - For Chengdu humid or rainy days: reduce heat-stress exposure, keep movement ventilated and moderate, emphasize drying clothes/shoes, warm regular meals, and indoor walking/mobility alternatives.
   - For Chengdu low-sunlight or cloudy days: encourage morning outdoor light exposure when weather allows, while avoiding claims that light exposure treats disease.
   - For sleep complaints: emphasize light exposure, caffeine/alcohol timing, wind-down routine, gentle movement, and referral if severe or persistent.
   - For pain: avoid high-impact or painful movement, suggest gentle range-of-motion or walking only if tolerated, and include red-flag guidance.
   - For sedentary users: start with low volume and frequent breaks.
   - For trained users: keep moderate daily guidance unless the user asks for a training plan.

## Output Rules

- Do not provide disease names as conclusions from symptoms.
- Do not prescribe herbs, formulas, acupuncture points, moxibustion operations, cupping, scraping, or medical devices.
- Do not claim that a food, exercise, or routine treats or prevents a disease.
- Do not use mystical certainty, fortune telling, or "吉凶" language.
- Use clear uncertainty: "可作为养生参考", "如有明显不适应就医", "不能替代医生诊疗".

## References

- Read `references/source-policy.md` for accepted source tiers and citation wording.
- Read `references/daily-calendar-template.md` for the standard daily calendar format.
- Read `references/safety-boundary.md` before handling symptoms, pain, chronic disease, pregnancy, older adults, children, or exercise-risk prompts.

## Regional Customization

The initial version is tuned for Chengdu, Sichuan. To adapt it for another region:

- Replace the default location in this file and `references/daily-calendar-template.md`.
- Add official meteorological sources for the target city to `references/source-policy.md`.
- Translate local climate traits into behavior-level guidance: sleep/light exposure, meal timing, hydration, indoor/outdoor exercise alternatives, heat/cold/rain precautions.
- Keep the same safety boundary. Regional customization must not add diagnosis, prescriptions, treatment claims, or folk remedies without authoritative support.

## Quality Bar

A successful answer is structured, actionable, sourced, conservative, and visibly non-diagnostic. It should help the user decide how to arrange today, not decide what disease they have or what treatment they need.
