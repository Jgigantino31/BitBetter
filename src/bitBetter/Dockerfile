FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /bitBetter

COPY . /bitBetter
COPY cert.cer /app/

RUN dotnet restore
RUN dotnet publish -c Release -o /app --no-restore

FROM mcr.microsoft.com/dotnet/sdk:10.0
LABEL org.opencontainers.image.source=https://github.com/Jgigantino31/BitBetter
WORKDIR /app
COPY --from=build /app .

ENTRYPOINT ["dotnet", "/app/bitBetter.dll"]
