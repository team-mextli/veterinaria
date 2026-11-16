# Backend Tests

## Architecture

- Web without SQL: Verified. A search in `Veterinaria.Web` finds no `INSERT INTO`, `DELETE FROM`, `UPDATE` or `SELECT` statements. The only `select` matches are `<select>` tags, `SelectListItem` and LINQ `.Select(...)`, which are not SQL.
- Web without MySqlConnection: Verified. There is no `MySqlConnection`, `MySqlCommand` or `MySqlDataReader` in `Veterinaria.Web`. Its `.csproj` references only `Veterinaria.Entidades` and `Veterinaria.Negocios`, not `Veterinaria.Datos`.
- Business uses Data: Verified. `ClienteNegocio`, `MascotaNegocio` and `ConfiguracionNegocio` use `Veterinaria.Datos`, and `Veterinaria.Negocios.csproj` references `Veterinaria.Datos`.
- Data uses MySql.Data: Verified. `Veterinaria.Datos.csproj` has the `MySql.Data` package, and `ClienteDatos`, `MascotaDatos` and `Conexion` use `MySql.Data.MySqlClient`.

## Rules

- Client with Pets: Deletion is blocked. `ClienteNegocio.Eliminar()` calls `TieneMascotas()` and throws `ReglaNegocioException`. `Clientes/Eliminar` shows the message and hides the Delete button.
- Pet with Consultations: Deletion is blocked. `MascotaNegocio.Eliminar()` calls `TieneConsultas()` and throws `ReglaNegocioException`. `Mascotas/Eliminar` shows the message and hides the Delete button.
- Future date: Rejected. `MascotaNegocio.Validar()` throws an `ArgumentException` when `FechaNacimiento` is later than today. `Nueva` and `Editar` show the message through `ModelState`.

## Parameterized Queries

- ClientData: Approved. All user-provided values use parameters (`@idCliente`, `@texto`, `@nombre`, etc.). The SQL strings are `const` with no concatenation or interpolation.
- PetData: Approved. All user-provided values use parameters (`@idMascota`, `@idCliente`, `@nombre`, etc.). The SQL strings are `const` with no concatenation or interpolation.

## Corrections Made

- `Clientes/Eliminar.cshtml.cs` and `Mascotas/Eliminar.cshtml.cs`: in `OnPost`, the data load (`BuscarPorId` / `Cargar`) was moved inside the `try` block, so a MySQL failure is handled by the `catch` and no longer ends in a 500 page.
