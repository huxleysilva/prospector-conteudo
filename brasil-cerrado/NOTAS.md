# NOTAS — Redesign Brasil Cerrado Arquitetura

## Situação de partida: um site que só existe para redirecionar

O site antigo, `https://sites.google.com/view/brasilcerradoarquitetura/início`,
é uma página institucional do Google Sites praticamente vazia: um wordmark e
**um único botão**, "Fale conosco aqui", que redireciona (via link de
rastreamento do Google) para `https://linktr.ee/brasilcerradoarquitetura`.
É lá — não no site — que ficam os contatos reais: dois links de WhatsApp
(um para "Elaboração de Projetos", outro para "Execução de Obras") e um PDF
de portfólio.

Na prática, o "site" é uma casca. Ele não tem página própria com serviços,
equipe, endereço ou prova social — tudo isso só existe espalhado entre o
Google Sites, o Linktree e o perfil do Google Maps. O redesign resolve
justamente isso: **traz para dentro do site tudo que hoje só existe em
outro lugar**, e elimina o Linktree como etapa obrigatória do contato.

## O que existe de fato (levantamento)

- **Nome e dupla de arquitetos**: Brasil Cerrado Arquitetura — Arqt. Pedro
  Bandona e Arqt. Iury Alves. (O Linktree grafa "Pedro Badona"; o material
  de proposta incorporado no próprio Google Sites grafa "Pedro Bandona" duas
  vezes. Usei "Bandona", por aparecer com mais consistência na peça oficial;
  vale confirmar com o cliente qual é o certo antes de publicar.)
- **Telefones/WhatsApp reais** (confirmados no Linktree e no Google Maps):
  - Elaboração de Projetos: `(61) 99644-1992` — é também o número cadastrado
    no perfil do Google Maps do escritório.
  - Execução de Obras: `(61) 99342-8340`.
- **Endereço real** (Google Maps, confirmado pela própria empresa há 6
  semanas): R. Cel. Batista, 290 — Sala 03, St. Central, Anápolis-GO,
  75020-080.
- **Nota e avaliações reais** (Google Maps): 5,0 com 12 avaliações. Usei os
  três comentários mais recentes e públicos, na íntegra, sem editar:
  Adriene Bezerra, Ana Badona Nutri e Lucas Guilherme Badona de Carvalho.
  Não inventei nenhum depoimento além desses três.
- **Textos institucionais com voz própria**, extraídos de uma peça de
  proposta comercial ("PROPOSTA-26.206") que está incorporada como imagem
  dentro do próprio Google Sites (e é a mesma imagem usada como foto de
  perfil do Linktree): "Arquitetura pensada para valorizar histórias, criar
  conexões e transformar espaços.", "Profissionais que transformam visão em
  realidade", os parágrafos sobre método de trabalho, e a lista de serviços
  dividida em dois blocos — Projetos (Projetos Arquitetônicos, Projeto
  Paisagístico, Projeto de Interiores, Projeto Reforma) e Obras (Construção
  Civil, Reformas, Acompanhamento de Obras). Todo esse texto foi preservado
  quase literalmente no novo site.
- **Portfólio em PDF**: existe e está linkado no Linktree
  (Google Drive, "PORTIFOLIO BRASIL CERRADO.pdf") — apontei o botão
  "Ver portfólio completo" do novo site para esse mesmo arquivo.
- **Paleta de marca**: oliva escuro, areia/travertino claro e terracota —
  usada de forma consistente em toda a peça de proposta (banda de abertura
  em oliva com texto script, ícones em traço fino terracota/oliva, fundo
  areia). Não é uma paleta genérica escolhida por mim: é a paleta que a
  própria Brasil Cerrado já usa. Preservei essas três famílias de cor no
  novo site (`--olive`, `--sand`, `--terracotta` em `index.html`).
- **Elemento gráfico de assinatura**: a peça de proposta usa, nos cantos,
  um traço fino orgânico (tipo contorno/linha de vegetação) como decoração
  recorrente. Reaproveitei exatamente esse traço como o elemento assinatura
  do hero do novo site (SVG leve, uma vez só, sem repetir em outras seções).

## Sobre as fotos de projeto (leia isto antes de perguntar "cadê a foto")

A regra número um deste processo é **nunca inventar foto de projeto do
cliente**. Isso teve consequência prática aqui:

1. Dentro da peça de proposta incorporada no Google Sites existem três
   imagens (renderizações de uma casa/piscina ao entardecer e uma foto dos
   dois arquitetos em pé diante de uma parede). Encontrei, visualizei e
   localizei precisamente essas imagens (inclusive as URLs de origem,
   `lh3.googleusercontent.com/sitesv/...`).
2. **Não há como confirmar que a casa/piscina renderizada é um projeto
   executado pela Brasil Cerrado.** O visual (render 3D, não fotografia) e o
   nome do arquivo de origem ("PROPOSTA-26.206") indicam que é material de
   um **modelo de proposta comercial genérico**, não necessariamente uma
   obra real do escritório — usar essa imagem como "projeto entregue" seria
   arriscar apresentar como deles algo que pode não ser. Por isso, mesmo se
   a extração técnica fosse possível, eu teria evitado usá-la como "projeto".
3. **O ambiente técnico usado neste redesign bloqueia deliberadamente a
   extração de arquivos binários/imagens de páginas de terceiros** (proteção
   contra exfiltração de dados: tentativas de baixar o JPEG via `fetch` +
   base64, ou de fazer o navegador salvar o arquivo em disco, foram
   bloqueadas ou não persistiram). Ou seja, mesmo a foto legítima dos dois
   arquitetos — que essa sim parece ser real — não pôde ser salva como
   arquivo `.webp` dentro de `assets/`. Esse é o mesmo limite documentado no
   redesign de outro lead nesta mesma sessão (Andressa Castro Arquitetura).

Diante disso, a escolha foi: **nenhuma foto no site novo.** Nem a
renderização de origem duvidosa, nem foto de banco de imagens genérica
fingindo ser projeto da Brasil Cerrado. Em vez disso, `index.html` usa
tratamento tipográfico e cromático forte — tipografia grande em serifada
com itálico, blocos de cor sólida na paleta real da marca, e o traço
orgânico de assinatura — exatamente nos lugares onde uma foto de projeto
entraria assim que o escritório fornecer os arquivos reais. Os dois
arquitetos aparecem como iniciais em círculo (mesmo recurso visual que a
própria peça de proposta já usa quando não tem foto: um ícone circular no
lugar do retrato), não como avatar genérico.

## O que foi mantido (é da Brasil Cerrado, não inventei)

- Nome do escritório, nomes e função dos dois arquitetos.
- Frase de abertura ("Arquitetura pensada para valorizar histórias...") e
  a frase da seção de equipe ("Profissionais que transformam visão em
  realidade..."), preservadas quase literalmente.
- Os dois parágrafos sobre método de trabalho ("Mais do que projetar
  espaços..." e "Da concepção do projeto ao acompanhamento da execução...").
- As duas listas de serviços (Projetos / Obras), com os itens exatamente
  como aparecem no material original — nenhum item foi adicionado ou
  removido.
- Os dois números de WhatsApp, agora rotulados (projeto vs. obra) em vez de
  aparecerem como dois botões idênticos e sem contexto no Linktree.
- Endereço, nota e avaliações — 100% vindos do Google Maps, sem edição de
  texto nas avaliações.
- Paleta de cor e o traço decorativo de assinatura.

## O que mudou (e por quê)

- **De "botão único para Linktree" para site institucional completo.** O
  visitante não precisa mais sair do site, cair num agregador de links de
  terceiros e escolher entre dois WhatsApp sem saber qual é qual. Os dois
  contatos, o endereço, o portfólio e as avaliações estão todos na própria
  página.
- **Prova social que não existia em canal próprio nenhum.** A nota 5,0/12
  avaliações e os depoimentos não apareciam nem no Google Sites nem no
  Linktree — só quem já ia direto ao Google Maps via. Agora está na seção
  "Prova".
- **Tipografia com opinião**: Instrument Serif (display, com itálico nativo
  que ecoa o traço script "sua história" já usado por eles) + Geist (corpo),
  no lugar do texto embutido dentro de uma imagem estática (o texto do site
  antigo não era nem selecionável, nem indexável pelo Google — estava
  "pintado" dentro de um JPEG).
- **Zero gradiente decorativo, zero sombra difusa, zero foto de banco.** O
  único elemento gráfico fixo é o traço orgânico de assinatura, usado uma
  única vez no hero.
- **Uma única animação**: revelação suave das seções ao rolar a página,
  respeitando `prefers-reduced-motion`.
- **Botão de WhatsApp flutuante e discreto**, sempre alcançável em mobile,
  apontando para o WhatsApp de projetos (o de maior intenção de contato).
- **OG image própria** (`assets/og-cover.jpg`, 1200×630), gerada localmente
  com a paleta e o nome do escritório, para o link ter preview decente
  quando compartilhado no WhatsApp — não é foto de projeto, é peça de
  identidade/capa, gerada por script local (Pillow), não baixada de
  terceiros.

## Restrições técnicas atendidas

- HTML/CSS puro, um arquivo (`index.html`), sem build, sem framework.
- Responsivo de 360px a 1920px (grid dos serviços empilha até 760px; grid de
  equipe/contato empilha até 820px).
- Foco de teclado visível (`:focus-visible` com contorno terracota em toda a
  página).
- `prefers-reduced-motion` respeitado (revelação de seção e scroll suave
  são desativados).
- Open Graph completo, com imagem própria 1200×630 em `assets/og-cover.jpg`.
- Sem imagens `<img>` de projeto (ver seção acima) — por isso os atributos
  `width`/`height`/`loading="lazy"`/`webp` para foto ainda não se aplicam.
  Assim que o escritório fornecer fotos reais de obra (ou autorizar puxar do
  Instagram/Google Meu Negócio), o lugar natural é: uma imagem de capa no
  `.hero` e 3–6 blocos de projeto entre "Serviços" e "Sobre" — inserir como
  `<img loading="lazy" width="…" height="…" src="assets/projeto-01.webp">`.
- Único uso de fonte externa: Google Fonts (Instrument Serif + Geist), com
  `preconnect` e `font-display: swap`. Não foi possível embutir os arquivos
  de fonte localmente porque o ambiente de sandbox usado para montar este
  redesign não tem acesso de rede geral para baixar `.woff2` — na hora de
  publicar de verdade, recomendo baixar e hospedar as duas fontes junto do
  site para remover essa única dependência externa.

## Pendências para antes de publicar

1. Confirmar a grafia correta do sobrenome "Bandona" vs. "Badona" com o
   escritório (o Linktree usa uma, o material de proposta usa a outra).
2. Pedir fotos reais de projetos executados (não renders de proposta
   genérica) para preencher a seção de projetos — hoje inexistente porque
   não há conteúdo real disponível publicamente.
3. Confirmar se o escritório quer manter o link do Linktree como canal
   secundário (redes sociais) ou aposentá-lo agora que o site tem os
   contatos diretos.
4. Confirmar registro no CAU/CAU-GO para incluir no rodapé (não encontrado
   em nenhuma fonte consultada).
5. Confirmar handle correto do Instagram — o Linktree referencia uma conta
   do Instagram, mas não consegui confirmar a URL exata dentro do escopo
   desta sessão; por isso não incluí link de Instagram no site novo para
   evitar apontar para um perfil errado.
