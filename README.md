# DigitalShop.Mvc

`DigitalShop.Mvc` is an ASP.NET Core MVC training e-commerce application for browsing digital products, adding them to a session-based cart, registering users through ASP.NET Core Identity, and managing catalog data from an admin area.

## Features

- product catalog with category filtering on the home page
- product details page with add/remove cart actions
- shopping cart stored in session
- ASP.NET Core Identity authentication and registration
- admin-only CRUD for categories, application types, and products
- image upload for products

## Tech Stack

- .NET 8
- ASP.NET Core MVC + Razor Pages
- Entity Framework Core + SQL Server / LocalDB
- ASP.NET Core Identity
- Bootstrap, jQuery, Summernote, Font Awesome

## Solution Structure

- `DigitalShop.Mvc` - web application, controllers, views, Identity UI, static files
- `DigitalShop.Access` - `AppDbContext` and EF Core migrations
- `DigitalShop.Models` - domain models and view models
- `DigitalShop.Utility` - shared constants and session helpers

## Configuration

The default connection string is stored in `DigitalShop.Mvc/appsettings.json`:

```json
"DefaultConnection": "Server=(localdb)\\MSSQLLocalDB;Database=DigitalShop;Trusted_Connection=True;MultipleActiveResultSets=True;"
```

If you want to use another SQL Server instance, update this connection string before starting the app.

## How To Run

1. Restore packages:

```powershell
dotnet restore .\DigitalShopMvc.sln
```

2. Apply migrations and create the database:

```powershell
dotnet ef database update --project .\DigitalShop.Access\DigitalShop.Access.csproj --startup-project .\DigitalShop.Mvc\DigitalShop.Mvc.csproj
```

3. Run the web app:

```powershell
dotnet run --project .\DigitalShop.Mvc\DigitalShop.Mvc.csproj
```

## Roles And Access

- `Customer` users can browse the catalog, register, sign in, and use the cart
- `Admin` users can manage categories, application types, products, and create additional admin users
- cart data is session-based and not persisted per user in the database
- first admin creation is not automated
