# Esport-Analysis-1998-2021

From the originals datasets I create some SQL querys in order to filter the information that I want the best way Possible

[Here's the querys I made](https://console.cloud.google.com/bigquery?sq=341570980120:b81a6622d2f0414491b7b12e184d17ec)

````
--CHECK THE TABLE STRUCTURE
SELECT *
FROM `esports-367514.Esports.GeneralEsportData` 
````
````
--TOP 10 Games with the highest Earnings 
SELECT Game, TotalEarnings
FROM `esports-367514.Esports.GeneralEsportData` 
ORDER BY TotalEarnings DESC
LIMIT 10 
````
````
--TOP 10 Games with the highest Tournaments Count
SELECT Game, TotalTournaments
FROM `esports-367514.Esports.GeneralEsportData`  
ORDER BY TotalTournaments DESC
LIMIT 10 
````
````
--Genres with the highest earnings all time
SELECT Genre, SUM(TotalEarnings) AS Total_Earnings, SUM(TotalPlayers) AS Total_Players, SUM(TotalTournaments) AS Total_Tournaments
FROM `esports-367514.Esports.GeneralEsportData` 
GROUP BY Genre 
ORDER BY SUM(TotalEarnings) DESC
````
````
--FOR COMPARISON IN BI
SELECT Game, TotalEarnings, TotalPlayers,TotalTournaments
FROM `esports-367514.Esports.GeneralEsportData` 
ORDER BY TotalEarnings DESC
LIMIT 50 
````
````
--Total of tournaments per year
SELECT EXTRACT(year from Date) AS Year, SUM(Tournaments) AS Tournaments,SUM(Players) AS Players, SUM(Earnings) AS Earnings
FROM `esports-367514.Esports.HistoricalEsportData`
GROUP BY year 
ORDER BY Year DESC
````

After export all the tables I uploaded to Tableau Public to do a Dashboard were I can visualice relevant Data about the Dataset

[1998-2021 Esports Analysis Tableau Dashboard](https://public.tableau.com/app/profile/carlos1863/viz/1998-2021EsportsAnalysis/Dashboard1)
<div class='tableauPlaceholder' id='viz1667778500795' style='position: relative'><noscript><a href='#'><img alt='Dashboard 1 ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;19&#47;1998-2021EsportsAnalysis&#47;Dashboard1&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='embed_code_version' value='3' /> <param name='site_root' value='' /><param name='name' value='1998-2021EsportsAnalysis&#47;Dashboard1' /><param name='tabs' value='no' /><param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;19&#47;1998-2021EsportsAnalysis&#47;Dashboard1&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='en-US' /></object></div>     
The insights we can get from this datasets are:

1. The game with the highest earnings of all times is Dota 2
2. Counter Strike Global Offensive is the game with more competitive playes 
3. The genre with the highest recaudation in all time is the MOBA
4. 2020 was the year with the highest earnings
