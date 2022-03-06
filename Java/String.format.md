#String.format

 
***JEDES % braucht einen Parameter*** 

**%s ... String**

**%d ... int, long**

**%f ... double, float**               

Beispiel: 

%5.2f ... double/float 5 Stellen Rechtsbündig mit 2 Nachkommenstellen.

###LINKS BÜNDIG mit Minus
Ausgabe: |x  ||10  ||3,14  |--

```java
System.out.println(String.format("|%-5s||%-8d||%-10.2f|", "x", 10, 3.14));
```


###RECHTS BÜNDIG ohne Minus
Ausgabe: |  x||  10||  3,14|--

```java
System.out.println(String.format"|%5s||%8d||%10.2f|", "x", 10, 3.14));
```
