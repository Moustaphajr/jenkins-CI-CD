# Utilisation de la plateforme spécifique (exemple : linux/arm64/v8)
FROM --platform=linux/arm64/v8 mcr.microsoft.com/dotnet/sdk:7.0 AS build

ARG TARGETPLATFORM
ARG TARGETARCH
RUN echo "I am running on  building"

WORKDIR /source
COPY *.csproj . 
RUN dotnet restore -a $TARGETARCH

COPY . . 
RUN dotnet publish -c release -o /app -a $TARGETARCH --self-contained false --no-restore

# Image finale de l'application
FROM mcr.microsoft.com/dotnet/runtime:7.0
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "Worker.dll"]
