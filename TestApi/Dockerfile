FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build

LABEL stage=build

COPY . .

RUN dotnet publish "TestApi.csproj" -r linux-x64 -c Release -o /app/publish

 

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS final

WORKDIR /app

COPY --from=build /app/publish .

ENTRYPOINT [ "dotnet", "TestApi.dll" ]
