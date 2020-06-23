# FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 as build-env

# WORKDIR /app
# COPY . /app
# RUN dotnet restore Tailspin.SpaceGame.Web.csproj 
#-SolutionDirectory ../ -Verbosity normal  
#--isolation=hyperv
# RUN MSBuild.exe Tailspin.SpaceGame.Web.csproj /t:build /p:Configuration=Release /p:OutputPath=./out  
#--isolation=hyperv

# FROM mcr.microsoft.com/dotnet/core/aspnet
# WORKDIR /app
# COPY --from=build-env app/out .

# FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env
# WORKDIR /app

# Copy csproj and restore as distinct layers
FROM mcr.microsoft.com/dotnet/core/sdk:3.1
COPY *.csproj ./
RUN dotnet restore ./Tailspin.SpaceGame.Web.csproj 

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release

# Build runtime image
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
# COPY /app/out .
ENTRYPOINT ["dotnet", "Tailspin.SpaceGame.Web.dll"]
