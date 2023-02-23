*** Replacing NULL value ***

```oracle
SELECT NAME,
			 HOUSES,
			 CATEGORY
FROM   OH_OWNERSHIP B
			 INNER JOIN
			 OH_OWENERSHIP A
			 ON COALESCE(B.HOUSES, -1) = COALESCE(A.NUMBEROF, -1);
```

<img src="D:\HTL\DBI\MIP\6BKIF\griesmayer\NULL_9.png" width="400"/>