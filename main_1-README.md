# 🎯 RTM Agile Coach & Capacity Planner

An advanced, flagship Remember The Milk (RTM) automation script powered by MilkScript, acting as your personal Agile Coach. It deeply analyzes your task schedules, generates workload heatmaps, intelligently predicts your real-world efficiency, and offers smart task-pruning or fatigue-aware overtime advice when your system is overloaded.

## ✨ Features
*   ⏱️ **Precision Capacity Engine:** Calculates your exact available working minutes strictly based on your configured working hours (e.g., 9-18), weekends, and holidays.
*   🌡️ **Daily Workload Heatmaps:** Generates a visually intuitive, text-based daily heatmap (🟢 Free / 🟧 Saturated / 🩸 Overloaded). It accurately maps your tasks into available time slots to expose future bottlenecks.
*   ✂️ **Smart Triage & Pruning Model:** Employs a weighted scoring system based on your horizon (Survival, Sprint, Project, or Vision modes). When overloaded, it analyzes Objective Priority, Task Priority, and Urgency to recommend exactly which tasks to drop, delay, or move to an empty slot.
*   🔋 **Fatigue-Aware Overtime Advice:** Calculates realistic overtime needs using an "Efficiency Factor" (e.g., 0.8 hours of output per 1 hour of overtime), and enforces late-night hard stops (Circuit Breakers) to prevent burnout.
*   🧠 **Adaptive Efficiency Tracking:** Automatically analyzes your historical 7/30/90/180 days of RTM task completion data to calculate your "Work Ratio". It features smart circuit breakers that adapt if you were on vacation or had data anomalies.
*   📊 **Multi-Layered Actionable Reports:** Generates structured notes in a dedicated RTM log task: **HUD** (Status), **Action Plan** (Decisions), **Deep Diagnosis** (Heatmaps & Schedules), and **Details**. It also updates pinned multi-view Smart Lists for easy navigation.

## 🚀 Installation & Setup

**Prerequisites:** You must have a Remember The Milk Pro account to use MilkScript.

1.  **Add Script:**
    *   Go to your RTM Web App -> Settings -> MilkScript.
    *   Create a new script, copy, and paste the entire source code into the editor.
2.  **Configure UI Parameters:** 
    Set up the UI arguments (`rtm.args`) exactly as follows to match the script's inputs:
    *   ☑️ `a.💥 Quick: Generate [Today] Report?` *(Type: Checkbox / Boolean)*
    *   ☑️ `b.💥 Quick: Generate [This Week] Report?` *(Type: Checkbox / Boolean)*
    *   ☑️ `c.🗓 Quick: Generate [1 Week Later] Report?` *(Type: Checkbox / Boolean)*
    *   ☑️ `d.🗓 Quick: Generate [This Month] Report?` *(Type: Checkbox / Boolean)*
    *   📆 `e.📆 (Optional) Specify Base Due Date` *(Type: Date/Time)*
    *   🔢 `f.🔢 (Advanced) Offset Value (0=End of Period)` *(Type: Text / String)*
    *   🏷️ `g.📐 (Advanced) Offset Unit (Tag)` *(Type: Tag)*
    *   ☑️ `h.💥 Quick: Generate [Tomorrow] Report?` *(Type: Checkbox / Boolean)*
    *   ☑️ `i.🈷️ Quick: Generate [1 Month Later] Report?` *(Type: Checkbox / Boolean)*
    *   🏷️ `x.🔧 (Internal) Query Action (Due/Start)` *(Type: Tag)*
    *   🏷️ `y.🔧 (Internal) Query Modifier (Before/After)` *(Type: Tag)*
    *   ☑️ `z.🧪 Use Test List?` *(Type: Checkbox / Boolean)*

## ⚙️ Configuration

Before running, highly customize the `CONFIG` object at the top of the script to perfectly match your lifestyle and working habits:

```javascript
const CONFIG = {
    WORKDAY_CONFIG: {
        startHour: 9,      // Working day starts at 9:00 AM
        endHour: 18,       // Working day ends at 6:00 PM
        workingDays: [1, 2, 3, 4, 5], // Monday to Friday (0=Sun, 6=Sat)
        holidays: [],      // Add 'YYYY-MM-DD' for personal holidays/leaves
    },
    // ...
};

const OVERTIME_CONFIG = {
    EFFICIENCY_FACTOR: 0.8, // 1 hour of overtime yields 0.8 hours of effective output
    LATE_THRESHOLD: 21      // Stop suggesting overtime for today after 9:00 PM
};
```

## 📖 How to Use

1.  **Quick Reports:** Trigger the script and simply check one of the shortcuts (e.g., `Generate [This Week] Report?`). The script will auto-calculate everything due by the end of this week.
2.  **Custom Horizons:** Leave the shortcuts blank and use `Specify Base Due Date` or `Offset Value` to generate a report for exactly 45 days into the future.
3.  **Review the HUD:** Check your RTM Inbox or `♻️` list for a task starting with the Period Name (e.g., `🛑 本周 | 159.5% | 逾期`). 
4.  **Take Action:** Open the task notes to read the **Action Plan**. It will tell you exactly how many hours to cut and automatically recommend specific tasks to delay based on their strategic priorities!
5.  **Smart Navigation:** Check your RTM left sidebar. The script will automatically create/update pinned Smart Lists (e.g., `☀️-今日计划-本周-🎯🔍`) for focused execution.

## 📄 License
This project is open-source and available under the MIT License.

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
