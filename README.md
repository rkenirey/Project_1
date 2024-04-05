# Team 5 Mist 4610 Group Project 1

# Team Name:
21479 Group 5

# Team Members
1. Rebecca Kenirey @rkenirey
2. Jonathan Adeyemo @JonathanTheDon
3. Doyin Adeyemo @doyinadeyemo
4. Abby Low @abbylow1
5. Rayan Merchant @rayanmerchant

# Problem Description:
The task for this project is to model and build a relational database as the governing soccer federation. In the data model, there are various entities representing the Clubs, their teams, facilities, staff, Sponsorships, finances, and partnerships. The Teams table will be connected with the information about the members on the team, the facilities, the individual matches, etc. The goal is to model the various relationships between the teams, their attributes, and the matches they play under the soccer federation. We also create queries that showcase the records that can be accessed by the soccer federation for their day-to-day operations.

# Data Model
## Explaination of data model:
The provided data model is designed to manage and store information for a soccer club. At the core of this model is the Club entity, which captures essential details about the club itself, such as its name, year of establishment, and a mission statement that defines its purpose and goals. Around this core, the Facility entity records the different locations associated with the club, delineating each facility's type—whether it's for administrative use, training, or match play—and its capacity. This allows for detailed tracking of the club's physical assets. The Team entity outlines the various soccer teams within the club, linked to the Club by a foreign key. Each team has attributes like age group and an association to a specific coach from the Staff entity. Staff details the individuals working for the club, not just limited to coaching personnel, but also including a diverse range of roles and qualifications, indicative of the club's operational depth. Around this core, the Facility entity records the different locations associated with the club, delineating each facility's type—whether it's for administrative use, training, or match play—and its capacity. This allows for detailed tracking of the club's physical assets. The Team entity outlines the various soccer teams within the club, linked to the Club by a foreign key. Each team has attributes like age group and an association to a specific coach from the Staff entity. Staff details the individuals working for the club, not just limited to coaching personnel, but also including a diverse range of roles and qualifications, indicative of the club's operational depth. Players are the heart of any club; in this model, they are associated with teams. Their personal information, positions, and team affiliations are tracked meticulously. The MatchDay table holds data about individual matches, including dates, locations, and results. This table is central to understanding the club's performance in competitions. It connects to Teams through the MatchTeam junction table, which handles the many-to-many relationship between teams and the matches they play, since each match involves two teams. The TrainingSession entity captures when and where each team trains, the focus of these sessions, and their duration—critical data for managing a team's preparation and performance. To handle the financial aspects, the Finance entity records transactions, classified into income or expenses, offering a snapshot of the club's financial health and aiding in fiscal planning. Sponsor documents the businesses or individuals financially supporting the club, with attributes detailing the nature of sponsorship and contract terms. This is linked to the Club through the ClubSponsor junction table to account for the possibility of multiple sponsors for a club and vice versa. Lastly, the Event entity stores information on various events held by the club, potentially at the facilities they own, enhancing the club's community engagement and outreach efforts. In essence, our data model showcases a Soccer Federation detailing the relationships between clubs, players, staff, facilities, equipment, finances, partnership, and matches.

<img width="469" alt="image" src="https://github.com/rkenirey/Project_1/assets/143122583/db29cfde-da08-40b9-b754-f310a3f2e7a8">

# Data Dictionary:
<img width="855" alt="Screenshot 2024-04-04 at 10 54 04 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/faa2beec-311c-4da0-bcf0-7ed3c519fdf9">
<img width="845" alt="Screenshot 2024-04-04 at 10 54 28 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/09fc99f0-e1b2-4b66-9664-38e9e3a2d19e">
<img width="835" alt="Screenshot 2024-04-04 at 10 54 54 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/bb4f0cd4-8726-4e33-b03d-8aed05c8eb18">
<img width="841" alt="Screenshot 2024-04-04 at 10 55 28 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/0a8e15b9-a887-4ac3-bf5b-bca59d02d48c">
<img width="852" alt="Screenshot 2024-04-04 at 10 57 11 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/66c9ec7e-325b-48d4-893d-255b32c37a8e">
<img width="841" alt="Screenshot 2024-04-04 at 10 57 43 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/8dce1a87-34ca-4f7f-8567-99235fca3429">
<img width="836" alt="Screenshot 2024-04-04 at 10 59 58 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/ff1c99e4-35ea-43a9-bf8a-1ba5e6dfbb0c">
<img width="840" alt="Screenshot 2024-04-04 at 11 00 53 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/ab67cadb-769b-44d9-b21e-c1577434d2cd">
<img width="835" alt="Screenshot 2024-04-04 at 11 01 42 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/95636b1e-04c6-4df9-a0cd-53dac87c7357">
<img width="842" alt="Screenshot 2024-04-04 at 11 02 36 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/e889fc07-5561-4f94-bcd4-d78e9c8a7efc">

# Relationships of Entities
<img width="328" alt="Screenshot 2024-04-04 at 11 33 37 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/9eca2d16-5edc-49f3-8492-1520a9ecba4c">

# Forward Engineering Tables
CREATE TABLE Club(
ClubID int,
Name VARCHAR(45),
YearOfEstablishment YEAR,
Primary key(ClubID)
);


CREATE TABLE Facility(
FacilityID INT,
Name VARCHAR(45),
Location VARCHAR(45),
TrainingType VARCHAR(45),
Capacity VARCHAR(45),
TeamID INT,
PRIMARY KEY(FacilityID),
Constraint club_has_facility foreign key(TeamID) references Team(TeamID)
);


CREATE TABLE Team(
	TeamID INT,
    Name VARCHAR(45),
    AgeGroup INT,
    ClubID int,
    PRIMARY KEY(TeamID),
	Constraint club_has_team FOREIGN KEY (ClubID) References Club(ClubID)
);



CREATE TABLE Players(
	PlayerID INT,
    Name VARCHAR(45),
    DateOfBirth DATE,
    Nationality VARCHAR(45),
    JoinDate DATE,
    ContractLength VARCHAR(45),
    TeamID INT,
    ClubID INT,
    PRIMARY KEY(PlayerID),
	Constraint fk_has_players FOREIGN KEY (TeamID) References Team(TeamID),
	constraint club_key FOREIGN KEY (ClubID) REFERENCES Club(ClubID));



CREATE TABLE Staff(
	StaffID INT,
    Name VARCHAR(45),
    Roll VARCHAR(45),
    Qualifications VARCHAR(45),
    SupervisorID INT,
    PRIMARY KEY(StaffID),
    CONSTRAINT staff_has_supervisor foreign key(SupervisorID) references Staff(StaffID)
);


CREATE TABLE MatchDay(
	MatchID INT,
    MatchDate DATE,
    Location VARCHAR(45),
    Result VARCHAR(45),
    Opponent VARCHAR(45),
    PRIMARY KEY(MatchID)
);



CREATE TABLE League(
	LeagueID INT,
    Name VARCHAR(45),
    Level VARCHAR(45),
    Season VARCHAR(45),
    PRIMARY KEY(LeagueID)
);



CREATE TABLE Equipment(
	EquipmentID INT,
    Type VARCHAR(45),
    Quality VARCHAR(45),
    ConditionState VARCHAR(45),
    PRIMARY KEY(EquipmentID)
);

CREATE TABLE Partnership(
	PartnershipID INT,
    PartnerName VARCHAR(45),
    ClubType VARCHAR(45),
    StartDate VARCHAR(45),
    EndDate VARCHAR(45),
    PRIMARY KEY(PartnershipID)
);

CREATE TABLE Finance(
	FinanceID INT,
    IncomeType VARCHAR(45),
    Amount INT,
    Date VARCHAR(45),
    Description VARCHAR(45),
    PRIMARY KEY(FinanceID)
);

CREATE TABLE TrainingSession(
	SessionID INT,
    Date DATE,
    FocusArea VARCHAR(45),
    Duration VARCHAR(45),
    PRIMARY KEY(SessionID)
);

CREATE TABLE Sponsor(
	SponsorID INT,
    Name VARCHAR(45),
    Industry VARCHAR(45),
    ContractStartDate DATE,
    ContractEndDate DATE,
    PRIMARY KEY(SponsorID)
);

CREATE TABLE Event(
	EventID INT,
    Name VARCHAR(45),
    Date VARCHAR(45),
    Location VARCHAR(45),
    CampType VARCHAR(45),
    PRIMARY KEY(EventID)
);

CREATE TABLE ClubSponsor(
ClubID int,
SponsorID INT,
Constraint club_sponsor_key1 Foreign KEY(ClubID) references Club(ClubID),
Constraint club_sponsor_key2 Foreign KEY(SponsorID) references Sponsor(SponsorID)
);

CREATE TABLE MatchTeam(
MatchID int,
TeamID INT,
ClubID int,
Constraint match_team_key1 Foreign KEY(ClubID) references Club(ClubID),
Constraint match_team_key2 Foreign KEY(TeamID) references Team(TeamID),
Constraint match_team_key3 Foreign KEY(MatchID) references MatchDay(MatchID)
);

CREATE TABLE TeamLeague(
LeagueID int,
TeamID INT,
ClubID int,
Constraint team_league_key1 Foreign KEY(ClubID) references Club(ClubID),
Constraint team_league_key2 Foreign KEY(TeamID) references Team(TeamID),
Constraint team_league_key3 Foreign KEY(LeagueID) references League(LeagueID)
);

CREATE TABLE TeamStaff(
StaffID int,
TeamID INT,
ClubID int,
Constraint team_staff_key1 Foreign KEY(ClubID) references Club(ClubID),
Constraint team_staff_key2 Foreign KEY(TeamID) references Team(TeamID),
Constraint team_staff_key3 Foreign KEY(StaffID) references Staff(StaffID)
);

CREATE TABLE TeamEquipment(
EquipmentID int,
TeamID INT,
ClubID int,
Constraint team_eq_key1 Foreign KEY(ClubID) references Club(ClubID),
Constraint team_eq_key2 Foreign KEY(TeamID) references Team(TeamID),
Constraint team_eq_key3 Foreign KEY(EquipmentID) references Equipment(EquipmentID)
);

CREATE TABLE FacilityEvent(
FacilityID int,
EventID INT,
ClubID int,
Constraint fac_ev_key1 Foreign KEY(ClubID) references Club(ClubID),
Constraint fac_ev_key2 Foreign KEY(FacilityID) references Facility(FacilityID),
Constraint fac_ev_key3 Foreign KEY(EventID) references Event(EventID)
);

# Query Check Box
<img width="975" alt="Screenshot 2024-04-04 at 11 30 06 PM" src="https://github.com/rkenirey/Project_1/assets/143122583/9680c804-bee1-4526-9306-ca5f8855234c">

# Queries

1. Query 1: List all players who have never played a match.
<img width="363" alt="image" src="https://github.com/rkenirey/Project_1/assets/143122583/fb5d6c88-0773-4e44-a960-f988c7558ca4">

Justification: Query 1 gives a list of all players who have never played a match. This is important when it comes to keeping individual records for players. This also allows the federation to check if certain players qualify to receive medals if their clubs win trophies.


2. Query 2: Identify teams that have never lost a match.
<img width="468" alt="image" src="https://github.com/rkenirey/Project_1/assets/143122583/ebff7aad-63a4-4a28-8df8-fead49c63214">

Justification: Query 2 lists teams that have never lost a match. This allows the federation to keep track of team records mainly to track the list of unbeaten teams. This could also be useful for historical records.


3. Query 3: Identify staff who have never managed a team with a losing match.
<img width="388" alt="image" src="https://github.com/rkenirey/Project_1/assets/143122583/fff868f8-b0fd-4081-aa83-b22bcac1b38b">

Justification: Query 3 lists out managers who have never coached a team with a losing record. This is used to draw information from historical records to highlight the prowess of the coach. This can also be used by other clubs in search of a new coach.

4. Query 4: List all current players attributes.
<img width="468" alt="image" src="https://github.com/rkenirey/Project_1/assets/143122583/7f6ef3b0-d8ee-474a-a358-3157a61178c7">

Justification: Query 4 will retrieve the number of players and get a view of their information such as name, date of birth and nationality. This allows the federation to keep track of players information and easily access them.


5. Query 5: lists the number of players in each age group. 
<img width="383" alt="image" src="https://github.com/rkenirey/Project_1/assets/143122583/a6457652-a6f4-4861-aae8-44ad72ed3f69">

Justification: Query 5 This allows clubs and the federation to keep track of the players on various teams across age groups. This is useful when it comes to roster planning and financial planning.


6. Query 6: List all sponsors whose contracts are due to expire by the end of the current year.
<img width="468" alt="image" src="https://github.com/rkenirey/Project_1/assets/143122583/60b29f54-1e2d-451a-bf8b-66f507513a79">

Justification: Query 6 provides a list of sponsors whose contracts expire at the end of the year. This allows clubs to access and keep track of contract information. This is necessary for club because it makes planning for future sponsorships easier.


7. Query 7: The average number of events per facility type for each club. 
<img width="468" alt="image" src="https://github.com/rkenirey/Project_1/assets/143122583/dd3f1993-4ee8-41fc-8573-b382b8869240">

Justification: Query 7 lists the amount of events for each facility type at each club. This is useful because it allows each club to keep track of event records and it also helps with future scheduling of events. This also allows the club to be more effective in facility maintenance.


8. Query 8: Clubs that have played more than five games.
<img width="468" alt="image" src="https://github.com/rkenirey/Project_1/assets/143122583/1ddba58c-7ad3-48be-99a4-c601154a341e">

Justification: Query 8 lists the clubs(regardless of age group) that has played more than five games in the season.  This is necessary to keep track of league standings and inform of teams that have games in standing that they are yet to play.![image](https://github.com/rkenirey/Project_1/assets/143122583/298bdc48-5d44-47ea-8b5a-d9ae011350da)

9. Query 9: Retrieve the names of facilities where training type is “average”.
<img width="468" alt="image" src="https://github.com/rkenirey/Project_1/assets/143122583/3512bc63-2cd3-4f76-826f-0d48d579c445">

Justification: This query selects the names of facilities from the Facility table where the training type column matches the value 'average'. It filters the results to only include facilities with the specified training type.


10. Query 10: Retrieve the names of facilities with the 75% capacity for each training type. 
<img width="468" alt="image" src="https://github.com/rkenirey/Project_1/assets/143122583/d7e61093-06f4-4aef-8b75-0328269e6e1d">

Justification: This query retrieves the names of facilities with 75% capacity for each training type by first finding 75% capacity for each training type. Then, it joins back to the Facility table to get the facility names with the maximum capacities for each training type, ordering the results by training type.
