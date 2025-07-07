FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY DotNetMinimalAPIDemo.csproj .
RUN dotnet restore DotNetMinimalAPIDemo.csproj
COPY . .
RUN dotnet publish DotNetMinimalAPIDemo.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT [ "dotnet", "DotNetMinimalAPIDemo.dll" ]