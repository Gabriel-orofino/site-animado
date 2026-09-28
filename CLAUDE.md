# Site animado com 4 skills grátis

Este arquivo é para o Claude Code. Ele prepara esta pasta para fazer um site inspirado num site premiado, com 4 skills gratuitas, e diz ao Claude como usar as quatro juntas.

**Como usar:** crie uma pasta vazia, coloque este arquivo dentro com o nome `CLAUDE.md`, abra o Claude Code nessa pasta e escreva `instala tudo`.

As 4 skills são de código aberto (licença MIT) e rodam com as mesmas permissões do Claude Code. O Claude pede a sua aprovação antes de cada comando.

---

## 1. Instalação (só na primeira vez)

Quando a pessoa pedir para instalar, ou se esta pasta ainda não tiver o arquivo `.instalado`, faça a instalação abaixo antes de qualquer outra coisa. Quem está do outro lado pode nunca ter usado um terminal: antes de cada passo, diga numa frase simples o que vai fazer e para quê. Pule o que já estiver instalado.

### 1.1 Ver o computador

Descubra o sistema (Mac, Windows ou Linux) e confira o que já existe:

- Node.js 18 ou mais novo (`node -v`)
- git (`git --version`)
- ffmpeg completo: `ffmpeg -hide_banner -filters` precisa listar mais de 200 filtros
- um navegador Chrome, Chromium ou Edge

Mostre para a pessoa uma lista curta: o que já tem e o que falta.

### 1.2 Instalar o que falta

| Programa | Mac | Windows | Linux (Debian/Ubuntu) |
|---|---|---|---|
| Node.js | `brew install node` | `winget install OpenJS.NodeJS.LTS` | `sudo apt install nodejs npm` |
| git | `xcode-select --install` | já vem com o Claude Code | `sudo apt install git` |
| ffmpeg | `brew install ffmpeg` | `winget install Gyan.FFmpeg` | `sudo apt install ffmpeg` |
| Navegador | `brew install --cask google-chrome` | o Edge do Windows já serve | `sudo apt install chromium` |

- **Mac sem Homebrew** (o comando `brew` não existe): o instalador pede a senha do computador, então peça para a pessoa abrir o app Terminal, colar o comando abaixo, seguir o que ele pedir e voltar aqui quando terminar. Se depois o `brew` continuar não sendo encontrado, rode `eval "$(/opt/homebrew/bin/brew shellenv)"`.

  ```
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```

- **Qualquer comando que peça senha** (`sudo` no Linux, instalador do Homebrew): a pessoa roda no Terminal dela. Você não consegue digitar a senha.
- **Windows:** depois de instalar com o `winget`, o terminal aberto ainda não enxerga o programa novo. Peça para a pessoa fechar o Claude Code, abrir de novo nesta pasta e escrever `instala tudo` outra vez. Você continua de onde parou, pulando o que já estiver pronto.
- Se o Node for mais velho que o 18, atualize antes de seguir.

### 1.3 As 4 skills

```
npx -y skills add zanwei/design-dna -a claude-code -g -y
npx -y skills add anthropics/skills --skill frontend-design -a claude-code -g -y
npx -y skills add Leonxlnx/taste-skill --skill design-taste-frontend -a claude-code -g -y
npx -y skills add nateherkai/scroll-craft --skill scroll-craft -a claude-code -g -y
```

Elas ficam em `~/.claude/skills/` e servem para qualquer pasta do computador.

| Skill | Autor | Para que serve |
|---|---|---|
| [Design DNA](https://github.com/zanwei/design-dna) | zanwei | Lê um site de referência e transforma o desenho dele num arquivo: fontes, cores, espaçamento e movimento |
| [Frontend Design](https://github.com/anthropics/skills) | Anthropic | Tira do site a cara de "feito por IA" |
| [Taste Skill](https://github.com/Leonxlnx/taste-skill) | Leonxlnx | Regula o quanto o design ousa, se mexe e enche a tela |
| [Scrollcraft](https://github.com/nateherkai/scroll-craft) | Nate Herk | Constrói o site guiado pela rolagem e confere o próprio trabalho no navegador |

### 1.4 O que as skills usam

1. A Design DNA mede as cores com um script que precisa da biblioteca `sharp`:

   ```
   npm install --prefix ~/.claude/skills/design-dna/scripts
   ```

2. Nesta pasta, o `playwright-core`. É com ele que a Scrollcraft abre o site no navegador para conferir o próprio trabalho, e que você tira os prints do site de referência para a Design DNA. Se ainda não existir um `package.json` aqui, rode `npm init -y` antes:

   ```
   npm i playwright-core
   ```

   O `playwright` completo não é necessário: o `playwright-core` usa o Chrome ou o Edge que já está no computador.

3. A área de trabalho da Scrollcraft, onde ficam os sites que ela constrói:

   ```
   node ~/.claude/skills/scroll-craft/scripts/workspace.mjs --ensure
   ```

4. As pastas do projeto: `marca/` (logo), `fotos/` e `video/`.

### 1.5 Conferir

```
node ~/.claude/skills/scroll-craft/scripts/doctor.mjs
```

- `FAIL` em node ou ffmpeg: resolva antes de seguir.
- Aviso de `libwebp`: pode seguir. As capas saem em JPEG.
- Aviso de `KIE_AI_API_KEY`: pode seguir. A chave só serve para a Scrollcraft gerar imagem e vídeo pagando, e aqui as imagens e o vídeo chegam prontos.
- Navegador não encontrado, mesmo instalado: defina `SCROLLCRAFT_CHROME` com o caminho do executável.
- O autor da Scrollcraft avisa que ela foi testada só no Windows. Se algo falhar no Mac ou no Linux, diga para a pessoa o que falhou e o que você tentou.

### 1.6 Terminar

Crie o arquivo `.instalado` com a data de hoje e diga para a pessoa:

> Pronto. Fecha o Claude Code e abre de novo nesta pasta, para as skills carregarem. Depois coloca o logo em `marca/`, as fotos em `fotos/` e o vídeo do topo em `video/`.

---

## 2. Fazer o site

Quando a pessoa pedir um site:

1. **Confira os arquivos.** Logo em `marca/`, fotos em `fotos/`, vídeo do topo em `video/`. Se faltar algo, pergunte antes de começar. Não invente foto nem vídeo.
2. **Design DNA primeiro.** Abra o site de referência no navegador com o `playwright-core`, tire prints de cada seção, no computador e no celular, e extraia o DNA: fontes, cores, espaçamento e movimento da rolagem. Mostre um resumo curto para a pessoa.
3. **Frontend Design e Taste Skill** decidem o acabamento: tipografia, respiro, quanto o site ousa e quanto se mexe.
4. **Scrollcraft constrói** a página guiada pela rolagem e confere o resultado no navegador, no computador e no celular.
5. **Logo com fundo claro:** deixe o fundo transparente para usar em cima das cores do site.
6. **Vídeo do topo:** roda sozinho em loop, sem som, e pausa quando sai da tela.
7. No fim, abra o site para a pessoa ver e mostre também os prints do celular.

Regras:

- O site de referência é inspiração. Use o DNA dele e não copie textos, imagens nem código: o desenho original é do estúdio que fez.
- Texto em português do Brasil, do jeito que fala o cliente do negócio.
- Não invente nota, número de avaliações, depoimento nem prêmio. Num negócio de demonstração, endereço e telefone ficam como exemplo.
- O site precisa funcionar bem no celular.
