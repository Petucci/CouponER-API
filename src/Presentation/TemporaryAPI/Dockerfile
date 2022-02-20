FROM mcr.microsoft.com/dotnet/sdk:6.0-alpine as build
WORKDIR /app/TemporaryAPI
COPY . .
RUN dotnet restore
RUN dotnet publish -o /app/TemporaryAPI/published-app

FROM mcr.microsoft.com/dotnet/aspnet:6.0-alpine as runtime
WORKDIR /app/TemporaryAPI
COPY --from=build /app/TemporaryAPI/published-app /app/TemporaryAPI
ENTRYPOINT [ "dotnet", "/app/TemporaryAPI/TemporaryAPI.dll" ]