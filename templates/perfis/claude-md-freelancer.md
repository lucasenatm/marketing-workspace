# [Seu Nome] — Claude Code OS

> Preencha os campos entre colchetes e apague este aviso.

## O que é esse workspace

[Uma ou duas frases descrevendo o que essa pasta representa. Ex: "Workspace de trabalho freelancer. Aqui ficam todos os meus clientes, entregas e projetos."]

**Estrutura de pastas:**
- `_contexto/` — memória do sistema (não apagar)
- `clientes/` — um subdiretório por cliente
- `conteudo/` — produção de conteúdo
- `templates/` — modelos reutilizáveis
- `dados/` — arquivos para análise (CSV, PDF, etc)
- `tarefas.md` — lista de tarefas corrente

## Sobre o negócio

Sou [nome], freelancer de [área: marketing / design / dev / copywriting / etc].
Atendo [tipo de clientes] com foco em [especialidade ou nicho].

## O que mais faço aqui

- [entregável 1: ex. propostas comerciais]
- [entregável 2: ex. campanhas de tráfego pago]
- [entregável 3]

## Clientes e contexto

[Descrição dos clientes atuais e tipo de projeto que costuma atender]

## Tom de voz

[Como você escreve pro cliente e em comunicações]

Evitar: [o que destoa do seu estilo]

## Ferramentas conectadas

- [ ] [ferramenta 1]
- [ ] [ferramenta 2]

*(Marcar conforme for instalando os MCPs)*

## Regras do sistema

- Cada cliente tem sua pasta em `clientes/[nome-cliente]/`
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
