**Standardaufbau**
```sqlite
select Feldname(n)
from Tabellenname
where Filteranweisungen(just table name or table name with function)
order by (Sortieranweisung)
```

Vergleichsoperationen : <, >, =, !=, is null, is not null

Kommentieren mit --

Platzhalter(wildcard) : '%'


```sqlite
substring(string(fieldname), position, number of characters)

where fieldname in ('  ', '  ');

where fieldname between 2000 and 3000;

select *, strftime('%Y', L_Gebdat) as GebJahr --Spalten hinzufügen 

strftime('%Y-%m-%d', 1) -- Achtung, nur Y ist Großbuchstabe.

Difference in days: junlianday(arrival) - julianday(departure)

instr : select instr('SQLite', 'L') position; --3
advanced: instr(S_Hausnummer,'/')=0``` -- Hausnummer, after the /. (wo keine Stiege eingegeben ist.)
```
