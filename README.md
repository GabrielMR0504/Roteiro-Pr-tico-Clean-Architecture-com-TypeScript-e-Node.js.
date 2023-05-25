# Roteiro-Pratico-Clean-Architecture-com-TypeScript-e-Node.js.

### Autores:
#### André Guilherme de Almeida Macedo - Matrícula: 20203018875
#### Celso França Neto - Matrícula: 20203018570
#### Gabriel de Medeiros Ribeiro - Matrícula: 20193025181
#### Jorge Hiroki de Castro Sato - Matrícula: 20203018650

## I. Introdução:

  Clean Architecture é um conceito desenvolvido por Robert C. Martin, conhecido como Uncle Bob, e é amplamente utilizado na indústria para criar sistemas escaláveis e de alta qualidade. Ao seguir os princípios da Clean Architecture, é possível obter um código mais flexível, fácil de entender e adaptável a mudanças futuras.

  Neste roteiro, vamos explorar os fundamentos e a implementação da Clean Architecture, uma abordagem de design de software que promove a separação de preocupações e a manutenção de um código limpo, modular e testável. Iremos nos aprofundar nos princípios e benefícios da Clean Architecture, bem como forneceremos orientações práticas sobre como aplicar esses conceitos em um projeto real usando TypeScript e Node.js. 

  Apresentaremos como estruturar seu código em camadas, definir a lógica de negócios de forma isolada, lidar com a interação com bancos de dados e serviços externos, e criar interfaces de usuário eficientes. Ao final deste roteiro, você estará familiarizado com os princípios da Clean Architecture e será capaz de aplicá-los em seus projetos, resultando em um software mais robusto, testável e de fácil manutenção.

  Vamos iniciar explorando os fundamentos do Clean Architecture e os benefícios que essa abordagem pode trazer para o desenvolvimento de software.


## II. Fundamentos do Clean Architecture

  Antes da implementação prática da Clean Architecture com TypeScript e Node.js, é necessário compreender os fundamentos por trás dessa abordagem de design de software. Iremos descrever os principais conceitos e princípios da Clean Architecture.


### A. Conceitos básicos de arquitetura de software:
A arquitetura de software refere-se à estrutura global de um sistema de software e aos princípios fundamentais que guiam o seu design.
Alguns conceitos básicos e importantes relacionados ao tema são:
 * Modularidade: é a divisão do sistema em módulos independentes, cada um responsável por uma funcionalidade específica.
 * Componentização: ela envolve a construção de um sistema a partir de componentes reutilizáveis. Cada componente é uma unidade coesa e independente, que pode ser implantada e substituída de forma isolada. Isso promove a reutilização de código e facilita a manutenção do sistema.
 * Arquitetura em camadas: O sistema é dividido em camadas distintas, cada uma sendo responsável por funcionalidades específicas. A comunicação entre elas é feita por interfaces bem definidas. Essa abordagem auxilia na separação de preocupações e ajuda na escalabilidade e manutenção do sistema.
 * Padrões de projeto: são soluções comprovadas para problemas comuns de design de software. Eles fornecem abstrações e diretrizes para a criação de sistemas robustos, flexíveis e de fácil manutenção. Exemplos de padrões de projeto incluem MVC (Model-View-Controller), Singleton, Observer, entre outros.
 * Arquitetura em microservices: engloba a produção de um sistema como um conjunto de serviços independentes, com funções de negócio específicas a cada um. São implantados e escalados separadamente, o que permite uma maior flexibilidade, modularidade e longevidade do sistema.
 * Escalabilidade: A arquitetura de software deve permitir que o sistema seja escalável, ou seja, capaz de lidar com o aumento da carga e do número de usuários. Isso pode ser alcançado por meio de técnicas como a divisão em camadas, a utilização de balanceamento de carga e a distribuição de tarefas entre vários servidores.
 * Segurança: A segurança é um aspecto crítico da arquitetura de software. É necessário projetar o sistema de forma a proteger os dados sensíveis, prevenir ataques e garantir a integridade e a confidencialidade das informações. Isso envolve a implementação de práticas de autenticação, autorização e criptografia adequadas.

### B. Princípios do Clean Architecture:
 * Independência de Frameworks: como manter a lógica de negócio isolada de frameworks externos, garantindo flexibilidade e portabilidade.
 * Testabilidade: a importância de projetar um sistema que seja facilmente testável, permitindo a criação de testes unitários e de integração eficazes.
 * Independência de tecnologia: como a Clean Architecture permite que as diferentes tecnologias utilizadas no projeto possam ser substituídas ou atualizadas sem afetar a lógica central do sistema.
 * Separação de camadas: compreender a estruturação das camadas da Clean Architecture, como a camada de domínio, casos de uso, infraestrutura e interfaces de usuário.
 * Independência de Banco de Dados: O acesso ao banco de dados deve ser isolado em uma camada separada, de modo que as regras de negócio não dependam de um banco de dados específico. Isso permite que diferentes tecnologias de persistência possam ser usadas sem afetar o restante do sistema.
 * Princípio da Dependência Inversa (DIP): O princípio DIP estabelece que as dependências devem ser direcionadas para abstrações, não para implementações concretas. Isso promove um acoplamento fraco e permite que as implementações possam ser facilmente substituídas sem afetar outras partes do sistema.

### C. Benefícios e vantagens do uso de Clean Architecture:
 * Manutenção: como a Clean Architecture promove um código limpo e bem organizado, facilitando a manutenção contínua do sistema.
 * Testabilidade: a separação de preocupações e a dependência inversa possibilitam a criação de testes automatizados mais eficientes.
 * Escalabilidade: a arquitetura em camadas permite que o sistema seja escalável, com a possibilidade de adicionar ou modificar funcionalidades sem afetar o restante do código.
 * Reutilização de código: a separação clara das responsabilidades em camadas facilita a reutilização de componentes em outros projetos ou partes do sistema.
 * Independência de Tecnologia: A arquitetura limpa permite que você troque ou atualize tecnologias específicas, como frameworks ou bibliotecas, sem afetar o restante do sistema. Isso significa que você pode aproveitar os benefícios de novas tecnologias ou adaptar-se a requisitos futuros sem refatorar todo o sistema. Isso resulta em um sistema mais flexível e adaptável.
 * Foco nas Regras de Negócio: A arquitetura limpa coloca as regras de negócio no centro do sistema. Isso facilita a compreensão do propósito e das funcionalidades do sistema, além de simplificar a evolução das regras de negócio ao longo do tempo.
 * Facilidade de Onboarding de Desenvolvedores: A arquitetura limpa fornece uma estrutura organizada e clara, o que facilita a entrada de novos desenvolvedores no projeto, pois a utilização dela facilita a compreensão dos fluxos e interação do sistema.

### D. Visão geral da estrutura de um projeto utilizando Clean Architecture:
 * Camada de Domínio: concentra as regras de negócio e entidades principais do sistema.
 * Camada de Casos de Uso: implementa os casos de uso específicos do sistema, orquestrando a interação entre as entidades e a infraestrutura.
 * Camada de Infraestrutura: contém a implementação dos adaptadores externos, como bancos de dados e serviços externos.
 * Camada de Interfaces de Usuário: oferece interfaces para interação com os usuários, como APIs ou interfaces gráficas.


## III. Preparação do Ambiente de Desenvolvimento

Antes de começarmos a implementar a Clean Architecture com TypeScript e Node.js, é importante preparar o ambiente de desenvolvimento adequado. Esta seção abordará os passos necessários para configurar corretamente o ambiente e as ferramentas necessárias.

### A. Instalação do Node.js e configuração do ambiente:

1. Baixe e instale a versão mais recente do Node.js a partir do [site oficial](https://nodejs.org).
2. Verifique se a instalação foi bem-sucedida executando o comando `node -v` no terminal. Você deve ver a versão instalada do Node.js.

### B. Configuração do TypeScript no projeto:

1. Crie um diretório para o seu projeto e navegue até ele no terminal.
2. Inicialize um novo projeto Node.js executando o comando `npm init -y`. Isso criará um arquivo `package.json` para o seu projeto.
3. Instale o TypeScript como uma dependência de desenvolvimento, executando o comando `npm install typescript --save-dev`.
4. Crie um arquivo de configuração do TypeScript chamado `tsconfig.json` na raiz do projeto. Você pode gerar um arquivo básico de configuração usando o comando `npx tsc --init`.
5. Configure o `tsconfig.json` de acordo com as necessidades do seu projeto. Certifique-se de definir o diretório de saída (`outDir`) para uma pasta adequada, como `dist/`.
6. Agora você está pronto para escrever e executar código TypeScript em seu projeto.

### C. Configuração das dependências do projeto:

1. Determine as bibliotecas e pacotes que você precisa para o seu projeto com base nos requisitos.
2. Utilize o npm ou yarn para instalar as dependências necessárias, como o Express para construir a API, o TypeORM para acesso ao banco de dados, ou outras bibliotecas conforme a necessidade do seu projeto.
3. Certifique-se de adicionar as dependências ao arquivo `package.json`, especificando as versões corretas e salvando-as como dependências de produção (`dependencies`) ou desenvolvimento (`devDependencies`).

### D. Estrutura inicial do projeto:

1. Crie uma estrutura básica para o seu projeto, com diretórios para as diferentes camadas da Clean Architecture, como `src/domain`, `src/usecases`, `src/infrastructure` e `src/interfaces`.
2. Dentro de cada diretório, você pode criar subdiretórios adicionais, conforme necessário, para organizar melhor os arquivos do seu projeto.
3. Certifique-se de que a estrutura do projeto esteja alinhada com a divisão de responsabilidades proposta pela Clean Architecture.

Com o ambiente de desenvolvimento devidamente configurado, você está pronto para começar a implementar a Clean Architecture em seu projeto usando TypeScript e Node.js. A próxima seção abordará a definição das camadas da arquitetura.


## IV. Definindo as Camadas da Arquitetura
### A Clean Architecture

A Clean Architecture propõe uma divisão clara e estruturada das responsabilidades em diferentes camadas. Cada camada possui um conjunto específico de responsabilidades, permitindo a separação de preocupações e a manutenção de um código modular e testável. Nesta seção, iremos definir as camadas da arquitetura e suas principais responsabilidades.

### A. Camada de Domínio

**Responsabilidades:**
- Define as entidades principais do sistema, representando os conceitos centrais da aplicação.
- Contém as regras de negócio e a lógica fundamental do sistema.
- Evita dependências externas, mantendo-se independente de frameworks ou bibliotecas.

**Ações recomendadas:**
- Crie as classes ou interfaces para representar as entidades do domínio.
- Defina as regras de negócio e a lógica relacionada às entidades do sistema.
- Evite a dependência de bibliotecas externas nesta camada.

### B. Camada de Casos de Uso

**Responsabilidades:**
- Implementa os casos de uso específicos da aplicação, orquestrando a interação entre as entidades do domínio.
- Manipula as regras de negócio e coordena as ações entre diferentes entidades.
- Fornece uma interface para a interação entre a camada de interface de usuário e a camada de domínio.

**Ações recomendadas:**
- Implemente as classes ou funções que representam os casos de uso.
- Utilize as entidades do domínio para executar a lógica de negócio específica.
- Mantenha esta camada livre de detalhes de infraestrutura ou implementações específicas.

### C. Camada de Infraestrutura

**Responsabilidades:**
- Lida com detalhes de implementação técnica, como acesso a bancos de dados, serviços externos, APIs, entre outros.
- Implementa os adaptadores necessários para se comunicar com os recursos externos.
- Gerencia a persistência de dados e a comunicação com serviços externos.

**Ações recomendadas:**
- Implemente os adaptadores necessários para o acesso a bancos de dados, serviços externos, APIs, entre outros.
- Utilize bibliotecas apropriadas para interagir com recursos externos, como ORM (Object-Relational Mapping) para acesso a bancos de dados.
- Mantenha essa camada isolada, evitando referências diretas a outras camadas.

### D. Camada de Interfaces de Usuário

**Responsabilidades:**
- Fornecer interfaces para a interação com os usuários, como APIs RESTful, interfaces gráficas, entre outros.
- Lida com validação de entrada, formatação de saída e tratamento de erros específicos da interface de usuário.
- Interage com os casos de uso para executar as ações solicitadas pelos usuários.

**Ações recomendadas:**
- Implemente os controladores ou classes responsáveis pela lógica de interface de usuário.
- Defina as rotas da API, tratando as solicitações recebidas e chamando os casos de uso correspondentes.
- Realize a validação de entrada, tratamento de erros e formatação de saída de acordo com as necessidades da interface.

Ao estruturar seu projeto com base nessas camadas, você estará seguindo os princípios da Clean Architecture, permitindo um código modular, flexível e testável. Na próxima seção, iremos explorar a implementação de cada camada com exemplos práticos usando TypeScript e Node.js.




## V. Implementação do Projeto

Nesta seção, iremos abordar a implementação prática da Clean Architecture com TypeScript e Node.js. Vamos nos concentrar em cada uma das camadas da arquitetura e fornecer exemplos de como estruturar e organizar o código.

### A. Implementação da Camada de Domínio:

- Crie um diretório chamado `domain` dentro do diretório `src` para armazenar as classes ou interfaces que representam as entidades do domínio.
- Defina as entidades do domínio, como por exemplo, `User`, `Product`, `Order`, entre outros. Essas entidades devem conter os atributos e comportamentos relevantes para o seu sistema.
- Implemente as regras de negócio relacionadas a essas entidades no próprio arquivo da entidade ou em arquivos separados, dependendo da complexidade.
- Certifique-se de que a camada de domínio não tenha dependências externas, mantendo-a focada nas regras de negócio e na representação do domínio.

### B. Implementação da Camada de Casos de Uso:

- Crie um diretório chamado `usecases` dentro do diretório `src` para armazenar as classes ou funções que implementam os casos de uso.
- Implemente cada caso de uso como uma classe ou função que utiliza as entidades do domínio para realizar a lógica de negócio específica.
- Considere utilizar interfaces para definir os contratos dos casos de uso, tornando-os mais flexíveis e permitindo a substituição de implementações em testes unitários.
- Evite adicionar detalhes de infraestrutura ou dependências externas nesta camada, focando apenas na coordenação das entidades do domínio.

### C. Implementação da Camada de Infraestrutura:

- Crie um diretório chamado `infrastructure` dentro do diretório `src` para armazenar os adaptadores e implementações de recursos externos.
- Implemente os adaptadores para acessar bancos de dados, serviços externos ou outras dependências externas.
- Utilize bibliotecas apropriadas, como ORM (Object-Relational Mapping) para interagir com bancos de dados, e APIs ou bibliotecas de cliente para acessar serviços externos.
- Certifique-se de que os adaptadores estejam isolados das outras camadas e que as dependências externas sejam devidamente configuradas.

### D. Implementação da Camada de Interfaces de Usuário:

- Crie um diretório chamado `interfaces` dentro do diretório `src` para armazenar as classes ou controladores responsáveis pela interação com os usuários.
- Dependendo da interface escolhida (API RESTful, interface gráfica, etc.), implemente os controladores ou classes que tratam as solicitações dos usuários e interagem com os casos de uso correspondentes.
- Defina as rotas da API ou as interfaces de usuário necessárias para atender às necessidades do seu projeto.
- Realize a validação de entrada, tratamento de erros e formatação de saída de acordo com os requisitos da interface escolhida.
- Certifique-se de seguir os princípios da Clean Architecture ao implementar essas camadas, mantendo a separação de responsabilidades e evitando vazamentos de abstração.

### E. Testes:

- Lembre-se da importância dos testes em cada uma das camadas da arquitetura.
- Na camada de domínio, escreva testes unitários para validar as regras de negócio e o comportamento das entidades.
- Na camada de casos de uso, escreva testes de unidade ou testes de integração para garantir que a lógica de negócio esteja funcionando corretamente.
- Na camada de infraestrutura, escreva testes de integração para verificar a interação com recursos externos, como bancos de dados ou serviços.
- Na camada de interfaces de usuário, realize testes de interface ou testes de integração para garantir o correto funcionamento da interação com os usuários.




## VI. Considerações Finais

Exploramos os fundamentos e a implementação prática da Clean Architecture com TypeScript e Node.js. Ao seguir esse padrão de arquitetura, você poderá desenvolver sistemas modulares, flexíveis e de fácil manutenção. A Clean Architecture promove a separação clara de responsabilidades, permitindo que as diferentes camadas do sistema sejam independentes umas das outras. Isso facilita a substituição ou atualização de componentes, bem como a realização de testes automatizados eficazes.

As seguintes práticas são importantes para implementar a Clean Architecture:

- Separe as responsabilidades de cada camada: a camada de domínio deve conter as entidades e regras de negócio, a camada de casos de uso orquestra a interação entre as entidades, a camada de infraestrutura lida com recursos externos e a camada de interfaces de usuário fornece interfaces para interação com os usuários.

- Mantenha as dependências externas isoladas: evite que as camadas dependam diretamente de frameworks ou bibliotecas externas. Use adaptadores ou interfaces para se comunicar com recursos externos e mantenha a flexibilidade de substituição de implementações.

- Priorize a testabilidade: a separação de responsabilidades em camadas facilita a criação de testes unitários e de integração, permitindo uma cobertura abrangente dos diferentes componentes do sistema.

- Mantenha o código limpo e bem organizado: siga as boas práticas de programação, como nomes descritivos de variáveis e funções, funções curtas e coesas, e mantenha um estilo de código consistente.

A Clean Architecture é um guia e pode ser adaptada às necessidades específicas do seu projeto. É importante entender os princípios e adaptá-los de acordo com o contexto.
