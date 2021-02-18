# QUARKUS

### Requisitos para seguir sem dores:
- Java 11+
- Maven 3.6.2+
- Gerenciador de containers: (Ex.: Docker)

---

## Criando o projeto Quarkus

Para criar um projeto Quarkus pode-se usar o comando Maven abaixo:<br>
`mvn io.quarkus:quarkus-maven-plugin:1.11.3.Final:create`<br>
dessa maneira o prompt do maven solicitará os dados.

Ou pode-se usar o comando:<br>
`mvn io.quarkus:quarkus-maven-plugin:1.11.3.Final:create -DprojectGroupId=com.xpto -DprojectArtifactId=borala -DclassName="com.xpto.borala.Olar" -Dpath="/olar"`<br>
Que já cria o projeto com as nomenclaturas definidas de uma vez.

---

## Modo Desevolvimento

Para rodar o projeto e conhecer o Hot-Reload(Recarregamento Automático), utilizar o comando maven abaixo:<br>
`mvn quarkus:dev`

Nesse momento vc pode alterar o código do endpoint criado e visualizar o resultado(no browser, postman, insomnia, curl) sem precisar fazer o stop/start da aplicação.

---

## Compilação de Executável Nativo

Um grande destaque do Quarkus é a compilação de um executável nativo, que reduz consideravelmente o tamanho da aplicação e consumo de memória (Lógico que como tudo na área de software, **depende** do modo como a aplicação é desenvolvida para que esses benefícios possam ser vistos).
O Quarkus funciona muito bem no contexto de microserviços com pipeline bem definida e deploy em containers.

### Compilação Nativa
Para executar a compilação nativa pode-se utilizar o comando abaixo:<br>
`./mvnw package -Pnative -Dquarkus.native.container-build=true -Dquarkus.native.builder-image=quay.io/quarkus/ubi-quarkus-mandrel:20.3.1.2.Final-java11`

Alguns detalhes do comando:

`quarkus.native.container-build=true`<br>
Esse parametro indica que a compilação nativa deve utilizar um gerenciador de containers(Docker), com isso não é necessária a instalação da JVM compativel (GraalVM like), o que facilita na automatização e evita conflitos na instalação de diferentes JVMs.

`quarkus.native.builder-image=quay.io/quarkus/ubi-quarkus-mandrel:20.3.1.2.Final-java11`<br>
Aqui define-se a imagem (GraalVM like) que será feito o build da aplicação. No exemplo utilizo a imagem Mandrel.

As imagens disponiveis para compilação podem ser consultadas em:<br>
[Mandrel](https://quay.io/repository/quarkus/ubi-quarkus-mandrel?tab=tags) - É uma derivação da Oracle GraalVM CE, otimizada para Java(não inclui suporte a programação poliglota) e utiliza a VM OpenJDK. É recomendado apenas para build em containers Linux.<br>
[GraalVM](https://quay.io/repository/quarkus/ubi-quarkus-native-image?tab=tags) - É a imagem oficial utilizando a GraalVM<br>

## Resumo
A intenção aqui é mostrar como a criação de um projeto Quarkus, pode ser feita de maneira simples, inclusive com a compilação nativa.<br>
O Quarkus tem constantes implementações de funcionalidades e compatibilidade com bibliotecas Java.
Por isso é bom avaliar se as bibliotecas utilizadas no seu projeto são compatíveis com a otimização do Quarkus.<br>
O Quarkus oferece muitas possibilidades como: implementação do microprofile(health, tracing, openAPI, metrics, falt tolerance) e programação reativa<br>
Com certeza é uma grande ferramenta para o desenvolvimento utilizando tendências do mercado(cloud e/ou microserviços).

