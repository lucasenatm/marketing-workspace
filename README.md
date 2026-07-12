# lucasena-os

Sistema de onboarding e organização de workspace para Claude Code.

## Skills incluídas

| Comando | O que faz |
|---|---|
| `/comecar` | Configura o workspace pro seu negócio — faz perguntas, gera contexto, estrutura pastas e recomenda MCPs |
| `/iniciar` | Starter de sessão — carrega o contexto e mostra o foco atual. Usar no começo de cada dia |
| `/mapear` | Entrevista sobre processos repetitivos e cria skills personalizadas pro seu dia a dia |
| `/novo-projeto` | Cria pasta de projeto com CLAUDE.md dedicado. Ideal pra novo cliente ou lançamento |
| `/atualizar` | Varre o projeto e sincroniza os arquivos de contexto com o estado real do workspace |
| `/syncar` | Salva o workspace no GitHub (commit + push), com setup automático se for a primeira vez |

## Também inclui

- `templates/perfis/` — templates de CLAUDE.md pra freelancer, agência, solopreneur e empresa
- `templates/ferramentas/catalogo.md` — referência de APIs, CLIs e MCPs disponíveis pra usar em skills
- `templates/skills/catalogo.md` — skills externas prontas pra instalar

## Instalação

### Opção 1 — Via prompt (mais fácil)

Com o Claude Code aberto em qualquer pasta, copie e cole esse prompt:

```
Instala pra mim o plugin https://github.com/lucasenatm/lucasena-os adicionando as entradas necessárias no ~/.claude/settings.json e rode /comecar
```

O Claude faz tudo: lê o repositório, configura o `settings.json` e inicia a configuração.

### Opção 2 — Manual

Adicione ao seu `settings.json` do Claude Code (`~/.claude/settings.json`):

```json
{
  "enabledPlugins": {
    "lucasena-os@lucasena-os": true
  },
  "extraKnownMarketplaces": {
    "lucasena-os": {
      "source": {
        "source": "github",
        "repo": "lucasenatm/lucasena-os"
      }
    }
  }
}
```

Depois abra o Claude Code e rode:

```
/comecar
```

## Como usar

1. `/comecar` — rode uma vez pra configurar o workspace
2. `/mapear` — rode depois pra criar skills personalizadas pro que você mais faz
3. `/syncar` — rode sempre que quiser salvar o trabalho no GitHub

## by lucasena.

[lucasena.com](https://lucasena.com)
