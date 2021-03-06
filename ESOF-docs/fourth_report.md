# Relatório 4 - ESOF #
## Verificação e Validação de Software ##
### Introdução

Este relatório tem como objetivo a análise dos processos de verificação e validação (V&V) no desenvolvimento da aplicação Android WordPress. 

Iremos explorar a testabilidade do software. Será analisado o grau de controlabilidade, de observabilidade,  de isolabilidade, de separação, de inteligibilidade e de heterogeneidade associados aos componenetes do projeto. Por fim, serão apresentadas estatísticas reveladoras da verificação e validação do software.
Esta avaliação será acompanhada de exemplos e de referências que suportam a nossa interpretação.

### Testabilidade do Software

Iremos agora avaliar o quão testável o projeto WordPress para Android é, isto é, até que ponto é possível verificar e validar o mesmo em termos de implementação. É importante salientar que depois de analisado o código e lido algumas especificações podemos constatar que o projeto utiliza a [Android Testing Framework] (http://developer.android.com/intl/ko/tools/testing/testing_android.html) que proporciona uma arquitetura bem como um conjunto de ferramentas que permitem testar todos os aspetos da aplicação, através de testes unitários.

![test_framework](http://developer.android.com/images/testing/test_framework.png)


#### Controlabilidade

A extensão [Android JUnit] (http://developer.android.com/intl/ko/tools/testing/testing_android.html#JUnit) proporciona  classes especificas para os casos de teste. Estas classes proporcionam métodos de auxilio para criar *mock objects* e métodos para controlar o ciclo de vida de um componente.
As ferramentas proporcionadas são um conjunto de métodos ou *"hooks"* do sistema Android. Estes *"hooks"* controlam cada componente independentemente do seu ciclo de vida normal bem como o *loading* de aplicações.

É ainda de salientar que é utilizada a ferramente [Travis](https://travis-ci.org/) que permite sincronizar o projeto (existente no GitHub) com o Travis que, por sua vez, testa o codigo rápidamente. Os testes são realizados ao nível dos *packages* e permite correr testes em paralelo, bem como ver os testes em tempo real e detalhadamente.


#### Observabilidade
Como já foi referido anteriormente, as duas ferramentas usadas no projeto WordPress para Android, para efeitos de teste, são a extensão Android JUnit, para testes unitários, e o Travis, para testes de integração.
A extensão Android JUnit contem um conjunto de ferramentas que facilitam os testes. Em termos de observabilidade a extensão proporciona uma class *Observable* que permite notificar alterações nas classes, ou seja qualquer alteração nas propriedades da mesma. Existem ainda a classe *TestListener* e outras classes que facilitam a observabilidade dos testes pois permitem num estado intermédio e final verificar isoladamente os resultados. Permite ainda a execução de testes em processos paralelos, o que resulta num melhor desempenho.
Por outro lado a ferramenta Travis sujeita os pull requests a vários testes automatizados definidos, de forma a possibilitar a adição, sem conflitos das novas funcionalidades. Estes testes não são testes de aceitação, mas antes testes de integração sobre o código submetido. Na página da ferramenta, é possível ver o resultado dos testes realizados sobre os pull requests submetidos ao projeto do React.


#### Isolabilidade
No que diz respeito ao isolamento de cada componente aquando a criação de testes unitários, é necessário ter em conta que para diferentes componentes o isolamento pode ser diferente. Isto vem do facto de haver componentes dependentes de outros, fazendo com que o isolamento não seja o ideal. Quão mais básico o componente for, mais isolado e independente ele se torna, podendo então ter testes unitários que acabam por ser mais viáveis pois não ficam dependentes de o código de outros componentes estar bem realizado ou não. 

Por exemplo, usando a classe de testes geral existente para o blog [(BlogTest.java)](https://github.com/wordpress-mobile/WordPress-Android/blob/develop/WordPress/src/androidTest/java/org/wordpress/android/models/BlogTest.java) pode-se comprovar que se trata de uma suite de testes bem isolada, testando a classe Blog, havendo testes para os diversos atributos desta, assim como de todos os seus métodos de *sets* e *gets*. Pode-se referir que a maior parte das suites de testes criadas para este projeto isolam bem os seus componentes, embora não haja muita abundância de testes.


#### Separação
Na realização de projetos com uma dimensão considerável há que ter em conta à forma como o código está estruturado, tentado torná-lo sempre o mais modular possível. O que isto quer dizer é que se isto não acontecer, pode levar a tornar o código confuso, fazendo com que este se torne mais difícil de se desenvolver em ambientes com vários colaboradores.

Como tal, a separação das funcionalidades deve ser algo a ter em conta para facilitar tudo isto, ou seja, como foi referido no ponto anterior, tentar isolá-los de forma a facilitar a realização de testes unitários.

No caso deste projeto em si, a separação de funcionalidades é algo que têm em conta, dado a sua [estruturação](https://github.com/wordpress-mobile/WordPress-Android/tree/develop/WordPress/src/main/java/org/wordpress/android), no entanto é de referir que no que diz respeito à separação de funcionalidades nos testes unitários esta é realizada mas não abrange todas as funcionalidades da aplicação.


#### Inteligibilidade

O projeto, como já foi mencionado nos relatórios anteriores apresenta uma estrutura, organização e regras bem definidas para os possíveis desenvolvedores, aplicando-se o mesmo aos testes unitários.
Existe um package “androidTest” onde contém tudo o que é relacionado com os testes unitários. Este package contém um ficheiro readme.md onde explica como se corre os testes assim como se limpa a base de dados existente.
A grande maioria das classes tem nomes auto explicativos estando também documentadas através de comentários e hiperligações com informações adicionais.


#### Heterogeneidade

Como já foi mencionado, este projeto baseia-se no Android Testing Framework, assim, utiliza a API do JUnit para trabalhar com os testes unitários. A extensão para Android do JUnit faculta diferentes classes específicas para diferentes casos de forma a facilitar a implementação dos testes.
Na página de explicação do Android Testing Framework é possível ler:

>“Test suites are contained in test packages that are similar to main application packages, so you don't need to learn a new   set of tools or techniques for designing and building tests"

Podemos perceber que o Junit facilita muito a implementação dos testes unitários e reduz a utilização de outros métodos e/ou ferramentas para uma possível complementação, pelo que se apresenta como uma ferramenta única mas completa de modo a centralizar e unificar os esforços ao nível da implementação dos testes unitários.

Ainda assim, para além da utilização do JUnit, os desenvolvedores utilizam ainda o Travis, uma ferramenta de integração ao GitHub que permite verificar o código na altura de fazer commit, para isso, o travis tenta compilar e verificar os testes unitários implementados, notificando o desenvolvedor.


### Estatísticas de Teste

Para proceder à análise estatística de testes deste projeto encontramos algumas dificuldades para compilar e correr a ferramenta que eles utilizam para criar um log dessas estatísticas. Como tal, conseguimos realizar uma cobertura, usando o [Android Studio](https://developer.android.com/sdk/index.html), não ideal mas que dá uma ideia de como o projeto está estruturado relativamente a testes unitários. Na imagem seguinte pode-se ver a quantidade de classes de produção de código, assim como o número de classes de testes unitários.

![testes](./images/testes.png)

* Número de classes de testes unitários automáticos: 78
* Número de classes: 1977

### Análise Crítica

De um modo geral, nota-se uma clara preocupação por parte da equipa do WordPress em ter uma biblioteca automatizada de testes por forma a validar e verificar os componentes de software através da Android Testing Frameword e do Travis. É importante ainda salientar que a equipa utiliza a framework [RoboElectric](http://robolectric.org/), uma framework de testes unitários que utiliza o jar do Android SDK para correr testes de sobre aplicações Android sendo que estes ocorrem dentro da JVM da workstation em questão e ocorrem em poucos segundos. 

A Android Testing Framework por integrar testes unitários através da API JUnit torna-se muito viável e facilmente implementável devido à [documentação fornecida pelo google para developers](http://developer.android.com/intl/ko/tools/testing/testing_android.html). Acrescentando o facto da framework RoboElectric, mencionada acima, torna os testes mais rápidos e facilmente executaveis acreditamos ser uma implementação exemplar.

A contínua integração das várias contribuições dos variados colaboradores do projeto é possibilitada pela ferramenta Travis.Esta desempenha um papel muito útil ao nível da realização de testes de integração sobre o código submetido em pull requests e facilita o trabalho à equipa WordPress.


### Autores



* Fábio Amarante
* Luís Gonçalves
* Ricardo Lopes


## Contribuição

Relativamente à contribuição de cada elemento para a realização deste relatório, o grupo considera que o trabalho foi igualmente dividido pelos três elementos.
