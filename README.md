# Site animado com 4 skills grátis do Claude

O arquivo [CLAUDE.md](CLAUDE.md) deste repositório faz o Claude Code instalar sozinho as 4 skills do vídeo e tudo o que elas precisam. Depois, ele diz ao Claude como usar as quatro juntas para fazer um site inspirado num site premiado.

## Como usar

1. Crie uma pasta vazia no seu computador.
2. Baixe o [CLAUDE.md](CLAUDE.md) para dentro dela: abra o arquivo e clique no botão de baixar (a setinha para baixo, "Download raw file"). O nome precisa ficar `CLAUDE.md`.
3. Abra o Claude Code nessa pasta e escreva:

   ```
   instala tudo
   ```

4. Quando ele terminar, feche o Claude Code e abra de novo na mesma pasta, para as skills carregarem.

**Sem baixar nada:** abra o Claude Code numa pasta vazia e cole isto:

```
Baixa o arquivo https://raw.githubusercontent.com/Gabriel-orofino/site-animado/main/CLAUDE.md, salva nesta pasta com o nome CLAUDE.md e segue as instruções dele para instalar tudo.
```

O Claude pede a sua aprovação antes de cada comando. O que precisa da senha do computador, ele pede para você rodar no Terminal.

## O que ele instala

| O quê | Para quê |
|---|---|
| Node.js, git, ffmpeg e Chrome (no Windows, o Edge já serve) | O que as skills usam por baixo. Só instala o que faltar |
| As 4 skills | Ficam em `~/.claude/skills/` e servem para qualquer pasta |
| `sharp` | A Design DNA mede as cores do site de referência com ele |
| `playwright-core` | O Claude abre o site no navegador para tirar prints e conferir o próprio trabalho |

## As 4 skills

Todas grátis, de código aberto (licença MIT). O crédito é de quem fez:

| Skill | Autor | O que faz |
|---|---|---|
| [Design DNA](https://github.com/zanwei/design-dna) | zanwei | Lê um site de referência e transforma o desenho dele num arquivo: fontes, cores, espaçamento e movimento |
| [Frontend Design](https://github.com/anthropics/skills) | Anthropic | Tira do site a cara de "feito por IA" |
| [Taste Skill](https://github.com/Leonxlnx/taste-skill) | Leonxlnx | Regula o quanto o design ousa, se mexe e enche a tela |
| [Scrollcraft](https://github.com/nateherkai/scroll-craft) | Nate Herk | Constrói o site guiado pela rolagem e confere o resultado no navegador |

O autor da Scrollcraft avisa que ela foi testada só no Windows.

## Depois de instalar

Coloque na pasta o logo em `marca/`, as fotos em `fotos/` e o vídeo do topo em `video/`, e peça o site ao Claude dizendo qual site premiado usar de inspiração. Ele usa o desenho desse site como referência, sem copiar texto, imagem nem código.
