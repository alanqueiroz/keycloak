![keycloak](https://www.keycloak.org/resources/images/keycloak_logo_480x108.png)

# Keycloak
Logon único, permitindo a autenticação e autorização de usuários, aplicativos e serviços, trata-se de uma solução opensource da Red Hat.

## Quais são as funcionalidades do Keycloak ?

* Criação de usuário (podendo ser criados pelo administrador do sistema, e habilitado ou não para o próprio usuário se cadastrar);<br>
* Login, “esqueci minha senha”, login com plataformas externas como redes sociais;<br>
* Integração dos usuários com Active Directory;<br>
* Ativação de usuários por confirmação de e-mail;<br>
* Obrigar aceitação de termos de uso antes de logar;<br>
* Customização das páginas que o usuário acessa (como a própria tela de login);<br>
* Serviços para que outras aplicações busquem dados de usuários;<br>
* Criação de permissões que seu sistema vai usar;<br>
* Criação de grupos de usuário;<br>
Entre outras configurações e customizações mais avançadas que você pode definir!<br>

## Instruções para subir o ambiente do keycloak em Docker

Clone o projeto<br>
```shell
git clone https://github.com/alanqueiroz/keycloak.git
```
2 - Acesse o diretório keycloak que foi clonado<br>
```shell
cd keycloak
```
3 - Renomeie o arquivo .env-template para .env<br>
```shell
mv .env-template .env
```
4 - Edite os campos (usuário e senha) referentes a aplicação e banco no arquivo .env, definindo os valores de sua preferência e salve o arquivo.<br>
```shell
# BANCO - MYSQL
DB_PASS_ROOT=SenhaRootMySQL
DB_NAME=keycloak
DB_USER=usr_keycloak
DB_PASS=SenhaDBkeycloak

# APLICACAO - KEYCLOAK
DB_PORT=3306
DB_NAME_KEYCLOAK=keycloak
DB_USER_KEYCLOAK=usr_keycloak
DB_PASS_KEYCLOAK=SenhaDBkeycloak
USER_KEYCLOAK=Admin
PASS_USER_KEYCLOAK=SenhaKeycloak
```
5 - Execute o comando `make up` para construir o ambiente do keycloak<br>
```shell
make up
```
Nota: Para destruir os containers execute `make down`
```shell
make down
```
