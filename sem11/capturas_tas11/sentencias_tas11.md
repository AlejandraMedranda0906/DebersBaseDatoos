# TAS11 - Views projects
## 1. Crear las siguientes views en el proyecto invoice.
## invoice_VIEW.
  - Sentencia:
  ```
  CREATE VIEW invoice_view AS
  SELECT
  i.id,
  i.code,
  i.create_at,
  i.total,
  c.fullname
  FROM 
  invoice i
  JOIN 
  client c ON i.client_id = c.id;
  ```
  - Captura:

<img src="./capturas_tas11/view01.jpg" alt="drawing" width="500"/>
  ```
 SELECT * FROM invoice view
  ```
  - Captura:

<img src="./capturas_tas11/view02.jpg" alt="drawing" width="500"/>

## 2. detail VIEW.
  - Sentencia:
  ```
  CREATE VIEW detail_view AS
  SELECT 
  d.id,
  d.quantity,
  p.description,
  d.price,
  (d.quantity * d.price) AS subtotal
  FROM 
  detail d
  JOIN 
  product p ON d.product_id = p.id;

  ```
  - Captura:

<img src="./capturas_tas11/view03.jpg" alt="drawing" width="500"/>

 - Sentencia:
  ```
  SELECT * FROM detail view

  ```
   - Captura:
<img src="./capturas_tas11/view04.jpg" alt="drawing" width="500"/>