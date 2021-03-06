# Relatório 1 - ESOF #
## Descrição do projeto ##

O WordPress é uma das mais famosas ferramentas na criação de blogues, principalmente via web e é, normalmente, adotado por pessoas que procuram um blogue mais profissional e com mais recursos.

Encaramos a sua abordagem no mundo móvel e neste caso no líder de mercado, Android, como um forte pensamento de liderança, desenvolvimento e interesse no projeto. O seu rápido crescimento e utilização massiva é explicada pelo seu tipo de licença livre, facilidade de uso e principais características e recursos.

Este projeto encontra-se em desenvolvimento no GitHub (https://github.com/wordpress-mobile/WordPress-Android) e apresenta uma dimensão considerável: perto de meia centena de colaboradores ,mais de onze mil submissões de código (commits) e com 38 ramos (branches). É frequentemente atualizado, sendo que apresenta atualizações importantes a cada mês. É um projeto muito organizado, simples e claro a nível de colaboração e apresentação do projeto.

Tudo isto mostra o interesse dos participantes e da organização mãe que defende o lema “We are passionate about making the web a better place”.

A aplicação está disponível no Google Play e apresenta até ao momento entre 5 a 10 milhões de donwloads e quase oitenta mil classificações, muitas delas positivas, o que permitem uma classificação de quatro ponto dois em cinco.


## Processo ##

Embora tenhamos tentado comunicar com vários dos contribuidores não obtivemos respostas da maior parte dos que tentámos contactar daí não termos determinado o processo. No entanto, o o modelo utilizado no desenvolvimento do projeto segue alguns princípios Agile. À medida que novos requisitos são determinados a partir do feedback dos utilizadores, programadores e colaboradores é iniciado um processo focado na correcão e evolução contínua do software, com novas versões a ser lançadas de forma constante e activa.

A nível de colaboração, esta é facilitada pela página oficial para contribuidores onde possui um pequeno tutorial de como começar a usar o GitHub, realizando um fork e um clone do seu repositório, de maneira a facilitar o desenvolvimento na máquina de cada um e sem causar estragos no repositório original.

Existe também uma secção em que explicam como o seu sistema de controle de versão está definido, como se pode ver de seguida:
* Versão x.y (2.8 ou 4.0 por exemplo) destinam-se a lançamentos grandes. Não há distinção entre uma versão 2.9 ou uma versão 3.0, querendo evitar nomear como 2.142 assim a versão após X.9 (2.9) é simplesmente x + 1,0 (3,0). A nova versão principal é lançada a cada 4 semanas, aproximadamente.
* Versão x.y.z (2.8.1 ou 4.0.2 por exemplo) destinam-se a lançamentos de hotfixes (correcções). São lançados apenas quando existe uma grande falha na versão atualmente lançada.

Em relação ao estilo de código, optaram por usar como base as regras usadas para Android (https://source.android.com/source/code-style.html), modificando apenas duas regras:
* Comprimento de linha é de 120 caracteres
* FIXME não deve ser usado no repositório, substituindo por TODO. FIXME pode ser usado unicamente no repositório local
Sendo existe um processo de verificação em que é gerado um relatório em html.

A maneira como a equipa organiza as *branches* recorrem a um modelo bastante dinâmico e de fácil entendimento por todos os elementos da equipa, permitindo criar mais ramos sem se tornar um projeto confuso. Este modelo intitula-se de *Git flow branching* e resume-se a no seu núcleo possuir dois ramos principais:

* master - é o ramo destinado ao código fonte que se encontra pronto e estável a ser lançado, ou seja, neste ramo são lançadas as versões finais do projeto.
* develop - é o ramo destinado ao código fonte onde estão a ser implementadas alterações para a próxima versão, ou seja, é considerado como um ramo de integração porque quando o código se encontra estável e as alterações planeadas estejam realizadas, deve ser realizado um *merge* com o ramo master e ser-lhe atribuído uma versão de lançamento.

Para além destes dois ramos principais, existem os ramos secundários destinados a apoiar o desenvolvimento paralelo entre os membros da equipa, permitindo saber que funcionalidades estão a ser implementadas, preparar para futuros lançamentos e para ajudar rapidamente a resolver problemas na linha de produção. Estes ramos, ao contrário dos principais, têm um tempo de vida limitado, uma vez que acabam por ser removidos eventualmente. Existem três tipos de ramos:

* *Feature branches* - Estes ramos servem para desenvolvimento de novas funcionalidades para a aplicação ou para uma versão distante desta. Estes ramos são essencialmente criados a partir do develop e mais tarde, quando a funcionalidade está bem implementada e estável, acabam por levarem *merge* com o develop.
* *Release branches* - Estes ramos servem para preparar a versão de lançamento final, ou seja, ajuda a aperfeiçoar o código e a eliminar qualquer tipo de problema antes da versão final ser lançada no master.
* *Hotfix branchs* - Estes ramos são muito semelhante aos ramos do master e servem para corrigir erros minimamente preocupantes na aplicação. Permitem que a equipa continue a desenvolver o seu trabalho no develop, enquanto um ou mais membros se dedicam a corrigir o erro detetado.

### Slack ###

WordPress utiliza Slack como principal plataforma de comunicação em tempo real e assim sendo juntámo-nos à página. É aberta a qualquer pessoa sendo que basta fazer o pedido e é enviado o convite sem qualquer tipo de critérios. Já foram implementados várias ferramentas por forma a melhorar o desempenho dos seus colaboradores como, por exemplo, a implementação de bots de Trac e SVN. Assim sendo, sempre que um utilizador quer aceder a um pedido ou alteração de versão basta introduzir, por exemplo, #12345 e um bot irá imprimir o URL desse ticket e outras informações. Os tickets contém informações sobre a ocorrência, sendo que esta pode ser um relatório de bug, pedido, etc, informações sobre quem é o responsável pela criação desse ticket e outras informações importantes como anexos e comentários. 

O Slack da Wordpress está dividido em múltiplos canais sendo que existe o canal #core onde são tratados a maior parte dos bugs e impressas as alterações (ou pedidos de alterações) ao código, no entanto existem canais de ajuda bem como canais direcionados somente a partes especificas do código como, por exemplo, #design. São aproximadamente 7000 os membros da página sendo que, durante tempo em que observámos, houve sempre muita actividade nos diferentes canais do Slack especialmente no #core onde há muita interação entre os membros, bem como entreajuda. 


## Análise Crítica ##

Acreditamos que o modelo mais adequado ao projeto em mãos, modelo este que achamos ser o modelo utilizado pelos desenvolvedores apesar de não termos confirmação, é o Agile. Todos os aspectos de desenvolvimento são constantemente revisitados sendo que são constantemente as situações em que a equipa, ou alguns elementos da mesma, param para re-avaliar o projeto e consequentemente a sua direcção. No entanto, tendo em conta o elevado número de contribuidores é provavel que o modelo Agile não seja necessáriamente o implementado pois o conceito de processo de desenvolvimento de software pode não ser comum entre todos apesar de existir uma clara coordenação principalmente devido ao modelo de submissão de branching utilizado.

![Gráfico de commits](./images/grafico_commits.PNG)

### Commits ###

Desde Setembro de 2009, data em que o repositório foi criado, que este está ativo em termos de commits sendo que especialmente a partir de 2014 a sua atividade aumentou exponencialmente e desde então não decrementou. Apesar da aplicação se encontrar atualmente completa o elevado número de commits por semana (média de 73.45) demonstra que há sempre pormenores a melhorar e features a acrescentar bem como falhas a corrigir.

### Organização ###

#### Código #####

Depois de analisados alguns documentos e consultada a informação disponibilizada pelos próprios contribuidores, é possível concluir que o código está exemplarmente organizado. Como foi mencionado anteriormente as [Android Code Style Guidelines] (https://source.android.com/source/code-style.html) são a base do estilo de código do projeto.

#### Repositório ####

Como mencionado na parte do processo, o modelo de branching utilizado é o [git flow branching model] (http://nvie.com/posts/a-successful-git-branching-model/) que, tal como mencionado na cadeira, é um modelo apropriado. Permitindo um modelo mental elegante que é fácil de compreender e permite aos contribuidores um entendimento comum dos processos de ramificação.

### Objetivos ###

No momento da escrita deste relatório o principal foco dos colaboradores não é a criação de uma aplicação ou de funcionalidades mas sim a finalização de uma aplicação já criada. Como já foi referido o principal objetivo dos colaboradores é corrigir possíveis erros e actualizar a aplicação mantendo a mesma a par dos standards atuais, quer de aspeto ou organização.

Assim sendo, não existem reuniões como o que acontece, por exemplo, no modelo de processo Scrum, pois a aplicação está “concluída” e todo o tipo de comunicações é feita de forma constante e em tempo real pelo Slack.

### Conclusão ###

De uma forma geral, o conjunto de práticas seguidas parece-nos adequado para o desenvolvimento da aplicação. Depois de alguma pesquisa e estudo dos métodos e práticas neste projeto, acreditamos que o modelo Agile seja o mais adequado, devido à sua flexibilidade e às práticas já utilizadas pelos contribuidores quer pela constante comunicação através do Slack quer pelos osbetivos do projeto em si.

## Autores

* Fábio Amarante
* Luís Gonçalves
* Ricardo Lopes
