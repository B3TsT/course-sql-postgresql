# PostgeSQL Exercises 
## -> Fundamentals

## SQL Lesson 1: SELECT queries
```
- SELECT * FROM "esquema"."PERSONAS"

    | PER   | NOMBRE | APELLIDO1 | APELLIDO2 | DNI | EDAD | DEP |
    | ----- | ------ | --------- | --------- | --- | ---- | --- |
    | Row 1 | Cell 2 | Cell 3    | ...       | ... | ...  | ... |

- SELECT "NOMBRE", "APELLIDO1" FROM "esquema"."PERSONAS"

    | NOMBRE | APELLIDO1 |
    | ------ | --------- |
    | Cell 2 | Cell 3    |

- SELECT * FROM "esquema"."PRODUCTOS"
- SELECT * FROM "esquema"."PEDIDOS"
- SELECT "PER", "NOMBRE", "DNI" FROM "esquema"."PERSONAS"

```

  - ### EJERCICIO
    Consulta los datos de las columnas PRODUCTO y PRECIO de la tabla PRODUCTOS
    ```
    - SELECT "PRODUCTO", "PRECIO" FROM "esquema"."PRODUCTOS"

        | PRODUCTO | PRECIO |
        | -------- | ------ |
        | ...      | ...    |
    ```

## SQL Lesson 2: DISTINCT queries

```
- SELECT * FROM "esquema"."PERSONAS"

    | NOMBRE  |
    | ------- |
    | ANTONIO |
    | LUIS    |
    | PEDRO   |
    | ANTONIO |

- SELECT DISTINCT("NOMBRE") FROM "esquema"."PERSONAS"

    | NOMBRE  |
    | ------- |
    | ANTONIO |
    | LUIS    |
    | PEDRO   |
```
 <!-- <table style="margin-left: 38px;">
    <thead>
        <tr>
            <th>NOMBRE</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td align="center">ANTONIO</td>
        </tr>
        <tr>
            <td align="center">LUIS</td>
        </tr>
        <tr>
            <td align="center">PEDRO</td>
        </tr>
    </tbody>
</table> -->

  - ### EJERCICIO
    Seleccionar los distintos productos de la tabla PEDIDOS
    ```
    - SELECT DISTINCT "PRODUCTO" FROM "esquema"."PRODUCTOS"

        | PRODUCTO  |
        | --------- |
        | IMPRESORA |
        | RATON     |
        | ORDENADOR |
        | TECLADO   |
    ```

## SQL Lesson 3: COUNT querie

```
- SELECT "PRODUCTO" FROM "esquema"."PRODUCTOS"

    | PRODUCTO  |
    | --------- |
    | IMPRESORA |
    | RATON     |
    | ORDENADOR |
    | TECLADO   |

- SELECT COUNT(*) FROM "esquema"."PRODUCTOS"

    | NOMBRE |
    | ------ |
    | 4      |
```

## SQL Lesson 4: WHERE queries
```
- SELECT * FROM "esquema"."PERSONAS" WHERE "EDAD" >= 40
- SELECT * FROM "esquema"."PERSONAS" WHERE "NOMBRE" = 'ANTONIO' AND "EDAD" > 30
```

## SQL Lesson 5: ORDER BY queries
```
- SELECT * FROM "esquema"."PERSONAS" ORDER BY "EDAD" DESC
- SELECT * FROM "esquema"."PERSONAS" ORDER BY "NOMBRE", "EDAD" ASC
- SELECT * FROM "esquema"."PERSONAS" ORDER BY "NOMBRE" DESC , "EDAD" ASC
```

## SQL Lesson 6: LIMIT queries
```
- SELECT count(*) FROM "esquema"."PERSONAS" -> result 4
- SELECT * FROM "esquema"."PERSONAS" LIMIT 3
```

## SQL Lesson 7: BETWEEN queries
```
- SELECT * FROM "esquema"."PEDIDOS"
- SELECT * FROM "esquema"."PEDIDOS" WHERE "IMPORTE" BETWEEN 100 and 200
- SELECT * FROM "esquema"."PEDIDOS" WHERE "FECHA" BETWEEN '2020-08-02' AND '2020-08-04'
- SELECT * FROM "esquema"."PEDIDOS" WHERE "FECHA" NOT BETWEEN '2020-08-02' AND '2020-08-04'
```

## SQL Lesson 8: IN queries
```
- SELECT * FROM "esquema"."PRODUCTOS" WHERE "PRODUCTO" IN ('ORDENADOR', 'IMPRESORA', 'TECLADO')
- SELECT * FROM "esquema"."PRODUCTOS" WHERE "PRODUCTO" NOT IN ('ORDENADOR', 'IMPRESORA', 'TECLADO')
- SELECT * FROM "esquema"."PRODUCTOS" WHERE "PRECIO" IN (10, 50)
```

## SQL Lesson 9: LIKE queries
```
- SELECT * FROM "esquema"."PERSONAS" WHERE "NOMBRE" LIKE 'A%'
- SELECT * FROM "esquema"."PERSONAS" WHERE "NOMBRE" ILIKE '_NT%'
```

## -> Data Grouping

## SQL Lesson 10: GROUP BY
```
- SELECT "PRODUCTO", SUM("IMPORTE") FROM "esquema"."PEDIDOS" GROUP BY "PRODUCTO"
```

## SQL Lesson 10: HAVING
```
- SELECT "PRODUCTO", SUM("IMPORTE") FROM "esquema"."PEDIDOS" GROUP BY "PRODUCTO" HAVING SUM("IMPORTE") > 200
```

## -> Table Joins

## SQL Lesson 10: AS
```
- SELECT "PRODUCTO", SUM("IMPORTE") AS "TOTAL" FROM "esquema"."PEDIDOS" GROUP BY "PRODUCTO" HAVING SUM("IMPORTE") > 200
```

## SQL Lesson 11: INNER JOIN
```
- SELECT "NOMBRE", "DEPARTAMENTO" FROM "esquema"."PERSONAS" 
    INNER JOIN "esquema"."DEPARTAMENTOS" 
    ON "esquema"."PERSONAS"."DEP" = "esquema"."DEPARTAMENTOS"."DEP"
```
## SQL Lesson 12: FULL JOIN
```
- SELECT "NOMBRE", "APELLIDO1", "DEPARTAMENTO" FROM "esquema"."PERSONAS" 
    FULL JOIN "esquema"."DEPARTAMENTOS" 
    ON "esquema"."PERSONAS"."DEP" = "esquema"."DEPARTAMENTOS"."DEP"
```

## SQL Lesson 13: LEFT JOIN
```
- SELECT "NOMBRE", "APELLIDO1", "DEPARTAMENTO" FROM "esquema"."PERSONAS" 
    LEFT JOIN "esquema"."DEPARTAMENTOS" 
    ON "esquema"."PERSONAS"."DEP" = "esquema"."DEPARTAMENTOS"."DEP"
```

## SQL Lesson 14: RIGHT JOIN
```
- SELECT "NOMBRE", "APELLIDO1", "DEPARTAMENTO" FROM "esquema"."PERSONAS" 
    RIGHT JOIN "esquema"."DEPARTAMENTOS" 
    ON "esquema"."PERSONAS"."DEP" = "esquema"."DEPARTAMENTOS"."DEP"
```

## SQL Lesson 15: UNION JOIN
```
- SELECT "PRODUCTO", "IMPORTE" FROM "esquema"."PEDIDOS" 
    WHERE "IMPORTE" > 200
- SELECT "PRODUCTO", "IMPORTE" FROM "esquema"."PEDIDOS" 
    WHERE "PRODUCTO" = 'RATON'
    
<!-- UNION -->
- SELECT "PRODUCTO", "IMPORTE" FROM "esquema"."PEDIDOS" 
    WHERE "IMPORTE" > 200
  UNION
  SELECT "PRODUCTO", "IMPORTE" FROM "esquema"."PEDIDOS" 
    WHERE "PRODUCTO" = 'RATON'
```

## -> Advanced Features

## SQL Lesson 16: DATE and TIME
https://www.postgresql.org/docs/current/functions-formatting.html
```
- SELECT NOW()
- SELECT TIMEOFDAY()
- SELECT TIMEOFDAY()
- SELECT CURRENT_TIME
- SELECT CURRENT_DATE

- SELECT EXTRACT(DAY FROM "FECHA") AS DIA,
  EXTRACT(MONTH FROM "FECHA") AS MES,
  EXTRACT(YEAR FROM "FECHA") AS AÑO,
  EXTRACT(QUARTER FROM "FECHA") AS QUARTER
  FROM "esquema"."PEDIDOS"

- SELECT AGE("FECHA") AS "ANTIGUEDAD"
  FROM "esquema"."PEDIDOS"

- SELECT to_char(current_timestamp, 'HH:MM:SS')
  FROM "esquema"."PEDIDOS"

- SELECT to_char(current_timestamp, 'DD:MM:YYYY')
  FROM "esquema"."PEDIDOS"

- SELECT to_char("FECHA", 'DD:MM:YYYY')
  FROM "esquema"."PEDIDOS"
```

## SQL Lesson 17: MATH FUNCTIONS
https://www.postgresql.org/docs/current/functions-math.html
```
- SELECT "IMPORTE", "CANTIDAD", "IMPORTE" / "CANTIDAD" AS "Precio unitario" 
  FROM "esquema"."PEDIDOS" 
```

## SQL Lesson 18: STRING FUNCTIONS
https://www.postgresql.org/docs/current/functions-string.html
```
- SELECT "NOMBRE", LENGTH("NOMBRE") AS "Longitud"
  From "esquema"."PERSONAS"
-SELECT "NOMBRE", LOWER("NOMBRE") AS "Minuscula"
  From "esquema"."PERSONAS"
- SELECT "NOMBRE", LEFT("NOMBRE", 3) AS "Nom"
  From "esquema"."PERSONAS"
- SELECT "NOMBRE" || ' ' || "APELLIDO1" AS "Nombre completo"
  From "esquema"."PERSONAS"
```

## SQL Lesson 19: SUBQUERY WITH NUMERIC VALUE
```
- SELECT AVG("IMPORTE") From "esquema"."PEDIDOS"

- SELECT "PRODUCTO", "IMPORTE", "FECHA" FROM "esquema"."PEDIDOS"
  WHERE "IMPORTE" > (SELECT AVG("IMPORTE") From "esquema"."PEDIDOS")
```

## SQL Lesson 20: SUBQUERY WITH LIST VALUE
```
- SELECT "DEP", "DEPARTAMENTO" FROM "esquema"."DEPARTAMENTOS"
  WHERE "DEP" IN (SELECT "DEP" From "esquema"."PERSONAS" WHERE "EDAD" > 30)
```

## SQL Lesson 21: SUBQUERY WITH EXISTS
```
- SELECT "NOMBRE", "APELLIDO1","DEP"
  FROM "esquema"."PERSONAS" AS P
  WHERE EXISTS
  (SELECT * FROM "esquema"."DEPARTAMENTOS" AS D
  WHERE D."DEP" = P."DEP")

- SELECT "NOMBRE", "APELLIDO1","DEP"
  FROM "esquema"."PERSONAS" AS P
  WHERE NOT EXISTS
  (SELECT * FROM "esquema"."DEPARTAMENTOS" AS D
  WHERE D."DEP" = P."DEP")
```

## SQL Lesson 22: JOIN A TABLE ONTO ITSELF
```
<!--SELECT T1."PRODUCTO", T2."PRODUCTO", T1."IMPORTE" -->

- SELECT *
  FROM "esquema"."PEDIDOS" AS T1
  INNER JOIN "esquema"."PEDIDOS" AS T2
  ON (T1."ID" != T2."ID") AND (T1."IMPORTE" = T2."IMPORTE")
```