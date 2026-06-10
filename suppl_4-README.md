# 🍅 RTM Pomodoro Estimator

A straightforward and highly effective Remember The Milk (RTM) automation script powered by MilkScript. It is designed to help you plan your daily sprints by quickly applying time estimates to your tasks and adding a neat, visual Pomodoro indicator directly to the task names.

## ✨ Features
*   ⏱️ **Rapid Time Estimation:** Quickly set or update the estimated time for multiple selected tasks at once. If you don't input anything, it defaults to a standard 30-minute block.
*   🍅 **Visual Pomodoro Badges:** Automatically calculates how many Pomodoros your time equates to (based on 30 mins/Pomodoro) and appends a visual suffix to the task name (e.g., `Task Name - 1.50🍅`).
*   ♻️ **Smart Suffix Updating:** Changed your mind about the estimate? Run the script again! It uses precise Regular Expressions (`Regex`) to detect existing Pomodoro emojis and safely replaces the old suffix without duplicating emojis or messing up your task name.
*   🔄 **Automatic Time Conversion:** Seamlessly calculates and converts your flat minute input (e.g., `90`) into RTM's native `Hours/Minutes` estimate format (e.g., `1 hr 30 min`).

## 🚀 Installation & Setup

**Prerequisites:** You must have a Remember The Milk Pro account to use MilkScript.

1.  **Add Script:**
    *   Go to your RTM Web App -> Settings -> MilkScript.
    *   Create a new script, copy, and paste the entire source code into the editor.
2.  **Configure UI Parameters:** 
    Set up the UI argument (`rtm.args`) exactly as follows so the script can ask for your input:
    *   🔢 `How many minutes do you plan to estimate for this task? The default is 30 minutes.` *(Type: Text / String)*

## ⚙️ Configuration

This script is lightweight and doesn't require a complex configuration block. However, you can easily customize its core behavior by tweaking a few variables directly at the top of the source code:

```javascript
// Customize your preferred Pomodoro emoji
const emoji = '🍅'; // You can change this to '🍏', '⏳', etc.

// The script assumes 1 Pomodoro = 30 minutes. 
// If you prefer the standard 25-minute Pomodoro, simply change the math in the code:
// const suffix2append = '-' + (num / 25).toFixed(2) + emoji;
```

## 📖 How to Use

1.  **Select Tasks:** Check one or multiple tasks in your daily plan that need time estimates.
2.  **Run the Script:** Trigger the script from your web or mobile app.
3.  **Enter Minutes:** 
    *   Type a number (e.g., `60` for one hour, `45` for 45 minutes).
    *   Or simply leave it completely blank and press OK to instantly apply the default `30` minutes.
4.  **Check Output:** 
    *   Your tasks will now have a precise RTM Time Estimate added to their properties.
    *   Their names will be beautifully updated (e.g., `Read Documentation - 2.00🍅`).

## 📄 License
This project is open-source and available under the MIT License.
