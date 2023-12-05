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
#### Borrar bases de datos:
~~~sql
    DROP TABLE IF EXISTS Contiene, Dicta, Matricula, RutaDeAprendizaje, Aprendiz, Instructor, Curso, Carrera;
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
    (12, 'Métodos de Solda Soldadura ura'),
    (13, 'Fusión de Metale Soldadura '),
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
    (4, 'Nelson Raúl Buitr Soldadura go', 'Mecánica'),
    (5, 'Roy Hernando Llamas', 'Inglés'),
    (6, 'Maria Jimena Monsalve', 'Electrónica'),
    (7, 'Juan Carlos Cobos', 'Electrónica'),
    (8, 'Pedro Nell Santamaría', 'Sistemas'),
    (9, 'Andrea González', 'Sistemas'),
    (10, 'Marisela Sevilla', 'Salud Ocupacional');
    
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
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Desarrollo de Software con enfasis en Sistemas de Información Empresariales', 1),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Desarrollo de Software con enfasis en Sistemas de Información Empresariales', 1),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Desarrollo de Software con enfasis en Sistemas de Información Empresariales', 1),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Desarrollo de Software con enfasis en Sistemas de Información Empresariales', 1),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Desarrollo de Software con enfasis en Sistemas de Información Empresariales', 2),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Desarrollo de Software con enfasis en Sistemas de Información Empresariales', 2),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Desarrollo de Software con enfasis en Sistemas de Información Empresariales', 2),
    (1, 'Sistemas de Información Empresariales', 'Tecnólogo en Desarrollo de Software con enfasis en Sistemas de Información Empresariales', 2),
    (1, 'Videojuegos', 'Tecnólogo en Desarrollo de Software con enfasis en Videojuegos', 3),
    (1, 'Videojuegos', 'Tecnólogo en Desarrollo de Software con enfasis en Videojuegos', 3),
    (1, 'Videojuegos', 'Tecnólogo en Desarrollo de Software con enfasis en Videojuegos', 3),
    (1, 'Videojuegos', 'Tecnólogo en Desarrollo de Software con enfasis en Videojuegos', 4),
    (1, 'Videojuegos', 'Tecnólogo en Desarrollo de Software con enfasis en Videojuegos', 4),
    (1, 'Videojuegos', 'Tecnólogo en Desarrollo de Software con enfasis en Videojuegos', 4),
    (1, 'Machine Learning', 'Tecnólogo en Desarrollo de Software con enfasis en Machine', 5),
    (1, 'Machine Learning', 'Tecnólogo en Desarrollo de Software con enfasis en Machine', 5),
    (1, 'Machine Learning', 'Tecnólogo en Desarrollo de Software con enfasis en Machine', 5),
    (2, 'Microcontroladores', 'Tecnólogo en Electrónica con enfasis en Microcontroladores', 6),
    (2, 'Microcontroladores', 'Tecnólogo en Electrónica con enfasis en Microcontroladores', 6),
    (2, 'Microcontroladores', 'Tecnólogo en Electrónica con enfasis en Microcontroladores', 6),
    (2, 'Microcontroladores', 'Tecnólogo en Electrónica con enfasis en Microcontroladores', 7),
    (2, 'Microcontroladores', 'Tecnólogo en Electrónica con enfasis en Microcontroladores', 7),
    (2, 'Microcontroladores', 'Tecnólogo en Electrónica con enfasis en Microcontroladores', 7),
    (2, 'Robótica', 'Tecnólogo en Electrónica con enfasis en Robótica', 8),
    (2, 'Robótica', 'Tecnólogo en Electrónica con enfasis en Robótica', 8),
    (2, 'Robótica', 'Tecnólogo en Electrónica con enfasis en Robótica', 9),
    (2, 'Robótica', 'Tecnólogo en Electrónica con enfasis en Robótica', 9),
    (2, 'Robótica', 'Tecnólogo en Electrónica con enfasis en Robótica', 9),
    (5, 'Soldadura Eléctrica', 'Tecnólogo en Soldadura con enfasis en Soldadura Eléctrica', 10),
    (5, 'Soldadura Eléctrica', 'Tecnólogo en Soldadura con enfasis en Soldadura Eléctrica', 10),
    (5, 'Soldadura Autógena', 'Tecnólogo en Soldadura con enfasis en Soldadura Autógena', 11),
    (5, 'Soldadura Autógena', 'Tecnólogo en Soldadura con enfasis en Soldadura Autógena', 11);
    
    --Contiene
    INSERT INTO Contiene (id_ruta_aprendizaje, id_curso)
    VALUES
    (1, 17),
    (2, 2),
    (3, 3),
    (4, 18),
    (5, 1),
    (6, 2),
    (7, 3),
    (8, 4),
    (9, 1),
    (10, 2),
    (11, 3),
    (12, 4),
    (13, 1),
    (14, 2),
    (15, 3),
    (16, 4),
    (17, 17),
    (18, 5),
    (19, 19),
    (20, 20),
    (21, 5),
    (22, 19),
    (23, 20),
    (24, 5),
    (25, 19),
    (26, 5),
    (27, 19),
    (28, 20),
    (29, 11),
    (30, 13),
    (31, 11),
    (32, 14);
    ~~~
***
### CONSULTAS
***
#### 1. Agregue un campo Estado_Matrícula a la tabla Matrícula que indique si el estudiante se encuentra “En Ejecución”, “Terminado” o “Cancelado”
    ~~~sql
       CREATE TABLE Matricula (
        id_matricula INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
        Estado VARCHAR(50) NOT NULL,
        id_aprendiz BIGINT UNSIGNED NOT NULL,
        id_ruta_aprendizaje BIGINT UNSIGNED NOT NULL,
        FOREIGN KEY (id_aprendiz, id_ruta_aprendizaje) REFERENCES RutaDeAprendizaje(id_aprendiz, id_ruta_aprendizaje)
    ); 
        --MATRICULA
        INSERT INTO Matricula (Estado, id_aprendiz, id_ruta_aprendizaje)
        VALUES
        ('Activo', 1, 1),
        ('Activo', 1, 2),
        ('Activo', 1, 3),
        ('Activo', 1, 4),
        ('Activo', 2, 5),
        ('Activo', 2, 6),
        ('Activo', 2, 7),
        ('Activo', 2, 8),
        ('Cancelado', 3, 9),
        ('Cancelado', 3, 10),
        ('Cancelado', 3, 11),
        ('Activo', 4, 12),
        ('Activo', 4, 13),
        ('Activo', 4, 14),
        ('Activo', 5, 15),
        ('Activo', 5, 16),
        ('Activo', 5, 17),
        ('Terminado', 6, 18),
        ('Terminado', 6, 19),
        ('Terminado', 6, 20),
        ('Terminado', 7, 21),
        ('Terminado', 7, 22),
        ('Terminado', 7, 23),
        ('Terminado', 8, 24),
        ('Terminado', 8, 25),
        ('Cancelado', 9, 26),
        ('Cancelado', 9, 27),
        ('Cancelado', 9, 28),
        ('Terminado', 10, 29),
        ('Terminado', 10, 30),
        ('Terminado', 11, 31),
        ('Terminado', 11, 32);

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
    FROM Aprendiz A
    INNER JOIN Matricula M ON A.id_Aprendiz = M.id_aprendiz
    INNER JOIN RutaDeAprendizaje R ON M.id_ruta_aprendizaje = R.id_ruta_aprendizaje
    WHERE M.Estado = 'Cancelado';
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
    SELECT A.nom_aprendiz, C.nom_carrera, R.nom_ruta_aprendizaje
    FROM Aprendiz A
    INNER JOIN Matricula M ON A.id_Aprendiz = M.id_aprendiz
    INNER JOIN RutaDeAprendizaje R ON M.id_ruta_aprendizaje = R.id_ruta_aprendizaje
    INNER JOIN Carrera C ON R.id_carrera = C.id_carrera
    WHERE M.Estado = 'Terminado';
    ~~~
***
#### 9.Genere un listado de los aprendices matriculados en el curso “Bases de Datos Relacionales”.
    ```sql
    SELECT A.nom_aprendiz
    FROM Aprendiz A
    JOIN RutaDeAprendizaje RDA ON A.id_aprendiz = RDA.id_aprendiz
    JOIN contiene C ON C.id_ruta_aprendizaje = RDA.id_ruta_aprendizaje
    JOIN curso CUR ON CUR.id_Curso = C.id_curso
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

## Preguntas de selección múltiple

#### Pregunta 1: 
¿Qué cláusula SQL se utiliza para combinar filas de dos o más tablas en base a una condición relacionada?
    
    a) JOIN
    b) UNION
    c) GROUP BY
    d) CONCAT
    
    Respuesta correcta: a) JOIN

#### Pregunta 2: 
¿Cuál es la función de la cláusula ORDER BY en SQL?
    
    a) Filtrar filas basadas en una condición de agrupación
    b) Ordenar filas en un conjunto de resultados
    c) Filtrar filas basadas en una condición individual
    d) Combinar filas de múltiples tablas
    
    Respuesta correcta: b) Ordenar filas en un conjunto de resultados

#### Pregunta 3: 
¿Cuál es la operación utilizada para combinar múltiples condiciones en una consulta?
    
    a) OR
    b) XOR
    c) AND
    d) NOT
    
    Respuesta correcta: c) AND

#### Pregunta 4: 
¿Qué tipo de clave se utiliza para identificar de manera única cada fila en una tabla?
    
    a) Clave primaria
    b) Clave foránea
    c) Clave externa
    d) Clave única
    
    Respuesta correcta: a) Clave primaria

***
