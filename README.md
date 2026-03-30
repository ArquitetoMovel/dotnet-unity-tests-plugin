# Fluxo de uso

  1. Claude Code invoca dotnet-tester-reviewer → gera test-plan.md
  2. Claude Code invoca dotnet-tester-creator → lê o plano e implementa os testes
  3. Para projetos independentes (marcados como paralelizáveis na seção 4 do plano), Claude Code pode invocar múltiplas instâncias   do creator em paralelo
  