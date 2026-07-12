# [Nome da Empresa] — Claude Code OS

> Preencha os campos entre colchetes e apague este aviso.

## O que é esse workspace

[Uma ou duas frases descrevendo o que essa pasta representa. Ex: "Workspace central da empresa. Cada setor tem sua pasta com processos, entregas e documentos."]

**Estrutura de pastas:**
- `_contexto/` — memória do sistema (não apagar)
- `marketing/` — campanhas, conteúdo, mídia paga, redes sociais
- `comercial/` — propostas, pipeline, materiais de venda
- `financeiro/` — relatórios, fluxo de caixa, orçamentos
- `rh/` — processos seletivos, onboarding, documentos de equipe
- `operacoes/` — processos internos, SOPs, fornecedores
- `projetos/` — projetos que envolvem mais de um setor
- `dados/` — arquivos para análise (CSV, PDF, etc)
- `tarefas.md` — lista de tarefas corrente

## Sobre a empresa

[Nome da empresa] é uma [tipo: consultoria / comércio / serviços / tech].
Atuamos em [mercado/segmento] atendendo [perfil de clientes].
Somos [tamanho da equipe] pessoas organizadas em [setores].

## Setores e responsáveis

- **Marketing:** [quem cuida, o que produz]
- **Comercial:** [quem cuida, o que faz]
- **Financeiro:** [quem cuida, o que acompanha]
- **RH:** [quem cuida, o que gerencia]
- **Operações:** [quem cuida, processos principais]

*(Adicione ou remova setores conforme a realidade da empresa)*

## O que mais fazemos aqui

- [entregável frequente 1: ex. campanhas de marketing]
- [entregável frequente 2: ex. propostas comerciais]
- [entregável frequente 3: ex. relatórios financeiros mensais]

## Tom de voz

[Como a empresa se comunica — interno vs externo pode ser diferente]

Evitar: [o que não combina com a marca]

## Ferramentas conectadas

- [ ] [ferramenta 1]
- [ ] [ferramenta 2]

*(Marcar conforme for instalando os MCPs)*

## Regras do sistema

- Cada setor tem sua pasta na raiz
- Projetos que cruzam setores ficam em `projetos/`
- Propostas comerciais salvar em `comercial/propostas/`
- Relatórios salvar em `financeiro/relatorios/`
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
