# EventsVIP
Proyecto académico ITM C# - Plataforma de Gestión de Eventos

#### Flujo de una petición HTTP
```
Request HTTP
↓
Controller (API) → Recibe DTO, mapea a Entity, llama al Service
↓
Service (Domain) → Ejecuta lógica de negocio, llama al Repository
↓
Repository (DataAccess) → Ejecuta queries con EF Core contra la BD
↓
SQL Server
```

#### Construcción base

```
# Proyecto API (Web API)
dotnet new webapi -n EventsVIP.API -controllers

# Proyecto Domain (Class Library)
dotnet new classlib -n EventsVIP.Domain

# Proyecto DataAccess (Class Library)
dotnet new classlib -n EventsVIP.DataAccess

dotnet sln add EventsVIP.API/EventsVIP.API.csproj
dotnet sln add EventsVIP.Domain/EventsVIP.Domain.csproj
dotnet sln add EventsVIP.DataAccess/EventsVIP.DataAccess.csproj

# API referencia a Domain
dotnet add EventsVIP.API/EventsVIP.API.csproj reference EventsVIP.Domain/EventsVIP.Domain.csproj


# API referencia a DataAccess (para registrar servicios en Program.cs)
dotnet add EventsVIP.API/EventsVIP.API.csproj reference EventsVIP.DataAccess/EventsVIP.DataAccess.csproj


# DataAccess referencia a Domain
dotnet add EventsVIP.DataAccess/EventsVIP.DataAccess.csproj reference EventsVIP.Domain/EventsVIP.Domain.csproj
```


#### Paqueteria

```
cd EventsVIP.DataAccess
dotnet add package Microsoft.EntityFrameworkCore -v 8.0.*
dotnet add package Microsoft.EntityFrameworkCore.SqlServer -v 8.0.*
dotnet add package Microsoft.EntityFrameworkCore.Tools -v 8.0.*

cd EventsVIP.API
dotnet add package Microsoft.EntityFrameworkCore.Design -v 8.0.*
dotnet add package AutoMapper.Extensions.Microsoft.DependencyInjection
dotnet add package Swashbuckle.AspNetCore

cd EventsVIP.Domain
dotnet add package Microsoft.Extensions.Logging.Abstractions
```

#### Herramientas
1. Visual Studio 2022
2. Net 9.0
3. SQL Server