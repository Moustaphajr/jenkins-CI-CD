# Utilisation du SDK .NET pour la construction
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build

WORKDIR /source
COPY *.csproj . 
RUN dotnet restore

COPY . . 
RUN dotnet publish -c release -o /app --self-contained false --no-restore

# Image d'exécution avec .NET Runtime
FROM mcr.microsoft.com/dotnet/runtime:7.0

WORKDIR /app
COPY --from=build /app . 
ENTRYPOINT ["dotnet", "Worker.dll"]
