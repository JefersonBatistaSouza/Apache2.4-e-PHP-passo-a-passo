# Apache2.4-e-PHP-passo-a-passo
### Instalação do apache no windows

* Clique no Link para fazer o Download do Apache [Download Apache](https://www.apachelounge.com/download/#google_vignette)
* Após download descompactar a pasta e mover a pasta Apache24 para "C:"

* Verificar se a porta 80 está disponível com o comando: **netstat -anb | findstr 0.0.0.0:80** , caso retorne algo altere a porta.
* Acessar a pasta conf e editar o arquivo httpd.conf

* Após abrir o arquivo procurar por **SRVROOT**, o caminho da pasta deve ser iguais
* Procurar a palavra **Listen**, para verficar a porta
* Procurar por **serverName** e colocar um dominio, podendo ser tbm **localhost:80**
* Acessar a pasta **bin** e executa o Apache como um serviço, com o comando **httpd.exe -k install** , após terminar deve-se permitir acesso
* Inciar o serviço **Apache2.4**

### Instalação do PHP

* Clique no link para fazer download do php [PHP DOWNLOAD](https://www.php.net/)
* Após baixa extrair para a pasta C: e de preferência renomea-la. **Exemplo: php7.4**
* Renomei o arquivo php.ini-development para php.ini
* Acesse o arquivo php.ini e descomente as seguintes extenções

    > extension=curl  
    > extension=gd2  
    > extension=mbstring  
    > extension=openssl
    > extension=pdo_firebird  
    > extension=pdo_mysql
    > extension=pdo_odbc  
     
 * Descomente também
    
    > session.save_path ="/tmp"  
    
    
* e aponte para pasta temporária do windows

    >session.save_path ="C:/Windows/temp"  
    
* Devemos mostrar onde estão as DLLs descomentando a linha a seguir:
  
    > extension_dir = "ext"
    
 * Agora temos que dizer pro Apache que o PHP está instalado na maquina, volte para a pasta do Apache e abra novamente o arquico httpd.conf.
  
   > Abaixo destas linhas:  
   > _AddType application/x-compress .Z_  
   > _AddType application/x-gzip .gz .tgz_  
   
 * escreva:
   
   > AddHandler application/x-httpd-php .php  
   > AddType application/x-httpd-php .php .html  
   > Action application/x-httpd-php "C:/php7.4/php-cgi.exe"
   
 * Após isso devemos procurar as diretivas LoadModules, e abaixo de todas elas vamos adicionar uma outra LoadModules a seguir:
 
   > LoadModule php7.4_module "C:/php7.4/php7apache2_4.dll"
  
 * Após isso no final do arquivo vamos adicionar uma diretiva chamada:
 
   > PHPIniDir "C:/php7.4"  
   > Timeout 240

 * Adicione também mais um arquivo padrão, pesquise por index.html e modifique a linha confome abaixo:
   
   > DirectoryIndex index.php index.html
   
 * Salva o arquivo e renicie o apache e crie um arquivo index.php dentro da pasta htdocs do apache com o seguinte comando
 
    ~~~PHP
        <?php phpinfo(); ?>
    ~~~
    
  * Se tudo ocorreu bem, você verá a tela de informações do PHP.
 
