# Base image
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80

# Build image
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app
COPY backend/*.csproj ./backend/
RUN dotnet restore ./backend/YourBackendApp.csproj
COPY backend/ ./backend/
RUN dotnet publish ./backend/YourBackendApp.csproj -c Release -o /app/publish

# Final image
FROM base AS final
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "YourBackendApp.dll"]
