# Modelo Relacional de Bases de Datos 16



## Descripción



Este documento detalla el esquema y la estructura del modelo relacional de bases de datos para un sistema de gestión inmobiliaria, enfocado en el control de propietarios, propiedades, empleados, inquilinos, contratos de alquiler y pagos.

---

## Estructura de Tablas y Atributos



### 1. Propietario



* **PK (Clave Primaria):** `id_CUIT_DNI`


* **Atributos:**
* `nombre`


* `apellido`


* `teléfono`


* `correo_electronico`





### 2. Propiedad



* **PK (Clave Primaria):** `id_codigo_catastral`


* **Atributos:**
* `dirección`


* `ciudad`


* `tipo_de_propiedad`


* `superficie`




* **FK (Claves Foráneas):**
* `id_CUIT_DNI` (asociado a la tabla Propietario)





### 3. Empleado



* **PK (Clave Primaria):** `id_empliado`


* **Atributos:**
* `nombre`


* `apellido`


* `teléfono`


* `correo_electronico`





### 4. Inquilino



* **PK (Clave Primaria):** `id_CUIT_DNI1`


* **Atributos:**
* `nombre`


* `apellido`


* `teléfono`


* `correo_electronico`





### 5. Contrato



* **PK (Clave Primaria):** `id_Contrato`


* **Atributos:**
* `fecha_inicio`


* `fecha_finalización`


* `monto_mensual`




* **FK (Claves Foráneas):**
* `id_empliado` (asociado a la tabla Empleado)


* `id_codigo_catastral` (asociado a la tabla Propiedad)


* *(Nota: Relacionado también de forma directa con el Inquilino mediante su identificador)*





### 6. Pago



* **PK (Clave Primaria):** `id_pago`


* **Atributos:**
* `fecha_efectiva`


* `monto_abonado`


* `medio_de_pago`


* `reacargo_por_demora`




* **FK (Claves Foráneas):**
* `id_Contrato` (asociado a la tabla Contrato)





---

## Relaciones Principales



* **Propietario y Propiedad:** Un propietario puede registrar múltiples propiedades vinculadas mediante su identificador `id_CUIT_DNI`.


* **Empleado y Contrato:** Los contratos de alquiler son gestionados o administrados por empleados de la inmobiliaria (`id_empliado`).


* **Propiedad, Inquilino y Contrato:** El contrato de alquiler vincula una propiedad específica (`id_codigo_catastral`) con un inquilino, estableciendo las condiciones temporales y económicas del acuerdo.


* **Contrato y Pago:** Cada contrato de alquiler genera múltiples registros de transacciones o cuotas en la tabla `Pago` mediante la clave foránea `id_Contrato`.
