 # CASE statement # 

### Simple case expression 
```sqlite
CASE case_expression
WHEN when_expression_1 THEN result_1
WHEN when_expression_2 THEN result_2
...
[ ELSE result_else ]
END
```

### Examples

--Verringere allen Lehrern, die keine Klassenvorstände sind, das Gehalt um 5% 

-- und erhöhe es für die Lehrer, die Klassenvorstände sind, dafür um 50 Euro.

--Felder: Lehrername, Klasse, Gehalt_alt, Gehalt_neu
```sqlite
SELECT  L_Name, k_nr, L_Gehalt,   
CASE 
    WHEN K_Nr is not null THEN L_Gehalt + 50
    ELSE L_Gehalt * 0.95
END AS neuesGehalt
FROM Lehrer l
LEFT JOIN Klasse k on (l.L_Nr = k.K_Vorstand);
```

```sqlite
SELECT report_code, year, month, day, wind_speed,
CASE
    WHEN wind_speed >= 40 THEN 'HIGH'
    WHEN wind_speed >= 30 AND wind_speend < 40 THEN 'MODERATE'
    ELSE 'Low'
END AS wind_severity
FROM station_data
LIMIT 10;
```
```sqlite
SELECT year, month,
round(SUM(CASE WHEN tornado = 1 THEN precipitation ELSE 0 END), 2) AS tornado_precipitation
round(SUM(CASE WHEN tornado = 0 THEN coalesce(precipitation, 0) ELSE 0 END), 2) AS no_tornado_precipitation 
FROM station_data
GROUP BY year, month;
-- round(x,y) : y ~ A number indicating up to how many decimal places N will be rounded.
```

