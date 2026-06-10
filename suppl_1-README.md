# ⏱️ RTM Task Starter & Reclocker

A smart Remember The Milk (RTM) automation script powered by MilkScript that streamlines your task execution workflow. It effortlessly handles starting tasks, reclocking time, cloning tasks for time-tracking, and smartly extracting instances from recurring tasks—all while keeping your status tags perfectly organized.

## ✨ Features
*   **🔄 Smart Reclocking & Starting:** Instantly start a selected task or reset its start time (`setStartTime(now)`) if you are picking it up again after a break.
*   **🔁 Recurring Task Extraction:** Automatically handles recurring tasks! It creates a standalone clone for today's execution and safely advances the original repeating schedule (by deleting the current occurrence).
*   **🏷️ Automated Status Tagging:** Keeps your workspace clean. Automatically strips away old status tags (prefixed with `2.`) and applies the `2.3-in_progress` tag so you always know what you're working on.
*   **🧬 Faithful Task Cloning:** When creating a new task to track time, it flawlessly copies the original task's List, Priority, URL, Parent hierarchy, Tags, and chronologically sorts and copies all Notes.
*   **📅 Dynamic Due Dates:** Automatically adjusts due dates and time estimates based on whether you are starting immediately or scheduling the clone for later.

## 🚀 Installation & Setup

**Prerequisites:** You must have a Remember The Milk Pro account to use MilkScript.

1.  **Add Script:**
    *   Go to your RTM Web App -> Settings -> MilkScript.
    *   Create a new script, copy, and paste the entire source code into the editor.
2.  **Configure UI Parameters:** 
    Set up the UI arguments (`rtm.args`) exactly as follows to match the script's `CONFIG.PROMPTS`:
    *   ☑️ `Do you want to reclocking?` *(Type: Checkbox / Boolean)*
    *   ☑️ `Do you want to create new task to track time?` *(Type: Checkbox / Boolean)*
    *   ☑️ `Do you want to start new task now?` *(Type: Checkbox / Boolean)*
    *   📆 `When(default is now) do you want to due this/new task?` *(Type: Date/Time)*

## ⚙️ Configuration

Before running, you can customize the `CONFIG` object at the top of the script to match your personal tagging system and UI prompt preferences:

```javascript
const CONFIG = {
    PROMPTS: {
        RECLOCK: 'Do you want to reclocking?',
        CREATE_NEW_TASK: 'Do you want to create new task to track time?',
        DUE_DATE: 'When(default is now) do you want to due this/new task?',
        START_NEW_TASK: 'Do you want to start new task now?',
    },
    TAGS: {
        IN_PROGRESS: '2.3-in_progress', // The tag applied when a task starts
        STATUS_PREFIX: '2.',            // The prefix used to find and remove old status tags
    }
};
```
*Note: Ensure your workflow uses the `2.` prefix for statuses (e.g., `2.1-todo`, `2.2-waiting`) so the script can accurately clean them up before applying `2.3-in_progress`.*

## 📖 How to Use

1.  **Select Tasks:** Check one or multiple tasks in your RTM web interface or mobile app.
2.  **Run the Script:** Trigger the script and answer the prompts based on your current need:
    *   *Just starting a normal task?* Leave everything blank; it will set the start time to now and update tags.
    *   *Continuing an old task?* Check **"Do you want to reclocking?"**.
    *   *Working on a recurring task?* Just run it! The script automatically knows to clone it, start the clone, and advance the recurring schedule.
3.  **Check Output:** The console will log `任务 " [Task Name]" 已成功开始！`, and your task will instantly move to your "In Progress" view.

## 📄 License
This project is open-source and available under the MIT License.
