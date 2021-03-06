# Module 1 - Development Environment Setup

## Prerequisites
- [.NET 5.0 SDK][1.1]
- [Node.js v12.16.1][1.2]
- [Microsoft SQL Server 2017 Express][1.3]
- [Redis][1.4]
- [Git][1.5]

## Tools
- [Visual Studio 2019][2.1]
    - [Editor Guidelines][2.1A]
    - [Trailing Whitespace Visualizer][2.1B]
- [Visual Studio Code][2.2]
    - [C# Extension][2.2A]
    - [ESLint][2.2B]
    - [Prettier][2.2C]
    - [.NET Test Explorer][2.2D]
- [Microsoft SQL Server Management Studio (SMSS)][2.3]
- Redis CLI
- Code Generator

## Setup ROC
- Download ROC
- Install EF Core Tools: `dotnet tool install --global dotnet-ef`
- Configure Redis: `redis-server --service-install redis.windows.conf --loglevel verbose`
- Confirm SQL Server and Redis are running
- Build the Solution: `dotnet build`
- Database Setup
    - Login to SSMS at Server Name: `.\SQLEXPRESS`
    - Create a new database titled: `RocCommerce`
    - Run Migrations: `cd Roc.Migrations.Commerce | dotnet ef database update`
- Run Setup Script: `Scripts/Setup.ps1`
- Hosts File: `C:\Windows\System32\drivers\etc`
```
# ROC Project: roccommerce
127.0.0.1 web.roccommerce.local
127.0.0.1 alt.roccommerce.local
127.0.0.2 admin.roccommerce.local
127.0.0.3 api.roccommerce.local
127.0.0.4 tasks.roccommerce.local
```
- Seed Application: `cd Roc.Tasks | dotnet run`
- Install Admin and Web node_modules
    - `cd Roc.Admin | npm install`
    - `cd Roc.Web | npm install`

## Run ROC Admin
- Start Admin react app: `cd Roc.Admin | npm run dev`
- Start Admin backend server: `cd Roc.Admin | dotnet run`
- Navigate to http://admin.roccommerce.local:5000/
- Setup a power user
- Confirm that new power user can login to the admin
- Configure Default Site Host Url
    - Navigate to the sites listing page: http://admin.roccommerce.local:5000/system/multi-site/sites
    - Edit the default `RocCommerce` site to have the following:
        - Host: `web.roccommerce.local`
        - Port: `5000`

## Create a Product
- Navigate to the create product page: http://admin.roccommerce.local:5000/commerce/products/create
- Add the following properties
    - Name
    - Sku
    - Price/Packaging
    - Picture (Optional)
- Publish the product

## Run ROC Web
- Start Web react app: `cd Roc.Web | npm run dev`
- Start Web backend server: `cd Roc.Web | dotnet run`
- Navigate to http://web.roccommerce.local:5000/
- Basic auth
    - username: `roc`
    - password: `design`
- Navigate to the product
- Checkout
- The order can now be viewed on web and admin

## Conclusion - Next Steps

[1.1]: <https://dotnet.microsoft.com/download/dotnet/5.0>
[1.2]: <https://nodejs.org/dist/v12.16.1/node-v12.16.1-x64.msi>
[1.3]: <https://www.microsoft.com/en-us/download/details.aspx?id=55994>
[1.4]: <https://github.com/MicrosoftArchive/redis/releases/download/win-3.0.504/Redis-x64-3.0.504.msi>
[1.5]: <https://git-scm.com/download/win>

[2.1]: <https://visualstudio.microsoft.com/vs/>
[2.1A]: <https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines>
[2.1B]: <https://marketplace.visualstudio.com/items?itemName=MadsKristensen.TrailingWhitespaceVisualizer>
[2.2]: <https://code.visualstudio.com/>
[2.2A]: <https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp>
[2.2B]: <https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint>
[2.2C]: <https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode>
[2.2D]: <https://marketplace.visualstudio.com/items?itemName=formulahendry.dotnet-test-explorer>
[2.3]: <https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15>
