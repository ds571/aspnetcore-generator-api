# Compiling and Publishing Application (Build Stage)
FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build-env
WORKDIR /api
COPY api.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -o /publish

# Runtime Image Stage
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim
WORKDIR /publish
# Copy from stage 0 above
COPY --from=build-env /publish .
WORKDIR /publish
ENTRYPOINT ["dotnet", "api.dll"]