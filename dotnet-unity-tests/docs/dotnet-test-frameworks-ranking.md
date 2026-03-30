# Ranking de Frameworks de Teste — Plataforma .NET

> Avaliação técnica especializada para projetos .NET Framework 4.7.2, .NET 8, .NET 9 e .NET 10+

---

## Critérios de Avaliação

| Critério                        | Peso |
|---------------------------------|------|
| Ecossistema & adoção            | 20   |
| Compatibilidade .NET            | 20   |
| Recursos & extensibilidade      | 20   |
| Integração CI/CD                | 15   |
| Legibilidade & DX               | 15   |
| Performance                     | 10   |
| **Total**                       | **100** |

---

## 🥇 1º Lugar — xUnit.net — 92/100

**Padrão da indústria para .NET moderno**

### Pontuação por versão

| Plataforma        | Pontuação | Classificação |
|-------------------|-----------|---------------|
| .NET Framework 4.7.2 | 72/100 | ⚠️ Limitado |
| .NET 8            | 95/100    | ✅ Excelente  |
| .NET 9            | 96/100    | ✅ Excelente  |
| .NET 10+          | 98/100    | ✅ Excelente  |

### Justificativa da pontuação

O xUnit é o framework adotado pela própria equipe do .NET para testar o runtime e as bibliotecas padrão da plataforma. Isso garante evolução em sincronia com cada nova versão do SDK. No .NET 8, 9 e 10+ ele aproveita totalmente os recursos modernos da linguagem e da plataforma: suporte nativo a `async/await`, interface `IAsyncLifetime` para setup e teardown assíncronos, e um modelo de isolamento por instância que elimina por design o risco de efeito colateral entre testes. O sistema de dados parametrizados via `[Theory]` é o mais flexível entre os três frameworks, com suporte a `[InlineData]`, `[MemberData]` e `[ClassData]`.

A perda de pontos no .NET Framework 4.7.2 (72/100) se deve ao fato de o xUnit ter sido projetado pensando no futuro — no ambiente legado ele funciona, mas exige adaptadores adicionais e não oferece a mesma experiência fluida que oferece no .NET moderno.

### Pontos fortes

- Framework oficial da equipe de engenharia do .NET
- Suporte nativo a `async/await` e `IAsyncLifetime`
- Isolamento total por instância — sem estado compartilhado entre testes
- `[Theory]` + `[InlineData]` / `[MemberData]` / `[ClassData]` extremamente poderosos
- Integração de primeira classe com `dotnet test`, Rider, Visual Studio e Azure DevOps
- Extensível via `ITestOutputHelper` e sistema de traits
- Ecossistema rico de bibliotecas complementares (FluentAssertions, NSubstitute, Bogus)

### Pontos fracos

- Ausência de `[SetUp]` / `[TearDown]` clássicos — curva de aprendizado para devs vindos de NUnit/JUnit
- No .NET Framework 4.7.2: dependência de adaptadores extras e limitações com xUnit v2
- Compartilhamento de fixtures entre classes exige `IClassFixture<T>` — mais verboso que o NUnit
- Assertivas nativas básicas — necessita FluentAssertions ou Shouldly para expressividade

---

## 🥈 2º Lugar — NUnit — 83/100

**Veterano maduro com ampla compatibilidade**

### Pontuação por versão

| Plataforma           | Pontuação | Classificação |
|----------------------|-----------|---------------|
| .NET Framework 4.7.2 | 90/100    | ✅ Excelente  |
| .NET 8               | 86/100    | ✅ Excelente  |
| .NET 9               | 85/100    | ✅ Excelente  |
| .NET 10+             | 83/100    | ✅ Excelente  |

### Justificativa da pontuação

O NUnit é exatamente o inverso do xUnit em termos de perfil: quanto mais antigo o ambiente, melhor ele se sai. No .NET Framework 4.7.2 recebe 90/100 por ser o mais maduro e confiável nesse contexto, com suporte robusto ao ciclo de vida de testes via `[SetUp]`, `[TearDown]` e `[OneTimeSetUp]`. Para equipes migrando de Java (JUnit) ou Ruby (RSpec), a curva de aprendizado é mínima. No .NET moderno ele segue competente, mas o ritmo de evolução é mais conservador, ficando progressivamente atrás do xUnit em elegância para cenários avançados.

### Pontos fortes

- Melhor escolha para projetos .NET Framework 4.7.2 legados
- `[SetUp]`, `[TearDown]`, `[OneTimeSetUp]` familiares a devs de JUnit e TestNG
- Constraint Model de assertivas expressivo e embutido (`Assert.That(...)`)
- `[TestCase]` e `[TestCaseSource]` para testes parametrizados com dados complexos
- Comunidade ativa com mais de duas décadas de adoção
- Suporte nativo a categorias de teste e ordenação de execução

### Pontos fracos

- Instância única por fixture — risco de estado compartilhado entre testes
- Evolução mais lenta em features específicas para .NET moderno (8/9/10+)
- Suporte a `async` menos elegante que o xUnit em alguns cenários de setup
- Ecossistema de plugins menor comparado ao xUnit

---

## 🥉 3º Lugar — MSTest (v2 / v3) — 74/100

**Nativo da Microsoft — confiável em ambientes corporativos**

### Pontuação por versão

| Plataforma           | Pontuação | Classificação |
|----------------------|-----------|---------------|
| .NET Framework 4.7.2 | 88/100    | ✅ Excelente  |
| .NET 8               | 78/100    | ✅ Bom        |
| .NET 9               | 79/100    | ✅ Bom        |
| .NET 10+             | 80/100    | ✅ Bom        |

### Justificativa da pontuação

No passado, a versão v1 era notoriamente lenta e limitada, gerando uma reputação negativa que o v2 e o v3 ainda estão corrigindo. O ponto forte real é a integração zero-config com Visual Studio e Azure DevOps — em ambientes corporativos 100% Microsoft ele ainda é uma escolha muito razoável. A pontuação cresce levemente do .NET 8 para o 10+ porque o MSTest v3 trouxe paralelismo real e melhorias de performance que vão sendo refinadas. No .NET FW 4.7.2 ele pontua bem (88/100) por ser a escolha nativa da Microsoft naquela era.

### Pontos fortes

- Integração nativa com Visual Studio e Azure DevOps (zero configuração)
- Template padrão de projeto de testes no Visual Studio
- MSTest v3: melhorias significativas de performance e paralelismo real
- Ideal para equipes totalmente dentro do ecossistema Microsoft
- `[DataRow]`, `[DataTestMethod]` e `[DynamicData]` disponíveis a partir do v2

### Pontos fracos

- Ecossistema de extensões de terceiros menor que xUnit e NUnit
- MSTest v1 (legado) era lento e limitado — reputação ainda impacta a adoção
- Assertivas mais verbosas e menos expressivas que xUnit (com FluentAssertions) e NUnit
- Paralelismo limitado em versões anteriores ao v3
- `[DataRow]` menos poderoso e flexível que `[Theory]` do xUnit

---

## Comparativo consolidado

| Critério                    | xUnit.net | NUnit  | MSTest v3 |
|-----------------------------|-----------|--------|-----------|
| Ecossistema & adoção        | 19/20     | 16/20  | 13/20     |
| Compatibilidade .NET        | 18/20     | 17/20  | 16/20     |
| Recursos & extensibilidade  | 19/20     | 17/20  | 14/20     |
| Integração CI/CD            | 14/15     | 13/15  | 13/15     |
| Legibilidade & DX           | 13/15     | 12/15  | 10/15     |
| Performance                 | 9/10      | 8/10   | 8/10      |
| **Total**                   | **92**    | **83** | **74**    |

---

## Legenda de classificação por versão

| Faixa       | Classificação |
|-------------|---------------|
| 85 – 100    | ✅ Excelente  |
| 70 – 84     | ✅ Bom        |
| Abaixo de 70 | ⚠️ Limitado  |

---

## Recomendação por cenário

| Cenário                                      | Framework recomendado |
|----------------------------------------------|-----------------------|
| Projeto novo em .NET 8 / 9 / 10+             | **xUnit.net**         |
| Manutenção de projeto .NET Framework 4.7.2   | **MSTest v2/v3**      |
| Migração de Java/JUnit para .NET             | **NUnit**             |
| Ambiente 100% Microsoft (VS Enterprise + ADO) | **MSTest v3**        |
| Migração gradual de legado para .NET moderno | **NUnit → xUnit**     |

---

## Stack complementar recomendada (xUnit + .NET 8+)

| Finalidade              | Biblioteca         | Versão  |
|-------------------------|--------------------|---------|
| Assertivas expressivas  | FluentAssertions   | 6.12.x  |
| Mocking                 | NSubstitute        | 5.1.x   |
| Dados falsos realistas  | Bogus              | 35.x    |
| Testes de integração DB | Testcontainers     | 3.x     |
| Cobertura de código     | coverlet.collector | 6.x     |

---

*Avaliação realizada em março de 2026. Versões e pontuações sujeitas a revisão conforme evolução dos frameworks.*
