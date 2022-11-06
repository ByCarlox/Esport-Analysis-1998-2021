# Esport-Analysis-1998-2021

From the originals datasets I create some SQL querys in order to filter the information that I want the best way Possible

[Here's the querys I made](https://console.cloud.google.com/bigquery?sq=341570980120:b81a6622d2f0414491b7b12e184d17ec)

'
--CHECK THE TABLE STRUCTURE
SELECT *
FROM `esports-367514.Esports.GeneralEsportData` 


--TOP 10 Games with the highest Earnings 
SELECT Game, TotalEarnings
FROM `esports-367514.Esports.GeneralEsportData` 
ORDER BY TotalEarnings DESC
LIMIT 10 


--TOP 10 Games with the highest Tournaments Count
SELECT Game, TotalTournaments
FROM `esports-367514.Esports.GeneralEsportData`  
ORDER BY TotalTournaments DESC
LIMIT 10 

--Genres with the highest earnings all time
SELECT Genre, SUM(TotalEarnings) AS Total_Earnings, SUM(TotalPlayers) AS Total_Players, SUM(TotalTournaments) AS Total_Tournaments
FROM `esports-367514.Esports.GeneralEsportData` 
GROUP BY Genre 
ORDER BY SUM(TotalEarnings) DESC


--FOR COMPARISON IN BI

SELECT Game, TotalEarnings, TotalPlayers,TotalTournaments
FROM `esports-367514.Esports.GeneralEsportData` 
ORDER BY TotalEarnings DESC
LIMIT 50 


--Total of tournaments per year
SELECT EXTRACT(year from Date) AS Year, SUM(Tournaments) AS Tournaments,SUM(Players) AS Players, SUM(Earnings) AS Earnings
FROM `esports-367514.Esports.HistoricalEsportData`
GROUP BY year 
ORDER BY Year DESC

'
