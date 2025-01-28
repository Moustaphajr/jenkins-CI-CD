FROM microsoft/dotnet:2.0.0-sdk

WORKDIR /code

ADD ./Worker /code/src/Worker

RUN dotnet restore -v minimal ./Worker \
    && dotnet publish -c Release -o "./" "./Worker/" 

CMD dotnet src/Worker/Worker.dll