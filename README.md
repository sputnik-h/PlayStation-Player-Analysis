[Click Here](https://public.tableau.com/app/profile/yixuan.liu2688/viz/PlayStationPlayerAnalytics/Dashboard2) to view on Tableau.

---

## Summary

This project analyzes PlayStation Player data starting from 2008 with Tableau dashboards and Python notebook. More specifcally, the project looks at the basic demographics of the players, track their retention vased on their cohort and how engaged a playe they are, and answering the central question for PlayStation Platform Analytics, Who is playing what by how much, by using player trophy count as an proxy as their engagement measures.

---

## Dataset Used

- **achievements** – achievements available in each game  
- **games** – a list of games with general information (title, publisher, genre, etc.)  
- **history** – user gaming activity for 2008–2025 (46k userID)  
- **players** – a list of PlayStation users (356k userID)  
- **prices** – price history for each game in 5 different currencies, starting from 22-02-2025 (updated every 2 days)  
- **purchased_games** – a list of games purchased by each user
- **player_achievement_cluster_details** – genreated with Python transformation and clustering, detailing player's trophy's count by genre and rarity, along with cluster assigned by K-means Clustering algorithm

---
## Visualization Part
### Part 1  
![Alt text](https://github.com/sputnik-h/Tableau-PlayStation-Player-Analysis/blob/main/images/demographics.png)  
This Tableau dashboard titled **"PlayStation Player Demographics"** visualizes global player behavior and engagement across three key dimensions.

1. **PlayStation Player Geographical Distribution** (Top Map)  
   Visualizes where players are located globally.

2. **Top 10 Countries by Median Number of Games Owned** (Bottom Left)  
   Highlights countries where players tend to own the most games.

3. **Most Played Game in Selected Country** (Bottom Center)  
   Displays the most popular game based on player activity in the selected country.

4. **Top 10 Countries by Median Number of Achievements Completed** (Bottom Right)  
   Highlights countries where players are most engaged in completing in-game achievements.

#### Overall Takeaway  
This dashboard enables interactive exploration of where the most engaged, invested, and active PlayStation players are, based on:

---

### Part 2  
![Alt text](https://github.com/sputnik-h/Tableau-PlayStation-Player-Analysis/blob/main/images/retention.png)  
This Tableau dashboard titled **"Retention Analysis"** visualizes PlayStation player engagement and retention trends across different time periods and player cohorts.

1. **Monthly Active Users (MAU) Recorded with Achievements** (Top Left)  
   Tracks the trend of active players over time, based on achievement activity.

2. **Cohort Total Engagement Time** (Top Middle)  
   Measures total playtime (or total achievement interaction time) by cohort (based on first achievement date).

3. **Average Engagement Level Across Cohort** (Top Right)  
   Shows how consistently each cohort remains active on a month-to-month basis.

4. **Cohort Retention Analysis Heatmap** (Bottom)  
   Tracks what percentage of players in each cohort remain active in subsequent quarters.

---

### Part 3  
![Alt text](https://github.com/sputnik-h/Tableau-PlayStation-Player-Analysis/blob/main/images/ind_activity.png)  
This Tableau dashboard titled **"Individual Player Activity"** visualizes long-term engagement patterns of PlayStation users on a per-player basis.
