# Hello JPA ☕️
Entendendo o JPA.

O JPA utiliza um modelo de mapeamento chamado **ORM**(Mapeamento Objeto Relacional).
* Esse mapeamento representa **tabelas** de um Banco de Dados relacional através de Classes no Java.

## Exemplos de Mapeamentos:

   BD     |  Java
--------- | ------
Tapela    | Classe
Coluna    | Atributo
Registro  | Objeto

## JPA - Java Persistence API

Para padronizar as interfaces das implementações **ORM** foi criada uma especificação oficial chamada **JPA**(Java Persistence API). Ela descreve como deve ser o compotamento dos frameworks Java ORM que desejarem implementar sua especificação.

* Observação: O JPA é uma interface única, "como se fosse uma tomada, onde você pode plugar vários aparelhos". O JPA é só isso, uma interface, ele não implementa nada, ele não realiza nenhuma função!
* Se a sua aplicação tiver apenas o JPA ela não vai rodar, porque para persistir os dados com JPA é necessário escolher uma **implementação** que irá executar todo o trabalho.

## Como utilizar o JPA

1. Realizar o download da Java Persistence API (JPA) utilizando o Maven ou Gradle.
2. Baixar o Driver JDBC para o banco que será usado. A implementação que usará a JPA precisa do JDBC para realizar as conexões com o BD.
3. Criar o arquivo **persistence.xml** e configurar os seguintes parâmetros:
  * URL da string de conexão
  * Driver
  * endereço do BD
  * Nome do BD
  * Usuário do BD
  * Senha do BD
  * Driver e classes que serão utilizadas pelo JPA.

4. Utilizar as **annotations** nas classes que serão mapeadas para uso so Hibernate.
5. Configurar o **entityManager**
