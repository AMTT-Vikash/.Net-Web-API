FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

COPY ./WebApplication1/WebApplication1.csproj ./WebApplication1/WebApplication1.csproj
COPY *.sln ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o build --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build ./build .
ENV ASPNETCORE_URLS=http://*:5050
EXPOSE 5050
ENTRYPOINT [ "dotnet", "WebApplication1.dll" ]
