# database-boilerplate
database

sentencia para copiar archivo a contenedor de postgres
docker cp dataset.csv postgres_container:/docker-entrypoint-initdb.d/dataset.csv


tablas y sentencias para pasarlos de csv a base de datos.

create table canciones (
index int,
track_id text,
artists text,
album_name text,
track_name text,
popularity text,
duration_ms text,
explicit text ,
danceability text,
energy text,
key text,
loudness text,
mode text,
speechiness text,
acousticness text,
instrumentalness text,
liveness text,
valence text,
tempo text,
time_signature text,
track_genre text
)

select * from canciones;
drop table canciones;

copy canciones 
from '/docker-entrypoint-initdb.d/dataset.csv'
with (
	format csv,
	header true
);
