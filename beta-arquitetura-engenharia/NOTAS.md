# Beta Arquitetura e Engenharia — Notas do redesign

Lead: Beta - Arquitetura e Engenharia, Cristalina-GO. Nota 5,0 no Google Maps
(12 avaliações). Site antigo ao vivo em `https://www.betaarqeng.com/`
(Wix.com Website Builder).

## A descoberta principal: o site é um template clonado, não customizado

Abrindo o site ao vivo e todas as subpáginas (`/`, `/nossa-historia`,
`/projetos`, `/projeto-1` a `/projeto-5`, `/daniel-melo`, `/contato`), ficou
claro que o site nunca foi finalizado — é um template Wix de outro escritório
("RéguaArquitetos") com o conteúdo da Beta parcialmente colado por cima.
Evidências, com URL de origem:

1. **Rodapé assinado por outra empresa.** Todas as páginas terminam em
   `© 2023 por RéguaArquitetos. Orgulhosamente criado com Wix.com` — nunca
   trocado para "Beta Arquitetura e Engenharia". Isso está publicado, ao vivo,
   desde pelo menos 2023.
2. **Menu "Contato" quebrado.** O item de menu `CONTATO` do cabeçalho aponta
   para a própria home (`https://www.betaarqeng.com`), não para
   `/contato`. A URL `/contato` existe mas carrega em branco (sem título, sem
   conteúdo, confirmado via fetch direto).
3. **Texto placeholder ainda ativo.** Na home, dentro de "Projetos em
   Destaque", o card "Projeto Residencial JA-05" mostra o lorem ipsum padrão
   do Wix: *"Sou um parágrafo. Clique aqui para editar (...) Sinta-se à
   vontade para arrastar e soltar (...)"* — nunca foi escrito o texto real
   desse projeto. Por isso o projeto JA-05 **não entrou** no site novo: preferi
   cortar a seção a inventar uma descrição para ela. Se o cliente quiser, dá
   pra reincluir assim que ele mandar o texto real.
4. **Nome de sócio trocado por nome de outro escritório.** A página
   `/daniel-melo` tem `<title>DANIEL MELO | Beta Arquitetura E</title>` — ou
   seja, o slug e o título SEO da página do sócio ainda carregam o nome
   "Daniel Melo", que não é ninguém da Beta. O conteúdo visível da página,
   porém, já mostra a foto e o texto certos: "Guilherme Oliveira Lima, Sócio,
   27 anos, formado há 4 anos em Engenharia Civil, pós-graduado em estruturas
   e fundações". Ou seja, o card de equipe funciona visualmente, mas a URL e o
   metadado (o que aparece na aba do navegador, no Google e ao compartilhar o
   link) ainda dizem "Daniel Melo" — outro nome do template original nunca
   apagado. O mesmo vale para o sócio Ed Wilson: a URL dele é
   `/stela-melo` ("Stela Melo" também não é ninguém da Beta).
   Isso é sinal forte de que o site foi clonado de outro projeto Wix
   ("RéguaArquitetos", com sócios "Daniel Melo" e "Stela Melo") e a Beta nunca
   recebeu um site pensado para ela.

Esses quatro pontos (rodapé de outra empresa, menu quebrado, lorem ipsum
publicado, e nomes de outro escritório vazando nas URLs/títulos) são
argumento concreto e verificável para a proposta: não é "o site está feio",
é "o site não é da Beta".

## O que funciona de verdade no site antigo (preservado)

- **Nome, atuação e sócios reais**, confirmados na página `/nossa-historia`:
  Ed Wilson Verussa Junior (arquiteto e urbanista) e Guilherme Oliveira Lima
  (engenheiro civil), fundadores. Texto institucional real: *"A Beta
  Arquitetura e Engenharia foi criada pelos sócios Ed Wilson, o arquiteto, e
  Guilherme Lima, o engenheiro."* — mantido quase literal no site novo.
- **Quatro projetos com texto próprio, real e específico** (não genérico):
  - JA-04 — edifício multifamiliar em Cristalina, 3 apartamentos + comercial,
    sacadas grandes, terraço com vista 360°.
  - JA-30 — residência de alto padrão em lote de 250m², fachada minimalista,
    madeira e tijolinho aparente.
  - JA-21 (Projeto de Interiores) — área de lazer de pouco mais de 60m²,
    espaço de reunião/churrasco, banheiros, lavatório externo, depósito.
  - PC-06 — chopperia em Caldas Novas, lote de esquina, cobertura "flutuante"
    em madeira e metal, revestimento tipo tijolo rústico, 4 jardins verticais.
  Todos os quatro foram mantidos com o texto original (levemente cortado por
  tamanho, nunca reescrito na essência).
- **Fotos/renders reais dos projetos e dos dois sócios** (Ed Wilson e
  Guilherme), usadas no site novo.
- **Endereço, telefone e redes reais**: Avenida Antonino Camilo de Andrade,
  Quadra A, Lote 17B, Sala 1 — Sul I, Cristalina-GO, 73850-000; telefone/
  WhatsApp (61) 99620-2960; Instagram `@betta_arqeng`; Facebook
  `/betaarqeng`.
- **Logotipo real** (`logo-branca-1.png`), usado no cabeçalho do site novo.

## O que mudou e por quê

- **Corrigido**: rodapé agora diz "© 2026 Beta Arquitetura e Engenharia",
  não mais "RéguaArquitetos". Menu de navegação tem só as âncoras que
  existem de verdade (Projetos, Sobre, Contato) — nada de item de menu
  morto.
- **Cortado**: projeto JA-05 (só tinha lorem ipsum), a página "Nossa
  História" separada e as páginas de sócio separadas — viraram uma seção
  "Sobre" única na home, porque não havia conteúdo real suficiente para
  sustentar 4 páginas (o site antigo tentou ter várias páginas e ficou vazio
  na maioria delas: `/contato` em branco, páginas de sócio com slug errado).
  Página única, mais longa, é mais honesta com a quantidade de conteúdo real
  que a Beta tem hoje.
- **Estrutura**: hero com foto de projeto em tela cheia (sem texto por cima —
  o texto vem logo abaixo, em bloco sólido, para a foto não perder força),
  projetos um a um com "ficha técnica" curta ao lado, prova social com a nota
  5,0/12 avaliações do Google (dado real, verificado no Maps), contato com
  WhatsApp como canal principal — é como esse tipo de cliente fecha negócio.
- **Tipografia**: trocada a fonte padrão de tema Wix por Fraunces (títulos,
  peso editorial/arquitetônico) + Geist (corpo, técnico e legível).
- **Paleta nova**, construída a partir do vocabulário de material que aparece
  nos textos reais dos projetos (tijolinho aparente, madeira, jardim
  vertical) — não é a paleta arbitrária do template Wix (fundo escuro
  genérico com logo branco por cima de qualquer imagem):
  - `--grafite #1c1a17` — estrutura, texto, fundo escuro do header/footer
  - `--areia #f5f1ea` — fundo claro, papel
  - `--tijolo #a8563c` — acento principal, vem direto de "tijolinho exposto" /
    "revestimento que imita tijolo rústico" nos textos dos projetos
  - `--musgo #4b5c44` — verde, vem de "pegada mais garden, mais verde" /
    "jardins verticais" (projeto PC-06); usado no CTA de WhatsApp
  - `--bronze #8a7657` — tom de madeira, de "revestimentos tradicionais a
    madeira" (projeto JA-30)
  - `--branco #ffffff` — contraste em cards
- **Elemento de assinatura**: cada projeto é rotulado como "Prancha JA-04",
  "Prancha PC-06" etc. — uma referência tipográfica a prancha técnica de
  projeto, reforçando que o escritório é tanto arquitetura quanto engenharia
  (cálculo + desenho), não um portfólio genérico de fotos bonitas.
- **Sem invenção**: não foram criados depoimentos de clientes (o site antigo
  não tinha nenhum, e nenhum foi encontrado nas páginas capturadas) — a prova
  social usa só o dado real e verificável (5,0 no Google, 12 avaliações). Não
  foi inventado e-mail de contato (o site antigo não expõe um endereço de
  e-mail confiável); o contato principal é WhatsApp, telefone, endereço e
  redes sociais, todos reais.

## Pendência técnica antes de publicar de verdade

O ambiente desta sessão não tem saída de rede liberada para baixar e
reconverter arquivos binários (o proxy da sandbox bloqueia `curl`/`wget` para
qualquer domínio externo, incluindo `static.wixstatic.com`; a ferramenta de
fetch de página só traz HTML/texto, não bytes de imagem). Por isso, todas as
imagens em `index.html` estão referenciadas diretamente do CDN da Wix
(hotlink), já com parâmetros de redimensionamento (`w_`, `h_`, `q_85`,
`enc_avif`) para carregar leves — mas ainda dependem do domínio
`static.wixstatic.com` estar no ar.

Antes da publicação definitiva (skill `publicar` / `deploy-servidor`):
baixar as ~13 imagens referenciadas (logo, 2 fotos de sócio, 4 fotos de
projeto, 1 foto de contato), converter para `.webp` local em `assets/`, e
trocar os `src` em `index.html` e o `og:image` para os arquivos locais. A
pasta `assets/` desta entrega está vazia por esse motivo — este arquivo
documenta a pendência em vez de simular uma otimização que não pôde ser
feita de fato.

Nenhuma foto foi inventada ou trocada por banco de imagens genérico: todas as
imagens referenciadas são fotos/renders reais dos projetos e sócios da Beta,
extraídas do próprio site antigo.
