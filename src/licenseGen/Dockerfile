FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /licenseGen

COPY . /licenseGen
COPY Core.dll /app/
COPY cert.pfx /app/

RUN dotnet restore
RUN dotnet publish -c Release -o /app --no-restore

FROM mcr.microsoft.com/dotnet/sdk:8.0
LABEL org.opencontainers.image.source=https://github.com/Jgigantino31/BitBetter
WORKDIR /app
COPY --from=build /app .

ENTRYPOINT [ "dotnet", "/app/licenseGen.dll", "--core", "/app/Core.dll", "--cert", "/app/cert.pfx" ]
