# [Nome da Agência] — Claude Code OS

> Preencha os campos entre colchetes e apague este aviso.

## O que é esse workspace

[Uma ou duas frases descrevendo o que essa pasta representa. Ex: "Workspace de operações da agência. Aqui ficam todos os clientes, propostas e entregas."]

**Estrutura de pastas:**
- `_contexto/` — memória do sistema (não apagar)
- `clientes/` — um subdiretório por cliente
- `briefings/` — briefings recebidos
- `propostas/` — propostas em andamento e enviadas
- `conteudo/` — produção de conteúdo
- `dados/` — arquivos para análise (CSV, PDF, etc)
- `tarefas.md` — lista de tarefas corrente

## Sobre o negócio

Somos uma [tipo: agência de marketing / design / conteúdo / consultoria].
Atendemos [perfil de clientes: PMEs / e-commerces / startups / empresas locais].
Nossos principais serviços: [lista de 3-5 serviços].

## O que mais produzimos aqui

- Propostas comerciais para novos clientes
- [entregável frequente 2]
- [entregável frequente 3]

## Clientes ativos

[Descrição dos clientes atuais e tipos de projeto em andamento]

## Tom de voz

[Como a agência escreve e se comunica com clientes e na produção de conteúdo]

Evitar: [palavras, construções ou estilos que não combinam]

## Ferramentas conectadas

- [ ] [ferramenta 1]
- [ ] [ferramenta 2]

*(Marcar conforme for instalando os MCPs)*

## Regras do sistema

- Propostas salvar em `propostas/`
- Clientes novos criar pasta em `clientes/[nome-cliente]/`
- [outras regras de organização]

---

## Contexto do negócio

No início de toda conversa, ler os seguintes arquivos (se existirem):

1. `_contexto/empresa.md` — quem é o usuário, o que faz, como funciona o negócio
2. `_contexto/preferencias.md` — tom de voz, estilo de escrita, o que evitar
3. `_contexto/estrategia.md` — foco atual, prioridades, o que pode esperar

Para tarefas visuais, consultar `marca/design-guide.md`.

---

## Fluxo de trabalho

Antes de executar qualquer tarefa, verificar se existe uma skill relevante em `.claude/skills/` ou `.claude/commands/`.
Se não encontrar, executar a tarefa normalmente.

Ao concluir uma tarefa repetível, perguntar:
> "Isso pode virar uma skill pra próxima vez. Quer que eu crie?"
