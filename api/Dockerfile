# Build Stage
FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build-env

# Set working directory
WORKDIR /generator

# Restore
COPY api/api.csproj ./api/
RUN dotnet restore api/api.csproj
COPY tests/tests.csproj ./api/
RUN dotnet restore tests/tests.csproj

# Copy Src
COPY . .

# Test
RUN dotnet test tests/tests.csproj

# Publish
RUN dotnet publish api/api.csproj -o /publish 

# Runtime Stage
FROM mcr.microsoft.com/dotnet/core/sdk:2.2
COPY --from=build-env /publish /publish
WORKDIR /publish
ENTRYPOINT ["dotnet", "api.dll"]