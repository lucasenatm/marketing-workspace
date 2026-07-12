# [Seu Nome / Nome do Negócio] — Claude Code OS

> Preencha os campos entre colchetes e apague este aviso.

## O que é esse workspace

[Uma ou duas frases descrevendo o que essa pasta representa. Ex: "Workspace principal do meu negócio. Aqui eu produzo conteúdo, planejo lançamentos e toco as operações do dia a dia."]

**Estrutura de pastas:**
- `_contexto/` — memória do sistema (não apagar)
- `conteudo/` — produção de conteúdo por tipo
- `projetos/` — projetos internos
- `templates/` — modelos reutilizáveis
- `dados/` — arquivos para análise (CSV, PDF, etc)
- `tarefas.md` — lista de tarefas corrente

## Sobre o negócio

Sou [nome]. [O que você faz em uma frase].
Meu negócio é [descrição do negócio/canal/produto].

## O que mais faço aqui

- [atividade principal: ex. produzir conteúdo pra redes sociais]
- [atividade 2]
- [atividade 3]

## Meu público

[Quem acompanha o que você cria ou compra o que você vende]

## Posicionamento

[O que você defende, o que te diferencia, o ponto de vista que você tem sobre o mercado]

## Tom de voz

[Como você escreve e se comunica com seu público]

Nunca: [o que não combina com você]

## Ferramentas conectadas

- [ ] [ferramenta 1]
- [ ] [ferramenta 2]

*(Marcar conforme for instalando os MCPs)*

## Regras do sistema

- Conteúdo salvar em `conteudo/[tipo]/`
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
