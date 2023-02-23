***not equal sign***
!= <> ^=
all has same function, but <> is the standard. 

```oracle
SELECT * FROM OH_OWNERSHIP WHERE HOUSE<>0 -- this returns where the value is not 0. 


-- If I want to get all the values inclusive null value then,

SELECT * FROM OH_OWNERSHIP WHERE HOUSE<>0
UNION
SELECT * FROM OH_OWNERSHIP WHERE HOUSE=0
UNION
SELECT * FROM OH_OWNERSHIP WHERE HOUSE IS NULL;
```