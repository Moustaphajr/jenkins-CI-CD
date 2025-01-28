# Utilise l'image SDK de .NET pour la construction
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build

WORKDIR /source

# Copie les fichiers .csproj et restaure les dépendances
COPY *.csproj .
RUN dotnet restore

# Copie tout le code source et construit l'application
COPY . .
RUN dotnet publish -c Release -o /app

# Crée une image plus légère pour l'exécution
FROM mcr.microsoft.com/dotnet/runtime:7.0

WORKDIR /app

# Copie l'application publiée depuis l'image de build
COPY --from=build /app .

ENTRYPOINT ["dotnet", "Worker.dll"]
