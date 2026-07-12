# lucasena-os

Plugin pra Claude Code que configura e organiza qualquer workspace em minutos. Faz perguntas sobre o seu negócio, gera os arquivos de contexto certos, cria a estrutura de pastas pro seu perfil e instala os MCPs que fazem sentido pra você.

Feito por [lucasena.](https://lucasena.com)

---

## O que você ganha

Seis skills que cobrem o ciclo completo de um workspace organizado:

**`/configurar`** — configura tudo do zero. Faz perguntas sobre o negócio, detecta seu perfil (freelancer, agência, solopreneur, empresa), gera os arquivos de contexto, monta a estrutura de pastas e recomenda os MCPs certos pra você. Rode uma vez.

**`/iniciar`** — use no começo de cada sessão. Carrega o contexto do negócio, mostra o foco atual e os pendentes. Nada de repetir o que você faz toda vez que abre o Claude.

**`/escanear`** — entrevista você sobre os processos repetitivos do dia a dia e cria skills personalizadas pra cada um. Quanto mais você usa, mais o sistema aprende o que você faz.

**`/novo-projeto`** — cria uma pasta de projeto com CLAUDE.md dedicado. Útil quando entra cliente novo ou começa um lançamento. O Claude passa a ter contexto separado pra aquele projeto específico.

**`/calibrar`** — mantém os arquivos de contexto em dia. Varre o estado real do workspace e aponta o que ficou desatualizado: pastas novas, skills instaladas, MCPs adicionados. Útil depois de sessões longas.

**`/salvar`** — commit e push no GitHub. Configura o remote se for a primeira vez, detecta o que mudou e salva tudo com uma mensagem de commit automática.

---

## Instalação

**Mais fácil:** cole esse prompt no Claude Code com qualquer pasta aberta.

```
Instala pra mim o plugin https://github.com/lucasenatm/lucasena-os adicionando as entradas necessárias no ~/.claude/settings.json e rode /configurar
```

**Manual:** adicione ao `~/.claude/settings.json`:

```json
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
```

Depois rode `/configurar`.

---

## Estrutura do plugin

```
skills/
  comecar/       — onboarding e configuração inicial
  iniciar/       — starter de sessão
  mapear/        — criação de skills personalizadas
  novo-projeto/  — criação de projeto com contexto
  atualizar/     — manutenção de contexto
  syncar/        — backup no GitHub

templates/
  perfis/        — templates de CLAUDE.md por perfil
  ferramentas/   — catálogo de APIs, CLIs e MCPs disponíveis
  skills/        — catálogo de skills externas prontas pra instalar
```

---

## Licença

MIT
