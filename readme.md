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

>[!TIP]
>Para saber que as máquinas se "ven", podes facer `ping` entre elas.
>Se o servidor no ten o bash básico `ip` para saber a súa ip, podes instalalo con:`apt update && apt install iproute2`

  ## 4. Mostra unha páxina html aloxada no apache2 dende o teu navegador.
   Agora como a miña carpeta "compartida" e o "htdocs" do servidor están montadas, creo na miña máquina un documento de texto chamado index.html, cuna páxina web básica en código HTML simple.
![Esto es un texto de prueba alternativo a la imagen.](https://github.com/luk295/P2.Montando-volumes-en-Apache/blob/main/imagen.png)


4.1 Para añadir a imaxe, fixen unha captura. Gardei a imaxe no repositorio e fixen git commit e git push.
4.2 Logo copiei o enlace da imaxe, que se encuentra xa no repositorio remoto. Seguindo os pasos de MarkDown.
 
 ## 5. Crea un contenedor 'asir_web1' que use este mesmo directorio para 'htdocs' e o puerto 8000

>[!NOTE]
>Creamos o contenedor co comando: `docker run --name "asir_web1" -it -p 8000:80 -v "$PWD"/compartida:/usr/local/apache2/htdocs/ httpd`

 Creo o contenedor coas seguintes características:

 O contenedor mapeado no porto 8000:80 (8000 máquina real : 80 porto do servidor.)

 Con a carpeta 'compartida' montada sobre a carpeta htdocs do apache do servidor.

 Unha vez creada, para coñecer a súa ip fago ip a.

 ![A segunda captura, esta vez no porto 8000](https://github.com/luk295/P2.Montando-volumes-en-Apache/blob/main/porto8000.png)

Aquí vexo que as páxinas poden verse aínda que ambos servidores compartan nº de puerto 80...
Isto é porque os contenedores están individualizados e cada un ten o seu propio porto 80.

## 6. Crea outro contenedor 'asir_web2' có el mesmo directorio e otro puerto, como o 8090.Comproba que los dous servidores mostran a mesma páxina

**Fixen sen darme conta, o exercicio 6 tamén no exercicio 5.** 

Así que para abreviar pondré só a explicación, a modo de resumo moi xenérico:

1_ Arranco o contenedor 'asir_web2' co porto 8090 da máquina local e 80 da virtual. Fago tamén bind mount na carpeta común na que me quera montar.

2_ Se o preciso podo instalar os comandos ip e ping para probar se vense as máquinas entre elas.

3_ Vexo no navegador a páxina web entrando coa dirección ip do servidor e o porto no que está recibindo a resposta.

4_ E vense as mesmas páxinas web, utilizando portos distintos da máquina local.