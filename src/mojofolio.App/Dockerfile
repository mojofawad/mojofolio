FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env
WORKDIR /mojofolio.App

COPY . ./
RUN dotnet restore
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /mojofolio.App
COPY --from=build-env /mojofolio.App/out .
ENTRYPOINT ["dotnet", "mojofolio.App.dll"]
EXPOSE 80