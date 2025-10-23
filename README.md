# Team 1 – MIST 4610 Group Project 1

## Team Name
Group 1

## Team Members
1. Tejas Lingamaneni
2. Megan Chen
3. Dillan Mangabhai
4. Ceci Motley
5. Jeb Salter

## Problem Description
This project models a fictional college football conference database that manages the operations of the **United Collegiate Conference (UCC)**. The UCC is an entirely imaginary athletic league created for the purpose of this database project.

Each team in the conference competes across multiple seasons, maintains player rosters, employs coaching staff, and plays scheduled games in home stadiums. The database stores key football operations information, including:

- Teams and divisions within the conference

- Players and seasonal rosters

- Coaching staff assignments

- Games and schedules

- Player performance statistics

The goal of this database is to accurately represent these relationships using a relational data model while enforcing referential integrity with foreign keys. This structure will allow meaningful SQL queries to be performed, such as analyzing team performance, tracking player development, and comparing statistics across seasons.

Although the world of the UCC is fictional, all entities and relationships reflect realistic college football operations.

## Data Model 
Our model is based on the structure of a collegiate football database designed to manage teams, players, coaches, and games across multiple seasons. The overall goal of this model is to track all essential components of a football program while maintaining historical accuracy from season to season. The entities within this database interact to represent how teams, coaches, and players relate to one another over time.

At the top level of the model, the Conference and Division entities organize teams by league hierarchy. Each conference is composed of many divisions, and each division contains multiple teams, which is represented by the one-to-many relationship between Conference → Division and Division → Team. The Team entity holds information such as team name, school name, city, state, stadium, and division membership. Because each team belongs to one division but may play in many games and seasons, Team serves as a key relational hub in the model.

The Coach and Coach_Assignment tables work together to show how coaches are assigned to specific teams and seasons. The Coach table holds static information about each coach, including their name and specialty. The Coach_Assignment table captures dynamic relationships — when a coach is employed by a specific team during a particular season and in what role (e.g., Head Coach, Offensive Coordinator, Defensive Coordinator). This design allows the same coach to appear in multiple seasons or change teams without duplicating personal information.

Within Coach_Assignment, a recursive one-to-many relationship has been created to show the coaching hierarchy within each team and season. Each Offensive Coordinator, Defensive Coordinator, and Assistant Coach contains a head_coach_id field that references the Head Coach of the same team and season. This relationship is labeled “Head Coach” and represents which head coach supervises each subordinate coach. This recursive relationship provides organizational structure and enables advanced reporting, such as identifying staff under each head coach.

Players and their participation across teams and seasons are modeled through the Player, Roster, and Player_Game_Stats entities. The Player table contains biographical and physical information for each athlete, including position and hometown. However, because players may transfer teams, redshirt, or leave mid-season, their connection to a team cannot be stored solely within the Player or Team tables. To address this, the Roster table acts as an associative entity that connects Player, Team, and Season.

A unique idroster identifier was added as the primary key for this table, rather than using the combination of Season ID and Team ID. This decision allows for greater flexibility, ensuring that players who transfer or leave mid-season can still be tracked accurately. For example, if a player begins the season on one team and later joins another, both roster entries can coexist without violating primary key constraints. This approach preserves historical integrity and prevents data conflicts when a player’s affiliation changes during the same season.

Each player’s performance is captured through the Player_Game_Stats table, which records detailed statistics for every game a player participates in. This table includes metrics such as passing yards, rushing attempts, tackles, and touchdowns. It is connected to both the Player table and the Game table, representing a many-to-one relationship from Player_Game_Stats to both Player and Game.

The Game entity records each football matchup, including the home and away teams, final scores, attendance, and stadium location. Because each game occurs within a specific season, there is a one-to-many relationship between Season and Game. Additionally, both Home Team and Away Team are foreign keys referencing the same Team table, allowing each matchup to be represented accurately while maintaining referential integrity.

The Season table defines each football year and is referenced by multiple entities including Game, Roster, and Coach_Assignment, ensuring that all seasonal data is properly grouped. The Stadium entity stores information about the venues in which games are played, including capacity and location. Each stadium can host many teams and games, establishing a one-to-many relationship with both Team and Game.

Lastly, the Position entity categorizes players by role (such as Quarterback, Linebacker, or Wide Receiver). Each player is assigned exactly one position, creating a one-to-many relationship between Position and Player.

<img width="1739" height="1359" alt="UnitedConference" src="https://github.com/user-attachments/assets/5ff4776c-3c2a-492d-b411-d406206b58a9" />

## Data Dictionary 

## Queries 

## Database Information
 
