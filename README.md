# Go Digital Portal

**Go Digital Portal** es una plataforma web integral diseñada para la gestión, seguimiento y colaboración en solicitudes de transformación digital (DX) y soporte técnico. Permite a los usuarios y administradores coordinar esfuerzos, priorizar proyectos, dar retroalimentación a través de comentarios y visualizar el estado de cada iniciativa tecnológica en tiempo real.

---

## 📋 Descripción Corta (para el repositorio)
> "Portal web de gestión y seguimiento de solicitudes de transformación digital, construido con ASP.NET Core Web API (C#) y Quasar Framework (Vue 3 / TypeScript)."

---

## 🛠️ Arquitectura del Proyecto

El sistema está estructurado en dos partes principales bajo un enfoque de desarrollo desacoplado:

### 1. Backend (`GoDigital.API`)
* **Framework:** ASP.NET Core 8 Web API
* **Base de Datos:** PostgreSQL con **Entity Framework Core** (EF Core) y proveedor `Npgsql`.
* **Validación:** FluentValidation para la validación de peticiones (DTOs).
* **Documentación:** Swagger/OpenAPI para pruebas rápidas de los endpoints.
* **Características:** Arquitectura basada en servicios, middleware global para manejo de excepciones y soporte SPA (sirve los archivos estáticos del frontend si es necesario).

### 2. Frontend (`go-digital-frontend`)
* **Framework:** Quasar Framework (Vue.js 3 / Vite)
* **Lenguaje:** TypeScript
* **Gestor de Estado:** Pinia
* **Estilos:** Sass / SCSS y componentes nativos de Quasar
* **Comunicación:** Axios para consumo de la API REST.

---

## 🚀 Requisitos Previos

Antes de ejecutar el proyecto localmente, asegúrate de tener instalado:
* **Node.js** (versión 18 o superior)
* **SDK de .NET 8.0** o superior
* **PostgreSQL** (activo y con una base de datos configurada)

---

## ⚙️ Configuración y Configuración de Base de Datos

1. Abre el archivo [`GoDigital.API/appsettings.json`](file:///c:/Users/junni/Downloads/GoDigitalProject%20test/GoDigital.API/appsettings.json) (o `appsettings.Development.json`).
2. Configura tu cadena de conexión a PostgreSQL en la sección `ConnectionStrings`:
   ```json
   "ConnectionStrings": {
     "DefaultConnection": "Host=localhost;Database=GoDigitalDb;Username=tu_usuario;Password=tu_contraseña"
   }
   ```
3. Genera las tablas ejecutando las migraciones desde la consola dentro del directorio `GoDigital.API`:
   ```bash
   dotnet ef database update
   ```

---

## 🏁 Cómo Iniciar el Proyecto

### Opción A: Inicio rápido (Windows) ⚡
Si estás en Windows y configuraste tu conexión de base de datos correctamente, simplemente ejecuta el archivo script batch que iniciará automáticamente tanto el Backend como el Frontend:
* Ejecuta: Double click en [`Start Digital.bat`](file:///c:/Users/junni/Downloads/GoDigitalProject%20test/Start%20Digital.bat)

El portal estará disponible en tu navegador en: **`http://localhost:9000`**

### Opción B: Inicio Manual 🛠️

**Paso 1: Iniciar el Backend API**
```bash
cd GoDigital.API
dotnet run --urls http://localhost:5044
```
* La API y documentación de Swagger estarán disponibles en: `http://localhost:5044/swagger`

**Paso 2: Iniciar el Frontend (SPA)**
```bash
cd go-digital-frontend
npm install
npx quasar dev
```
* El servidor de desarrollo del frontend iniciará en: `http://localhost:9000`

---

## 🔑 Cuentas de Prueba Pre-configuradas

Puedes iniciar sesión en la aplicación con cualquiera de los siguientes perfiles semilla:

| Perfil | Correo Electrónico | Contraseña | Rol / Descripción |
| :--- | :--- | :--- | :--- |
| **Administrador** | `admin@godigital.com` | `admin123` | Control total, administración de catálogos y solicitudes |
| **Equipo DX** | `dx@godigital.com` | `dx123` | Equipo técnico de transformación digital |
| **Usuario General** | `user@godigital.com` | `user123` | Usuario final para crear y monitorear solicitudes |

---

## 📂 Estructura del Repositorio

* `/GoDigital.API` - Proyecto backend en C#.
  * `/Controllers` - Controladores de API REST.
  * `/Data` - Contexto de BD y semillas de migración.
  * `/Models` - Entidades del dominio de datos (Requests, Users, Comments).
* `/go-digital-frontend` - Aplicación frontend Vue/Quasar.
  * `/src/components` - Componentes reutilizables de UI.
  * `/src/pages` - Vistas y pantallas (Login, Detalle, Crear Solicitudes).
  * `/src/stores` - Control de estado global con Pinia.
* `Start Digital.bat` - Script de ejecución conjunta para Windows.
* `.gitignore` - Filtro de exclusión de git para ambos entornos.
