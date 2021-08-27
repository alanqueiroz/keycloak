# Keycloak
Logon único, permitindo a autenticação e autorização de usuários, aplicativos e serviços, trata-se de uma solução opensource da Red Hat.

## Quais são as funcionalidades do Keycloak ?

Criação de usuário (podendo ser criados pelo administrador do sistema, e habilitado ou não para o próprio usuário se cadastrar);<br>
Login, “esqueci minha senha”, login com plataformas externas como redes sociais;<br>
Integração dos usuários com Active Directory;<br>
Ativação de usuários por confirmação de e-mail;<br>
Obrigar aceitação de termos de uso antes de logar;<br>
Customização das páginas que o usuário acessa (como a própria tela de login);<br>
Serviços para que outras aplicações busquem dados de usuários;<br>
Criação de permissões que seu sistema vai usar;<br>
Criação de grupos de usuário;<br>
Entre outras configurações e customizações mais avançadas que você pode definir.<br>

### Instruções para subir o ambiente do keycloak em Docker ###

1 - Clone o projeto<br> 
2 - Renomeie o arquivo .env-template para .env<br>
2.1 - Edite os campos (usuário e senha) referentes a aplicação e banco no arquivo .env, definindo os valores de sua preferência e salve o arquivo.<br>
3 - Execute o comando "make up" sem aspas para construir o ambiente do keycloak<br>
