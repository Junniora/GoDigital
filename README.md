# Go Digital

**Go Digital Portal** is a comprehensive web platform designed for managing, tracking, and collaborating on Digital Transformation (DX) requests and technical support. It enables users and administrators to coordinate efforts, prioritize projects, provide feedback through comments, and monitor the status of each technology initiative in real time.

---

## 📋 Short Description (for the repository)

> "Web-based portal for managing and tracking digital transformation requests, built with ASP.NET Core Web API (C#) and Quasar Framework (Vue 3 / TypeScript)."

---

## 🛠️ Project Architecture

The system is divided into two main components following a decoupled architecture:

### 1. Backend (`GoDigital.API`)

- **Framework:** ASP.NET Core 8 Web API
- **Database:** PostgreSQL with **Entity Framework Core** (EF Core) using the `Npgsql` provider.
- **Validation:** FluentValidation for request (DTO) validation.
- **Documentation:** Swagger/OpenAPI for testing API endpoints.
- **Features:** Service-based architecture, global exception handling middleware, and SPA support (serves frontend static files when required).

### 2. Frontend (`go-digital-frontend`)

- **Framework:** Quasar Framework (Vue.js 3 / Vite)
- **Language:** TypeScript
- **State Management:** Pinia
- **Styling:** Sass / SCSS with Quasar UI components
- **Communication:** Axios for consuming the REST API.

---

## 🚀 Prerequisites

Before running the project locally, make sure you have the following installed:

- **Node.js** (version 18 or later)
- **.NET 8 SDK** or later
- **PostgreSQL** (running with a configured database)

---

## ⚙️ Database Configuration

1. Open the `GoDigital.API/appsettings.json` file (or `appsettings.Development.json`).
2. Configure your PostgreSQL connection string under the `ConnectionStrings` section:

```json
"ConnectionStrings": {
  "DefaultConnection": "Host=localhost;Database=GoDigitalDb;Username=your_username;Password=your_password"
}
```

3. Apply the database migrations from the `GoDigital.API` directory:

```bash
dotnet ef database update
```

---

## 🏁 Running the Project

### Option A: Quick Start (Windows) ⚡

If you're using Windows and have already configured your database connection, simply run the batch script to start both the Backend and Frontend automatically.

Run:

```text
Start Digital.bat
```

The application will be available at:

```
http://localhost:9000
```

---

### Option B: Manual Startup 🛠️

#### Step 1: Start the Backend API

```bash
cd GoDigital.API
dotnet run --urls http://localhost:5044
```

The API and Swagger documentation will be available at:

```
http://localhost:5044/swagger
```

#### Step 2: Start the Frontend

```bash
cd go-digital-frontend
npm install
npx quasar dev
```

The frontend development server will start at:

```
http://localhost:9000
```

---

## 🔑 Preconfigured Demo Accounts

You can sign in using any of the following seeded accounts:

| Role | Email | Password | Description |
| :--- | :--- | :--- | :--- |
| **Administrator** | `admin@godigital.com` | `admin123` | Full access, catalog management, and request administration |
| **DX Team** | `dx@godigital.com` | `dx123` | Digital Transformation technical team |
| **General User** | `user@godigital.com` | `user123` | End user who can create and track requests |

---

## 📂 Repository Structure

- **`/GoDigital.API`** – Backend project written in C#.
  - `/Controllers` – REST API controllers.
  - `/Data` – Database context and migration seed data.
  - `/Models` – Domain entities (Requests, Users, Comments).

- **`/go-digital-frontend`** – Vue/Quasar frontend application.
  - `/src/components` – Reusable UI components.
  - `/src/pages` – Application pages (Login, Request Details, Create Request).
  - `/src/stores` – Global state management using Pinia.

- **`Start Digital.bat`** – Windows script to launch both the backend and frontend.
- **`.gitignore`** – Git ignore rules for both environments.
