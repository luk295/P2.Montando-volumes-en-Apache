# Práctica 2: Montando volumes en apache

## Primeriros pasos:
    Creo o repositorio e engado o readme.md
    Creo o repositorio, e no repositorio local (o clonado), creo o readme.md onde gardarei os rexistros.
   
    git add readme.me,
    git commit -m "mensaxe"
    git push
  
  ## Exercicios:
  ## 1. Comproba que tes a imaxe httpd.
  Para comprobar que teño a imaxe de Docker httpd, escribo o comando
  `docker image ls`.

  ## 2. Crea un contenedor de nome "asir_httpd".
  Executo o comando
  `sudo docker run --name 'asir_httpd' -it httpd bash` para crear o contenedor coa imaxe httpd e o nome asir_tppd.

  ## 3.Mapea o porto 80 do contenedor có 8080 da túa máquina.
Para mapear o contenedor volvo a crear un contenedor mapeando o porto e utilizando bind mount para montar o directorio do apache2 'htdocs' nun directorio da miña elección.

   ### 3.1.Creo primero a carpeta onde o directorio apache estará montado: `mkdir compartida` 
   ### 3.2.creo o contenedor co comando: `docker run --name "asir_httpd" -it -p 8080:80 -v "$PWD"/compartida:/usr/local/apache2/htdocs/ httpd`

[!TIP]
>Para saber que as máquinas se "ven", podes facer `ping` entre elas.
>Se o servidor no ten o bash básico `ip` para saber a súa ip, podes instalalo con: `apt update && apt install iproute2`

  ## 4. Mostra unha páxina html aloxada no apache2 dende o teu navegador.
   Agora como a miña carpeta "compartida" e o "htdocs" do servidor están montadas, creo na miña máquina un documento de texto chamado index.html, cuna páxina web básica en código HTML simple.

 