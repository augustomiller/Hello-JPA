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
* Se a sua aplicação tiver apenas o JPA ela não vai rodar, porque para persistir os dados com JPA é necessário escolher uma **implementação** que irá executar todo o trabalho, por exemplo o 'Hibernate'.
* O JPA "terceiriza" tudo ;)

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

6. Configurar o **entityManager** (Manipular as classes que foram mapeadas).
* O EntityManager é utilizado para gerenciar o ciclo de vida das entidades. Principais métodos são (find, persist e remove).

![Captura de Tela 2021-08-09 às 17 45 14](https://user-images.githubusercontent.com/990877/128772147-a5744b94-6b60-4ff0-87b1-e00d92347d19.png)

## Persistir os dados no banco de dados:

Para persistir dados com as entidades mapeadas, é obrigatório iniciar uma transação. Para manipular transações é necessário utilizar o seguinte método do **entityManager**:
* **getTransaction**: Retorna uma **EntityTransaction**, sendo obrigatório o seu uso quando utilizar algum método que realiza alterções no banco de dados.

Pode utilizar os seguintes métodos:
* **begin**: Inicia uma transação;
* **commit**: Finaliza uma transação, persistindo todos os dados que foram modificados desde o início da transação;
* **rollback**: Finaliza uma transação, revertendo todos os dados que foram modificados desde o início da transação.

# Implementação da JPA | Hibernate ⎔

* Hibernate é uma ferramenta ORM Open Source e é a lider no mercado, foi a inspiração para a especificação da JPA.

Para utilizar Hibernate para implementar JPA, basta seguir os seguintes passos:
1. Realizar o download da API de implementação através so Maven ou Gradle.

![Captura de Tela 2021-08-09 às 18 12 27](https://user-images.githubusercontent.com/990877/128775141-57f5521a-6422-4ba0-8e17-41dbaa0ff7eb.png)

2. Modificar o arquivo **persistence.xml** configurando a tag **<provider>** indicando a classe da implementação que será utilizada.
   
![Captura de Tela 2021-08-09 às 18 17 36](https://user-images.githubusercontent.com/990877/128775765-ce894b80-4e5b-494f-9378-a840169e90e7.png)
   
# JPQL | Java Persistence Query Language
* O SQL interage diretamente com o BD, o JPQL interage com as Entidades utilizando as propriedades da Orientação a Objetos.

Porque usar o JPQL e não o entityManager?
   
* Operações de busca, atualização e remoção de entidades em "Massa", ao invés de realizar operações em apenas uma instância por vez através de chaves primárias.
* Realizar consultas mais complexas;
* Realizar funções de agragação;
   
