# .NET 6

## .NET 3.1, .NET 5

https://github.com/boeschenstein/dotnet5

## Compatibility, Breaking changes

https://docs.microsoft.com/en-us/dotnet/core/compatibility/6.0

## Nullable

```cs
// int?                        - nullable value type
// string?                     - nullable reference type
// id?.ToString()              - null conditional operator (BEWARE: same name BUT different: 'conditional operator': int x = a == 33 ? 1 : 2;)
// var v = i ?? 0;             - null coalescing operator
// (y ??= new()).Add(8);       - null coalescing assignment operator
// <nullable>enable</nullable> - nullable annotation context
// s!.ToString()               - null forgiving operator
```

4 nullable annotation context options: enable, disable, annotations, warnings

9 nullable-enable directives: enable, disable, restore, enable warnings, enable annotations, ...

```cs
#nullable disable
... OR Mapper Class (EF, Dapper) ...
#nullable restore
```

Nullable Reference Types: <https://learn.microsoft.com/en-us/dotnet/csharp/nullable-references>

Nullable with Generics: <https://learn.microsoft.com/en-us/dotnet/csharp/nullable-references#generics>

From: <https://www.youtube.com/watch?v=-bn4e5xUEeM>

## Upgrade .NET Core 3 -> .NET 6

Edit csproj, change from:

```xml
<TargetFramework>netcoreapp3.1</TargetFramework>
```

to:

```xml
<TargetFramework>net6.0</TargetFramework>
```

## CLI

### Info

Lists all installed sdk and runtime:

`dotnet --info`

### dotnet Tools

- https://docs.microsoft.com/en-us/dotnet/core/tools/global-tools
- https://www.nuget.org/packages?packagetype=dotnettool

Open Visual Studio's Package Manager Console (where Package Source `https://api.nuget.org/v3/index.json` is configured) and start:

```cmd
dotnet tool install --global dotnet-dump  
dotnet tool install --global dotnet-ef  
dotnet tool install --global dotnet-gcdump  
dotnet tool install --global dotnet-trace  
dotnet tool install --global dotnet-counters  
dotnet tool install -g dotnet-symbol

dotnet tool install --global Microsoft.Web.LibraryManager.Cli
```

or

```cmd
dotnet tool install --global dotnet-dump --version 6.*
dotnet tool install --global dotnet-ef --version 6.*
dotnet tool install --global dotnet-gcdump --version 6.*
dotnet tool install --global dotnet-trace --version 6.*
dotnet tool install --global dotnet-counters --version 6.*
dotnet tool install -g dotnet-symbol --version 6.*

dotnet tool install --global Microsoft.Web.LibraryManager.Cli --version 6.*
```

or

```cmd
dotnet tool update --global dotnet-dump  
dotnet tool update --global dotnet-ef  
dotnet tool update --global dotnet-gcdump  
dotnet tool update --global dotnet-trace  
dotnet tool update --global dotnet-counters  
dotnet tool update -g dotnet-symbol

dotnet tool update --global Microsoft.Web.LibraryManager.Cli
```

Using nuget.config

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <activePackageSource>
        <add key="NuGet official package source" value="https://api.nuget.org/v3/index.json" />
    </activePackageSource>
</configuration>
```

tool-update.cmd

```dos
SET nugetFile=.\nuget.config

dotnet tool uninstall --global dotnet-dump
dotnet tool uninstall --global dotnet-ef
dotnet tool uninstall --global dotnet-gcdump 
dotnet tool uninstall --global dotnet-trace
dotnet tool uninstall --global dotnet-counters
dotnet tool uninstall -g dotnet-symbol
dotnet tool uninstall --global Microsoft.Web.LibraryManager.Cli

dotnet tool update --global dotnet-dump  --configfile %nugetFile%
dotnet tool update --global dotnet-ef  --configfile %nugetFile%
dotnet tool update --global dotnet-gcdump  --configfile %nugetFile%
dotnet tool update --global dotnet-trace  --configfile %nugetFile%
dotnet tool update --global dotnet-counters  --configfile %nugetFile%
dotnet tool update -g dotnet-symbol  --configfile %nugetFile%
dotnet tool update --global Microsoft.Web.LibraryManager.Cli  --configfile %nugetFile%

dotnet tool list --global
```

### Performance Diagnosing

- `dotnet counters`
- `dotnet trace`
- `dotnet dump`
- `dotnet monitor`

### Upgrade to .NET 6

install or upgrade project converter

```cmd
dotnet tool install -g try-convert
```

install or upgrade "Upgrade assistant"

```cmd
dotnet tool install -g upgrade-assistant
```

Details: <https://github.com/dotnet/upgrade-assistant>

### Upgrade ASP.NET to .NET 6

https://docs.microsoft.com/en-us/aspnet/core/migration/50-to-60

## New Features in .NET 6

### Scoped Namespace

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-10.0/file-scoped-namespaces

## Tools

### AutoMapper

>Alternatives: Pure functions (faster, less hassle)

- <https://cezarypiatek.github.io/post/why-i-dont-use-automapper/>
- <https://ivanazure.wordpress.com/2015/12/02/why-automapping-is-bad-for-you/>

### LibMan - Client Side Package Manager

1. Install LibMan
2. Right-Click on your project: Add... Client-Side Library

## Information

- Nuget: <https://github.com/boeschenstein/nuget>
- LibMan: <https://docs.microsoft.com/en-us/aspnet/core/client-side/libman/libman-cli>

