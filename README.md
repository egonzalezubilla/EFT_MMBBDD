# Modelamiento de Bases de Datos - Gestión de Clubes y Asociación de Fútbol

## 📋 Información General

- **Estudiante:** Elías González Ubilla
- **Asignatura:** Modelamiento de Bases de Datos
- **Carrera:** Analista Programador
- **Institución:** Duoc UC
- **Fecha:** 11 de Octubre de 2026

---

## 🏢 Descripción del Proyecto

El proyecto consiste en el diseño e implementación integral de una base de datos relacional para el sistema de gestión de la **Asociación de Fútbol y Clubes Asociados**. La solución permite administrar de manera centralizada la estructura geográfica (Regiones y Comunas), las entidades administrativas (Asociaciones, Clubes, Escuelas de Fútbol), el personal institucional (Trabajadores, Jugadores y Personal de Planta) y las relaciones contractuales e idioma del plantel.

La solución abarca desde la preparación e implementación DDL, definición estricta de restricciones de integridad referencial, secuencias automatizadas, poblamiento con datos de prueba (DML), hasta la generación de consultas analíticas para la toma de decisiones presupuestarias y operativas.

---

## 🛠️ Estructura del Script y Solución Implementada

El desarrollo del proyecto se encuentra consolidado en un script SQL único ejecutable en **Oracle SQL Developer**, estructurado de la siguiente manera:

1. **Limpieza del Entorno:** Eliminación controlada de tablas y secuencias mediante bloques dinámicos PL/SQL (`DROP TABLE ... CASCADE CONSTRAINTS`) para permitir la re-ejecución limpia del script.
2. **Implementación del Modelo (DDL):**
   - **Tablas Maestras Fuertes:** Creación de `REGION`, `IDIOMA`, `NACIONALIDAD`, `ESCUELA_FUTBOL` y `ASOCIACION` con sus correspondientes restricciones de clave primaria (`PK`), reglas de validación (`CHECK`) y restricciones de unicidad (`UNIQUE`).
   - **Tablas de Entidades y Subtipos:** Creación de `COMUNA`, `TRABAJADOR`, `PERSONAL_PLANTA`, `JUGADOR` y `CLUB_FUTBOL` (incorporando la secuencia `SEQ_CLUB_FUTBOL` para la generación de IDs).
   - **Tablas Intermedias (M:N):** Creación de `CONTRATO_CLUB_JUGADOR` (relación de muchos a muchos con atributos propios como `fecha_ingreso` y `fecha_salida`) y `NIVEL_IDIOMA`.
3. **Integridad Referencial (Foreign Keys):** Aplicación estructurada de todas las restricciones `FOREIGN KEY` garantizando el orden jerárquico del modelo (p. ej., `COMUNA` depende de `REGION`, `TRABAJADOR` de `COMUNA` y `NACIONALIDAD`, y `JUGADOR`/`PERSONAL_PLANTA` heredan de `TRABAJADOR`).
4. **Poblamiento del Modelo (DML):** Inserción ordenada de registros representativos asegurando la coherencia entre regiones, comunas, clubes, jugadores y contratos activos.
5. **Consultas e Informes Analíticos:**
   - **Gestión de Asociaciones:** Recuperación de asociaciones registradas y sus fechas de creación.
   - **Análisis Patrimonial de Clubes:** Consulta analítica que calcula y convierte el patrimonio de los clubes de fútbol desde pesos chilenos ($CLP$) a dólares estadounidenses ($USD$).

---

## 🚀 Instrucciones de Uso

1. Conéctate a tu base de datos Oracle (o instancia en Oracle Cloud) utilizando tus credenciales de usuario o el esquema asignado.
2. Abre **Oracle SQL Developer** y carga el archivo con el script `.sql`.
3. Ejecuta el script completo (tecla `F5` o botón "Ejecutar Script").
4. Revisa la pestaña de **Salida de Script** para verificar la creación limpia de tablas, claves foráneas, la inserción de registros y los resultados de los informes SQL finales.