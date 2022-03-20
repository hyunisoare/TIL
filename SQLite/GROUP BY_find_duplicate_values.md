#GROUP BY :: find duplicate values 

Beispiel:Geben Sie die letzte Stunde der 3BAIF für jeden Wochentag aus. 
***Achtung: wenn 2 Lehrer in einer Klasse die letzte Studn machen, werden 2 datensätz geliefert***

--Spalten: StKlass, St_tag, st_Stunde, stGEgenstnd, st_lehrer

```sql
select St_Klasse, St_tag, (
select max(St_Stunde) from Stunde s1
where st_Klasse like '3BAIF' and s1.St_Tag=s.St_Tag
) as maxStd,
st_Stunde, st_Gegenstand, st_lehrer
from Stunde s
where s.St_Klasse = '3BAIF' and St_Stunde = maxStd
group by St_Tag;
```
<img src="D:\HTL\DBI\groupby1.PNG" width="400"/>

it shows only one each values which grouped by day.  

```sql
select St_Klasse, St_tag, (
select max(St_Stunde) from Stunde s1
where st_Klasse like '3BAIF' and s1.St_Tag=s.St_Tag
) as maxStd,
st_Stunde, st_Gegenstand, st_lehrer
from Stunde s
where s.St_Klasse = '3BAIF' and St_Stunde = maxStd
group by St_Tag, St_Lehrer;
```
<img src="D:\HTL\DBI\groupby.PNG" width="400"/>

With 2 properties for GROUP BY, it shows duplicate values for each day. 