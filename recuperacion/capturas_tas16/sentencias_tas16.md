# Crear script DDL

- Sentencia:
    ```
    CREATE TABLE Rutine (
    id INT PRIMARY KEY,
    description TEXT,
    disclaimer TEXT,
    sex VARCHAR(10)
    );
    ```

- Captura:

<img src="./capturas_tas16/rutine16.jpg"alt="drawing" width="500"/>

- sentencia:
    ``` 
    CREATE TABLE Exercise (
    id INT PRIMARY KEY,
    detail TEXT,
    video_url VARCHAR(255)
    );
    ```  
- Captura:

<img src="./capturas_tas16/exeecise16.jpg"alt="drawing" width="500"/>

- sentencia:
    ``` 
    CREATE TABLE Routine_exercise (
    id INT PRIMARY KEY,
    series INT,
    repetitions INT,
    rutine_id INT,
    exercise_id INT,
    FOREIGN KEY (rutine_id) REFERENCES Rutine(id),
    FOREIGN KEY (exercise_id) REFERENCES Exercise(id)
    );
    ```
- Captura:

<img src="./capturas_tas16/routine_exercise16.jpg"alt="drawing" width="500"/>





# Poblar con datos

- Sentencia:
    ```
    INSERT INTO Rutine (id, description, disclaimer, sex) VALUES 
    (1, 'Rutina para adultos mayores', 'Consulte a un médico antes de comenzar', 'Femenino'),
    (2, 'Rutina avanzada de todas las edades','Deben tener conocimiento basico', 'Femenino');

    INSERT INTO Exercise (id, detail, video_url) VALUES 
    (1, 'Flexiones', 'http://example.com/dominadasfemenino'),
    (2, 'Bailes', 'http://example.com/dominadas');

    INSERT INTO Routine_exercise (id, series, repetitions, rutine_id, exercise_id) VALUES 
    (1, 3, 12, 1, 1),
    (2, 4, 10, 2, 2);
    ```
- Captura:

<img src="./capturas_tas16/img16.jpg"alt="drawing" width="500"/>
- Captura:

<img src="./capturas_tas16/rutina17.jpg"alt="drawing" width="500"/>
- Captura:

<img src="./capturas_tas16/img17.jpg"alt="drawing" width="500"/>



# Crear una vista con las 3 tablas

- Sentencia:
    ```
    CREATE VIEW CompleteRoutine AS
    SELECT 
    r.id AS rutine_id,
    r.description,
    e.id AS exercise_id,
    e.detail,
    re.series,
    re.repetitions
    FROM 
    Rutine r
    JOIN 
    Routine_exercise re ON r.id = re.rutine_id
    JOIN 
    Exercise e ON re.exercise_id = e.id;
    ```
- Captura:

    <img src="./capturas_tas16/img18.jpg"alt="drawing" width="500"/>

- Captura:

    <img src="./capturas_tas16/img19.jpg"alt="drawing" width="500"/>


