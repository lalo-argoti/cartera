# ========= BUILD =========
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Capa cacheable (restore)
COPY CarteraVirtual.csproj .
RUN dotnet restore

# Código fuente
COPY . .
RUN dotnet publish -c Release -o /app/out --no-restore

# ========= RUNTIME =========
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app

COPY --from=build /app/out .

EXPOSE 8000
ENTRYPOINT ["dotnet", "CarteraVirtual.dll"]
