# Funcionamentos do Kafka Connector

## Primeiros passos

- Abra um terminal na raiz do projeto e utilize o comando: `docker-compose up -d`
- Para certificar que os containeres estão rodando, abra o control-center no seu navegador: `localhost:9021`

---

### Configurando MySQL (Source):

- Utilize o `docker-compose ps` e copie o nome do container que possuir `mysql`
![img_3.png](img_3.png)

- Logo, vamos entrar no bash do MySql: `docker exec -it fc2-kafka-connector-mysql-1 bash`
- Para acessar o db digite: `mysql -uroot -p fullcycle` e digite a senha: ~~**root**~~
- Crie a tabela de categoria: `create table categories (id int auto_increment primary key, name varchar(255));`
- Adicione um registro: `Insert into categories (name) values('Eletronicos');`

---

### Configurando Source e Sink na interface do ControlCenter:
- Ao abrir o control-center, vamos clicar em cima de `controlcenter.cluster`
  ![img.png](img.png)
- Vamos clicar em `Connect` e depois em `connect-default`
  ![img_1.png](img_1.png)
- Na próxima página clicaremos no botão: `Add Conector`
- E na seguinte página, importaremos nosso arquivo de configuração dos connectors,
que esta em: `fc2-kafka-connector/connectors/mysql.properties`

#### Faça o mesmo procedimento com o arquivo: `mongodb.properties`

![img_2.png](img_2.png)
- Em seguida, vá até o final da página e clique em _**Continue**_, e na página abaixo
clique em Launch.
![img_4.png](img_4.png)
- E assim que criado, ele irá mostrar na tela
![img_5.png](img_5.png)

- O gif abaixo, mostra as informações que cadastramos no MySQL
![gif_explicativo.gif](gif_explicativo.gif)

> Caso queira fazer alguns testes, adicione outras informações na tabela de `categories`
e veja que aparecerá rapidamente na interface de **_Messages_** do ControlCenter.

---

### Conferindo se o MongoDB está recebendo as informações do MySQL:

- Acesse no navegador por: localhost:8085
- Coloque as credenciais `root` em Usuario e Senha

![gif_interface_mongodb.gif](gif_interface_mongodb.gif)
> Caso o database `fullcycle` não apareça, faça um novo insert no db do MySQL

---