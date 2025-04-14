# UNIDAD 6. PROGRAMACIÓN DE BASES DE DATOS



# Programación en Bases de Datos (Nivel Básico)

## ✅ 1. Introducción a la programación en bases de datos

En una base de datos, además de almacenar datos, también podemos **programar lógica** que se ejecuta dentro del propio motor de la base de datos. Esta programación se puede usar para:

- Automatizar tareas.
- Centralizar la lógica de negocio (por ejemplo, cálculos, validaciones).
- Reutilizar código (mediante funciones o procedimientos).
- Mejorar el rendimiento al reducir viajes entre la base de datos y la aplicación.

### 🔧 ¿Qué se puede programar en una base de datos?

- **Procedimientos almacenados (Stored Procedures):** bloques de código que realizan acciones, con o sin parámetros.
- **Funciones:** devuelven un valor y pueden ser usadas en consultas.
- **Triggers (disparadores):** código que se ejecuta automáticamente al producirse un evento (INSERT, UPDATE, DELETE).
- **Cursores y control de flujo:** para manejar filas una a una y aplicar lógica condicional o bucles.

---

## ✅ 2. Variables

Una **variable** es un espacio en memoria que se utiliza para **guardar temporalmente un valor** durante la ejecución de un bloque de código.

### 📌 ¿Para qué sirven?

- Para almacenar datos intermedios.
- Para contar, acumular, comparar o devolver resultados.

### 📐 Declaración de variables en MySQL

Las variables deben declararse **al principio** de un bloque `BEGIN...END`, normalmente dentro de un procedimiento o función.

```sql
DECLARE nombre_variable TIPO;
```

#### 📌 Ejemplos:

```sql
DECLARE contador INT;
DECLARE nombre_cliente VARCHAR(50);
DECLARE fecha_actual DATE;
```

### 🔄 Asignación de valores

```sql
SET contador = 10;
SET nombre_cliente = 'María López';
SET fecha_actual = CURDATE(); -- Asigna la fecha actual
```

También se pueden usar en operaciones:

```sql
SET contador = contador + 1;
```

---

## 🧪 Ejemplo completo

```sql
DELIMITER //

CREATE PROCEDURE ejemplo_variables()
BEGIN
   DECLARE edad INT;
   DECLARE nombre VARCHAR(30);
   SET edad = 25;
   SET nombre = 'Carlos';

   SELECT CONCAT(nombre, ' tiene ', edad, ' años') AS mensaje;
END //

DELIMITER ;

CALL ejemplo_variables();
```



## ✅ 3. Procedimientos almacenados (Stored Procedures)

Un **procedimiento almacenado** es un bloque de código SQL que se guarda en la base de datos y se puede ejecutar cuantas veces queramos. Sirve para automatizar tareas, encapsular lógica y reutilizar código.

### 🎯 ¿Por qué usar procedimientos?

- Para **automatizar procesos** complejos o repetitivos.
- Para **organizar mejor** el código SQL.
- Para **reducir errores** al evitar escribir consultas largas cada vez.
- Para **centralizar la lógica** de negocio en la base de datos.

---

### 🧱 Sintaxis básica de un procedimiento en MySQL

```sql
DELIMITER //

CREATE PROCEDURE nombre_procedimiento()
BEGIN
   -- Código SQL aquí
END //

DELIMITER ;
```

> ✅ Es importante cambiar el delimitador (`DELIMITER //`) para que MySQL no interprete el `;` del interior del bloque como el final de la sentencia.

### ▶️ Ejecutar un procedimiento

```sql
CALL nombre_procedimiento();
```

---

### 🧪 Ejemplo 1: Procedimiento sin parámetros

```sql
DELIMITER //

CREATE PROCEDURE saludar()
BEGIN
   SELECT '¡Hola desde la base de datos!' AS saludo;
END //

DELIMITER ;

CALL saludar();
```

---

### 🧪 Ejemplo 2: Procedimiento con parámetro de entrada

```sql
DELIMITER //

CREATE PROCEDURE saludar_persona(nombre_usuario VARCHAR(50))
BEGIN
   SELECT CONCAT('Hola, ', nombre_usuario, '!') AS saludo;
END //

DELIMITER ;

CALL saludar_persona('María');
```

---

### 🔄 Parámetros en procedimientos

- `IN`: parámetro de **entrada** (el más común).
- `OUT`: parámetro de **salida** (devuelve un valor).
- `INOUT`: entrada y salida.

---

### 🧠 Ejercicios propuestos

1. Crea un procedimiento llamado `mostrar_fecha` que muestre la fecha actual.
2. Crea un procedimiento llamado `cuadrado_numero` que reciba un número y muestre su cuadrado.
3. Crea un procedimiento llamado `info_usuario` que reciba un nombre y un apellido y muestre un mensaje de bienvenida personalizado.

> 💡 Consejo: prueba cada procedimiento y modifica valores para ver cómo se comporta.



## ✅ 4. Funciones

Una **función** es un bloque de código almacenado en la base de datos que **devuelve un único valor**. A diferencia de los procedimientos, las funciones **pueden utilizarse dentro de una consulta**, como si fueran una función de MySQL (`NOW()`, `CONCAT()`, etc.).

---

### 🔍 Diferencias entre procedimiento y función

| Característica       | Procedimiento         | Función                 |
|----------------------|------------------------|--------------------------|
| Devuelve un valor    | No necesariamente      | Sí, siempre              |
| Se usa en consultas  | No                     | Sí (`SELECT`, `WHERE`)   |
| Se invoca con...     | `CALL procedimiento()` | `SELECT funcion()`       |
| Puede modificar datos| Sí                     | No (solo lectura)        |

---

### 🧱 Sintaxis básica de una función en MySQL

```sql
DELIMITER //

CREATE FUNCTION nombre_funcion(parametro TIPO) RETURNS TIPO
BEGIN
   DECLARE resultado TIPO;
   -- lógica
   SET resultado = ...;
   RETURN resultado;
END //

DELIMITER ;
```

---

### 🧪 Ejemplo 1: Función que devuelve el doble de un número

```sql
DELIMITER //

CREATE FUNCTION doble(numero INT) RETURNS INT
BEGIN
   RETURN numero * 2;
END //

DELIMITER ;

SELECT doble(5); -- Resultado: 10
```

---

### 🧪 Ejemplo 2: Función que indica si alguien es mayor de edad

```sql
DELIMITER //

CREATE FUNCTION es_mayor_edad(edad INT) RETURNS VARCHAR(20)
BEGIN
   RETURN IF(edad >= 18, 'Mayor de edad', 'Menor de edad');
END //

DELIMITER ;

SELECT es_mayor_edad(20); -- Resultado: 'Mayor de edad'
```

---

### 🧠 Ejercicios propuestos

1. Crea una función llamada `saludo_personal` que reciba un nombre y devuelva un saludo tipo "Hola, Juan".
2. Crea una función llamada `area_circulo` que reciba el radio de un círculo y devuelva su área (`π * r²`). Usa `PI()` y `POW()` de MySQL.
3. Crea una función llamada `iva_incluido` que reciba un precio y devuelva el precio con un 21% de IVA.

> 💡 Prueba las funciones usando `SELECT` directamente.



### 🧭 Sección final: Resumen visual / Mapa de conceptos


## 📌 Resumen visual: Programación en bases de datos

### 🧠 Conceptos clave

- **Variable**: espacio de memoria temporal dentro de un bloque `BEGIN...END`.
- **Procedimiento (Stored Procedure)**: bloque de código que ejecuta acciones (puede modificar datos).
- **Función**: bloque que devuelve un valor y se puede usar en consultas.
- **Parámetros**:
  - `IN`: entrada.
  - `OUT`: salida.
  - `INOUT`: ambos.
- **DELIMITER**: se usa para indicar a MySQL dónde empieza y termina un bloque de código.

---

### 🧩 Diferencias rápidas

| Elemento       | Usa CALL | Devuelve valor | Se usa en SELECT | Modifica datos |
|----------------|----------|----------------|------------------|----------------|
| Procedimiento  | ✅        | Opcional       | ❌               | ✅              |
| Función        | ❌        | ✅              | ✅               | ❌              |

---

### 🧪 Buenas prácticas

- Usa nombres claros y descriptivos (`calcular_total`, `mostrar_fecha`).
- Comenta tu código con `-- comentario`.
- Prueba tus funciones y procedimientos paso a paso.


## ✅ Autoevaluación: Programación en Bases de Datos – Nivel básico

Responde a las siguientes preguntas tipo test. Solo una opción es correcta en cada caso.

---

### 🧠 Preguntas

**1. ¿Cuál de estas afirmaciones sobre las variables es correcta?**

a) No pueden usarse dentro de procedimientos.  
b) Solo pueden almacenar números enteros.  
c) Se declaran con `DECLARE` y pueden usarse dentro de bloques `BEGIN...END`.  
d) Siempre deben tener el mismo nombre que el procedimiento.

---

**2. ¿Qué palabra clave se utiliza para crear un procedimiento en MySQL?**

a) `MAKE PROCEDURE`  
b) `NEW PROCEDURE`  
c) `CREATE PROCEDURE`  
d) `SET PROCEDURE`

---

**3. ¿Qué instrucción permite ejecutar un procedimiento almacenado?**

a) `EXEC`  
b) `SELECT`  
c) `RUN`  
d) `CALL`

---

**4. ¿Qué diferencia principal hay entre una función y un procedimiento?**

a) La función se guarda en la base de datos y el procedimiento no.  
b) El procedimiento devuelve un valor, la función no.  
c) La función puede usarse en consultas `SELECT`, el procedimiento no.  
d) No hay ninguna diferencia.

---

**5. ¿Cuál de estas funciones sería válida en una función de MySQL?**

a) `CALL saludar();`  
b) `SELECT saludar();`  
c) `CREATE PROCEDURE saludar();`  
d) `RUN saludar();`

---

**6. ¿Qué delimitador se suele usar para definir procedimientos o funciones en MySQL?**

a) `DELIMITER //`  
b) `DELIMITER --`  
c) `DELIMITER END`  
d) `DELIMITER $`

---

**7. ¿Cuál de estas opciones es incorrecta sobre las funciones?**

a) Siempre devuelven un valor.  
b) Pueden modificar datos en la base de datos.  
c) Pueden usarse dentro de `SELECT`.  
d) Se crean con `CREATE FUNCTION`.

---

**8. ¿Cuál es el tipo de parámetro que solo recibe datos (sin devolver)?**

a) `IN`  
b) `OUT`  
c) `INOUT`  
d) `RETURN`

---

### ✅ Soluciones (ocultas)

<details>
  <summary>Mostrar respuestas</summary>

  1. c  
  2. c  
  3. d  
  4. c  
  5. b  
  6. a  
  7. b  
  8. a

</details>

