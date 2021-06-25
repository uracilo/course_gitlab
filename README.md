# course_gitlab

## Levantar gitlab

```
web:
  image: 'gitlab/gitlab-ee:latest'
  restart: always
  hostname: 'gitlab.example.com'
  environment:
    GITLAB_OMNIBUS_CONFIG: |
      external_url 'http://gitlab.example.com:8929'
      gitlab_rails['gitlab_shell_ssh_port'] = 2224
  ports:
    - '8929:8929'
    - '2224:22'
  volumes:
    - '$GITLAB_HOME/config:/etc/gitlab'
    - '$GITLAB_HOME/logs:/var/log/gitlab'
    - '$GITLAB_HOME/data:/var/opt/gitlab'
```


## Cambiar password

```
gitlab-rake "gitlab:password:reset"
```

## Arrancamos el contenedor con Ubuntu

```
sudo docker run -it ubuntu:latest

```
## Actualizar nuestro ambiente

```
apt-get update
apt-get install wget
apt-get install apache2
apt-get install git
service apache2 start

```
## Clonar nuestro repositorio en el directior de apache

```
cd /var/www/html
rm *
git clone <URL del proyecto> /var/www/html

```
## Regitrar el runner para el pipeline
```
wget -O /usr/local/bin/gitlab-runner https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64

chmod 777 /usr/local/bin/gitlab-runner
gitlab-runner register
gitlab-runner run

```
  
## generar el pipeline
  
```  
  stages:
  - init
  - despliegue

hello:
  stage: init
  script:
    - echo "Hello world!"

deploy:
  stage: despliegue
  script:
    - cd /var/www/html
    - git pull http://<username>:<password>@<url del repositorio>
  
```
  
  
  
  
  
  
  
  
  
  
