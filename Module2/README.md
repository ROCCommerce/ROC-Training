# Module 2 - Roc Basics: Scaffold a new Feature

## Learning Goals
- ROC Code Generator
- Mediator
- Slices
- Entity Framework

## Getting Started - ROC Code Generator
- Install the ROC Code Generator: `dotnet new -i NewRocFeature --nuget-source http://roc-nuget.idevdesign.net/nuget`
- Create a new feature: `dotnet new rocfeature -s Lawyer -p Lawyers -cf lawyers -f Lawyers -m Lawyer`
- Advantages of code generator
  - Saves time
  - Prevents mistakes
  - Ensures consistency

## ROC Hierarchy
- Core Files: `Roc\Features\Lawyers\`
    - Models
    - Services
    - Slices
- Admin Files:
    - Backend Controllers: `Roc.Admin\Features\Lawyers\`
    - React Components: `Roc.Admin\ClientApp\features\lawyers\`
- Storefront Files:
    - Controllers and Views: `Roc.Web\Features\Lawyers\`
    - React Components: `Roc.Web\ClientApp\features\lawyers\`

## Add Lawyer Table to the Database
- Navigate to the migrations project: `cd Roc.Migrations.Commerce`
- Create a migration: `dotnet ef migrations add AddLawyers`
- Run the migration: `dotnet ef database update`

