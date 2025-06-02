## 📊 Summary

This project analyzes **PlayStation player data (2008–2025)** using **Tableau dashboards** and **Python notebooks**. Specifically, it explores:

- Basic demographics of players  
- Retention patterns by cohort  
- Player engagement levels based on trophy data  

The central question for PlayStation Platform Analytics is:  
**“Who is playing what, and how much are they playing?”**  
To answer this question, Trophy counts are used as a proxy for engagement in this project.

---

## 📁 Datasets Used

- **achievements** – Trophies available in each game  
- **games** – Game metadata (title, publisher, genre, etc.)  
- **history** – Player activity records from 2008–2025 (~46K players)  
- **players** – PlayStation user data (~356K users)  
- **prices** – Historical game prices in 5 currencies (updated every 2 days since Feb 22, 2025)  
- **purchased_games** – Games purchased per user  
- **player_achievement_cluster_details** – Engineered dataset detailing player trophy counts by genre and rarity, plus K-means clustering results  

---

## 🔍 Clustering Analysis

To answer "Who’s playing what by how much?", I applied **K-means clustering** to group players based on their trophy activity by genre and rarity. Since direct interaction logs are unavailable, **trophy data serves as a proxy** for engagement.

Trophies (especially rare ones) reflect time and effort invested in gameplay. Players who earn more trophies are likely more engaged.

---

### 🧾 Data Overview

Merged data from `history`, `achievements`, and `games` to create a player-trophy history table.  
**Key columns:**

- `playerid` – Unique player ID  
- `achievementid` – Unique trophy ID  
- `gameid` – Unique game ID  
- `rarity` – Trophy rarity: Bronze, Silver, Gold, Platinum  
- `genres` – List of genres associated with each game  

---

### 🛠️ Data Preparation

#### 1. Genre Grouping  
Games have multiple genres, leading to 530+ unique genre combinations. To simplify:

- Extracted basic genre tags  
- Created a new `genre_group` column with 9 high-level categories  
  (`Action & Combat`, `Sports & Racing`, etc.)

#### 2. Genre + Rarity Breakdown  
Created **36 columns** for each genre-rarity combo (4 rarities × 9 genre groups), and **9 columns** for total trophies per genre.  
Result: a wide-format player-feature matrix for clustering.  

![Genre-Rarity Distribution](https://github.com/sputnik-h/Tableau-PlayStation-Player-Analysis/blob/main/images/genre_rarity_distribution.png)

#### 3. K-means Clustering  
Used the **elbow method** to determine the optimal number of clusters (k = 7).  
![Elbow Plot](https://github.com/sputnik-h/Tableau-PlayStation-Player-Analysis/blob/main/images/elbowmethodresults.png)

#### 4. Cluster Result Summary  
Cluster centroids (average trophy count per genre per cluster):  

![Cluster Plot](https://github.com/sputnik-h/Tableau-PlayStation-Player-Analysis/blob/main/images/clusteringplot.png)

---

# 🎮 Cluster Analysis of Player Trophies by Genre

From the K-means clustering results, we identified **7 distinct player clusters** based on the total number of trophies earned in each genre. Below is an interpretation of each cluster, ordered by the number of players within each group:

---

## 1. Cluster 0 – Casual Players  
**Size:** 770 players  

- These players show low engagement across all genres.  
- Their trophy activity is concentrated in **Action & Combat**, **Strategy & Simulation**, and **Thematic & Narrative**, though the counts remain significantly lower than other clusters.  
- Likely to be casual users or newer players who haven't explored many games or genres extensively.

---

## 2. Cluster 4 – Moderately Engaged Players  
**Size:** 376 players  

- Similar genre preferences to Cluster 0, but with noticeably higher engagement across most categories.  
- Shows increased interest in **Arcade & Classics**, suggesting deeper genre exploration beyond just mainstream titles.

---

## 3. Cluster 2 – Niche Genre Explorers  
**Size:** 94 players  

- Builds upon the activity patterns seen in Cluster 4, but with even greater engagement across **smaller or niche genres**.  
- Particularly more involved in **Arcade & Classics** and **Puzzle & Educational**, suggesting a willingness to experiment beyond traditional action/strategy genres.

---

## 4. Cluster 5 – Social Gamers  
**Size:** 80 players  

- Comparable overall engagement to Cluster 4, but stands out for significantly higher activity in **Online & Multiplayer** titles.  
- Also shows stronger performance in **Action & Combat**, which aligns with popular multiplayer formats—both competitive and cooperative.  
- Likely represents players who enjoy shared gaming experiences and community-driven play.

---

## 5. Clusters 6, 1, and 3 – Hardcore Gamers  
**Combined Size:** 23 players (17 + 5 + 1)  

- These three clusters feature players with **exceptionally high trophy counts** across nearly all genres.  
- **Cluster 6** represents general hardcore gamers with consistent high engagement in mainstream categories.  
- **Cluster 1** shows extreme specialization in **Action & Combat** and **Sports & Racing**, suggesting a taste for fast-paced, adrenaline-fueled games.  
- **Cluster 3**, though it contains only one player, demonstrates unparalleled activity in **Thematic & Narrative** and **Puzzle & Educational**, possibly indicating a completionist or RPG enthusiast. However, due to its size, this cluster provides limited generalizable insight.  
- Overall, these players are highly engaged, likely completionists, genre experts, or long-term enthusiasts.

---

## 🧠 Summary

The clustering analysis reveals a spectrum of player types—from casual participants to niche explorers and hardcore completionists. This segmentation can inform personalized engagement strategies, game recommendations, and community initiatives tailored to each player type’s behavior and preferences. Notably:

- **Clusters 0–2** represent the bulk of the user base, offering opportunities for onboarding, progression nudges, or retention efforts.  
- **Clusters 4–5** indicate mid-core users ready for tailored challenges or social features.  
- **Clusters 6, 1, and 3** consist of highly valuable users whose play patterns can inspire community content, elite reward systems, or ambassador programs.

---

### 🧠 Insights Summary

This clustering reveals a spectrum from **casual players to hardcore completionists**, useful for personalization and engagement strategy.

- **Clusters 0–2:** Large, casual base. Target for onboarding & retention.  
- **Clusters 4–5:** Mid-core players. Ideal for social features or challenges.  
- **Clusters 6, 1, 3:** Power users. Consider elite rewards or community roles.

---

## 📈 Visualization Dashboards

### 🎯 Part 1: Player Demographics  
![Demographics](https://github.com/sputnik-h/Tableau-PlayStation-Player-Analysis/blob/main/images/demographics.png)

- 🌍 Geographic distribution of players  
- 🕹️ Top countries by games owned and achievements completed  
- 🎮 Most played game per country  

---

### 🔄 Part 2: Retention Analysis  
![Retention](https://github.com/sputnik-h/Tableau-PlayStation-Player-Analysis/blob/main/images/retention.png)

- 📈 Monthly Active Users based on achievements  
- ⌛ Total engagement time per cohort  
- 🔁 Retention rate heatmaps  
- 📊 Cohort engagement trends over time  

---

### 👤 Part 3: Individual Player Activity  
![Individual Activity](https://github.com/sputnik-h/Tableau-PlayStation-Player-Analysis/blob/main/images/ind_activity.png)

- Timeline view of monthly activity per player  
- Identify long-term engagement patterns  
- Spot dormant vs. active players  

---

### 👥 Part 4: Engagement Clustering  
![Engagement Clustering](https://github.com/sputnik-h/Tableau-PlayStation-Player-Analysis/blob/main/images/engagement%20clustering.png)

- 🌍 Geographic distribution of players  
- 🎯 Player segmentation based on clustering results  
- 📈 Identify long-term engagement patterns  
- 🔍 Drill down to each genre and rarity level  
