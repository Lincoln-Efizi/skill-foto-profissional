# Skill: foto profissional com IA

Uma skill para o **Claude Code** que pega uma foto simples, tirada no celular, e devolve **a mesma foto** com cara de
foto profissional. Serve para:

- 🛍️ **Produto** que você vende no marketplace ou na loja online
- 🍔 **Lanche** e pratos no app de delivery
- 🏠 **Anúncio de aluguel** e hospedagem
- 👔 **Foto de perfil** para o LinkedIn

A regra da skill é **não inventar nada**: o produto, a comida, os móveis e o rosto continuam os mesmos. Muda a luz, a
cor, a nitidez e o enquadramento. Assim o seu cliente vê exatamente o que vai receber, só que numa foto que chama a
atenção.

A geração das imagens é feita pela **Higgsfield**. Você precisa de uma conta lá, com créditos.

---

## Como instalar

### 1. Instale o Claude Code

Siga o guia oficial de instalação do Claude Code, da Anthropic.

### 2. Instale o programa da Higgsfield (CLI)

**macOS ou Linux:**
```bash
curl -fsSL https://raw.githubusercontent.com/higgsfield-ai/cli/main/install.sh | sh
```

**Windows:** baixe o arquivo `hf_<versão>_windows_amd64.tar.gz` em
https://github.com/higgsfield-ai/cli/releases, extraia, renomeie `hf.exe` para `higgsfield.exe` e coloque numa pasta
que esteja no seu PATH.

Confira se instalou:
```bash
higgsfield version
```

### 3. Entre na sua conta Higgsfield

```bash
higgsfield auth login
```

Vai abrir o navegador para você entrar. Depois confira:
```bash
higgsfield account status
```

### 4. Instale a skill

```bash
npx skills add Lincoln-Efizi/skill-foto-profissional
```

Ou copie a pasta `skills/foto-profissional` para `~/.claude/skills/foto-profissional`.

---

## Como usar

Abra o Claude Code e escreva, por exemplo:

> /foto-profissional melhore essa foto do meu lanche para o app de delivery: C:\fotos\lanche.jpg

ou só:

> Deixa essa foto do meu produto profissional para eu vender no marketplace

e arraste a foto para o chat. A foto nova é salva ao lado da original, com o nome terminando em `_profissional`.

**Dica:** quanto melhor a foto original (o produto inteiro aparecendo, sem dedo na frente), melhor o resultado.

---

## Custos

A skill é grátis. Cada foto gerada gasta créditos da **sua** conta Higgsfield. Os preços estão no site da Higgsfield.

## Créditos

Feito pela Efizi Tech (@efizitech no Instagram). A geração usa o
[CLI da Higgsfield](https://github.com/higgsfield-ai/cli). Para as skills oficiais da Higgsfield (vídeo, marca, fotos
de produto e mais), veja https://github.com/higgsfield-ai/skills (licença MIT).

## Licença

MIT. Veja o arquivo [LICENSE](LICENSE).
