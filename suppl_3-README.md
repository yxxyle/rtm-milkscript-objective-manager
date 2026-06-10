# ✅ RTM Task Completer & Pomodoro Tracker

A comprehensive Remember The Milk (RTM) automation script powered by MilkScript to finalize your workflow. It handles everything from calculating time spent, appending Pomodoro counts to task names, safely checking off recurring tasks, to automatically generating "subsequent tasks" when your work needs to carry over.

## ✨ Features
*   **🍎 Automated Pomodoro Logging:** Calculates the exact minutes spent on a task and appends a clean Pomodoro visualizer to the task name (e.g., `Task Name - 1.50🍏`). It safely updates existing suffixes without duplicate clutter.
*   **⏭️ Continuous Workflow (Subsequent Tasks):** Work isn't finished yet? Check a box to instantly generate a clean, connected follow-up task. It strips the old Pomodoro suffix, sets the status to "In Progress," and carries over all tags and notes.
*   **🔁 Smart Recurring Task Handling:** Automatically extracts today's instance of a recurring task into a standalone clone for accurate time-logging, while safely advancing the original schedule.
*   **🏷️ Status & Exception Management:** Easily finalize tasks as `done`, `cancelled`, `abandoned`, or `lost`. The script is smart enough to skip time-tracking for discarded/cancelled tasks (`2.7`, `2.10`, `2.14`).
*   **⏱️ Flexible Time Overrides:** Automatically calculates time elapsed using your Due Time, but allows manual override inputs if you forgot to track exactly.

## 🚀 Installation & Setup

**Prerequisites:** You must have a Remember The Milk Pro account to use MilkScript.

1.  **Add Script:**
    *   Go to your RTM Web App -> Settings -> MilkScript.
    *   Create a new script, copy, and paste the entire source code into the editor.
2.  **Configure UI Parameters:** 
    Set up the UI arguments (`rtm.args`) exactly as follows to match the script's `CONFIG.PROMPTS`:
    *   ☑️ `Do you want to complete task now?` *(Type: Checkbox / Boolean)*
    *   ☑️ `Do you want to create subsequent task?` *(Type: Checkbox / Boolean)*
    *   🏷️ `Select statusTag(input 2. to filter) for this/new task when you want to cancel/abandon/lost it?` *(Type: Tag)*
    *   🔢 `How many estimate minutes do you want to set for this task? default is calculated.` *(Type: Text / String)*
    *   📆 `When(default is now) do you want to due this/new task?` *(Type: Date/Time)*

## ⚙️ Configuration

Before running, you can customize the `CONFIG` object to match your preferred Pomodoro length, tracking emoji, and tagging habits:

```javascript
const CONFIG = {
    TAGS: {
        WITHOUT_ESTIMATE: ['2.7-cancelled', '2.10-abandon', '2.14-lost'], // Skips time tracking for these statuses
        IN_PROGRESS: '2.3-in_progress',
        DONE: '2.4-done',
        STATUS_PREFIX: '2.',
    },
    POMODORO: {
        MINUTES_PER_SESSION: 30, // Change this to 25 if you prefer standard Pomodoros
        EMOJI: '🍏',             // Change to '🍅' or any emoji you like
    },
    MILLISECONDS_IN_MINUTE: 60 * 1000,
};
```

## 📖 How to Use

1.  **Select Tasks:** Check one or multiple tasks you have finished working on.
2.  **Run the Script:** Trigger the script and configure the prompts:
    *   **Normal Completion:** Check "Complete task now?". Leave manual time empty to auto-calculate.
    *   **Need more time?** Don't check "Complete", but DO check "Create subsequent task?". It will log the time spent *so far* on the current task and generate a fresh one for the next session.
    *   **Abandoning a task?** Select the `2.10-abandon` tag in the status prompt. The script will safely skip adding time estimates and Pomodoro emojis.
3.  **Check Output:** 
    *   Your task's name will update with ` - X.XX🍏`.
    *   Status tags will update cleanly.
    *   If selected, follow-up tasks will instantly appear in your active list.

## 📄 License
This project is open-source and available under the MIT License.
