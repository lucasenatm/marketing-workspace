# Catálogo de Skills

Skills externas prontas pra instalar. Use como referência ao criar skills novas com `/mapear` ou instale diretamente as que fizerem sentido pro seu negócio.

> Skills globais ficam em `~/.claude/skills/` e funcionam em qualquer projeto.
> Skills locais ficam em `.claude/commands/` e só funcionam nesse projeto.

---

## Escrever copy e textos de venda

### Schwartz Copy (resposta direta)
**O que faz:** Escreve copy de vendas usando a metodologia de Eugene Schwartz (Breakthrough Advertising). Diagnostica o nível de consciência e sofisticação do mercado antes de gerar qualquer texto.
**Bom pra:** Landing pages, emails de venda, VSLs, cartas de venda, páginas de captura
**Como instalar:** Já vem como skill global. Chamar com `/schwartz-copy`

### Ogilvy Copy (marca e posicionamento)
**O que faz:** Gera copy institucional usando a metodologia de David Ogilvy. Pesquisa profunda, big idea, headlines informativas.
**Bom pra:** Manifestos de marca, campanhas institucionais, taglines, brand voice, posicionamento
**Como instalar:** Já vem como skill global. Chamar com `/ogilvy-copy`

---

## Criar interfaces e páginas web

### Frontend Design
**O que faz:** Cria interfaces web completas com design de alta qualidade. Gera código HTML/CSS/React pronto pra usar, com visual profissional.
**Bom pra:** Landing pages, dashboards, componentes web, páginas de produto
**Como instalar:** Já vem nativo no Claude Code. Chamar com `/frontend-design`

---

## Criar visuais e arte

### Canvas Design
**O que faz:** Cria arte visual em PNG e PDF usando princípios de design. Posters, capas, peças gráficas.
**Bom pra:** Capas de ebook, banners, peças visuais, thumbnails
**Como instalar:** Já vem nativo no Claude Code. Chamar com `/canvas-design`

---

## Trabalhar com documentos

### PDF
**O que faz:** Manipula PDFs: extrai texto e tabelas, cria novos, junta/separa documentos, preenche formulários.
**Como instalar:** Já vem nativo no Claude Code. Chamar com `/pdf`

### DOCX
**O que faz:** Cria e edita documentos Word com formatação, tracked changes e comentários.
**Como instalar:** Já vem nativo no Claude Code. Chamar com `/docx`

### PPTX
**O que faz:** Cria e edita apresentações PowerPoint com layouts, speaker notes e formatação.
**Como instalar:** Já vem nativo no Claude Code. Chamar com `/pptx`

### XLSX
**O que faz:** Cria e edita planilhas com fórmulas, formatação e gráficos.
**Como instalar:** Já vem nativo no Claude Code. Chamar com `/xlsx`

---

## Extrair transcrição de vídeo

### YT Transcript
**O que faz:** Extrai transcrições de vídeos do YouTube usando yt-dlp. Suporta múltiplos idiomas.
**Bom pra:** Criar conteúdo a partir de vídeos (carrosséis, newsletters, posts)
**Precisa de:** yt-dlp instalado (`brew install yt-dlp`)
**Como instalar:** Já vem como skill global. Chamar com `/yt-transcript`

---

## Descobrir skills disponíveis

### Find Skills
**O que faz:** Ajuda a descobrir e instalar skills quando você não sabe se existe alguma pra resolver o que precisa.
**Bom pra:** Quando o `/mapear` não acha template e você quer pesquisar antes de criar do zero
**Como instalar:** Já vem nativo no Claude Code. Chamar com `/find-skills`

---

## Testar sites e apps

### Webapp Testing
**O que faz:** Testa aplicações web locais usando Playwright. Captura screenshots, verifica funcionalidade, lê logs do browser.
**Bom pra:** Testar landing pages antes de publicar, verificar se tudo funciona em diferentes tamanhos
**Como instalar:** Já vem nativo no Claude Code. Chamar com `/webapp-testing`

---

## Criar skills novas

### Skill Creator
**O que faz:** Guia pra criar skills novas do zero. Ajuda a estruturar, definir triggers e testar.
**Como instalar:** Já vem nativo no Claude Code. Chamar com `/skill-creator`

---

## Como adicionar skills a este catálogo

Se você testou uma skill e quer adicionar aqui pra referência futura:

```markdown
### Nome da Skill
**O que faz:** [descrição em uma frase]
**Bom pra:** [casos de uso práticos]
**Como instalar:** [comando ou instrução]
```
