# 🎯 RTM Objective Manager & Sync Engine

An advanced, system-level Remember The Milk (RTM) automation script powered by MilkScript. Designed for heavy users, it turns your RTM into a fully-fledged OKR (Objectives and Key Results) and Sprint management system. It handles bi-directional linking, dynamic goal-tagging, topological sorting for task dependencies, and automatic sprint rollovers.

## ✨ Features
*   🔗 **Bi-directional Smart Syncing:** Automatically generates and updates clean, readable "Summary Notes" in parent objectives containing all child task statuses. Simultaneously injects "Parent Info Notes" into child tasks so you never lose context.
*   🏷️ **Dynamic Tagging & Auto-Healing:** Automatically generates unique goal tags (e.g., `0_2026-06-10_my-project`). If you change an objective's name or due date, the script detects the "drift" and automatically renames the tag across all linked tasks without breaking connections.
*   🔄 **Smart Sprint Rollovers (Subsequent Objectives):** When you complete an objective but still have unfinished subtasks, the script intelligently archives the current tag (`0_` to `99_`), creates a "Sprint-2" objective, and moves the incomplete tasks over seamlessly.
*   🕸️ **Topological Dependency Sorting:** Built-in Kahn's Algorithm! If your tasks have dependencies (via `dep:` notes), the script calculates the exact execution order and topologically sorts them in your parent objective's summary note.
*   🚥 **Auto-Completion & State Aggregation:** If all subtasks are finished, it automatically marks the parent objective as complete. If you add a new uncompleted subtask later, it revokes the parent's completion status.

## 🚀 Installation & Setup

**Prerequisites:** You must have a Remember The Milk Pro account to use MilkScript.

1.  **Add Script:**
    *   Go to your RTM Web App -> Settings -> MilkScript.
    *   Create a new script, copy, and paste the entire source code into the editor.
2.  **Configure UI Parameters:** 
    Set up the UI arguments (`rtm.args`) exactly as follows to match the script's `CONFIG.PROMPTS`:
    *   🔢 `1.Input objective type number(Default is 6-quick wins🎉) for NEW objective. 1-long-term visions🔭; 2-yearly goals🗽; 3-quarterly objectives🎯; 4-monthly milestones⛳; 5-weekly wins📌; 6-quick wins🎉` *(Type: Text / Number)*
    *   📝 `2.Give name to NEW objective.` *(Type: Text / String)*
    *   📆 `3.When(default is today) do you want to due the objective?` *(Type: Date/Time)*
    *   📆 `4.When(default is Never) do you want to start the objective?` *(Type: Date/Time)*

## ⚙️ Configuration

The script uses a very specific OKR tagging hierarchy. You can adjust these in the `CONFIG` object to match your specific emoji and tagging workflow:

```javascript
const CONFIG = {
    TAGS: {
        OBJECTIVE_TYPES: ['1.1-🔭', '1.2-🗽', '1.3-🎯', '1.4-⛳', '1.5-📌', '1.10-🎉'],
        DEFAULT_OBJECTIVE_TYPE: '1.10-🎉',
        DEFAULT_COMPLETION: '2.4-done',
        COMPLETED_STATUS: ['2.4-done', '2.7-cancelled', '2.8-closed', '2.9-failed', '2.10-abandon', '2.12-unproductive', '2.13-reduced', '2.14-lost'],
        OBJECTIVE_TAG_OPEN_PREFIX: '0_',  // Active goal tags start with this
        OBJECTIVE_TAG_CLOSE_PREFIX: '99_',// Archived goal tags start with this
    },
    NOTE_PREFIX: {
        CHILD_NOTE: "child",
        PARENT_NOTE: "parent",
    }
};
```

## 📖 How to Use

This script acts as a dual-engine and operates in two distinct modes based on your inputs:

### Mode 1: Linking & Creation Mode (链接与创建模式)
*When you fill in the UI prompts.*
1.  **Select Tasks:** Select the tasks you want to group into a project/objective.
2.  **Run Script & Fill Prompts:** Provide the objective type (1-6) and a name (e.g., `Revamp Website`).
3.  **Result:** The script will create a new Objective task, dynamically generate a tag for it, link all selected tasks to this new Objective (via Tags and URLs), and write cross-linking Notes.

### Mode 2: Synchronization Mode (同步与结转模式)
*When you select exactly ONE objective task and leave all UI prompts BLANK.*
1.  **Select ONE Objective:** Select an existing parent objective.
2.  **Run Script (Empty Prompts):** Just hit OK without typing anything.
3.  **Result:** 
    *   The script scans all linked child tasks and rebuilds the dependency graph.
    *   It updates the Parent Note with a perfectly sorted, emoji-rich summary of what's done and what's pending.
    *   *Magic Rollover:* If the parent objective is marked as completed, but subtasks remain, it will instantly generate `[Objective Name]-2`, link the leftover tasks to the new sprint, and safely archive the old goal tag!

## 📄 License
This project is open-source and available under the MIT License.
