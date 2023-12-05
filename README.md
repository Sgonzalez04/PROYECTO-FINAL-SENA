# PROYECTO-FINAL-SENA
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
  
  CREATE TABLE Estado_Matricula (
      id_matricula INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
      Estado VARCHAR(50) NOT NULL,
      id_aprendiz BIGINT UNSIGNED NOT NULL,
      id_ruta_aprendizaje BIGINT UNSIGNED NOT NULL,
      FOREIGN KEY (id_aprendiz, id_ruta_aprendizaje) REFERENCES RutaDeAprendizaje(id_aprendiz, id_ruta_aprendizaje)
  );

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
    
    ***
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
    ('Terminado', 10, 28),
    ('Terminado', 10, 29),
    ('Terminado', 11, 30),
    ('Terminado', 11, 31);
    
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
