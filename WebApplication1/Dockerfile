FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app

COPY *.csproj .

RUN dotnet restore

COPY . ./

RUN dotnet publish --no-restore -c Release -o out

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /app
COPY --from=publish /app/out .
ENTRYPOINT ["dotnet", "WebApplication1.dll"]