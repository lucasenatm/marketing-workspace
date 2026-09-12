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

**Antes de pedir qualquer coisa ao usuário,** descubra o que já existe na máquina:

```bash
gh --version
gh auth status
```

O caminho muda conforme a resposta, e a regra é sempre a mesma: **ensine só o degrau que falta.** Quem já tem tudo pronto não deve ver tutorial de cadastro, e quem nunca usou GitHub não deve receber os quatro degraus de uma vez.

| O que você encontrou | Vá para |
|---|---|
| `gh` instalado e autenticado | **A1**, cria o repositório e pronto |
| `gh` instalado, mas não autenticado | **A2** |
| `gh` não instalado | **A3** |

Sempre que um degrau for resolvido, volte a verificar e siga para o de cima. O destino final é sempre o A1.

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

### A2: o `gh` existe, mas não está autenticado

Aqui tem uma bifurcação que não dá para adivinhar: o usuário pode nunca ter tido conta no GitHub. Pergunte antes de mandar comando, e explique o porquê primeiro, porque quem é de marketing não tem motivo nenhum para saber o que é GitHub:

> "Antes de guardar seu trabalho, preciso te conectar no GitHub. Explicando rápido: é onde os seus arquivos ficam guardados fora do seu computador. Se o note morrer amanhã, você abre em outro e está tudo lá.
>
> É de graça, e o seu vai ficar privado, então ninguém vê o que tem dentro.
>
> Você já tem conta no GitHub?"

**Se já tem conta:**

> "Então é rápido. Roda isso:"

```bash
gh auth login
```

> "Ele vai te fazer umas perguntas. Responde assim:
>
> - What account do you want to log into? **GitHub.com**
> - What is your preferred protocol? **HTTPS**
> - Authenticate Git with your GitHub credentials? **Yes**
> - How would you like to authenticate? **Login with a web browser**
>
> Aí ele mostra um código tipo `A1B2-C3D4`. Copia, aperta enter, o navegador abre, você cola o código e autoriza. Quando voltar, me chama que eu crio o repositório."

**Se não tem conta:** vá para o bloco **"Criando a conta do zero"** logo abaixo.

Quando o usuário voltar, rode `gh auth status` de novo e siga para o **A1**.

---

### A3: o `gh` não está instalado

> "Falta um programa aqui, o GitHub CLI. É ele que me deixa conversar com o GitHub sem você precisar ficar copiando link e senha. Instala com isso:"

No Windows:

```bash
winget install --id GitHub.cli
```

No Mac:

```bash
brew install gh
```

> "Uma coisa importante: depois de instalar, **fecha e abre o terminal de novo**. Se você continuar nessa janela, o comando não vai ser encontrado e vai parecer que deu errado. É só isso, ele só aparece numa janela nova.
>
> Quando reabrir, me chama."

Quando o usuário voltar, rode `gh --version` para confirmar e siga para o **A2**.

---

### Bloco: criando a conta do zero

Para quem nunca usou GitHub. **Uma etapa por vez, esperando o usuário confirmar antes de seguir.** Não despeje as quatro etapas de uma vez, porque é exatamente aqui que a pessoa desiste.

**Etapa 1, criar a conta:**

> "Abre github.com/signup. Vai pedir email, senha e um nome de usuário.
>
> Só um cuidado com o nome de usuário: ele vai aparecer no endereço dos seus projetos, tipo `github.com/seunome/meu-workspace`. Então escolhe algo que você não vá se arrepender de mostrar pra cliente.
>
> Me avisa quando criar."

**Etapa 2, confirmar o email:**

> "Eles mandam um código no seu email. Cola lá e a conta está feita. Se aparecer pergunta sobre plano, o gratuito serve, não precisa de pago pra nada do que a gente vai fazer.
>
> Feito?"

**Etapa 3, conectar aqui:**

> "Agora volta pro terminal e roda:"

```bash
gh auth login
```

> "As respostas são: **GitHub.com**, depois **HTTPS**, depois **Yes**, depois **Login with a web browser**.
>
> Ele mostra um código, você copia, aperta enter, o navegador abre, cola o código e autoriza."

**Etapa 4, fechar:**

> "Terminou? Me chama que agora eu crio o repositório e subo tudo, isso é comigo."

Quando o usuário confirmar, rode `gh auth status` e siga para o **A1**.

---

### A4: o usuário prefere fazer na mão

Só ofereça este caminho se o usuário pedir, ou se o `gh` falhar duas vezes. Ele existe como saída de emergência, não como alternativa equivalente.

> "Dá pra fazer sem o GitHub CLI também:
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

**Na primeira vez, o degrau é sagrado**

- Nunca despeje a escada inteira. Diagnostique com `gh --version` e `gh auth status`, e ensine **só o degrau que falta**. Quem já tem conta não deve ver tutorial de cadastro.
- No bloco de criar conta, **uma etapa por vez**, esperando o usuário confirmar antes de seguir. Quatro etapas de uma vez é onde a pessoa desiste.
- Nunca peça ao usuário para criar repositório no navegador se o `gh` estiver autenticado. O manual (**A4**) é saída de emergência, não alternativa equivalente.
- Diga o porquê antes do como. Quem é de marketing não tem motivo para saber o que é GitHub, e faz diferença ouvir que é de graça e que o repositório é privado antes de ser mandado para uma tela de cadastro.
- Depois de qualquer degrau resolvido, verifique de novo em vez de assumir que deu certo.

**Sempre**

- Nunca commitar `.env`, `.env.local` ou qualquer arquivo com chaves secretas
- Tom direto, sem explicar git em detalhes a não ser que o usuário pergunte
- Nunca usar travessão. No lugar dele, vírgula, ponto ou dois-pontos
- Se der erro, sempre mostrar o que fazer a seguir, nunca só mostrar o erro
- Se o usuário perguntar "o que está indo pro backup" ou similar, ler o `.gitignore` da raiz e resumir em linguagem simples o que fica de fora e o que entra. Nunca simplesmente colar o conteúdo bruto do arquivo
- O `.gitignore` é só o padrão inicial. Se o usuário pedir pra incluir ou excluir algo do backup, editar o arquivo na hora e confirmar o que mudou
