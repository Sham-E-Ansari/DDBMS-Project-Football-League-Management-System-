# DDBMS-Project-Football-League-Management-System-
Football is very much popular among the football lovers across the world. Our project is to make database for Football League Management System. In this database there are many information related to this football league system such as player details, team details, match information etc. All this information must be managed in an efficient and cost wise fashion so that the resources may be effectively utilized. Our objective is to use distributed database to manage the system to make it more efficient and error free.

In our Football league database management systems, we have created a database which is distributed in two sites and there is a host server. We have successfully setup the database link between server and site. In the site part, we’ve put all our tables and fragmented them in two sites. We have inserted a handsome amount of data in every table. From server pc we can access all of them as we have linked the database. To access data, we used some functions and procedures. We also created a package where we can access the functions and procedures altogether. We made two operator trees. Again we created a database profile and triggers after update and insert or delete operation and we also showed a semi-join operation.
Database Link:
In database link there are two parts, host and site. First we need to switch off firewall in both host and site computer. Then check the connection by IP address ping. Some slight changes are done on the listener of the site computer as per instructions. Then the cmd prompt is run in administration to see if the listener is working successfully. The host will create a database link and access the tables of the site computer.


Database Tables (Global Schema):  
stadium (stadium_name, city, capacity) 
coach (coach_id,nationality, coach_name) 
team (team_id, team_name,coach_id, stadium_name)  
team_stats(team_id,season,position) 
referee (ref_id, ref_name, nationality) 
time_slot(time_slot_id,start_time)
player (player_id,player_name, nationality, weight, height, date_of_birth, player_position, team_id)
player_stats (player_id, p_season, apps, goals, assists, own_goals, yellow_card, red_card)
matchplay (match_id, score, stadium_name, ref_id, home_team_id, away_team_id)
match_details (match_id, home_pos, away_pos, home_goals, away_goals, home_fouls, away_fouls)
schedules (match_id, time_slot_id, paly_date)
fouls (player_id, team_id, match_id, foul_time, card_type)
goals (player_id, team_id, match_id, goal_time)
point_table (point_table_id, apps, wins, draw, loses, points)

Fragmentation Schema:
coach1 = SL nationality = 'Spanish' PJ coach_id,nationality, coach_name (coach)
coach2 = SL nationality != 'Spanish' PJ coach_id,nationality, coach_name (coach)
player1 = SL team_id = 4 PJ player_id,player_name, nationality, weight, height, date_of_birth, player_position, team_id (player)
player2= SL team_id =15 PJ player_id,player_name, nationality, weight, height, date_of_birth, player_position, team_id (player)
refree1 = SL nationality = 'Spanish' PJ ref_id, ref_name, nationality (refree)
refree2 = SL nationality != 'Spanish' PJ ref_id, ref_name, nationality (refree)
stadiun1 = SL capacity >= 50000 PJ stadium_name, city, capacity (stadium)
stadiun2 = SL capacity < 50000 PJ stadium_name, city, capacity (stadium)
team1 = PJ team_id, team_name, coach_id, city (team JN stadium_name = stadium_name stadium1)
team2 = PJ team_id, stadium_name, capacity (team JN stadium_name = stadium_name stadium1)
Functions and Procedures:
In our project we have created 7 functions and procedures to perform different tasks. In what purpose we use which functions and procedures are given below.
Procedures:
1.	Displays the performance of the given team name : findTeamStat(tname)
2.	Displays list of coaches and their team name by  given nationality: coach_pro(c_nation)
3.	Displays the name of the player by given team name and player position : player_pro(pla_pos,tname2)
4.	Displays the upcoming matches next to the given date: up_pro(p_date)
Functions:
1.	Displays total goal of the given player: totalGoals(pname)

2.	Displays given team’s corresponding stadium: stad_func(t_name)

3.	Displays the top scorer:  topGoalScorer()


Database Package:
We have created a database package where we have put all the functions and procedures together and can display them altogether. There are three parts. First, we declared the functions and procedures altogether, then there is another body where we described the functions and procedures and finally we call them from a different sql, which works as a main function.
