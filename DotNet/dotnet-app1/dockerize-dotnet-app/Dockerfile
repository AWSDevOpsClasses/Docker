#Stage 1: Build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build 

WORKDIR /
#restore
COPY ["./learnwithjon-docker.csproj","image/"]
RUN dotnet restore 'image/learnwithjon-docker.csproj'
#build
COPY [".","image/"]
RUN dotnet build 'image/learnwithjon-docker.csproj' -c Release -o /app/build

#Stage 2: Publish
FROM build AS publish 
RUN dotnet publish 'image/learnwithjon-docker.csproj' -c Release -o /app/publish

#Stage 3: Run
FROM mcr.microsoft.com/dotnet/aspnet:8.0
ENV ASPNETCORE_HTTP_PORTS=6969
# Expose ONTAINER_PORT   [ docker run -p 5051:6969 --name dotnetapi dotnet-api:v1 ] [ HOST_PORT:CONTAINER_PORT ]
EXPOSE 6969
WORKDIR /app
COPY --from=publish /app/publish . 
ENTRYPOINT ["dotnet","learnwithjon-docker.dll"]
