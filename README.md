# 📦 hello-csharp

A simple self-contained .NET console application packaged as a Snap using Snapcraft and LXD.

---

## 🚀 Features

- .NET 8 self-contained build (no runtime dependency)
- Snapcraft packaging with strict confinement
- Includes `libicu` for Unicode and globalization support
- CLI executable available as `hello-csharp`

---

## 🧱 Project Structure

hello-csharp/
├── snapcraft.yaml # Snap definition
└── HelloCsharpApp/
├── HelloCsharpApp.csproj
├── Program.cs
└── publish/ # Dotnet publish output

---

## 🛠 Setup Instructions

### 1. Create & Build .NET App

```bash
dotnet new console -n HelloCsharpApp
cd HelloCsharpApp
dotnet publish -c Release -r linux-x64 --self-contained true -p:PublishSingleFile=true -o publish
cd ..
