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
```text
🚀 ** Action Plan ** 
------------------------------------------------------------
⚠️ [High Pressure] Overtime Required (Projected Congestion: 117%)

🤔👉 **System Assessment**: Not yet overdue, but total load exceeds capacity.
   💪 **Overtime Rescue Plan**: 4 days remaining, requires **1.3h** of overtime per night (Estimated until 20:19).
      *(Note: The suggested overtime is the "Best Case": how much you need to catch up at night assuming you maxed out your daytime hours.)*
      *(Note: Calculated at 80% fatigue efficiency, costing an additional 64m of fatigue loss)*
--------------------------------------------------
   ✂️ **Load Reduction Advice**: To avoid severe fatigue, recommend cutting approx. **1.6h** of estimated work (see list below).
💡 **Smart Pruning Recommendations (Frees up 2.5h)**:
*(Sprint Model: 30% Objective + 45% Time + 25% Task)*
---------------------------------------------
    ✂️ 🔄 Move to 2026-06-10 (Wed) [P2 ⤷ None] 
     1.4-⛳-1.**Step-5 ⤷ 4.Distribute*** (0m) 
     ⏰82% | 2026-06-13 00:00:00 Saturday
---------------------------------------------
    ✂️ 🔄 Move to 2026-06-10 (Wed) [P2 ⤷ None] 
     1.10-🎉-5.Enter** "Readiness State" (Hardcore) ⤷ Phase 3: Reverse** -1.00🍅 (30m) 
     ⏰54% | 2026-06-12 00:00:00 Friday
---------------------------------------------
    ✂️ 🔄 Move to 2026-06-10 (Wed) [P2 ⤷ P3] 
     1.10-🎉-5.Enter** "Readiness State" (Hardcore) ⤷ 1.4, Practice [***] -2.00🍅 (60m) 
     ⏰54% | 2026-06-12 00:00:00 Friday

------------------------------------------------------------
📊 ** Core Metrics Overview **: 
• Schedule Congestion: 117.1% 
• Projected Time Needed: 29.0h (🔒0.5h) | Available: 24.8h
  * (Note: Projected Time = Weighted Task Hours + Calendar Events 📅)*

🧠 ** Deep Diagnosis ** 
------------------------------------------------------------
📅 **Real-time Tactical Schedule Deduction**
   • Estimated Completion: 2026-06-06 10:06:15 Saturday
   * (Note: The estimated completion in the schedule is the "Worst Case": if you have absolutely no time during the day, how late at night you will have to push this.)*
   🟢 [06-02 (Tue) 10:29 - 10:39] Check **** reply -0.33🍅 (10m)
   🟢 [06-02 (Tue) 10:39 - 11:39] Query **** materials? -1.00🍅 (30m)
   🟢 [06-02 (Tue) 11:39 - 13:40] 2.2.5-How to **** -2.00🍅 (60m)
   🟢 [06-02 (Tue) 13:40 - 15:40] 3-2-1-Update **** at **** -2.00🍅 (60m)
   🟢 [06-03 (Wed) 09:00 - 09:05] 3.**** Verification -0.17🍅 (5m)
   🟢 [06-03 (Wed) 09:05 - 09:35] Figure out what **** is -1.00🍅 (30m)
   🟢 [06-03 (Wed) 09:35 - 09:40] 3.**** Verification -0.17🍅 (5m)
   🟢 [06-03 (Wed) 09:40 - 11:40] Prepare **** materials -2.00🍅 (60m)
   🟢 [06-04 (Thu) 09:00 - 09:05] 3.**** Verification -0.17🍅 (5m)
   🟢 [06-05 (Fri) 09:00 - 09:05] 3.**** Verification -0.17🍅 (5m)
   ➖➖➖➖➖➖ 🧨 Standard Capacity Exhausted (Switching to Overtime Deduction) ➖➖➖➖➖➖
   🧨 [06-06 (Sat) 10:00 - 10:06] 3.**** Verification -0.17🍅 (5m) (Overtime)
      ↳ 📉 **Bottleneck**: High-priority tasks are occupying the overtime channel, forcing 2 subsequent tasks to be delayed.
   🧨 [06-06 (Sat) 10:06 - 10:06] 4.Distribute **** (0m) (Overtime)
   🧨 [06-06 (Sat) 10:06 - 10:06] 4.Distribute **** (0m) (Overtime)
   • Objective Deadline: 2026-06-06 23:59:59 Saturday

------------------------------------------------------------
🌡️ **Daily Real-time Load Heatmap**
   🟨 06-02 (Tue):  69% [ 5.2/ 7.5h] 🟢 Free 2.3h
   🟩 06-03 (Wed):  35% [ 3.2/ 9.0h] 🔒 Incl. Event📅(0.5h) 🟢 Free 5.8h
   🟩 06-04 (Thu):   1% [ 0.1/ 9.0h] 🟢 Free 8.9h
   🟩 06-05 (Fri):   1% [ 0.1/ 9.0h] 🟢 Free 8.9h
   🧨 06-06 (Sat):  N/A [ 0.1/ 0.0h] 🧨 Overtime 0.1h

------------------------------------------------------------
🕵️ **Calendar Blocking Audit📅**
   *(No calendar events without clear start time/estimates📅)*

------------------------------------------------------------
📊 **Real-time Tactical Capacity Analysis**
   • Actual📍Demand: 8.1h (Raw 4.6h +77%)
     ↳ Formula: ∑ (Estimate × Efficiency) / 60
     ↳ Details:
       • 1.5-📌-****: 1.50h × 2.00🌐 = 3.00h
       • 1.5-📌-1.Get **** ready-7: 1.00h × 2.01🎯 = 2.01h
       • 1.10-🎉-3.Update ****: 1.00h × 2.00🌐 = 2.00h
       • 1.4-⛳-1.**** Step-4: 1.08h × 1.00🎯 = 1.08h
   • Calendar📅 Blocked: 🔒0.5h
   • Available🟢 Capacity: 34.5h (Until 2026-06-06)

------------------------------------------------------------
📉 ** Historical Habit Analysis **: 
🕰️📈🌡️: **Raw Capacity & Throughput Evaluation (Velocity Check)** (Until 2026-06-06 23:59:59)
Pending Raw Estimate: 275m | Throughput Saturation based on Historical Velocity: 26.6%
Pending Raw Estimate: 275m < Expected Digestible Raw Estimate: 1033.65m (Formula: 3.83 Days Remaining × 269.63m Daily Avg)
👉 **Velocity Conclusion**: 🟢 For this cycle, you can safely add approx. 758.65 minutes of raw estimate.
```
