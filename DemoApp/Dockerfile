FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY DemoApp/DemoApp.csproj /src/DemoApp
RUN dotnet restore DemoApp/DemoApp.csproj
COPY . .
RUN dotnet publish DemoApp/DemoApp.csproj -c Release -o /app

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app .
EXPOSE 80
ENV ASPNETCORE_URLS=http://+:80
ENTRYPOINT [ "dotnet", "DemoApp.dll" ]

