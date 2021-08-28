![keycloak](https://www.keycloak.org/resources/images/keycloak_logo_480x108.png)

# Keycloak
Logon único, permitindo a autenticação, autorização de usuários, aplicativos e serviços, trata-se de uma solução opensource da Red Hat.

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

## Instruções para subir o ambiente do keycloak (banco e aplicação) em Docker

1 - Clone o projeto<br>
```shell
git clone https://github.com/alanqueiroz/keycloak.git
```
2 - Acesse o diretório keycloak que foi clonado<br>
```shell
cd keycloak
```
3 - Se deseja construir todo o ambiente (aplicação e banco) em único servidor, recomendado para ambiente de homologação/testes ou com restrição de recursos, renomeie o arquivo .env-template para .env. e siga para o passo 4<br>

- Nota: Se deseja construir um ambiente, onde o container da aplicação fique em um host diferente do host do container do banco, vá para o passo 6

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
5 - Execute o comando abaixo, para construir o ambiente completo (banco e aplicação) do keycloak<br>
```shell
make up
```
Nota: Para destruir o ambiente completo (banco e aplicação) do keycloak, execute o comando abaixo:
```shell
make down
```
6 - Deploy do container do banco (MySQL), renomeie o .env-template-mysql para .env , definindo os valores de sua preferência e salve o arquivo.<br>
```shell
# BANCO - MYSQL
DB_PASS_ROOT=SenhaRootMySQL
DB_NAME=keycloak
DB_USER=usr_keycloak
DB_PASS=SenhaDBkeycloak
```
6.1 - Execute o comando abaixo, para construir o container do banco MySQL
```shell
docker-compose -f mysql.yml up -d
```
7 - Deploy do container da aplicação (Keycloak), renomei o .env-template-keycloak para .env, definindo os valores de sua preferência e salve o arquivo.
```shell
# APLICACAO - KEYCLOAK
DB_PORT=3306
DB_ADDR=ip_ou_dns_servidor_mysql
DB_NAME_KEYCLOAK=keycloak
DB_USER_KEYCLOAK=usr_keycloak
DB_PASS_KEYCLOAK=SenhaDBkeycloak
USER_KEYCLOAK=Admin
PASS_USER_KEYCLOAK=SenhaKeycloak
```
7.1 - Execute o comando abaixo, para construir o container da aplicação Keycloak
```shell
docker-compose -f keycloak.yml up -d
```