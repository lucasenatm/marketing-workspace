---
name: novo-projeto
description: >
  Cria uma nova pasta de projeto com CLAUDE.md personalizado. Entrevista o usuário
  sobre o projeto, gera a estrutura e referencia no CLAUDE.md principal.
  Use quando o usuário chamar /novo-projeto, disser "novo cliente", "novo projeto",
  "criar pasta pro cliente X", "vou começar um projeto novo", ou quando precisar
  organizar um trabalho novo em pasta separada.
user-invokable: true
argument-hint: "<nome-do-projeto>"
license: MIT
---

# /novo-projeto — Criar Projeto com Contexto

Cria uma pasta de projeto com CLAUDE.md dedicado, entrevistando o usuário sobre o que é o projeto.

## Quando usar

- Novo cliente entrando
- Novo produto ou lançamento
- Qualquer trabalho que merece pasta própria e contexto separado

## Fluxo

### Passo 1: Entender o projeto

Perguntar em conversa natural (uma por vez):

**Pergunta 1:** "Qual é o nome do projeto?"

**Pergunta 2:** "Que tipo de projeto é?"
- Cliente (entrega de serviço pra alguém)
- Produto próprio (site, app, curso, loja)
- Conteúdo (canal, série, newsletter)
- Interno (processo, ferramenta, organização)

**Pergunta 3:** "Me explica em poucas palavras o que é o projeto e o que precisa ser entregue."

**Pergunta 4:** "Tem prazo, orçamento ou ferramenta específica que eu precise saber?"

Se o usuário der respostas completas logo de início, pular as perguntas já respondidas.

### Passo 2: Definir a pasta

Sugerir o local baseado no tipo de projeto e na estrutura existente:

- **Cliente** → `clientes/nome-do-cliente/`
- **Produto** → `projetos/nome-do-projeto/`
- **Conteúdo** → `conteudo/nome-do-projeto/`
- **Interno** → `projetos/nome-do-projeto/`

Verificar as pastas que já existem (ler CLAUDE.md principal) pra manter consistência.

Apresentar a sugestão e aguardar confirmação antes de criar.

### Passo 3: Criar a pasta e o CLAUDE.md

```markdown
# [Nome do Projeto]

## O que é
[descrição curta, 1-2 frases]

## Tipo
[Cliente / Produto / Conteúdo / Interno]

## Escopo
[o que precisa ser entregue]

## Contexto
[prazo, orçamento, ferramentas, qualquer detalhe relevante]

## Arquivos importantes
- (preencher conforme o projeto avança)

## Regras específicas
- (preencher conforme o projeto avança)
```

Se for **cliente**, adicionar também:

```markdown
## Contato
[nome do contato, se mencionou]

## Entregas
- [ ] [entrega 1]
- [ ] [entrega 2]
```

### Passo 4: Atualizar o CLAUDE.md principal

Encontrar a seção de estrutura de pastas e adicionar a nova pasta.

Se a seção não existir ou não fizer sentido editar, informar e deixar pro usuário.

### Passo 5: Atualizar contexto (se cliente novo)

Se for um cliente novo, perguntar:

> "Quer que eu adicione esse cliente em `_contexto/empresa.md` também?"

### Passo 6: Confirmar

```
Projeto criado.

Pasta: [caminho]
CLAUDE.md: [caminho/CLAUDE.md]
```

## Regras

- Tom direto, sem cerimônia
- Não criar subpastas dentro do projeto a menos que o usuário peça
- O CLAUDE.md do projeto deve ser curto no início — vai crescer com o uso
- Nunca mover pastas existentes sem perguntar
- Se o usuário já criou a pasta manualmente, só gerar o CLAUDE.md dentro dela
- Respeitar a estrutura de pastas que o `/comecar` criou
