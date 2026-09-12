---
name: salvar
description: >
  Salva o estado atual do workspace no GitHub (commit + push).
  Use quando quiser garantir que o trabalho está seguro, ao final de uma sessão produtiva,
  ou quando o usuário disser "salva no github", "faz commit", "salva", "salvar",
  "backup no github", "salva tudo", "manda pro github".
  Também configura o git pela primeira vez se ainda não estiver configurado.
user-invokable: true
argument-hint: ""
license: MIT
---

# /salvar · backup no GitHub

## Verificação inicial

Rode os dois comandos pra entender o estado atual:

```bash
git status --short
git remote get-url origin 2>/dev/null
```

---

## Fluxo A: sem remote configurado (primeira vez)

Se `git remote get-url origin` não retornar nada, o workspace ainda não está conectado.

**Antes de pedir qualquer coisa ao usuário,** verifique se o GitHub CLI está disponível e autenticado:

```bash
gh auth status
```

O caminho muda conforme a resposta.

### A1: o `gh` responde autenticado

Este é o caminho preferido. Não mande o usuário para o navegador, crie o repositório daqui.

Pergunte só o essencial, numa tacada:

> "Vou criar um repositório no GitHub pra guardar esse workspace. Que nome você quer? Se não tiver preferência, uso `meu-workspace`.
>
> E prefere privado ou público? Privado é o padrão e é o que eu recomendo, principalmente se tem coisa de cliente aqui dentro."

Com a resposta, garanta que existe pelo menos um commit antes de criar o repositório:

```bash
git branch -M main
git add -A
git commit -m "primeiro commit: workspace configurado"
```

Se o commit falhar por não ter nada para commitar, siga em frente, não é erro.

Depois crie e suba de uma vez:

```bash
gh repo create [nome] --private --source=. --remote=origin --push
```

Trocar `--private` por `--public` se o usuário pedir. O `--source=.` usa a pasta atual, o `--remote=origin` já configura o remote e o `--push` sobe tudo na hora, então não é preciso `git remote add` nem `git push` separados.

Se falhar porque já existe repositório com esse nome, avise e pergunte outro nome. Nunca invente um nome alternativo sozinho.

### A2: o `gh` não existe ou não está autenticado

Só aqui vale o caminho manual. Primeiro tente resolver sem ele:

> "Pra eu criar o repositório sozinho, preciso do GitHub CLI conectado. Se você já tem ele instalado, roda `gh auth login` que leva um minuto, e me chama de novo.
>
> Se preferir fazer na mão, também dá, é só me dizer."

Se o usuário quiser o caminho manual:

> "Então faz assim:
> 1. Abre github.com/new
> 2. Cria um repositório, pode ser privado. Nome sugerido: `meu-workspace`
> 3. Não marca a opção de inicializar com README, deixa vazio
> 4. Me manda o link do repositório (tipo https://github.com/seunome/meu-workspace)"

Depois de receber o link:

```bash
git branch -M main
git add -A
git commit -m "primeiro commit: workspace configurado"
git remote add origin [link]
git push -u origin main
```

Confirme:

> "Conectado. Seu workspace está agora em [link].
> A partir de agora, rode /salvar sempre que quiser salvar o que fez.
>
> Uma coisa importante: nem tudo vai pro GitHub. O `.gitignore` da raiz define o que fica de fora (normalmente dado bruto de cliente, briefings, propostas) e o que entra (entregas publicadas, identidade visual, diário de projeto). Se quiser ver exatamente o que está sendo ignorado, ou incluir mais coisa no backup, é só pedir."

Se o `.gitignore` ainda não existir nesse ponto (workspace não passou pelo `/configurar`), avisar antes de conectar:

> "Não achei um `.gitignore` configurado. Sem ele, tudo que estiver na pasta vai pro repositório, incluindo qualquer chave de API solta ou dado sensível de cliente. Quer que eu crie um básico antes de conectar?"

---

## Fluxo B: remote configurado, tem mudanças

Se `git status` mostrar arquivos modificados, liste o que vai ser salvo e faça o commit:

```bash
git add -A
git commit -m "sync: [descrição curta do que foi feito]"
git push
```

Para a descrição do commit, use o que foi feito na sessão (ex: "sync: nova proposta cliente X", "sync: carrossel episódio 42", "sync: atualização de contexto"). Se não souber o que colocar, use `sync: atualizações do dia`.

Após o push, confirme:

> "Salvo. Seu trabalho está seguro em [url do remote]."

---

## Fluxo C: sem mudanças

Se `git status` não mostrar nada:

> "Tudo já está sincronizado. Nenhuma mudança nova pra salvar."

---

## Fluxo D: erro no push

Se o push falhar (credenciais, conexão, etc.), mostre o erro de forma simples:

> "Não consegui enviar pro GitHub. O erro foi: [mensagem]
>
> Causas mais comuns:
> - Sem conexão com internet
> - Precisa configurar autenticação no GitHub (token ou SSH)
>
> Se quiser resolver agora, me diz e eu te ajudo passo a passo."

---

## Regras

- Nunca commitar `.env`, `.env.local` ou qualquer arquivo com chaves secretas
- Tom direto, sem explicar git em detalhes a não ser que o usuário pergunte
- Se der erro, sempre mostrar o que fazer a seguir, nunca só mostrar o erro
- Se o usuário perguntar "o que está indo pro backup" ou similar, ler o `.gitignore` da raiz e resumir em linguagem simples o que fica de fora e o que entra. Nunca simplesmente colar o conteúdo bruto do arquivo
- O `.gitignore` é só o padrão inicial. Se o usuário pedir pra incluir ou excluir algo do backup, editar o arquivo na hora e confirmar o que mudou
