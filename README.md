# 🎯 RTM Agile Coach & Workflow Suite

Welcome to the **RTM Agile Coach & Workflow Suite**! This repository contains a powerful collection of automation scripts powered by [MilkScript](https://www.rememberthemilk.com/services/milkscript/), designed specifically for Remember The Milk (RTM) Pro users. 

This suite transforms your basic RTM lists into a fully-fledged Agile, OKR (Objectives and Key Results), and Capacity Planning system.

---

## 🌟 The Ecosystem Architecture

This repository is not just a random collection of scripts; it operates as a **cohesive ecosystem**. 

It is divided into one **Core Engine** and five **Supplementary Tools**:

*   **👑 Core Engine (Main)**: The brain of the operation. It aggregates data, generates schedule deductions, creates workload heatmaps, calculates smart pruning advice, and outputs comprehensive analysis reports.
*   **🛠️ Supplementary Tools (Suppl)**: The data feeders. The core engine relies heavily on precise time-tracking and clear objective-linking. These supplementary scripts turn tedious manual actions like tracking, settling, suspending, estimating, and linking into seamless one-click operations.

> *💡 The main script generates advanced reports and heatmaps, while the supplementary scripts effortlessly feed it with accurate time-tracking and objective-linking data.*

---

## 📦 Script Catalog

Please click on **[📖 Docs]** to read the specific installation steps, UI parameter configurations, and usage guides for each script.

### 👑 Core Engine
The central dispatch of the system, used for high-level planning and system monitoring.

| File | Module Name | Description | Docs |
| :--- | :--- | :--- | :---: |
| [`main_1-rtm-objective-manager.milkscript`](./main_1-rtm-objective-manager.milkscript) | **RTM Agile Coach & Capacity Planner** | **[MAIN]** The core scheduling center. Analyzes task schedules, generates load heatmaps, dynamically calculates work ratios, and provides smart pruning/overtime advice when overloaded. | [📖 Docs](./main_1-README.md) |

### 🛠️ Supplementary Tools
These scripts help you quickly and accurately maintain task statuses during your daily execution, ensuring the Core Engine is fed with "clean and healthy" data.

| File | Module Name | Description | Docs |
| :--- | :--- | :--- | :---: |
| [`suppl_5-create_archive_objective_link_tasks.milkscript`](./suppl_5-create_archive_objective_link_tasks.milkscript) | **RTM Objective Manager & Sync Engine** | **[Architecture]** Auto-creates timestamped goal tags, achieves bi-directional syncing between goals and tasks, and topologically sorts dependencies. | [📖 Docs](./suppl_5-README.md) |
| [`suppl_1-start-tasks.milkscript`](./suppl_1-start-tasks.milkscript) | **RTM Task Starter & Reclocker** | **[Execution]** Instantly starts tasks, smartly handles the cloning and resetting of recurring tasks, and auto-applies 'In Progress' tags. | [📖 Docs](./suppl_1-README.md) |
| [`suppl_2-on-hold-tasks.milkscript`](./suppl_2-on-hold-tasks.milkscript) | **RTM Task Suspender & Auto-Estimator** | **[Execution]** Pauses tasks while automatically calculating the elapsed work time and appending it to the task's Time Estimate. | [📖 Docs](./suppl_2-README.md) |
| [`suppl_3-stop-tasks.milkscript`](./suppl_3-stop-tasks.milkscript) | **RTM Task Completer & Pomodoro Tracker** | **[Settlement]** Finalizes tasks, calculates exact time spent, appends Pomodoro visualizers (🍏), and can instantly generate follow-up tasks. | [📖 Docs](./suppl_3-README.md) |
| [`suppl_4-set-estimate.milkscript`](./suppl_4-set-estimate.milkscript) | **RTM Pomodoro Estimator** | **[Planning]** Rapidly batches time estimates for multiple selected tasks and appends visual Pomodoro badges (🍅) to their names. | [📖 Docs](./suppl_4-README.md) |

---

## 🚀 Global Installation Guide

All `.milkscript` files in this repository follow the exact same basic installation process.

*Prerequisite: You must have a **Remember The Milk Pro** account to use MilkScript.*

1. **Access Settings:** Open your RTM Web App, click the gear icon in the top right to enter **Settings**, and select the **MilkScript** tab.
2. **Create New Script:** Click the **Add Script** button.
3. **Copy & Paste:** Click on the desired script file in this GitHub repository (e.g., `main_1-rtm-objective-manager.milkscript`), copy the entire source code, and paste it into the RTM code editor.
4. **Configure UI Parameters:** *This is crucial!* Please open the corresponding **[📖 Docs]** for the script you are installing and strictly follow the `rtm.args` requirements to add the necessary input prompts (Checkboxes, Text fields, Tags, etc.) on the right panel of the editor.
5. **Save & Run:** Once saved, you can select tasks in your RTM interface and trigger the scripts anytime from the top menu bar.

---

## 📄 License

This project is open-source and available under the MIT License. Feel free to fork, customize, and build your own perfect workflow!
