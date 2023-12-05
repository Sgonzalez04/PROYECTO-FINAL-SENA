# PROYECTO-FINAL-SENA
## SENA_PROYECTO
### Sergio Alejandro Gonzalez Silva
### GRUPO R4
***
#### MODELO ENTIDAD RELACION
![modelo_entidad_relacion](Diagrama_entidad_relacion_SENA.png)
***
#### MODELO RELACIONAL
![Modelo Relacional](Modelo_relacional_SENA.png)
***
#### Creacion base de datos:
~~~sql
    CREATE DATABASE proyecto_sena;
~~~
***
#### Ingreso a la base de datos:
~~~sql
    USE proyecto_sena;
~~~
***
#### Creacion de las tablas:
~~~sql
  CREATE TABLE Carrera (
      id_carrera BIGINT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
      nom_carrera VARCHAR(100) NOT NULL
  );
  
  CREATE TABLE Curso (
      id_Curso INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
      nom_curso VARCHAR(100) NOT NULL
  );
  
  CREATE TABLE Instructor (
      id_instructor INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
      nom_instructor VARCHAR(100) NOT NULL,
      especialidad VARCHAR(255) NOT NULL
  );
  
  CREATE TABLE Aprendiz (
      id_Aprendiz BIGINT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
      nom_aprendiz VARCHAR(100) NOT NULL
  );
  
  CREATE TABLE RutaDeAprendizaje (
      id_ruta_aprendizaje BIGINT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
      id_carrera BIGINT UNSIGNED NOT NULL,
      nom_ruta_aprendizaje VARCHAR(100) NOT NULL,
      titulo VARCHAR(255) NOT NULL,
      id_aprendiz BIGINT UNSIGNED NOT NULL,
      FOREIGN KEY (id_carrera) REFERENCES Carrera(id_carrera),
      FOREIGN KEY (id_aprendiz) REFERENCES Aprendiz(id_Aprendiz)
  );
  
  CREATE TABLE Contiene (
      id_ruta_aprendizaje BIGINT UNSIGNED NOT NULL ,
      id_curso INT UNSIGNED NOT NULL,
      PRIMARY KEY (id_ruta_aprendizaje, id_curso),
      FOREIGN KEY (id_ruta_aprendizaje) REFERENCES RutaDeAprendizaje(id_ruta_aprendizaje),
      FOREIGN KEY (id_curso) REFERENCES Curso(id_Curso)
  );
  
  CREATE TABLE Dicta (
      id_curso INT UNSIGNED NOT NULL,
      id_instructor INT UNSIGNED NOT NULL,
      PRIMARY KEY (id_curso, id_instructor),
      FOREIGN KEY (id_curso) REFERENCES Curso(id_Curso),
      FOREIGN KEY (id_instructor) REFERENCES Instructor(id_instructor)
  );
~~~
#### Poblar la base de datos:
    ~~~sql
    --Cursos
    INSERT INTO Curso (id_Curso, nom_curso)
    VALUES
    (1, 'Matemáticas Básicas'),
    (2, 'Álgebra Computacional'),
    (3, 'Programación Básica'),
    (4, 'Inglés'),
    (5, 'Electrónica Básica'),
    (6, 'Motor de Cuatro Tiempos'),
    (7, 'Enfermedades Laborales'),
    (8, 'Higiene Postural en el Trabajo'),
    (9, 'Ergonomía'),
    (10, 'Legislación Laboral en Colombia'),
    (11, 'Materiales de Soldadura'),
    (12, 'Métodos de Soldadura'),
    (13, 'Fusión de Metales'),
    (14, 'Buceo 1'),
    (15, 'Buceo 2'),
    (16, 'Riesgo Eléctrico'),
    (17, 'Bases de Datos Relacionales'),
    (18, 'Bases de Datos NO Relacionales'),
    (19, 'Electrónica Digital'),
    (20, 'Microprocesadores');
    
    --Instructores
    INSERT INTO Instructor (id_instructor, nom_instructor, especialidad)
    VALUES
    (1, 'Ricardo Vicente Jaimes', 'Sistemas'),
    (2, 'Marinela Narvaez', 'Salud Ocupacional'),
    (3, 'Agustín Parra Granados', 'Soldadura'),
    (4, 'Nelson Raúl Buitrago', 'Mecánica'),
    (5, 'Roy Hernando Llamas', 'Inglés'),
    (6, 'Maria Jimena Monsalve', 'Electrónica'),
    (7, 'Juan Carlos Cobos', 'Electrónica'),
    (8, 'Pedro Nell Santamaría', 'Sistemas'),
    (9, 'Andrea González', 'Sistemas'),
    (10, 'Marisela Sevilla', 'Salud Ocupacional');
    
    --Carreras
    INSERT INTO Carrera (id_carrera, nom_carrera)
    VALUES
    (1, 'Desarrollo de Software'),
    (2, 'Electrónica'),
    (3, 'Mecánica Automotriz'),
    (4, 'Seguridad y Salud Ocupacional'),
    (5, 'Soldadura');
    
    --aprendiz
    INSERT INTO Aprendiz (nom_aprendiz)
    VALUES
    ('Carlos Saúl Gómez'),
    ('Leyla María Delgado Vargas'),
    ('Juan José Cardona'),
    ('Sergio Augusto Contreras Navas'),
    ('Ana María Velázquez Parra'),
    ('Gustavo Noriega Alzate'),
    ('Pedro Nell Gómez Díaz'),
    ('Jairo Augusto Castro Camargo'),
    ('Henry Soler Vega'),
    ('Antonio Cañate Cortés'),
    ('Daniel Simancas Junior');
    
    -- RutaDeAprendizaje
    INSERT INTO RutaDeAprendizaje (id_carrera, nom_ruta_aprendizaje, titulo, id_aprendiz)
    VALUES
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Bases de Datos Relacionales', 1),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Álgebra Computacional', 1),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Programación Básica', 1),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Bases de Datos NO Relacionales', 1),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Matemáticas Básicas', 2),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Álgebra Computacional', 2),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Programación Básica', 2),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Inglés', 2),
    (1, 'Videojuegos', 'Tecnólogo en Matemáticas Básicas', 3),
    (1, 'Videojuegos', 'Tecnólogo en Álgebra Computacional', 3),
    (1, 'Videojuegos', 'Tecnólogo en Programación Básica', 3),
    (1, 'Videojuegos', 'Tecnólogo en Inglés', 4),
    (1, 'Videojuegos', 'Tecnólogo en Matemáticas Básicas', 4),
    (1, 'Videojuegos', 'Tecnólogo en Álgebra Computacional', 4),
    (1, 'Machine Learning', 'Tecnólogo en Programación Básica', 5),
    (1, 'Machine Learning', 'Tecnólogo en Inglés', 5),
    (1, 'Machine Learning', 'Tecnólogo en Bases de Datos Relacionales', 5),
    (2, 'Microcontroladores', 'Tecnólogo en Electrónica Básica', 6),
    (2, 'Microcontroladores', 'Tecnólogo en Electrónica Digital', 6),
    (2, 'Microcontroladores', 'Tecnólogo en Microprocesadores', 6),
    (2, 'Microcontroladores', 'Tecnólogo en Electrónica Básica', 7),
    (2, 'Microcontroladores', 'Tecnólogo en Electrónica Digital', 7),
    (2, 'Microcontroladores', 'Tecnólogo en Microprocesadores', 7),
    (2, 'Robótica', 'Tecnólogo en Electrónica Básica', 8),
    (2, 'Robótica', 'Tecnólogo en Electrónica Digital', 8),
    (2, 'Robótica', 'Tecnólogo en Electrónica Básica', 9),
    (2, 'Robótica', 'Tecnólogo en Electrónica Digital', 9),
    (5, 'Soldadura Eléctrica', 'Tecnólogo en Materiales de Soldadura', 10),
    (5, 'Soldadura Eléctrica', 'Tecnólogo en Fusión de Metales', 10),
    (5, 'Soldadura Autógena', 'Tecnólogo en Materiales de Soldadura', 11),
    (5, 'Soldadura Autógena', 'Tecnólogo en Buceo 1', 11);
    
    --Dicta 
    INSERT INTO Dicta (id_curso, id_instructor)
    VALUES
    (1, 1),
    (2, 2),
    (3, 3),
    (4, 5),
    (5, 6),
    (6, 4),
    (7, 2),
    (8, 2),
    (9, 10),
    (10, 10),
    (11, 3),
    (12, 3),
    (13, 3),
    (15, 7),
    (16, 4),
    (17, 1),
    (18, 1),
    (19, 6),
    (20, 6);
    
    INSERT INTO Contiene (id_ruta_aprendizaje, id_curso)
    VALUES
    (1, 17),
    (1, 2),
    (1, 3),
    (1, 18),
    (2, 1),
    (2, 2),
    (2, 3),
    (2, 4),
    (3, 1),
    (3, 2),
    (3, 3),
    (3, 4),
    (4, 1),
    (4, 2),
    (4, 3),
    (4, 4),
    (5, 1),
    (5, 2),
    (5, 3),
    (5, 4),
    (6, 1),
    (6, 2),
    (6, 3),
    (7, 3),
    (7, 4),
    (7, 5),
    (8, 5),
    (8, 19),
    (8, 20),
    (9, 5),
    (9, 19),
    (9, 20),
    (10, 5),
    (10, 19),
    (10, 20),
    (11, 11),
    (11, 13),
    (12, 11),
    (12, 13),
    (13, 11),
    (13, 14),
    (14, 12),
    (14, 15),
    (15, 11),
    (15, 12),
    (15, 13),
    (15, 14);
    ~~~
***
### CONSULTAS
***
#### 1. Agregue un campo Estado_Matrícula a la tabla Matrícula que indique si el estudiante se encuentra “En Ejecución”, “Terminado” o “Cancelado”
    ~~~sql
    ALTER TABLE Matriculas
    ADD COLUMN estado_matricula VARCHAR(24) NOT NULL;

    INSERT INTO Matriculas(estado_matricula)
    VALUES("Activo"),("Cancelado"),("Terminado");

    ALTER TABLE Aprendices
    ADD COLUMN id_matricula INT;

    ALTER TABLE Aprendices
    ADD FOREIGN KEY(id_matricula)
    REFERENCES Matriculas(id_matricula);

    UPDATE Aprendices
    SET id_matricula = 1
    WHERE id_aprendiz IN (1,2,4,5);

    UPDATE Aprendices
    SET id_matricula = 2
    WHERE id_aprendiz IN (3,9);

    UPDATE Aprendices
    SET id_matricula = 3
    WHERE id_aprendiz IN (6,7,8,10,11);
    ~~~
***
#### 2. Agregue a el campo edad a la tabla de Aprendices.
~~~sql
    ALTER TABLE aprendiz
    ADD COLUMN edad INT;
    UPDATE Aprendiz
    SET edad = 20;
~~~
***
#### 3. Si suponemos que los cursos tienen una duración diferente dependiendo de la ruta que lo contenga ¿qué modificación haría a la estructura de datos ya planteada?
#### RESPUESTA:agregar una columna llamada duracion_Curso a la tabla Curso y se toma por numero de semanas.
    ~~~sql
    ALTER TABLE Curso
    ADD COLUMN duracion_curso INT;
    ~~~
***

#### 4.Seleccionar los nombres y edades de aprendices que están cursando la carrera de electrónica.
    ~~~sql
    SELECT A.nom_aprendiz, A.edad
    FROM Aprendiz A
    INNER JOIN Matricula M ON A.id_aprendiz = M.id_aprendiz
    INNER JOIN RutaDeAprendizaje R ON M.id_ruta_aprendizaje = R.id_ruta_aprendizaje
    INNER JOIN Carrera C ON R.id_carrera = C.id_carrera
    WHERE C.nom_carrera = 'Electrónica';
    ~~~
***

#### 5. Seleccionar Nombres de Aprendices junto al nombre de la ruta de aprendizaje que cancelaron.
    ~~~sql
    SELECT A.nom_aprendiz, R.nom_ruta_aprendizaje
    FROM aprendiz A
    INNER JOIN Matricula M ON A.id_aprendiz = M.id_aprendiz
    INNER JOIN RutaDeAprendizaje R ON M.id_ruta_aprendizaje = R.id_ruta_aprendizaje
    WHERE M.Estado_Matricula = 'Cancelado';
    ~~~
***
#### 6. Seleccionar Nombre de los cursos que no tienen un instructor asignado.
    ```sql
    SELECT nom_curso
    FROM Curso
    WHERE id_Curso NOT IN (SELECT id_curso FROM Dicta);
    ~~~
***
#### 7. Seleccionar Nombres de los instructores que dictan cursos en la ruta de aprendizaje “Sistemas de Información Empresariales”.
    ```sql
    SELECT DISTINCT I.nom_instructor
    FROM Dicta D
    JOIN Curso C ON D.id_curso = C.id_Curso
    JOIN Instructor I ON D.id_instructor = I.id_instructor
    JOIN RutaDeAprendizaje R ON C.id_Curso = R.id_ruta_aprendizaje
    WHERE R.nom_ruta_aprendizaje = 'Sistemas de Información Empresariales';
    ~~~
***
#### 8. Genere un listado de todos los aprendices que terminaron una Carrera mostrando el nombre del profesional, el nombre de la carrera y el énfasis de la carrera (Nombre de la Ruta de aprendizaje)
    ```sql
    SELECT A.nom_aprendiz, Carr.nom_carrera, RDA.nom_ruta_aprendizaje
    FROM Aprendiz A
    JOIN Matricula M ON A.id_Aprendiz = M.id_aprendiz
    JOIN RutaDeAprendizaje RDA ON M.id_ruta_aprendizaje = RDA.id_ruta_aprendizaje
    JOIN Carrera Carr ON RDA.id_carrera = Carr.id_carrera
    WHERE M.`Estado_Matricula` = 'Terminado';
    ~~~
***
#### 9.Genere un listado de los aprendices matriculados en el curso “Bases de Datos Relacionales”.
    ```sql
    SELECT A.nom_aprendiz
    FROM Aprendiz A
    JOIN Matricula M ON A.id_Aprendiz = M.id_aprendiz
    JOIN RutaDeAprendizaje RDA ON M.id_ruta_aprendizaje = RDA.id_ruta_aprendizaje
    JOIN Contiene C ON RDA.id_ruta_aprendizaje = C.id_ruta_aprendizaje
    JOIN Curso Cur ON C.id_curso = Cur.id_Curso
    WHERE Cur.nom_curso = 'Bases de Datos Relacionales';
    ~~~
***
#### 10.Nombres de Instructores que no tienen curso asignado.
    ```sql
    SELECT nom_instructor
    FROM Instructor
    WHERE id_instructor NOT IN (SELECT DISTINCT id_instructor FROM Dicta);
    ~~~
***
## Preguntas seleccion multiple
#### Pregunta 1: ¿Qué cláusula SQL se utiliza para combinar filas de dos o más tablas en base a una condición relacionada?
    a) JOIN
    b) UNION
    c) GROUP BY
    d) CONCAT
    Respuesta correcta: a) JOIN
#### Pregunta 2: ¿Cuál es la función de la cláusula ORDER BY en SQL?
    a) Filtrar filas basadas en una condición de agrupación
    b) Ordenar filas en un conjunto de resultados
    c) Filtrar filas basadas en una condición individual
    d) Combinar filas de múltiples tablas
    Respuesta correcta: b) Ordenar filas en un conjunto de resultados
#### Pregunta 3: ¿cuál es la operacion utilizada para combinar múltiples condiciones en una consulta?
    a) OR
    b) XOR
    c) AND
    d) NOT
    Respuesta correcta: c) AND
#### Pregunta 4: ¿Qué tipo de clave se utiliza para identificar de manera única cada fila en una tabla?
    ¿Qué tipo de clave se utiliza para identificar de manera única cada fila en una tabla?
    a) Clave primaria
    b) Clave foránea
    c) Clave externa
    d) Clave única
    Respuesta correcta: a) Clave primaria
***

