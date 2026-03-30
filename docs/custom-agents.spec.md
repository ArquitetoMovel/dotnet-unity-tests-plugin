# Definição da criação de agentes personalizados para o plugin

## Introdução

O plugin *dotnet-unity-tests-plugin* deverá contar com alguns agentes customizados para auxiliar no processo de revisão, criação e manutenção dos testes unitários votados para plataforma **dotnet**.
A seguir, temos os detalhes dos agentes customizados que deverão ser criados.

### dotnet-tester-reviewer

O agente *dotnet-tester-reviewer*, deverá ter sólidos conhecimentos em frameworks de testes e mocks.
O papel do agente *dotnet-tester-reviewer* é fazer um deep dive na solução **.NET** com objetivo de identificar os seguintes pontos da solução e projetos relacionados.

- Levantar e documentar a versão do **dotnet** referente aos projetos da solução Ex: **net8+** ou **net472**.
- Inspecionar projetos de testes existentes e percentual de cobertura da solução.
- Fazer uso da SKILL adequada de acordo com a versão do **dotnet** presente nos projetos da solução indicando *MSTest* para **net472** e *xUnit* para **net8+**.
- Deverá gerar uma especificação e um plano de execução para:
        - Planejar a criação de novos casos de testes para um projeto de testes existente.
        - Planejar a modernização de projetos *MSTest v2* para **MSTest V3**.
        - Planejar a criação de projeto de testes para soluções **dotnet** sem projetos de testes unitários.
        - Sugerir exclusão de cobertura para componentes de infraestrutura e inicialização das aplicações.

### dotnet-tester-creator

O agente *dotnet-tester-creator*, deverá ter sólidos conhecimentos em *dotnet*, *csharp*, *xUnit*, *MSTest* e boas praticas de desenvolvimento de testes unitários.
Procura sempre variar os testes com *InlineData*, *DataRow* com objetivo de evitar mutantes.
Poderá fazer uso de skills para entender como criar os projetos e casos de testes de forma adequada de acordo com a versão do **dotnet** e framework de testes.
O papel do agente *dotnet-tester-creator* é ler a especificação e plano gerado pelo *dotnet-tester-reviewer* e seguir com as implementações.

- Deverá utilizar ferramentas de terminal para garantir que o projeto compila e os testes rodam como `dotnet build` e `dotnet test`.
- Deverá garantir uma cobertura minima de 80%.

### dotnet-tester-coordinator

O papel do agente *dotnet-tester-coordinator* é orquestrar os agentes *dotnet-tester-reviewer* e *dotnet-tester-creator*.
Poderá haver mais de uma instancia rodando em paralelo do *dotnet-tester-creator* de acordo com o plano de execução gerado.
