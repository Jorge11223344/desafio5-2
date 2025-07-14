# database-boilerplate
database

sentencia para copiar archivo a contenedor de postgres
docker cp dataset.csv postgres_container:/docker-entrypoint-initdb.d/dataset.csv

CREATE TABLE IF NOT EXISTS INSCRITOS(cantidad INT, fecha DATE, fuente
VARCHAR);

INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 44, '01/01/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 56, '01/01/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 39, '01/02/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 81, '01/02/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 12, '01/03/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 91, '01/03/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 48, '01/04/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 45, '01/04/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 55, '01/05/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 33, '01/05/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 18, '01/06/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 12, '01/06/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 34, '01/07/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 24, '01/07/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 83, '01/08/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 99, '01/08/2021', 'Página' );

select * from INSCRITOS;

--¿Cuantos registros hay?
SELECT COUNT(*) FROM INSCRITOS;

--¿Cuantos inscritos hay?
SELECT SUM(cantidad) FROM INSCRITOS;

--¿Cual o cuales son los registros de mayor antiguedad?

select fecha, cantidad
from inscritos
where fecha = (select min(fecha)
from inscritos);

--¿Cuantos inscritos hay por día?
SELECT fecha, SUM(cantidad) as inscritos_diarios
FROM INSCRITOS 
GROUP BY fecha 
ORDER BY fecha asc;

--¿Que dia se inscribieron la mayor cantidad de personas y cuatas personas se inscribieron ese dia?
SELECT fecha, SUM(cantidad) AS total_Inscritos_por_dia 
FROM INSCRITOS 
GROUP BY fecha 
ORDER BY total_Inscritos_por_dia DESC 
LIMIT 1;
