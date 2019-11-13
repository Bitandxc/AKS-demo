FROM microsoft/dotnet:2.1.300-sdk as build-env

COPY NuGet.config ./

WORKDIR /ProjWeb
RUN dotnet restore

COPY . ./

RUN dotnet publish --configuration Release --output releaseOutput --no-restore

FROM microsoft/dotnet:2.1.0-aspnetcore-runtime
WORKDIR /TechTalksAPI
COPY --from=build-env /ProjAPI/releaseOutput ./
ENTRYPOINT ["dotnet","ProjAPI.dll"]

