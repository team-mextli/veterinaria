# Sistema Veterinario

Sistema para administrar la operación de una clínica veterinaria: clientes, mascotas, consultas, historial clínico, veterinarios, recetas y medicamentos. Reemplaza el registro en papel por una base de datos relacional donde cada dato se guarda una sola vez y la información puede crecer sin cambiar la estructura.

---

## El problema

Una clínica que registra todo a mano repite los mismos datos en cada hoja: el propietario, la mascota y el veterinario se vuelven a escribir en cada formato, y si uno cambia hay que corregirlo en todos lados. Además, hay información que no tiene un límite fijo — las mascotas de un cliente, las consultas de una mascota o los medicamentos de una receta — y no cabe en un formato de papel sin recurrir a hojas anexas.

El sistema resuelve esto con:

### Registro centralizado

Clientes, mascotas, veterinarios y medicamentos se registran una sola vez y se relacionan entre sí, sin copiar sus datos en cada consulta o receta.

### Historial clínico

Cada consulta conserva sus signos vitales, diagnóstico y tratamiento. El expediente de una mascota es el conjunto de sus consultas, con sus recetas y alergias.

### Recetas con cualquier número de medicamentos

Una consulta puede o no generar una receta, y una receta puede incluir tantos medicamentos como se necesiten, sin un máximo fijo.

---

## Modelo de datos

La base de datos está normalizada hasta Tercera Forma Normal y consta de ocho tablas:

| Tabla            | Contenido                                                           |
| ---------------- | ------------------------------------------------------------------- |
| `Cliente`        | Datos personales, contacto y domicilio del propietario.             |
| `Mascota`        | Datos de cada mascota; pertenece a un solo cliente.                 |
| `AlergiaMascota` | Alergias conocidas de una mascota (cero o varias).                  |
| `Veterinario`    | Nombre, cédula profesional y especialidad.                          |
| `Consulta`       | Atención médica de una mascota, a cargo de un veterinario.          |
| `Receta`         | Receta generada por una consulta (opcional, una por consulta).      |
| `Medicamento`    | Catálogo de medicamentos: nombre, presentación y concentración.     |
| `DetalleReceta`  | Medicamentos de cada receta, con dosis, vía, frecuencia y duración. |

---

## Documentación técnica

| Documento                                           | Contenido                                                                                              |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| [`CONTRIBUTING.md`](CONTRIBUTING.md)                | **Guía de contribución** — desarrollo local, convención de commits, ramas y pull requests.             |
| [`repository-config.md`](docs/repository-config.md) | **Ajustes del repositorio** — configuración de GitHub: Actions, ruleset de `main` y ajustes generales. |

---

## Stack técnico

- **Plataforma:** ASP.NET Core MVC (C#)
- **Entorno de desarrollo:** Visual Studio
- **Backend:** controladores, modelos y lógica de negocio en C#
- **Frontend:** vistas Razor (HTML, CSS y JavaScript) dentro del mismo proyecto
- **Base de datos:** SQL Server

---

## Equipo de desarrollo

| Nombre                                                          | Rol / área |
| --------------------------------------------------------------- | ---------- |
| [Mike Armando Montano Valencia](https://github.com/MikeArmando) | Backend    |
| [Mextli Citlali Perez Aguirre](https://github.com/mxcitali)     | Frontend   |
| [Emir Alexander Alcantar Martinez](https://github.com/ALVXNDR)  | DBA        |

---

<sub>Proyecto desarrollado como parte de la asignatura «Ambientes de Programación Visual» de Ingeniería en Software y Tecnologías Emergentes, Facultad de Ingeniería, Arquitectura y Diseño, Universidad Autónoma de Baja California (UABC), Ensenada.</sub>
