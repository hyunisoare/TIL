```sqlite
--****Übungen mit SchulDB: Inner Joins**** --

-- In welcher Abteilung ist Pramel der AV. Felder: Abteilungsname, Anz: 5
select Abt_Name as Anz from Abteilung a inner join Lehrer l on (Abt_Leiter = L_Nr) where L_Name like 'Pramel';

-- In welchen Klassen sind Schüler aus den Bezirken 21 und 22. Filder: K_Nr, K_jahrsem, anzu 95
select K_Nr k, K_Schuljahr k from Klasse inner join Schueler s on (K_Nr = S_Klasse) where S_Postleitzahl in (1210, 1220);
select DISTINCT  K_Nr k, K_Schuljahr k from Klasse inner join Schueler s on (K_Nr = S_Klasse) where S_Postleitzahl in (1210, 1220);
-- mit distinct, Anz : 60

-- Gib alle Klassen mit dem Namen der Abteilung aus. Felder: K_Nr, Abteilungsname, Anz: 116
select K_Nr, Abt_Name as Abteilungsname from Klasse inner join Abteilung on (K_Abteilung = Abt_Nr);
select K_Nr, K_Abteilung  as Abteilungsname from Klasse;
-- Ver2. ohne inner join 

-- Gib alle Abteilungen mit Name und Prüfungsfächer des AV aus. Felder: Abt_Name, L_Name, p_Gegenstand, Anzahl: 8
select DISTINCT Abt_Name, L_Name, P_Gegenstand from Abteilung 
	inner join Lehrer l  on (L_Nr  = Abt_Leiter)
	inner join Pruefung p on (L_Nr = p.P_Pruefer);
	
-- Welche Schüler haben ein evangelisches Religionsbekenntnis? Anz: 0
select * from Schueler s inner join Religion r on (S_Religion = r.Rel_ID) where S_Religion like '%evang%';

-- Gib alle Klassen mit dem Namen des AV aus. Felder: KNr, L_Name. Anz: 115
select K_Nr, L_Name from Klasse k 
	inner join Abteilung a on (a.Abt_Nr = k.K_Abteilung)
	INNER join Lehrer l on (a.Abt_Leiter  = l.L_Nr);
	

-- Gib alle Schülerinnen (nur weibl) mit Namen des KV aus, falls dieser an einem Montag Sprechstunde hat. S_Zuname, L_name; Anz 157
select S_Zuname, L_name  from Schueler s 
	left join Klasse k on (S_Klasse = K_Nr)  
	LEFT join Lehrer on (L_Nr = K_Vorstand) where L_Sprechstunde like 'MO%' and S_Geschlecht like 2;

-- Gib alle Klassen mit dem Namen des KV und des AV aus 
select K_Nr, l.L_Name as KV, l2.L_Name as AV from Klasse k
	inner join Lehrer l on (K_Vorstand = l.L_Nr) 
	inner join Abteilung a on (k.K_Abteilung = a.Abt_Nr)
	inner join Lehrer l2 on (l2.L_Nr = a.Abt_Leiter) ;

-- Gib alle Klassen aus, dazu das Beginndatum und Enddatum. 
--Falls dieses in der Klasse leer ist, verwende den Wert aus dem Schuljahr.
--Felder: K_bez, Enddatum, Anz: 116
select K_Bez , COALESCE (K_Datumvon, Sja_datumvon), COALESCE (K_Datumbis, Sja_datumbis) 
from klasse inner join Schuljahr on (K_Schuljahr = Sja_Nr);

-- Gib zu den Abteilungen aus, in welchen Schuljahren sie Klassen haben. Felder: abt_name, sja_bez; Anz: 116
select Abt_Name, Sja_bezeichnung from Abteilung a 
	inner join Klasse k on (Abt_Nr = K_Abteilung) 
	inner JOIN  Schuljahr s  on (Sja_Nr = K_Schuljahr);
select * from Schuljahr s ;

-- Gib für jeden Schüler aus, wie viele Tage er/sie am Ende des jeweiligen Klassenbesuches alt ist
-- Felder: S_Zuname, AlterinTagen
select S_Zuname, JULIANDAY(Sja_Datumbis)-JULIANDAY(Sja_datumvon) as AlterinTagen from Schueler s 
	left join Klasse k  on (K_Nr = S_Klasse) 
		left join Schuljahr s2 on (K_Schuljahr = Sja_Nr);
	
-- Gibt es Fälle, wo Schüler und Lehrer den gleichen Vornamen haben?
--Felder: S_Zuname, S_Vorname, L_Name, Anz: 200
select S_Zuname, S_Vorname , L_Vorname  from Schueler s 
	left  join Klasse on (S_Klasse = K_Nr) 
	LEFT join Lehrer on (L_Nr = K_Vorstand) where S_Vorname = L_Vorname;
```