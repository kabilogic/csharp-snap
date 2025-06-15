# hello-csharp

A simple self-contained .NET console application packaged as a Snap using Snapcraft and LXD.

---

## Features

- .NET 8 self-contained build (no runtime dependency)
- Snapcraft packaging with strict confinement
- Includes `libicu` for Unicode and globalization support
- CLI executable available as `hello-csharp`

---

## Project Structure

hello-csharp/
├── snapcraft.yaml # Snap definition
└── HelloCsharpApp/
├── HelloCsharpApp.csproj
├── Program.cs
└── publish/ # Dotnet publish output

---

##  Setup Instructions

### 1. Create & Build .NET App

```bash
dotnet new console -n HelloCsharpApp
cd HelloCsharpApp
dotnet publish -c Release -r linux-x64 --self-contained true -p:PublishSingleFile=true -o publish
cd ..
```
### 2. Create snapcraft.yaml
### 3. Build the Snap
```
snapcraft  # Will prompt to install LXD if needed
```
### 4. Install and Run
```
sudo snap install hello-csharp_1.0.0_amd64.snap --dangerous
hello-csharp
```
### Troubleshooting
ICU error?
Install libicu70 via stage-packages, or add this to .csproj:
```
<InvariantGlobalization>true</InvariantGlobalization>
```
or
Add the ICU dependency in your snapcraft.yaml:
```
parts:
  hello-csharp:
    ...
    stage-packages:
      - libicu70
```
This ensured that the ICU (International Components for Unicode) library — which .NET uses for globalization and string operations — is bundled into the Snap during the build.
---
## References
- [Snapcraft Documentation](https://snapcraft.io/docs)
- [.NET Deployment Guide](https://learn.microsoft.com/en-us/dotnet/core/deploying/)
- [.NET Globalization Options](https://learn.microsoft.com/en-us/dotnet/core/runtime-config/globalization)

