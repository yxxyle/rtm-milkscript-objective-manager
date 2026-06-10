# ⏸️ RTM Task Suspender & Auto-Estimator

A smart Remember The Milk (RTM) automation script powered by MilkScript designed to gracefully pause your ongoing tasks. When you need to take a break or switch contexts, it automatically calculates the exact time you've spent working, updates the task's total time estimate, and shifts its status to "On Hold"—all in one click.

## ✨ Features
*   **⏳ Automated Time Tracking:** Calculates the precise time elapsed between the task's last Due Time (acting as your start checkpoint) and *Now*. It automatically adds these elapsed minutes to the task's existing Time Estimate.
*   **⏸️ Seamless Context Switching:** Instantly transitions your task's status. It strips away the `2.3-in_progress` tag and neatly applies the `2.5-on_hold` tag to keep your task lists accurately reflected.
*   **🔄 Instant Checkpointing:** Sets the task's Due Date/Time to the exact moment you paused it (`now`). This creates a perfect timestamp checkpoint for the next time you resume the task.
*   **🛡️ Robust & Safe Execution:** Built-in safeguards ensure that tasks without a Due Date are gracefully skipped without crashing the script. It also guarantees that calculated time estimates never drop below zero.

## 🚀 Installation & Setup

**Prerequisites:** You must have a Remember The Milk Pro account to use MilkScript.

1.  **Add Script:**
    *   Go to your RTM Web App -> Settings -> MilkScript.
    *   Create a new script, copy, and paste the entire source code into the editor.
2.  **Configure UI Parameters:** 
    *   🎉 **Zero Configuration Required!** This script runs perfectly without any UI prompts (`rtm.args`). You can trigger it instantly without answering any pop-ups.

## ⚙️ Configuration

Before running, customize the `CONFIG` object at the top of the script if your personal tagging system differs from the defaults:

```javascript
const CONFIG = {
    TAGS: {
        IN_PROGRESS: '2.3-in_progress', // The tag to be removed when paused
        ON_HOLD: '2.5-on_hold',         // The tag to be applied when paused
    },
    MILLISECONDS_IN_MINUTE: 60 * 1000,  // Standard time conversion (do not change)
};
```

## 📖 How to Use

1.  **Work on a Task:** Ensure the task you are currently working on has a **Due Time** set (this script uses the Due Time as the timestamp of when you started or last reclocked the task).
2.  **Select Tasks:** Check one or multiple tasks you wish to pause in your RTM interface.
3.  **Run the Script:** Trigger the script from your web or mobile app.
4.  **Check Output:** 
    *   The script will calculate `Now - Due Time` in minutes.
    *   It will add those minutes to your current Estimate.
    *   The tag will change from "In Progress" to "On Hold".
    *   The Console will log exactly how many minutes were added to the estimate.

## 📄 License
This project is open-source and available under the MIT License.
