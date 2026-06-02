# thex
🇨🇳 专为Remember The Milk打造的自动化脚本，您的专属敏捷教练。它通过高精度排期引擎推演任务耗时，生成负载热力图。遇到排期溢出时，会自动提供智能削减或加班建议，并输出多维诊断报告，助您告别超载。 

🇬🇧 An advanced Remember The Milk script acting as your Agile coach. It simulates schedules, generates workload heatmaps, and offers smart task-pruning or overtime advice when overloaded, helping you conquer burnout with deep reports.

---

# 🎯 RTM Agile Coach (RTM 敏捷教练)

[🇨🇳 简体中文 (Simplified Chinese)](#-简体中文) | [🇬🇧 English](#-english)

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

<br>

# 🇨🇳 简体中文

专为 [Remember The Milk (RTM)](https://www.rememberthemilk.com/) 打造的自动化 MilkScript 脚本，您的专属敏捷教练。它通过高精度排期引擎推演任务耗时，生成负载热力图。遇到排期溢出时，会自动提供智能削减或加班建议，并输出多维诊断报告，助您告别超载。

## ✨ 核心亮点

- **⏱️ 高精度排期引擎**：毫秒级模拟任务执行流程，严格扣除下班时间、周末及节假日，还原最真实的可用工作容量。
- **🌡️ 可视化负载热力图**：在 RTM 笔记中直接渲染每日容量与负载图表（支持 Emoji 状态分级），瓶颈与空闲时段一目了然。
- **🧠 自适应效率追踪**：告别“盲目预估”。脚本会自动分析过去 7/30/180 天的历史完成数据，计算真实的“工时膨胀率”，并具备针对“休假黑洞”和“新手期稀释”的智能熔断机制。
- **✂️ 智能削减与补位**：当需求溢出时，基于加权归一化模型（目标优先级 + 任务优先级 + 时间紧迫度），精准建议您“推迟、移除或平移”哪些具体任务。
- **🔋 疲劳感知加班建议**：基于设定的“疲劳折损率”（默认 0.8），为您计算真实的加班代价，并在深夜（如 21:00 后）触发强制休息熔断。
- **📊 深度多层级报表**：自动生成渐进式披露报告——从抬头显示（HUD）、行动指南、深度诊断到原始明细，并在后台自动记录历史容量指标（CSV格式）供复盘使用。

## 🚀 安装与设置

1. **环境要求**：您需要拥有 **Remember The Milk Pro (高级账户)** 才能运行 MilkScript。
2. **添加脚本**：
   - 登录 RTM 网页版 -> 设置 (Settings) -> MilkScript。
   - 新建一个脚本，将全部源码粘贴进编辑器。
3. **配置 UI 参数**：根据代码中的 `rtm.args` 键值，在脚本设置中完整配置相应的用户输入项（例如：`a.💥 快捷：生成【今日】报告？` 等开关和下拉框）。

## ⚙️ 个性化配置

在开始运行之前，强烈建议您修改代码顶部的 `CONFIG` 对象，以匹配您真实的作息节律：

```javascript
const CONFIG = {
    // 定义您的标准工作日
    WORKDAY_CONFIG: {
        startHour: 9,      // 上班时间：早 9:00
        endHour: 18,       // 下班时间：晚 18:00
        workingDays: [1, 2, 3, 4, 5], // 周一至周五工作
        holidays: [],      // 特定节假日可在此添加 'YYYY-MM-DD'
    },
    ...
};

const OVERTIME_CONFIG = {
    EFFICIENCY_FACTOR: 0.8, // 疲劳折损：加班1小时仅相当于正常 0.8 小时的产出
    LATE_THRESHOLD: 21      // 深夜熔断：超过 21:00 建议放弃加班
};
```

*注意：本脚本深度依赖特定的标签语法体系（如使用 `1.1-🔭` 标记目标类型，使用 `0_` 和 `99_` 前缀链接子任务）。使用前请确保您的标签管理系统与 `CONFIG.TAGS` 的定义兼容。*

## 📖 使用指南

在 RTM 网页或移动端运行脚本时，您可以：
1. **快捷一键生成**：勾选参数面板上的快捷开关（如“今日”、“本周”、“本月”），直接一键生成对应周期的分析报告。
2. **自定义基准日**：手动指定一个目标截止日期或使用相对偏移量（高级玩法）。
3. **查看智能视图**：脚本运行后，会自动生成或更新诸如 `✨-本周-🎯🔍` 的智能列表（Smart List），方便您在侧边栏快速查阅。
4. **阅读报告**：前往回收站（`♻️`）或 Inbox 查看自动生成的图文任务笔记，根据“行动指南 (Action Plan)”做出你的排期决策！

## 📄 开源协议
本项目完全开源，遵循 [MIT License](LICENSE) 协议。欢迎提交 PR 和 Issue！
