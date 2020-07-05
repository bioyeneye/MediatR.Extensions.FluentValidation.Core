# MediatR.Extensions.FluentValidation.Core

MediatR extension for FluentValidation using asp.net core

### Install with nuget

```
Install-Package MediatR.Extensions.FluentValidation.Core
```

## Install with .NET CLI
```
dotnet add package MediatR.Extensions.FluentValidation.Core
```

# How to use

## Setup - Add configuration in startup 


```csharp

public void ConfigureServices(IServiceCollection services)
{
    // Add framework services etc.
    services.AddMvc();
    
    // Add MediatR
    services.AddMediatR(typeof(Startup));

    //Add FluentValidation
    services.AddFluentValidation(new[] {typeof(Startup).Assembly});
    
    //Add other stuffs
    ...
}

```
