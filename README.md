# onze-manager-assets

Repositório de conteúdo extra do ONZE — Football Manager (fotos, escudos e músicas).
O jogo (pacote leve) busca esses arquivos aqui em tempo real, via CDN jsDelivr,
em vez de trazê-los dentro do instalador.

## Estrutura

```
onze-manager-assets/
├── players/    <slug-do-jogador>.jpg     (ex: lionel-messi.jpg)
├── coaches/    <slug-do-tecnico>.jpg     (ex: pep-guardiola.jpg)
├── logos/      <abbr-minusculo>.png      (ex: mci.png)
├── stadiums/   <slug-do-estadio>.jpg     (ex: etihad-stadium.jpg)
└── audio/      qualquer .mp3/.ogg/.wav/.m4a (nome livre)
```

As regras de nome de arquivo (slug) são as mesmas de antes — veja os
READMEs dentro de cada pasta do projeto do jogo (`assets/players/README.md`,
etc.) para a tabela de conversão de nome → slug.

## Como publicar

```bash
git init
git remote add origin https://github.com/ryanss-zero/onze-manager-assets.git
git add .
git commit -m "assets iniciais"
git branch -M main
git push -u origin main
```

## URL usada pelo jogo

```
https://cdn.jsdelivr.net/gh/ryanss-zero/onze-manager-assets@main/<pasta>/<arquivo>
```

Essa é a linha configurada em `index.html` do jogo (`window.ONZE_ASSETS_BASE`).

## Atualizando arquivos depois

O jsDelivr cacheia agressivamente quando você aponta para `@main` (pode levar
até ~7 dias, ou até 24h para arquivos já acessados, para refletir mudanças).
Duas opções:

1. **Purge manual** (rápido, grátis): cole a URL do arquivo em
   https://www.jsdelivr.com/tools/purge depois de cada push.
2. **Versionar por tag** (mais previsível): crie uma tag Git (`v1`, `v2`...)
   a cada leva de assets novos e troque `@main` por `@v2` no `index.html`
   do jogo — arquivos com tag nova nunca ficam presos em cache antigo.

Já a pasta `players/` e `audio/` deste pacote vêm com os arquivos que já
existiam no seu projeto original.
