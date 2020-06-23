FROM microsoft/dotnet-framework-build:4.7.1 as build-env

WORKDIR /app
COPY . /app
RUN nuget.exe restore Tailspin.SpaceGame.Web.csproj -SolutionDirectory ../ -Verbosity normal  --isolation=hyperv
RUN MSBuild.exe Tailspin.SpaceGame.Web.csproj /t:build /p:Configuration=Release /p:OutputPath=./out  --isolation=hyperv

FROM microsoft/dotnet-framework:4.7.1
WORKDIR /app
COPY --from=build-env app/out .
