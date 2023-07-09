# Comandos úteis 

Lista de comandos úteis

# Google Cloud

*Copiar arquivo do Bucket*:
```console
gsutil cp link_do.zip .
```

*Configurando o gcloud:*
```powershell
gcloud init
gcloud auth login
gcloud auth configure-docker us-central1-docker.pkg.dev
gcloud artifacts locations list # lista de repositórios compatíveis
```

*Enviar imagem para o Artifact Registry*
```powershell
gcloud auth configure-docker us-central1-docker.pkg.dev
docker tag [SOURCE_IMAGE] us-central1-docker.pkg.dev/[PROJECT_ID]/[REPOSITORY]/[IMAGE]
docker push us-central1-docker.pkg.dev/[PROJECT_ID]/[REPOSITORY]/[IMAGE]
```

# Docker 

Exemplo de Dockerfile
```Dockerfile
FROM python:3.10.10-slim-buster

WORKDIR /usr/src/app
COPY . /usr/src/app

RUN pip install --upgrade pip 
RUN pip install -r requirements.txt

EXPOSE 8008

CMD ["python", "manage.py", "runserver", "0.0.0.0:8008"]
```

Comandos para criar imagem e container
```console
docker build -t nome_da_imagem .
docker run -p 8008:8008 --name nome_do_container -d nome_da_imagem  
```

# Github
```console
git clone url_do_repositorio -b nome_da_branch
```

To start over, downloading thebranch and overwriting all your local changes 
```console
git checkout thebranch
git reset --hard origin/thebranch
```

Command to display the information for the latest commit in your local repository:
```console
git log -n 1
```

# Django 

Check last errors raised by **gunicorn**:
```console
less +G gunicorn-error-log
```

```console
# clean gunicorn logs
echo '' > gunicorn-error-log

# Listen to the last modification (similar to the Watch functionality)
tail -f gunicorn-error-log
```

Restart Service and Socket of the Server
```console
sudo systemctl restart <NAME>.service
sudo systemctl restart <NAME>.socket
```
