FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env
WORKDIR /App

EXPOSE 80
EXPOSE 5024

COPY . ./

ENV MY_SECRET_KEY = ${MY_SECRET_KEY}

RUN dotnet restore
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /App
COPY --from=build-env /App/out .

ENTRYPOINT ["dotnet", "GitHubSecretExample.dll"]