FROM mcr.microsoft.com/dotnet/core/sdk as build-env

WORKDIR /app
COPY . /app
RUN dotnet restore Tailspin.SpaceGame.Web.csproj 
#-SolutionDirectory ../ -Verbosity normal  
#--isolation=hyperv
RUN MSBuild.exe Tailspin.SpaceGame.Web.csproj /t:build /p:Configuration=Release /p:OutputPath=./out  
#--isolation=hyperv

FROM mcr.microsoft.com/dotnet/core/aspnet
WORKDIR /app
COPY --from=build-env app/out .
