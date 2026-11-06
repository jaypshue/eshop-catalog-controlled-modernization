# Controlled modernization of the eShop Catalog module

Starting point: the legacy ASP.NET MVC (.NET Framework) Catalog area from  
[dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing)  
(eShopLegacyMVCSolution).

Microsoft’s sample “modernization” of this application was a lift-and-shift to Windows Containers. The application code and framework remained largely unchanged.

## What was done

Used EngineOS to run a controlled modernization of the Catalog area:

1. An Engineering Request defined the scope (CatalogController, CatalogService, related models, tests).
2. EngineOS generated a concrete implementation plan.
3. The plan was explicitly approved by a human before any code was written.
4. The Coder executed only after approval.
5. The result was recorded with file changes and verification.

## What changed

- Catalog controller, service, and interface moved toward ASP.NET Core style.
- Focused unit tests added for the Catalog service.
- Supporting files updated only as needed (project, DI registration).
- A change record (`CATALOG-MODERNIZATION.md`) documents what was changed and what was left unchanged.

## Verification

Command used:

    dotnet test .\eShopPorted.Tests\eShopPorted.Tests.csproj

Result: 6 tests passed.

The original eShopLegacyMVC project still has an environmental build dependency on Visual Studio Web Application targets. That failure is unrelated to the Catalog changes.

## What this demonstrates

A scoped, human-approved, evidence-backed modernization that goes beyond containerization. The dual-approval flow (request → derived plan → explicit approval → recorded result) keeps the change bounded and reviewable.
