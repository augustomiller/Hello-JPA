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
  * Exemplo:

![Captura de Tela 2021-08-09 às 17 16 33](https://user-images.githubusercontent.com/990877/128768730-1d7fad6c-a768-416b-bb4e-b39d5ef268db.png)


4. Mapeamento - utilizar as **annotations** nas classes que serão mapeadas para uso so Hibernate.
* @Entity: indica a aplicação que os objetos da classe especificada serão persistidos no banco de dados. @Entity quer dizer que a Classe Aluno tem uma representação dela no banco de dados (Tabela Aluno);

![Captura de Tela 2021-08-09 às 17 23 46](https://user-images.githubusercontent.com/990877/128769559-b4f44eaa-c891-4cc6-80a6-967d86a492b0.png)

Nas annotations de relacionamento, a propriedade "fetch" exige atenção especial. Seus possíveis valores são **eager**(ansioso) ou **lazy**(preguiçoso).
* **Eager**: a entidade mapeada com esse atributo sempre será carregada na aplicação, mesmo que nunca seja usada durante a execução da aplicação.
* **Lazy** a entidade mapeada com esse atributo somente será carregada na aplicação quando está for explicitamente consultada pela entidade que está mapeando.

6. Configurar o **entityManager** (Manuseia as classes que foram mapeadas).
* O EntityManager é utilizado para gerenciar o ciclo de vida das entidades. Principais métodos são (find, persist e remove).

![Captura de Tela 2021-08-09 às 17 45 14](https://user-images.githubusercontent.com/990877/128772147-a5744b94-6b60-4ff0-87b1-e00d92347d19.png)

