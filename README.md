# Crédito Hipotecario · API

Backend de una aplicación de crédito hipotecario: inicio de sesión, menú según el tipo de usuario y cambio de contraseña con historial.
El frontend está en [credito-hipotecario-web](https://github.com/Jmurga16/credito-hipotecario-web).

Proyecto de práctica (2023) centrado en aplicar **Clean Architecture** en .NET.

## Stack

- **.NET 6** · ASP.NET Core Web API
- **ADO.NET** sobre **SQL Server**
- **NLog** para logs

## Arquitectura

Clean Architecture con puertos y adaptadores: cada caso de uso tiene su *input port* (interactor) y su *output port* (presenter).

```
├── Entities/              # Entidades, interfaces de repositorio, excepciones y especificaciones
├── UseCasesDTOs/          # Request / Response de cada caso de uso
├── UseCasesPorts/         # Puertos de entrada y salida
├── UseCases/              # Interactores: Login, Menú, Cambio de contraseña
├── Presenters/            # Adaptan la salida de los casos de uso
├── ADONet/                # Acceso a datos con ADO.NET
├── WebExceptionPresenter/ # Filtros y manejadores de excepciones para la API
├── IoC/                   # Registro de dependencias
└── WebApi/                # Controladores: Login, Menu, Perfil
```

## Funcionalidades

- **Login** con tipos de usuario.
- **Menú dinámico** según el perfil del usuario.
- **Cambio de contraseña** (`POST api/perfil/change-password`) con historial de contraseñas y de sesiones.

## Ejecutar en local

Requiere .NET 6 SDK y SQL Server. Configurar la cadena de conexión en `WebApi/appsettings.json` y ejecutar:

```bash
dotnet run --project WebApi
```

---

Desarrollado por **José Murga** · [josemurga.dev](https://josemurga.dev)
