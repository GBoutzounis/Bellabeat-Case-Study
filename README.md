# Bellabeat Case Study: Analyzing Daily Consumer Fitness Habits

**Author:** Ioannis Boutzounis  
**Last Updated:** 25/9/2026

Bellabeat is a pioneering wellness company that designs high-tech, health-focused smart products for women. This project analyzes historical fitness tracker data to uncover the real-world daily habits of smart device users by examining daily step volumes, calorie burn rates, and weekly activity routines. The objective is to translate these data insights into targeted, actionable marketing strategies that boost user engagement, encourage daily consistency, and drive Bellabeat's future growth.

## Data Source & Reliability
*   **Origin:** Public FitBit Fitness Tracker dataset via Kaggle.
*   **Volume:** 1,165 logged days across approximately 35 unique users.
*   **Key Metrics:** Device-recorded daily steps, active minutes, and calories burned.
*   **Limitations:** The dataset has a small sample size and lacks demographic data such as age and gender.

## Tools & Methodology
The entire data cleaning and manipulation process was conducted in Excel, while Tableau was utilized to create some of the final data visualizations.

## Data Cleaning
Merged raw activity files into a single `Activity_Merged_Spreadsheet` and standardized all dates into a DD/MM/YY format. Checked for and removed 24 duplicate log entries based on ID and ActivityDate. Filtered out invalid tracking days to avoid skewing averages:
*   Removed days with 0 steps (138 rows removed).
*   Removed days with exactly 1,440 sedentary minutes, indicating the device was sitting on a nightstand for 24 hours (17 rows removed).
*   Removed days with fewer than 200 calories burned, which indicates partial tracking or a sync failure (3 rows removed).
*   Removed days with fewer than 600 total wear minutes (24 rows removed).
*   Removed days with fewer than 200 total steps (24 rows removed).

## Data Engineering
New custom variables were calculated in Excel to better analyze user habits:
*   **TotalWearMinutes:** Calculated as the sum of Very Active, Fairly Active, Lightly Active, and Sedentary minutes.
*   **TotalActivityMinutes:** Calculated as the sum of Very Active, Fairly Active, and Lightly Active minutes.
*   **Day_of_Week & Is_Weekend:** Extracted the specific day of the week and flagged weekend days to compare behaviors.
*   **ActivityLevel:** Categorized users into four distinct tiers based on daily step counts:

| Activity Level | Step Count Range |
| :--- | :--- |
| **Sedentary** | < 5,000 steps |
| **Lightly Active** | 5,000 - 7,499 steps |
| **Fairly Active** | 7,500 - 9,999 steps |
| **Highly Active** | $\ge10,000$ steps |

## Key Insights

*(Note: To view the full Tableau visualizations supporting these insights, please refer to the **`Bellabeat_Case_Study.pdf`** presentation included in this repository.)*

*   **Activity Level Breakdown (Calories & Minutes):** Moving more directly leads to burning more calories, with a significant jump when users reach the highest activity level. Sedentary days average about 1,900 calories burned and under 150 active minutes, while Highly Active days average over 2,700 calories burned and more than 300 active minutes.
*   **All-or-Nothing Activity Distribution:** Users are mostly either very active or not active at all, with very few "average" days in between. "Highly Active" is the most common daily level, making up 36% of all tracked days, followed by "Sedentary" days at 26%.
*   **Consistent Daily Output (Weekend vs. Weekday):** Users have the same activity habits every day, proving they do not just save their workouts for the weekends. Average step counts stay very steady (about 8,400 on weekdays and 8,300 on weekends), and total active time stays right around 250 minutes no matter the day.
*   **The 10,000 Step Tipping Point:** The data shows a clear positive correlation where taking more steps and staying active longer burns more calories. Reaching the "Highly Active" level (over 10,000 steps) reliably pushes burned calories well above 2,500 for the day.
*   **Mid-Week Peaks & Weekend Slumps:** Users are most active in the middle of the week, with Highly Active days peaking at 66 on Wednesdays. Motivation drops at the end of the week, with completely Sedentary days spiking on Fridays (51 days) and reaching a high of 57 days on Sundays.

## Marketing Recommendations

*   **Send Reminders on Fridays and Sundays:** Because users are most inactive on these specific days (sedentary days peak at 51 on Fridays and 57 on Sundays), Bellabeat should send targeted notifications or mini challenges to motivate users when they usually skip workouts.
*   **Reward Hitting 10,000 Steps:** Reaching the 10,000-step mark is the proven tipping point for burning over 2,500 calories a day. The Bellabeat app should use milestone badges and rewards to encourage average users to push just a little harder to cross this daily goal.
*   **Focus on Everyday Habits:** Data proves users do not save their workouts for the weekend, maintaining a steady ~8,400 daily steps. Marketing campaigns should stop focusing on intense "weekend warrior" workouts and instead promote building consistent, healthy daily routines.
