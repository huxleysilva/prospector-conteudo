# NOTAS — AP Studio Arquitetura (Caldas Novas, GO)

## Situação de partida (importante)

- O domínio oficial **apstudioarquitetura.com.br** retorna **erro 503 persistente** —
  hospedagem fora do ar. Não há snapshot desse domínio `.br` no Wayback Machine.
- Existe um domínio espelho, **apstudioarquitetura.com** (sem `.br`), citado como
  site oficial no Linktree do escritório. Esse domínio também está fora do ar hoje.
- O único material recuperável é um **snapshot do Wayback Machine de 6 de março de
  2023** do domínio `.com`:
  `http://web.archive.org/web/20230306181634/https://www.apstudioarquitetura.com/`
  — usado como "site antigo" neste redesign e no `comparar.html`. É uma versão
  **antiga** (mais de 3 anos), a mais recente disponível.
- **Nenhuma foto de projeto foi recuperável.** O site era feito em Wix; as imagens
  eram servidas dinamicamente de `static.wixstatic.com`. Testei diretamente essas
  URLs (as mesmas que o próprio snapshot tentava carregar) e todas retornam
  **404** — os arquivos de mídia foram removidos do CDN da Wix, provavelmente
  junto com o cancelamento da assinatura. Também verifiquei o CDX API do Wayback
  Machine para esses mesmos arquivos de imagem: **não há nenhuma captura
  arquivada** deles (Wix bloqueia crawlers de indexar essas URLs de mídia).
  Resultado: nem o snapshot, nem o CDN ao vivo, nem o Wayback Machine têm as
  fotos. Por isso este redesign **não usa nenhuma fotografia de projeto** — inventar
  fotos de fachada/interior que não são do AP Studio violaria a regra central deste
  processo (nunca substituir o portfólio real do cliente por imagens genéricas).

## O que foi mantido (extraído do snapshot real)

- **Nome e wordmark**: "AP STUDIO" — no site antigo é só tipografia (fonte
  Raleway), não existe um arquivo de logotipo separado. Recriei o wordmark como
  texto, igual ao original.
- **Tagline**: "Arquitetura • Arte • Design" — mantida literalmente, virou também
  a estrutura da seção de Serviços (3 pilares, um por palavra da tagline).
- **Texto institucional (voz própria)**: o parágrafo "O AP Studio acredita que a
  arquitetura vai além do design (...) realizando sonhos com personalidade e
  autenticidade" foi mantido na íntegra no hero e reaproveitado na seção Sobre.
- **Os 4 projetos reais e suas localizações**: Casa Lago Sul (Caldas Novas-GO),
  Casa Menos (Ceres-GO), Casa Cerrado (Caldas Novas-GO), Casa Samba (Caldas
  Novas-GO). O site antigo não expunha metragem, ano ou ficha técnica detalhada
  desses projetos (só nome + cidade) — não inventei esses dados. A "ficha técnica"
  de cada projeto no site novo mostra apenas o que é real: tipo (residencial),
  localização e escritório.
- **Dados de contato reais**: endereço (Rua Professor Josino Bretas, Quadra 31,
  Lote 11-D, Caldas Novas — Goiás), e-mail (contato@apstudioarquitetura.com,
  exatamente como aparece no snapshot — note que é o domínio `.com`, não `.com.br`)
  e telefone/WhatsApp (64) 99246-6029.
- **Paleta de cores**: extraída via inspeção computada do DOM do próprio snapshot
  (não estimada visualmente) — o wordmark do menu usa `#2c444e` e o wordmark
  grande do hero usa `#4b735b`. Os dois viraram os tokens `--ardosia` e
  `--verde-eucalipto` do site novo. Não inventei paleta nova.
- **Prova social real**: nota 5,0 com 15 avaliações no Google Maps (dado fornecido
  fora do site, mas real e verificável) — usada como estatística de confiança em
  vez de depoimentos inventados, já que nenhum texto de depoimento real estava
  disponível no site antigo.

## O que mudou e por quê

- **Layout movido de "moldura de foto" para "prancha tipográfica".** A regra do
  padrão visual é que a foto manda — mas não existe nenhuma foto real recuperável.
  Em vez de simular isso com stock photos genéricas (o que seria mentir sobre o
  portfólio do cliente) ou deixar placeholders quebrados, cada projeto virou um
  bloco no estilo "legenda de prancha de arquitetura": nome grande em serifada,
  linha fina, ficha técnica tabular. É um elemento assinatura pensado para
  arquitetura especificamente (grid de coordenadas discreto no hero, linhas
  técnicas, numeração 01–04) — não serviria do mesmo jeito para outro nicho.
- **Tipografia**: troquei Raleway (fonte genérica de template Wix) por uma dupla
  serifada de exibição (pilha `Georgia/Iowan Old Style/Palatino`, com personalidade
  de traço) para títulos e nomes de projeto, e uma pilha sans-serif de sistema para
  corpo de texto. Não usei fonte via CDN externo (Google Fonts) — o ambiente de
  build não tinha acesso de rede para baixar os arquivos de fonte, então optei por
  pilhas de fontes de sistema bem escolhidas em vez de depender de uma CDN em
  tempo de execução, o que também é mais rápido.
  Já a paleta e o wordmark são 100% extraídos do original, não genéricos.
- **Estrutura**: de site com 4 páginas (Início/Projetos/Sobre/Contato, típico Wix)
  para página única longa com âncoras — o escritório é pequeno, o conteúdo real
  cabe em uma rolagem, e isso elimina cliques desnecessários no celular.
- **Contato**: WhatsApp acessível (botão fixo no canto + botão no menu + linha de
  contato), formulário nativo com `mailto:` (sem back-end), sem widgets de terceiros.
- **Performance/acessibilidade**: HTML/CSS puro em arquivo único, sem fontes
  externas, sem framework, foco de teclado visível (`:focus-visible`), respeita
  `prefers-reduced-motion`, contraste alto entre texto e fundo, formulário com
  `label` associado a cada campo.
- **OG/compartilhamento**: como não há foto real, criei um cartão Open Graph
  (`assets/og-image.png`, 1200×630) só com o wordmark, a paleta real e o motivo de
  grid técnico — é claramente um cartão gráfico/tipográfico, não uma foto de
  projeto disfarçada.

## Arquivos entregues

- `index.html` — site novo, HTML/CSS puro, uma página.
- `comparar.html` — iframe duplo: antigo (snapshot do Wayback de 06/03/2023,
  domínio `.com`) × novo (`index.html`), com aviso explicando a situação do
  domínio `.com.br` offline e da ausência de fotos.
- `assets/` — `favicon.svg` / `favicon.png` (monograma "AP", cores reais da marca)
  e `og-image.png` / `og-image.webp` (cartão de compartilhamento, gerado a partir
  de `og-source.svg`). Não há fotos de projeto nesta pasta porque nenhuma foto
  real foi recuperável — ver seção "Situação de partida" acima.

## Se o cliente perguntar

- **"Cadê as fotos dos meus projetos?"** — o Wix apagou os arquivos originais
  (todas as URLs de imagem do CDN retornam 404) e o Wayback Machine nunca
  arquivou essas imagens. Preciso que ele envie fotos reais (mesmo que do
  celular) de Casa Lago Sul, Casa Menos, Casa Cerrado e Casa Samba para eu
  encaixar nos blocos de projeto já prontos — o layout foi desenhado exatamente
  para receber uma foto grande por projeto assim que ela existir.
- **"Por que tirou o menu de 4 páginas?"** — o conteúdo real de cada página
  antiga era curto (uma frase, um nome, um endereço); juntar tudo em uma rolagem
  com âncoras é mais rápido no celular e não perde nenhuma informação.
- **"Por que o domínio do e-mail no site é `.com` e não `.com.br`?"** — é
  exatamente o que estava escrito no snapshot original; não alterei sem
  confirmação do cliente sobre qual domínio/e-mail está em uso hoje.
