# Apache2.4-e-PHP-passo-a-passo
Instalação do apache e php no windows

* Clique no Link para fazer o Download do Apache [Download Apache](https://www.apachelounge.com/download/#google_vignette)
* Após download descompactar a pasta e mover a pasta Apache24 para "C:"

* Verificar se a porta 80 está disponível com o comando: **netstat -anb | findstr 0.0.0.0:80** , caso retorne algo altere a porta.
* Acessar a pasta conf e editar o arquivo httpd.conf

* Após abrir o arquivo procurar por **SRVROOT**, o caminho da pasta deve ser iguais
* Procurar a palavra **Listen**, para verficar a porta
* Procurar por **serverName** e colocar um dominio, podendo ser tbm **localhost:80**
* Acessar a pasta **bin** e executa o Apache como um serviço, com o comando **httpd.exe -k install** , após terminar deve-se permitir acesso
* Inciar o serviço **Apache2.4**

