FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
COPY Challenge1/Challenge1.csproj Challenge1/
RUN dotnet restore Challenge1/Challenge1.csproj
COPY . .
WORKDIR /src/Challenge1
RUN dotnet build Challenge1.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish Challenge1.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "Challenge1.dll"]
