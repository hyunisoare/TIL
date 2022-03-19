#correlated Subselect with and without alias

Beispiele:
HIF-Klassen mit schülern gesamt, männl und weibl Schülern

```SQLITE
-- without alias...it counts ALL male students. 
SELECT  K_Nr, count(S_Nr) as SchuelerGesamt,(
	select count(S_Nr) from Schueler s2 
	inner join Klasse k2 on (s2.S_Klasse=k2.K_Nr) 
	where s2.S_Geschlecht=1) as maennl
FROM Klasse k 
INNER JOIN Schueler s ON (k.K_Nr = s.S_Klasse)
WHERE k.K_Nr like '%HIF%'
GROUP BY K_Nr;
```

<img src="D:\HTL\DBI\without_alias.PNG" width="400"/>

```sqlite
-- with alias...it counts ONLY the students from HIF, like the outer query.
SELECT  K_Nr, count(S_Nr) as SchuelerGesamt,(
	select count(S_Nr) from Schueler s2 
	inner join Klasse k2 on (s2.S_Klasse=k2.K_Nr) 
	where s2.S_Geschlecht=1 and s2.S_Klasse=s.S_Klasse) as maennl
FROM Klasse k 
INNER JOIN Schueler s ON (k.K_Nr = s.S_Klasse)
WHERE k.K_Nr like '%HIF%'
GROUP BY K_Nr;
```

<img src="D:\HTL\DBI\with_alias.PNG" width="400"/>