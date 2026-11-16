# Base de datos Veterinaria

## Orden de ejecución

1. 00_crear_bd.sql
2. 01_datos_prueba.sql
3. 02_pruebas.sql

## Importante

La base de datos local NO se sincroniza automáticamente con GitHub.

GitHub conserva los scripts SQL. Cada integrante puede reconstruir
la misma base ejecutando los archivos en el orden indicado.

ADVERTENCIA:
00_crear_bd.sql contiene DROP DATABASE IF EXISTS Veterinaria.
Al ejecutarlo se elimina la base local Veterinaria y se crea nuevamente.

## Práctica 6

Archivo adicional:

- 03_verificacion_p6.sql

Este script NO crea nuevamente la base.
Se utiliza para comprobar las operaciones realizadas
desde la aplicación Web durante la Práctica 6.

Orden recomendado para reconstruir la base:

1. 00_crear_bd.sql
2. 01_datos_prueba.sql
3. 02_pruebas.sql
4. 03_verificacion_p6.sql — sólo para verificación

## Práctica 7

Archivo agregado:

- 04_verificacion_final_p7.sql

Finalidad:
comprobar el estado final de la base
durante las pruebas de aceptación,
incluyendo las 9 tablas, sus PK, sus FK
y las reglas de integridad referencial.

Orden recomendado:

1. 00_crear_bd.sql
2. 01_datos_prueba.sql
3. 02_pruebas.sql
4. 03_verificacion_p6.sql
5. 04_verificacion_final_p7.sql

Advertencia: 00_crear_bd.sql elimina y reconstruye la base local.

## Respaldo final

Archivo:
`backups/respaldo_veterinaria_p7.sql`

Estado:
generado después de aprobar P7.

Restauración:
- si el dump incluye CREATE DATABASE, ejecutarlo directamente;
- si no lo incluye, ejecutar antes `00_crear_bd.sql`.

Verificación: 9 tablas, 9 PK y 8 FK confirmadas con `04_verificacion_final_p7.sql`.
