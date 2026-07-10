# NOTAS — Redesign Andressa Castro Arquitetura e Interiores

## Situação de partida

O domínio original, `https://andressacastroarq.com.br/arquiteta`, está **fora do
ar** (DNS não resolve). Para reconstruir o site antigo e alimentar o lado
"antes" do `comparar.html`, usei o snapshot do Wayback Machine de
**30/03/2025**:

```
http://web.archive.org/web/20250330215711/https://andressacastroarq.com.br/
```

Confirmei via a API do próprio Wayback Machine (CDX) que **existem apenas 3
capturas no acervo**, e todas são só do HTML da página raiz — nenhuma imagem,
CSS ou outro arquivo do domínio foi arquivado. Ou seja: o Wayback Machine não
guardou nenhuma foto real do portfólio dela, só o texto e a estrutura da
página (que também aparecia com todas as imagens quebradas ao abrir o
snapshot — dá pra conferir).

## Sobre as fotos de projeto (leia isto antes de reclamar do "placeholder")

A regra número um deste processo é: **nunca inventar foto de projeto do
cliente**. Segui essa regra à risca, e isso teve um custo prático:

- O site antigo não tinha imagens arquivadas (ver acima).
- Localizei fotos reais dela no Instagram (**@andressacastro.arq**, perfil
  verificado, 583 posts, 6,1 mil seguidores — ativo e real) e confirmei que
  existem fotos de ambientes de qualidade editorial (uma delas: sala de estar
  em tom terroso/oliva, muito coerente com o posicionamento "sofisticação").
- Porém, o ambiente técnico usado neste redesign **bloqueia deliberadamente a
  extração de arquivos binários/imagens de páginas de terceiros** (uma
  proteção contra exfiltração de dados) — não consegui salvar essas fotos como
  arquivo real dentro da pasta `assets/`.

Diante disso, a escolha foi: **não fabricar uma foto falsa e não colocar
foto de banco de imagens fingindo ser projeto dela.** Em vez disso, o
`index.html` usa blocos geométricos com moldura fina (o mesmo motivo visual
do "traço de projeto arquitetônico") exatamente no lugar, proporção e recorte
onde a foto real vai entrar — com a legenda "foto real a inserir" visível só
como guia de montagem. Assim que a Andressa mandar as fotos (ou autorizar
puxar do Instagram/Google Meu Negócio), é literalmente arrastar o arquivo
`.webp` no lugar do bloco — a arte já está no tamanho, no `aspect-ratio` e no
recorte certos.

A **paleta de cores** do site novo (pedra clara, oliva, terracota) foi
extraída visualmente da própria fotografia real do portfólio dela vista no
Instagram — não é uma paleta genérica de template, é a cor real dos materiais
que ela usa (pedra/travertino claro, linho, estofado oliva, madeira
acastanhada).

## O que foi mantido (é dela, não mexi)

- **Nome do escritório**: Andressa Castro Arquitetura e Interiores.
- **Frase de abertura original**: "Seu Espaço, Sua Essência" — vira o H1.
- **Texto de posicionamento**, quase verbatim: "Transformamos ideias de
  ambientes em experiências únicas..." e o parágrafo de fechamento "Não é
  para todos. É para quem entende que design de interiores vai além da
  estética — é sobre criar experiências." (citação direta, sem alterar).
- **Os três serviços e as respectivas descrições em bullets**: Projeto de
  Interiores (Reformas), Consultoria de Interiores, Construção do Zero — texto
  original, só reorganizado visualmente.
- **O "Método Exclusivo" em 3 passos**: Consultoria Personalizada,
  Conceituação Única, Execução Impecável — texto original.
- **Os diferenciais**: 5+ anos de experiência, +300 ambientes, design
  exclusivo, supervisão de obra — texto original.
- **Contato real**: WhatsApp (61) 99655-4545 (número informado na
  qualificação do lead — é diferente do telefone que aparecia no rodapé do
  site arquivado, `(61) 9995-5517`; usei o número atual/correto), e-mail
  `andressacastro.arq@gmail.com` (do rodapé do site antigo), Instagram
  `@andressacastro.arq` (link do rodapé do site antigo, perfil confirmado
  ativo).
- **Nota do Google**: 5,0 com 21 avaliações, confirmada direto no Google Maps.
  Consegui resgatar **um trecho real de avaliação**: "Uma arquiteta
  competente, detalhista e com muito bom gosto!" — é o único texto de
  depoimento que consegui confirmar como autêntico; não inventei mais
  depoimentos para preencher a seção.
- **Os rótulos dos projetos** ("Ap1", "Ap2", "Ap3" no site antigo) — o site
  original não tinha metragem, ano ou nome específico de projeto, só esses
  três rótulos genéricos de galeria. Traduzi para "Apartamento 01/02/03", sem
  inventar dado nenhum que não existisse (nenhuma metragem/ano/local foi
  fabricado).

## O que mudou (e por quê)

- **De funil de captura para site institucional real.** O site antigo era
  uma landing page de "agência de tráfego" — bloco preto decorativo quebrado,
  três CTAs agressivos ("FALE COMIGO AGORA!") empilhados, zero fotos
  carregando, formulário externo (`form.overflowmkt.com`). Troquei por uma
  página única, com índice numerado (01–05) igual a um portfólio de
  arquitetura editorial, WhatsApp nativo (`wa.me`) em vez de formulário de
  terceiro, e um formulário próprio simples com `mailto:` como alternativa.
- **Tipografia com opinião**: Fraunces (serifada, com peso editorial) para
  títulos + Inter Tight para corpo, no lugar da tipografia default do
  construtor de sites anterior.
- **Espaço em branco**: um projeto por bloco, respiro generoso, nada de seção
  empilhada sem hierarquia.
- **Zero gradiente decorativo, zero sombra difusa** — o único elemento gráfico
  fixo é a moldura fina com cantos em L (referência a desenho técnico/traço de
  projeto), que também é o "elemento assinatura" da página.
- **Uma única animação**: revelação suave no scroll dos cards, respeitando
  `prefers-reduced-motion`.
- **Botão de WhatsApp flutuante e discreto**, sempre alcançável em mobile.
- **OG image própria** (`assets/og-cover.jpg`), gerada localmente com a
  paleta e o nome do escritório — para o link ter preview decente quando
  compartilhado no WhatsApp. Não é foto de projeto, é uma peça de
  identidade/capa.

## Restrições técnicas atendidas

- HTML/CSS puro, um arquivo (`index.html`), sem build.
- Responsivo de 360px a 1920px (grid muda em 760px/800px/860px/900px).
- Foco de teclado visível (`:focus-visible` com contorno terracota).
- `prefers-reduced-motion` respeitado.
- Open Graph completo com imagem própria 1200×630.
- Único uso de fonte externa: Google Fonts (Fraunces + Inter Tight), com
  `preconnect` e `font-display: swap`. Não foi possível embutir os arquivos de
  fonte localmente porque o ambiente de sandbox usado para montar este
  redesign não tem acesso de rede para baixar os `.woff2` — na hora de
  publicar de verdade, recomendo baixar e hospedar as duas fontes junto do
  site para tirar essa única dependência externa.
- Sem imagens `<img>` reais no momento (ver seção acima) — por isso os
  atributos `width`/`height`/`loading="lazy"`/`webp` ainda não se aplicam;
  assim que as fotos reais forem inseridas nos blocos `.hero-frame` e
  `.projeto-frame`, adicionar `<img loading="lazy" width="…" height="…"
  src="assets/projeto-01.webp">` no lugar do placeholder.

## Pendências para antes de publicar

1. Pedir para a Andressa os arquivos reais das fotos de projeto (Instagram,
   Google Meu Negócio ou pasta original) e substituir os três blocos
   `.projeto-frame` e o `.hero-frame` por `<img>` reais em `.webp`.
2. Confirmar se ela quer manter os dois números de telefone (o do site antigo
   e o da qualificação) ou só um.
3. Confirmar se existe registro no CAU/CAU-GO para incluir no rodapé (não
   encontrei esse dado em nenhuma fonte consultada).
