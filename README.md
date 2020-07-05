# MediatR.Extensions.FluentValidation.Core

[![NuGet](https://img.shields.io/nuget/dt/MediatR.Extensions.FluentValidation.Core.svg)](https://www.nuget.org/packages/MediatR.Extensions.FluentValidation.Core) 
[![NuGet](https://img.shields.io/nuget/vpre/MediatR.Extensions.FluentValidation.Core.svg)](https://www.nuget.org/packages/MediatR.Extensions.FluentValidation.Core)
[![license](https://img.shields.io/github/license/bioyeneye/MediatR.Extensions.FluentValidation.AspNetCore.svg)](https://github.com/bioyeneye/MediatR.Extensions.FluentValidation.Core/blob/master/LICENSE)

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

public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseHttpsRedirection();

    //Add FluentValidation Middleware
    app.UseFluentValidationExceptionHandler();

   //Add other stuffs
    ...
}

```

## Sample Validation

```csharp
public class CreateTodoCommandValidator : AbstractValidator<CreateTodoCommand>
{
    public CreateTodoCommandValidator()
    {
        RuleFor(x => x.Task)
            .NotEmpty();
    }
}

public class CreateTodoCommand : IRequest<Todo>
{
    public CreateTodoCommand(string task, bool isCompleted)
    {
        Task = task;
        IsCompleted = isCompleted;
    }

    public string Task { get; }
    public bool IsCompleted { get;}
}
```
