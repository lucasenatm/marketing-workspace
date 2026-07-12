---
name: atualizar
description: >
  Varre o estado atual do projeto e atualiza os arquivos de contexto que ficaram
  desatualizados. Compara o que existe nas pastas, skills e configurações com o que
  está documentado em CLAUDE.md, _contexto/ e marca/design-guide.md.
  Use quando o usuário chamar /atualizar, quando disser "atualiza o contexto",
  "os arquivos tão desatualizados", "sincroniza a memória", ou no fim de uma sessão
  longa com muitas mudanças.
user-invokable: true
argument-hint: ""
license: MIT
---

# /atualizar — Manutenção de Contexto

## O que fazer

Fazer uma varredura comparando o **estado real do projeto** com o que está **documentado nos arquivos de contexto**. Identificar diferenças e propor atualizações pro usuário aprovar.

## Passo 1: Levantar o estado real

Ler e anotar:

1. **Estrutura de pastas** — listar os diretórios de primeiro nível (ignorar `.git`, `node_modules`, `.claude`, `templates`, `dados`)
2. **Skills instaladas** — listar `.claude/skills/*/` e `.claude/commands/*.md` (exceto os padrão: comecar, iniciar, syncar, mapear, atualizar, novo-projeto)
3. **MCPs configurados** — verificar se `.claude.json` ou `.claude/mcp.json` existe e quais servers estão listados
4. **Arquivos recentes** — usar `git diff --name-only HEAD~5..HEAD` pra ver o que mudou recentemente
5. **Mudanças não commitadas** — `git status` pra ver trabalho em andamento

## Passo 2: Ler os arquivos de contexto

Ler cada um dos arquivos abaixo (se existir):

1. `CLAUDE.md` — foco em: estrutura de pastas, lista de skills, ferramentas conectadas, regras do sistema
2. `_contexto/empresa.md` — foco em: equipe, ferramentas, entregas, clientes
3. `_contexto/estrategia.md` — foco em: prioridade principal, fase, o que pode esperar
4. `_contexto/preferencias.md` — foco em: tom de voz, o que evitar
5. `marca/design-guide.md` — foco em: cores, fontes, estilo

## Passo 3: Comparar e identificar gaps

Para cada arquivo de contexto, verificar:

### CLAUDE.md
- Pastas listadas na estrutura batem com as pastas reais?
- Skills mencionadas existem de fato? Tem skills novas não documentadas?
- Ferramentas marcadas como conectadas estão de fato configuradas (MCPs)?
- Regras do sistema ainda fazem sentido com o estado atual?

### _contexto/empresa.md
- Ferramentas listadas incluem tudo que foi instalado (MCPs)?
- Clientes ou projetos mencionados ainda são atuais?
- Equipe mudou?

### _contexto/estrategia.md
- A prioridade principal ainda parece ser o foco (baseado nos arquivos recentes)?
- Tem prazos vencidos ou contextos datados?

### _contexto/preferencias.md
- Verificar se tem algo contraditório com o uso recente

### marca/design-guide.md
- Está preenchido ou ainda é template vazio?
- Se tem logo referenciado, o arquivo existe?

## Passo 4: Apresentar o diagnóstico

Mostrar um resumo organizado no formato:

```
## Diagnóstico de contexto

### Em dia
- [lista do que está atualizado]

### Desatualizado
- **[arquivo]:** [o que está errado e o que deveria ser]

### Não configurado
- [arquivos que existem mas estão vazios ou com template padrão]
```

Se tudo estiver em dia:

> "Tudo atualizado. Os arquivos de contexto refletem o estado atual do projeto."

## Passo 5: Aplicar as correções (com aprovação)

Para cada item desatualizado, mostrar a mudança proposta antes de aplicar.

Perguntar:

> "Quer que eu aplique essas atualizações?"

Se sim, aplicar todas de uma vez e mostrar resumo do que foi feito.
Se o usuário quiser aprovar uma a uma, respeitar.

## Regras

- Nunca reformatar um arquivo inteiro. Só editar as linhas relevantes
- Se não tem certeza se algo mudou, perguntar ao usuário em vez de assumir
- Não inventar informação. Se não consegue inferir do estado do projeto, perguntar
- Tom direto. Não exagerar no diagnóstico de coisas triviais
- Se o projeto acabou de ser configurado (poucos commits), dizer que está tudo certo e não forçar atualizações
