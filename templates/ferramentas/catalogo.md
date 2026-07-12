# Catálogo de Ferramentas

Referência de APIs, CLIs e conectores que podem ser usados dentro de skills do Claude Code.
Consulte este arquivo antes de criar skills novas pra saber o que já está disponível.

---

## Criar visuais (HTML pra PNG)

### Playwright CLI
**O que faz:** Renderiza qualquer HTML em imagem PNG (carrosséis, slides, propostas, cards)
**Precisa de conta:** Não, roda local
**Como instalar:**
```bash
npx playwright install chromium
```
**Como usar numa skill:**
```bash
npx playwright screenshot --viewport-size=1080,1350 --full-page "file:///caminho/slide.html" "slide.png"
```
**Tamanhos comuns:**
- Instagram feed: 1080x1350
- Instagram/TikTok story: 1080x1920
- Slide 16:9: 1920x1080
- Card quadrado: 1080x1080

### Remotion
**O que faz:** Gera vídeos programaticamente a partir de componentes React (animações, criativos de ads, intros)
**Precisa de conta:** Não, roda local
**Como instalar:** `npx create-video@latest`
**Quando usar:** Skills que geram criativos animados, abertura de vídeos, anúncios em vídeo, motion graphics simples
**Atenção:** Mais complexo que Playwright. Só usar quando precisar de animação/vídeo, não pra imagem estática

---

## Publicar na web

### Cloudflare Pages API
**O que faz:** Publica arquivos HTML estáticos com link público (propostas, landing pages, estudos, mini-LPs)
**Precisa de conta:** Sim, Cloudflare (grátis)
**Configurar:** Salvar `CLOUDFLARE_API_TOKEN` e `CLOUDFLARE_ACCOUNT_ID` no `.env`. Comando: `npx wrangler pages deploy .`
**Quando usar:** Sempre que a skill gerar um HTML que precisa ser compartilhado por link

### Cloudflare Workers (Wrangler)
**O que faz:** Código serverless rodando na borda da Cloudflare (APIs, webhooks, automações, redirects, cron jobs)
**Precisa de conta:** Sim, Cloudflare (grátis até 100k requests/dia)
**Configurar:** Salvar `CLOUDFLARE_API_TOKEN` e `CLOUDFLARE_ACCOUNT_ID` no `.env`. Comando: `npx wrangler deploy`
**Quando usar:** Skills que precisam de backend leve sem servidor: webhook de pagamento, redirect com UTMs, cron diário, automação que precisa de URL pública
**Diferença pro Pages:** Pages é pra HTML estático. Workers é pra código dinâmico

### Vercel CLI
**O que faz:** Publica apps Next.js, Vite, React em segundos com CDN global
**Precisa de conta:** Sim, Vercel (grátis pra projetos pessoais)
**Configurar:** `npm i -g vercel` e depois `vercel login`
**Como usar numa skill:** `vercel --yes --prod` dentro da pasta do projeto
**Quando usar:** Skills que constroem ou fazem deploy de apps Next.js, dashboards, plataformas

---

## Publicar em redes sociais

### Post for Me API
**O que faz:** Publica posts no Instagram e TikTok direto do Claude Code
**Precisa de conta:** Sim, postforme.dev
**Configurar:** Salvar `POSTFORME_API_KEY` no `.env`
**Como usar numa skill:**
```bash
node --env-file=.env scripts/publish-postforme.js
```
**Quando usar:** Skills de carrossel, conteúdo visual, publicação automática

### WhatsApp Cloud API / Z-API
**O que faz:** Envia e recebe mensagens de WhatsApp programaticamente (atendimento, notificação, automação)
**Precisa de conta:** Sim. Dois caminhos:
- **WhatsApp Cloud API (oficial Meta):** número verificado, mais regras, sem custo até certo volume
- **Z-API (terceiro):** mais simples de plugar, paga, usa número pessoal
**Configurar:** Tokens no `.env` (varia por provedor)
**Quando usar:** Skills de atendimento automático, envio de notificação, agente conversacional, follow-up de venda

---

## Buscar conteúdo da web

### WebFetch (nativo)
**O que faz:** Lê o conteúdo de qualquer URL e traz como texto
**Precisa de conta:** Não, já vem no Claude Code
**Quando usar:** Pesquisa de referências, ler artigos, buscar dados de sites

### WebSearch (nativo)
**O que faz:** Pesquisa no Google e traz resultados
**Precisa de conta:** Não, já vem no Claude Code
**Quando usar:** Quando o usuário precisa pesquisar antes de criar conteúdo

### Jina Reader
**O que faz:** Converte qualquer URL em markdown limpo (melhor que WebFetch pra artigos longos)
**Precisa de conta:** Não
**Como usar:** Acessar `https://r.jina.ai/{URL}` via WebFetch
**Quando usar:** Extrair texto de artigos, blog posts, páginas com muito HTML

### DataForSEO
**O que faz:** Dados de SEO/SEM em escala: volume de busca, SERP do Google e YouTube, palavras-chave, dificuldade
**Precisa de conta:** Sim, dataforseo.com (pago, mas barato por consulta)
**Configurar:** Salvar `DATAFORSEO_LOGIN` e `DATAFORSEO_PASSWORD` no `.env`
**Quando usar:** Skills de pesquisa de pauta, análise de oportunidade SEO, validação de nicho

---

## Extrair conteúdo de vídeo

### yt-dlp (CLI)
**O que faz:** Baixa transcrições/legendas de vídeos do YouTube e mais de 1000 sites (Instagram, TikTok, X, Vimeo, etc)
**Precisa de conta:** Não, roda local
**Como instalar:**
```bash
brew install yt-dlp
```
**Quando usar:** Skills que partem de um vídeo pra criar conteúdo (carrossel, newsletter, roteiro)

---

## Transcrever áudio

### OpenAI Whisper API
**O que faz:** Transcreve áudio em texto com alta qualidade, suporta vários idiomas
**Precisa de conta:** Sim, OpenAI (pago, ~$0.006/min)
**Configurar:** Salvar `OPENAI_API_KEY` no `.env`
**Quando usar:** Transcrever áudio de reunião, podcast, áudio de WhatsApp, qualquer arquivo de áudio que não seja vídeo do YouTube

### AssemblyAI
**O que faz:** Transcrição de áudio com features extras: identificação de quem falou, timestamps por palavra, sentimento, resumo automático
**Precisa de conta:** Sim, assemblyai.com (free tier generoso)
**Configurar:** Salvar `ASSEMBLYAI_API_KEY` no `.env`
**Quando usar:** Quando precisar saber quem falou cada parte (entrevista, reunião multi-pessoa), ou quiser features além da transcrição crua

---

## Gerar imagens com IA

### Gemini (Google AI)
**O que faz:** Gera imagens a partir de texto
**Precisa de conta:** Sim, Google AI Studio (grátis até certo limite)
**Configurar:** Salvar `GEMINI_API_KEY` no `.env`
**Quando usar:** Capas, ilustrações, imagens pra posts

### DALL-E (OpenAI)
**O que faz:** Gera imagens a partir de texto
**Precisa de conta:** Sim, OpenAI (pago)
**Configurar:** Salvar `OPENAI_API_KEY` no `.env`
**Quando usar:** Alternativa ao Gemini pra geração de imagens

### FAL API
**O que faz:** Plataforma de inferência de modelos de imagem premium: Flux, Recraft, Stable Diffusion 3, entre outros
**Precisa de conta:** Sim, fal.ai (pago por imagem, varia por modelo)
**Configurar:** Salvar `FAL_KEY` no `.env`
**Quando usar:** Quando Gemini/DALL-E não dão a qualidade necessária. FAL roda os modelos mais novos pra cada caso de uso

---

## Trabalhar com planilhas e dados

### Google Sheets API (gspread)
**O que faz:** Lê e escreve em planilhas do Google Sheets via Python
**Precisa de conta:** Sim, conta Google + service account no Google Cloud
**Configurar:**
1. Criar service account no console.cloud.google.com
2. Habilitar Google Sheets API e Google Drive API
3. Baixar JSON da service account
4. Compartilhar a planilha com o email da service account como editor
5. Salvar caminho do JSON no `.env`
**Quando usar:** Skills que leem planilha de controle, atualizam dados, geram relatório em planilha

---

## Trabalhar com código e Git

### gh CLI / GitHub API
**O que faz:** Interage com GitHub direto do terminal: criar PRs, releases, issues, ver checks de CI, gerenciar repos
**Precisa de conta:** Sim, GitHub (grátis)
**Como instalar:**
```bash
brew install gh
gh auth login
```
**Quando usar:** Skills que automatizam fluxo de Git: abrir PR, criar release, comentar em issue, listar PRs pendentes

---

## Tráfego pago e analytics

### Google Analytics 4 (Data API)
**O que faz:** Lê dados de propriedades GA4: sessões, usuários, pageviews, conversões, fontes de tráfego
**Precisa de conta:** Sim, propriedade GA4 + service account com acesso de leitura
**Quando usar:** Skills que precisam ler tráfego, performance de landing pages, conversões, dados de comportamento do site

### Meta Ads (Marketing API)
**O que faz:** Gerencia campanhas no Facebook/Instagram Ads: criar, editar, pausar, duplicar, ler insights
**Precisa de conta:** Sim, conta de anúncios Meta + token de longa duração
**Quando usar:** Skills de gestão de mídia paga Meta, relatórios de performance, criação de campanhas

### Google Ads API
**O que faz:** Lê e edita campanhas Google Ads (Search, Performance Max, Shopping), busca keywords, lê quality score
**Precisa de conta:** Sim, conta Google Ads + developer token
**Quando usar:** Skills de gestão Google Ads, pesquisa de keywords, relatórios de quality score

---

## Conectar com plataformas (MCPs)

MCPs são conectores que dão acesso direto a plataformas dentro do Claude Code.

Pra verificar quais MCPs já estão instalados: `claude mcp list`
Pra remover um MCP: `claude mcp remove nome-do-mcp`

### Notion
**O que faz:** Acessa projetos, bases de dados, briefings e tarefas do Notion
**Precisa de conta:** Sim, API key em notion.so/my-integrations
**Como instalar:**
```bash
claude mcp add notion -- npx -y @notionhq/notion-mcp-server
```

### Gmail
**O que faz:** Lê e compõe emails sem sair do Claude Code
**Como instalar:**
```bash
claude mcp add gmail -- npx -y @gongrzhe/server-gmail-autoauth-mcp
```

### Google Calendar
**O que faz:** Vê agenda, cria eventos e encontra horários disponíveis
**Como instalar:**
```bash
claude mcp add google-calendar -- npx -y @gongrzhe/server-google-calendar-autoauth-mcp
```

### Canva
**O que faz:** Acessa designs e cria novos assets visuais direto pelo Claude
**Precisa de conta:** Sim, Canva Pro
**Como instalar:**
```bash
claude mcp add canva -- npx -y @canva/canva-mcp-server
```

### Google Drive
**O que faz:** Lê e busca arquivos do Google Drive (docs, planilhas, PDFs, imagens)
**Quando usar:** Skills que precisam ler material que mora no Drive (briefings, base de conhecimento, decks antigos)

### context7
**O que faz:** Busca documentação atualizada de bibliotecas, frameworks, SDKs e APIs (React, Next.js, Prisma, Tailwind, etc)
**Precisa de conta:** Não
**Como instalar:**
```bash
claude mcp add context7 -- npx -y @upstash/context7-mcp
```
**Quando usar:** Sempre que a skill envolver código com biblioteca ou framework

### N8N
**O que faz:** Dispara automações e workflows do N8N
**Como instalar:**
```bash
claude mcp add n8n -- npx -y n8n-mcp
```

### Supabase
**O que faz:** Banco de dados e backend completo
**Quando usar:** Skills que precisam guardar dados, autenticação, backend

### Telegram
**O que faz:** Envia e recebe mensagens via bot do Telegram
**Quando usar:** Skills de notificação, comunicação automática

### Trello
**O que faz:** Lê e atualiza boards, listas e cards do Trello
**Configurar:** Salvar `TRELLO_KEY` e `TRELLO_TOKEN` no `.env`
**Quando usar:** Skills que leem briefing de card, atualizam status, criam card a partir de uma demanda

---

## Como adicionar ferramentas novas

Se você usa uma API ou ferramenta que não está nessa lista, adicione aqui seguindo o formato:

```markdown
### Nome da Ferramenta
**O que faz:** [descrição em uma frase]
**Precisa de conta:** [Sim/Não]
**Configurar:** [o que salvar no .env, se aplicável]
**Como usar numa skill:** [comando ou instrução]
**Quando usar:** [em que tipo de skill faz sentido]
```
