# RTM Objective Manager

An advanced Remember The Milk script acting as your Agile coach. It simulates schedules, generates workload heatmaps, and offers smart task-pruning or overtime advice when overloaded, helping you conquer burnout with deep reports.

---
## 📦 脚本列表 (Script Catalog)

| 脚本名称 | 简介 | 版本 | 文档 |
| :--- | :--- | :---: | :---: |
| [RTM Agile Coach](./scripts/rtm-agile-coach/script.js) | 个人敏捷教练，生成工作负载热力图与报告 | v1.2 | [📖 详情](./scripts/rtm-agile-coach/README.md) |
| [RTM Task Starter](./scripts/rtm-task-starter/script.js) | 任务启动与重置计时器，智能处理重复任务 | v1.0 | [📖 详情](./scripts/rtm-task-starter/README.md) |

# 🎯 RTM Agile Coach

An advanced [Remember The Milk (RTM)](https://www.rememberthemilk.com/) automation script powered by MilkScript, acting as your personal Agile Coach. It simulates schedules, generates workload heatmaps, and offers smart task-pruning or overtime advice when overloaded, helping you conquer burnout with deep reports.

## ✨ Features

- **⏱️ Precision Scheduling Engine**: Simulates task execution with millisecond precision, strictly adhering to your configured working hours, weekends, and holidays.
- **🌡️ Workload Heatmaps**: Visually displays your daily capacity and load, making it easy to spot bottlenecks and idle times at a glance.
- **🧠 Adaptive Efficiency Tracking**: Automatically calculates your real-world "Work Ratio" by analyzing 7/30/180 days of historical data, complete with circuit breakers for vacations or data anomalies.
- **✂️ Smart Triage & Pruning**: When your schedule overflows, it uses a weighted scoring model (Objective Priority + Task Priority + Urgency) to recommend exactly which tasks to drop, delay, or move to an empty slot.
- **🔋 Fatigue-Aware Overtime Advice**: Calculates realistic overtime needs using an "Efficiency Factor" (e.g., 0.8), warning you of hidden cognitive costs and late-night hard stops.
- **📊 Multi-layered Reporting**: Generates beautiful, structured notes in RTM (HUD, Action Plan, Deep Diagnosis, and Details) and logs historical metrics for long-term review.

## 🚀 Installation & Setup

1. **Prerequisites**: You must have a **Remember The Milk Pro** account to use MilkScript.
2. **Add Script**: 
   - Go to your RTM Web App -> Settings -> MilkScript.
   - Create a new script, copy and paste the entire source code into the editor.
3. **Configure Parameters**: Set up the UI parameters (`rtm.args`) to match the script's input requirements (e.g., `a.💥 快捷：生成【今日】报告？`, `e.📆 (可选) 指定基准截止日期`).

## ⚙️ Configuration

Before running, customize the `CONFIG` object at the top of the script to fit your lifestyle:

```javascript
const CONFIG = {
    // Define your typical workday
    WORKDAY_CONFIG: {
        startHour: 9,      // 9:00 AM
        endHour: 18,       // 6:00 PM
        workingDays: [1, 2, 3, 4, 5], // Mon to Fri
        holidays: [],      // Add 'YYYY-MM-DD' for specific holidays
    },
    ...
};

const OVERTIME_CONFIG = {
    EFFICIENCY_FACTOR: 0.8, // 1 hour of overtime ≈ 0.8 hours of output
    LATE_THRESHOLD: 21      // Stop suggesting overtime after 9:00 PM
};
```

*Note: The script heavily relies on specific tag structures (e.g., `1.1-🔭` for objectives, `0_` and `99_` prefixes for goal linking). Please ensure your RTM tagging system aligns with the `CONFIG.TAGS` definitions.*

## 📖 How to Use

Run the script from the RTM web interface or mobile app. The script respects priority inputs:
1. **Shortcuts**: Instantly generate reports for "Today", "Tomorrow", "This Week", or "This Month" via checkbox toggles.
2. **Manual Dates**: Select a specific Due Date baseline.
3. **Smart Lists**: The script automatically creates or updates Smart Lists (e.g., `✨-本周-🎯🔍`) pinned to your favorites for easy navigation.

Read the generated Task Notes starting with `📊-System-Log` or your period names to get actionable advice!

## 📄 License
This project is open-source and available under the [MIT License](LICENSE).

---

# 🧪 Sample Copy
```Sample Copy
🚀 ** 行动指南(Action Plan) ** 
------------------------------------------------------------
⚠️【高压预警】需加班 (预测拥挤度 117%)

🤔👉 **系统研判**: 暂未逾期，但总负荷已超标。
   💪 **加班挽救方案**: 剩余 4 天，每晚需加班 **1.3h** (预计至 20:19)。
      *(注: 建议展示的加班时间是“最优情况”（Best Case）：如果你白天尽力了，晚上还要补多少。)*
      *(注: 已按 80% 疲劳效率计算，额外付出 64m 疲劳折损成本)*
--------------------------------------------------
   ✂️ **减负建议**：为避免过度疲劳，建议削减约 **1.6h** 预估量（参考以下清单）。
💡 **智能削减建议 (可腾出 2.5h)**:
*(冲刺模式 (Sprint)模型: 30%目标 + 45%时间 + 25%任务)*
---------------------------------------------
    ✂️ 🔄移至 2026-06-10(周三) [P2 ⤷ 无] 
     1.4-⛳-1.**步骤-5 ⤷ 4.发放*** (0m) 
     ⏰82% | 2026-06-13 00:00:00 星期六
---------------------------------------------
    ✂️ 🔄移至 2026-06-10(周三) [P2 ⤷ 无] 
     1.10-🎉-5.进入**“备战状态”（硬核突击） ⤷ 第三阶段：反向** -1.00🍅 (30m) 
     ⏰54% | 2026-06-12 00:00:00 星期五
---------------------------------------------
    ✂️ 🔄移至 2026-06-10(周三) [P2 ⤷ P3] 
     1.10-🎉-5.进入**“备战状态”（硬核突击） ⤷ 1.4、实践【***】-2.00🍅 (60m) 
     ⏰54% | 2026-06-12 00:00:00 星期五

------------------------------------------------------------
📊 ** 核心指标速览 **: 
• 排期拥挤度: 117.1% 
• 预测总耗时: 29.0 h(🔒0.5h) | 可用 24.8 h
  * (注: 预测耗时 = 任务加权工时 + 日程📅)*

🧠 ** 深度诊断(Deep Diagnosis) ** 
------------------------------------------------------------
📅 **实时战略排期推演 (Schedule)**
   • 预计完工: 2026-06-06 10:06:15 星期六
   *（注：排期表展示的预计完工是“最坏情况”（Worst Case）：如果你白天完全没时间做这个任务，晚上要搞到几点。）*
   🟢 [06-02(二) 10:29 - 10:39] 检查****回复-0.33🍅 (10m)
   🟢 [06-02(二) 10:39 - 11:39] 查询****材料？-1.00🍅 (30m)
   🟢 [06-02(二) 11:39 - 13:40] 2.2.5-如何****-2.00🍅 (60m)
   🟢 [06-02(二) 13:40 - 15:40] 3-2-1-在****更新****-2.00🍅 (60m)
   🟢 [06-03(三) 09:00 - 09:05] 3.****验证-0.17🍅 (5m)
   🟢 [06-03(三) 09:05 - 09:35] 弄清楚****是什么-1.00🍅 (30m)
   🟢 [06-03(三) 09:35 - 09:40] 3.****验证-0.17🍅 (5m)
   🟢 [06-03(三) 09:40 - 11:40] 准备****材料-2.00🍅 (60m)
   🟢 [06-04(四) 09:00 - 09:05] 3.****验证-0.17🍅 (5m)
   🟢 [06-05(五) 09:00 - 09:05] 3.****验证-0.17🍅 (5m)
   ➖➖➖➖➖➖ 🧨 标准容量耗尽 (转入加班推演) ➖➖➖➖➖➖
   🧨 [06-06(六) 10:00 - 10:06] 3.****验证-0.17🍅 (5m) (加班)
      ↳ 📉 **阻塞瓶颈**: 高顺位任务占据加班通道，后续2任务被迫顺延。
   🧨 [06-06(六) 10:06 - 10:06] 4.发放**** (0m) (加班)
   🧨 [06-06(六) 10:06 - 10:06] 4.发放**** (0m) (加班)
   • 目标死线: 2026-06-06 23:59:59 星期六

------------------------------------------------------------
🌡️ **每日实时战略负载热力 (Load Heatmap)**
   🟨 06-02(二):   69% [  5.2/  7.5h]  🟢空闲2.3h
   🟩 06-03(三):   35% [  3.2/  9.0h] 🔒含日程📅(0.5h)  🟢空闲5.8h
   🟩 06-04(四):    1% [  0.1/  9.0h]  🟢空闲8.9h
   🟩 06-05(五):    1% [  0.1/  9.0h]  🟢空闲8.9h
   🧨 06-06(六):   N/A [  0.1/  0.0h] 🧨加班0.1h

------------------------------------------------------------
🕵️ **日程📅审计 (Blocking Audit)**
   *(没有未设置明确的开始时间/预估的日程📅)*

------------------------------------------------------------
📊 **实时战略容量分析 (Capacity)**
   • 实际📍需求: 8.1h (原始 4.6h +77%)
     ↳ 算式: ∑ (预估 × 效率) / 60
     ↳ 详情:
       • 1.5-📌-****: 1.50h × 2.00🌐 = 3.00h
       • 1.5-📌-1.将****准备好-7: 1.00h × 2.01🎯 = 2.01h
       • 1.10-🎉-3.更新****: 1.00h × 2.00🌐 = 2.00h
       • 1.4-⛳-1.****步骤-4: 1.08h × 1.00🎯 = 1.08h
   • 日程📅占用: 🔒0.5h
   • 可用🟢容量: 34.5h (截止 2026-06-06)

------------------------------------------------------------
📉 ** 历史习惯分析 **: 
🕰️📈🌡️: **纯产能与吞吐量评估 (Velocity Check)** (截止于 2026-06-06 23:59:59)
待办纯预估：275m | 基于历史均速的吞吐饱和度：26.6%
待办纯预估：275m < 预计可消化纯预估: 1033.65m (算式: 剩余3.83天 × 日均269.63m)
👉 **产能结论**: 🟢 本周期 可适当增加 约 758.65 分钟的纯预估量。
```
