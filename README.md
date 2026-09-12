# marketing workspace

Plugin pra Claude Code que monta e organiza o seu workspace de marketing em minutos. Faz perguntas sobre o seu negócio, gera os arquivos de contexto certos, cria a estrutura de pastas pro seu perfil e instala os MCPs que fazem sentido pra você.

Feito por [lucasena.](https://lucasena.com)

---

## O que você ganha

Seis skills que cobrem o ciclo completo de um workspace organizado:

**`/configurar`**: configura tudo do zero. Faz perguntas sobre o negócio, detecta seu perfil (freelancer, agência, solopreneur, empresa), gera os arquivos de contexto, monta a estrutura de pastas e recomenda os MCPs certos pra você. Rode uma vez.

**`/iniciar`**: use no começo de cada sessão. Carrega o contexto do negócio, mostra o foco atual e os pendentes. Nada de repetir o que você faz toda vez que abre o Claude.

**`/escanear`**: entrevista você sobre os processos repetitivos do dia a dia e cria skills personalizadas pra cada um. Quanto mais você usa, mais o sistema aprende o que você faz.

**`/projeto`**: cria uma pasta de projeto com CLAUDE.md dedicado. Útil quando entra cliente novo ou começa um lançamento. O Claude passa a ter contexto separado pra aquele projeto específico.

**`/calibrar`**: mantém os arquivos de contexto em dia. Varre o estado real do workspace e aponta o que ficou desatualizado: pastas novas, skills instaladas, MCPs adicionados. Útil depois de sessões longas.

**`/salvar`**: commit e push no GitHub. Configura o remote se for a primeira vez, detecta o que mudou e salva tudo com uma mensagem de commit automática.

---

## Instalação

No terminal, **antes de abrir o Claude Code**, rode os dois comandos:

```bash
claude plugin marketplace add lucasenatm/marketing-workspace
claude plugin install marketing-workspace@marketing-workspace
```

O primeiro registra o marketplace, o segundo baixa e instala. Depois é só abrir:

```bash
claude
```

E rodar:

```
/marketing-workspace:configurar
```

> **Por que antes de abrir o Claude Code:** plugin é carregado quando a sessão inicia. Se você instalar com o chat já aberto, as skills só aparecem na próxima vez que abrir. Rodando no terminal primeiro, elas já estão lá na primeira sessão.

### Os comandos

Todas as skills usam o prefixo do plugin:

| Comando | O que faz |
|---|---|
| `/marketing-workspace:configurar` | Configura o workspace do zero |
| `/marketing-workspace:iniciar` | Abre a sessão com o contexto carregado |
| `/marketing-workspace:escanear` | Cria skills a partir dos seus processos |
| `/marketing-workspace:projeto` | Cria projeto com contexto próprio |
| `/marketing-workspace:calibrar` | Atualiza o contexto desatualizado |
| `/marketing-workspace:salvar` | Salva tudo no GitHub |

---

## Estrutura do plugin

```
skills/
  configurar/     onboarding e configuração inicial
  iniciar/        starter de sessão
  escanear/       criação de skills personalizadas
  projeto/        criação de projeto com contexto
  calibrar/       manutenção de contexto
  salvar/         backup no GitHub

templates/
  perfis/         templates de CLAUDE.md por perfil
  ferramentas/    catálogo de APIs, CLIs e MCPs disponíveis
  skills/         catálogo de skills externas prontas pra instalar
```

---

## Licença

MIT
