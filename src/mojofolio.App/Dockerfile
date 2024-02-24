FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /source

COPY *.sln .
COPY mojofolio.App/*.csproj ./mojofolio.App/
RUN dotnet restore

COPY mojofolio.App/. ./mojofolio.App/
WORKDIR /source/mojofolio.App
RUN dotnet publish -c release -o /app --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["dotnet", "mojofolio.App.dll"]