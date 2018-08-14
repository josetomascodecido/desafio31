# desafio31

1.	Crear una base de datos llamada call_list

CREATE DATABASE call_list2;

2.	En la base de datos recien creada, crear la tabla users con los campos id (clave primaria), first_name, email.

CREATE TABLE users(id SERIAL PRIMARY KEY, first_name VARCHAR(50), email VARCHAR(25));

3.	Ingresar un usuario, llamado Carlos (el resto de los datos deben inventarlos).
    
INSERT INTO users (first_name, email) VALUES ('Carlos', 'carlos@gmail.com');

4.	Ingresar un usuario, llamada Laura (el resto de los datos deben inventarlos).

INSERT INTO users (first_name, email) VALUES ('Laura', 'laura@gmail.com');

5.	Crear una tabla llamada calls con los campos id (clave primaria), phone, date, user_id (foreign key relacionado a users).

CREATE TABLE calls(id SERIAL PRIMARY KEY, phone VARCHAR(25), date VARCHAR(25), user_id INTEGER REFERENCES users(id));

6.	Agregar a la tabla users el campo last_name.

ALTER TABLE users ADD COLUMN last_name VARCHAR(25);

7.	Ingresar el apellido del usuario Carlos.

UPDATE users SET last_name = 'Farias' WHERE id = 1;

8.	Ingresar el apellido del usuario Laura.

UPDATE users SET last_name = ‘Del rio’ WHERE id = 2;

9.	Ingresar 6 llamadas asociadas al usuario Laura.

INSERT INTO calls (id, phone, date, user_id) VALUES(1, ‘45637326’, ‘11-07’, 2);

10.	Ingresar 4 llamadas asociadas al usuario Carlos.

INSERT INTO calls (id, phone, date, user_id) VALUES(7, ‘45637326’, ‘11-07’, 1);

11.	Crear un nuevo usuario.

INSERT INTO users (id, first_name, email, last_name) VALUES (3, 'Sebastian', 'sebastian@gmail.com', 'Codecido');

12.	Seleccionar la cantidad de llamados de cada uno de los usuarios (nombre de usuario y cantidad de llamadas).

SELECT first_name, COUNT(calls) FROM users INNER JOIN calls on (users.id = calls.user_id)GROUP BY first_name;

13.	Seleccionar los llamados del usuario llamado Carlos ordenados por fecha en orden descendente.

SELECT * FROM calls WHERE user_id = 1 ORDER BY date ASC;

    13.1 Nuevos cambios solicitados por cliente.
    "Necesito agregar a la base una tabla de auditoría que registre el motivo del borrado de una llamada y el usuario que lo        efectuó."
	
  CREATE TABLE auditorias(id SERIAL PRIMARY KEY, descripcion VARCHAR(50), user_id INTEGER REFERENCES users(id));

	



