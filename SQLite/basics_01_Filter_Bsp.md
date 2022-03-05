**Übungen mit SchulDB** 
```squlite
 --Lehrer mit Sprechstunde am Montag, sortiert nach Lehrerkürzel
   -- Ver.1 mit wildcard
   SELECT L_Nr, L_Sprechstunde FROM Lehrer where L_Sprechstunde like '%MO%';
   -- Ver.2 mit substring
   SELECT L_Nr, L_Sprechstunde FROM Lehrer where SUBSTRING(L_Sprechstunde, 1, 2) like 'MO';

   --Welche Lehrer haben keine Sprechstunde eingetragen
   SELECT L_Nr, L_Sprechstunde from Lehrer where L_Sprechstunde is null;

   --Welche Klassen gehören zur Abteilung KIF
   SELECT K_Nr from Klasse k where K_Nr like '%KIF%';

   --Welche Klassen enden vor dem Schuljahresende (haben Inhalt in K_Datumbis)
   SELECT K_Nr, K_Datumbis  from Klasse k where K_Datumbis is not null ;

   --Welche Klassen sind Fachschulklassen (enthalten FIT)
   SELECT K_Nr from Klasse k where K_Nr like '%FIT%';

   --Welche Klassen gehören zum 1.Jahrgang
   -- Ver. 1 mit wildcard
   select K_Nr from Klasse k where K_Nr like '1%';
   -- Ver. 2 mit substring
   select K_Nr from Klasse k where substring(k_nr, 1,1) like 1;

   --Welche Klassen hat GT als KV
   select * from Klasse k  where K_Vorstand like 'GT';

   --Welche Schuljahre beginnen im Jahr 2019
   select * from Schuljahr s where  STRFTIME('%Y', Sja_Datumvon) like 2019 ;

   --Wie lange duern die verschiedenen Schuljahre
   select *,JULIANDAY(Sja_Datumbis)-JULIANDAY(Sja_Datumvon) as Dauer, * from Schuljahr s where Dauer > 200;

   --Welche Schüler besuchen HBG, Ausgabe sortiert nach Alphabet
   select S_Zuname,S_Klasse  from Schueler s where S_Klasse like '%HBG%' order by S_Klasse  asc;

   --Welche Schüler der Abteilung HIF heißen Michael
   select s_vorname, S_Klasse from Schueler s where S_Vorname like 'Michael' AND s_klasse like '%HIF%';
   select * from Schueler;
   --Welche Schüler wohnen an einem Weg in den Bezirken 2,12,21,22 oder 23
   select S_Zuname, S_Postleitzahl  from Schueler s where S_Postleitzahl in (1020, 1120, 1210, 1220, 1230);

   --Welche Schüler wohnen nicht in Wien und sind vor 1993 geboren
   select S_Zuname, S_Gebdatum  from Schueler s where STRFTIME('%Y', S_Gebdatum) < 1993 ;
   select s_gebdatum from Schueler s ;

   --Welche Schüler wohnen in Bezirken an 2er-Linie
   select S_Zuname, s_postleitzahl from Schueler s where S_Postleitzahl in (1020);

   --Was bedeutet die Bedingung s_geschlecht = mnoth(s_gebdatum)
   select s_geschlecht, s_gebdatum from Schueler s where S_Geschlecht = STRFTIME('%m', S_Gebdatum);

   --was bedeutet die Bedingung Where instr(S_Hausnummer,'/')=0
   select S_Strasse ,S_hausnummer from  Schueler s where instr(S_Hausnummer, '/') = 0 ;
   select s_hausnummer from Schueler s ;

   select S_strasse from Schueler s where instr(S_Strasse, '-') = 0;

```
  
