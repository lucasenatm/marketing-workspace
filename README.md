# lucasena-os

Sistema de onboarding e organização de workspace para Claude Code.

## Skills incluídas

| Comando | O que faz |
|---|---|
| `/comecar` | Configura o workspace pro seu negócio — faz perguntas, gera contexto, estrutura pastas e recomenda MCPs |
| `/mapear` | Entrevista sobre processos repetitivos e cria skills personalizadas pro seu dia a dia |
| `/syncar` | Salva o workspace no GitHub (commit + push), com setup automático se for a primeira vez |

## Instalação

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
