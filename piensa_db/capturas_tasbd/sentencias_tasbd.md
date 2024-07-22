# Diagrama

  - Captura:

<img src="./capturas_tasbd/001db.jpg" alt="drawing" width="500"/>

## 2.En la venta de herramienta de consulta (Query Tool) creo las tablas en base a mi diagrama.
  
```
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  firstName VARCHAR(255) NOT NULL,
  lastName VARCHAR(255) NOT NULL,
  age INT NOT NULL,
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

  ```

  ```
CREATE TABLE devices (
  id SERIAL PRIMARY KEY,
  code VARCHAR(255) NOT NULL,
  capacityBattery INT NOT NULL,
  design VARCHAR(255) NOT NULL,
  model VARCHAR(255) NOT NULL,
  totalUse INT DEFAULT 0,
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

  ```

  ```
CREATE TABLE registers (
  id SERIAL PRIMARY KEY,
  usageTime TIMESTAMP NOT NULL,
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  userId INT REFERENCES users(id),
  deviceId INT REFERENCES devices(id)
);


  ```

  - Captura:

<img src="./capturas_tasbd/002bd.png" alt="drawing" width="500"/>

# 3. Ejecuto el código.

```
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  firstName VARCHAR(255) NOT NULL,
  lastName VARCHAR(255) NOT NULL,
  age INT NOT NULL,
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

  ```

  ```
CREATE TABLE devices (
  id SERIAL PRIMARY KEY,
  code VARCHAR(255) NOT NULL,
  capacityBattery INT NOT NULL,
  design VARCHAR(255) NOT NULL,
  model VARCHAR(255) NOT NULL,
  totalUse INT DEFAULT 0,
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
 ```
```
CREATE TABLE registers (
  id SERIAL PRIMARY KEY,
  usageTime TIMESTAMP NOT NULL,
  createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  userId INT REFERENCES users(id),
  deviceId INT REFERENCES devices(id)
);

  ```

 - Captura:

<img src="./capturas_tasbd/0033bd.png" alt="drawing" width="500"/>


## 4. Ejecuto un nuevo código para mas adelante llamar al trigger.
  - Sentencia:
  ```
  SELECT
  m.fullname AS nombre_miembro,
  m.email AS correo,
  (SELECT COUNT(*)
  FROM register r
  WHERE r.member_id = m.id) AS numero_conferencias
  FROM
  member m;

  ```
  - Captura:

<img src="./capturas_tas12/0bd.png" alt="drawing" width="500"/>

## 2. subconsulta  en WHERE
### Listar los eventos donde el total de asistentes es mayor que el número promedio de asistentes en todos los eventos.
  - Sentencia:
  ```
  SELECT
  e.description AS descripcion_evento,
  e.start_date AS fecha_inicio,
  e.end_date AS fecha_fin,
  e.total_attendees AS total_asistentes,
  e.city AS ciudad
  FROM
  event e
  WHERE
  e.total_attendees > (SELECT AVG(total_attendees)
  FROM event);

  ```
  - Captura:

<img src="./capturas_tas12/.jpg" alt="drawing" width="500"/>

