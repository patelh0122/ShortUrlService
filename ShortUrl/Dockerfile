ARG VERSION=8.0-alpine

FROM mcr.microsoft.com/dotnet/sdk:$VERSION AS build
WORKDIR /app

COPY ./src/*.csproj ./
RUN dotnet restore

COPY ./src/*.* .

RUN dotnet publish -c Release -o /out --no-restore


FROM mcr.microsoft.com/dotnet/aspnet:$VERSION AS runtime
WORKDIR /app
COPY --from=build /out ./
ENTRYPOINT ["dotnet", "ShortUrl.dll"]