# Bastion

## Projektstruktur

```
Bastion.sln
│
├── Bastion.Wpf/                  (WPF-klienten, .NET 8, WinExe)
│   ├── Models/
│   ├── ViewModels/
│   ├── Views/
│   ├── Services/
│   │   ├── ApiClient.cs          (HttpClient mot Bastion.Api)
│   │   ├── GameLoopService.cs
│   │   └── AudioService.cs
│   ├── Commands/
│   ├── Converters/
│   ├── Resources/
│   ├── Assets/
│   ├── Helpers/
│   ├── App.xaml
│   └── App.xaml.cs
│
├── Bastion.Core/                 (Class library: ren spellogik)
│   ├── Entities/
│   ├── Rules/
│   └── Interfaces/
│
├── Bastion.Shared/               (Class library: DTO:er som både klient och API använder)
│   └── Dtos/
│
├── Bastion.Api/                  (ASP.NET Core Web API)
├── Endpoints/
├── Data/                         (DbContext, migrations)
│   ├── Models/                   (databasentiteter)
│   ├── Services/
│   ├── appsettings.json
│   └── Program.cs
│
└── Bastion.Tests/                (xUnit)
    ├── Core/
    └── Api/
```
