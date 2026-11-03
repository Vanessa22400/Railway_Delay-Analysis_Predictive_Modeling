## Project at a Glance

![Railway Delay Analysis — analytical dashboard](Images/railway_dashboard_cover.png)

This independent project started with a real commuting problem in Tübingen, Germany. I analyzed **24,760 railway records** to examine punctuality patterns, test operational hypotheses and model critical delay risk.

**Key observations:** 67.6% of services recorded some delay, although the average was only 3.23 minutes. Monday had the highest average weekday delay, and express services were more delayed on average than regional services.

The Random Forest classification study reached **82% overall accuracy**, but only **27% recall for critical delays** (>5 minutes), highlighting the limits of prediction without additional operational context.

### Selected Visualizations

| Weekday patterns | Delay trends |
|---|---|
| ![Mean delays by weekday](Images/weekday_average_delay.png) | ![Monthly average delay](Images/monthly_average_delay.png) |

![Average delay by train category](Images/train_category_average_delay.png)

*All visualizations are generated directly from the cleaned historical dataset in the project notebook. They summarize observed data, not a deployed real-time dashboard.*
