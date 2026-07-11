# NOTAS — Studio Noas Arquitetura (Caldas Novas, GO)

## Plano de tokens usado

- **Cores** (extraídas da própria marca, não inventadas): o logo do cliente
  se chama `NOAS_MARCA-01_VERDE` e o ícone de favicon do site antigo se
  chama `NOAS_SIMBOLO-01_TERRACOTA` — ou seja, verde e terracota já eram a
  identidade do escritório, só nunca tinham virado uma paleta de fato.
  - `--verde: #3C4A34` (cor primária, títulos de destaque, botões)
  - `--verde-escuro: #20261C` (fundo do rodapé, da faixa do hero e da seção de depoimentos)
  - `--terracota: #B5623B` (acento único — números dos projetos, aspas, eyebrow)
  - `--areia: #F4F1EA` (fundo geral, evoca o clima de Caldas Novas)
  - `--pedra: #DAD3C3` (linhas divisórias, grade de serviços)
  - `--tinta: #20221D` (texto)
- **Tipografia:** Fraunces (serifada, com opinião) para títulos e números de
  projeto; Inter Tight para corpo de texto. Nada de Poppins/Montserrat/Roboto.
- **Conceito de layout em uma frase:** uma página só, longa como um passeio
  pela propriedade — cada projeto ocupa a largura toda, com um numeral
  serifado ao lado (01, 02, 03...) como se fosse anotação de prancha, e a
  foto nunca divide espaço com decoração.
- **Elemento assinatura:** o numeral serifado em terracota ao lado de cada
  projeto e de cada serviço — funciona como remissão a desenho técnico
  (planta numerada), o que não faria sentido nenhum no site de um
  nutricionista ou de qualquer outro nicho — é uma escolha para arquitetura.

## O que foi mantido (do cliente, sem alteração de conteúdo)

- Logo real do escritório (`NOAS_MARCA-01_VERDE-horizontal.png`).
- Todas as fotos de projeto são reais, do portfólio do próprio cliente —
  nenhuma foto foi inventada, gerada ou trocada por banco de imagens.
- Nomes dos projetos exatamente como o cliente nomeia: Aldeia das Thermas,
  Casa L2, Residência A+R, Arena Beach Tennis, Pet Center — com a
  cidade/categoria real de cada um. **Não inventei metragem nem ano**: o
  site original também não informa esses dados projeto a projeto, então não
  fabriquei números que o cliente não forneceu.
- Texto institucional "Como nasceu o Studio Noas" é o texto real do cliente,
  apenas condensado (o original tem ~4 parágrafos longos repetidos em duas
  páginas; aqui está em 2 parágrafos, mesmos fatos: Carlos — UEG 2015,
  intercâmbio em Torino 2012, estágio em Anápolis; Andrea — designer de
  interiores desde 2018; a origem do nome NOAS como monograma do casal).
- As 3 descrições de serviço (Arquitetura / Interiores / Obras) vêm do
  conteúdo real de cada página de serviço do site antigo, resumidas para
  uma frase cada.
- Depoimentos são de clientes reais do Google (Alex Sandro Alves da Silva,
  Marcos Soares, Rosely Nogueira de Souza Oliveira), parafraseados e
  encurtados, com atribuição — não são inventados.
- Endereço, e-mail (`contato@studionoas.com.br`) e redes sociais
  (Instagram/Facebook) reais, copiados do rodapé do site atual.

## O que mudou e por quê

- **WhatsApp do botão de orçamento corrigido.** O botão "FAZER ORÇAMENTO" do
  site antigo aponta para `http://wa.me/556499866600` — esse número tem um
  dígito faltando (falta um "9" do nono dígito móvel: `556499866600` tem 12
  dígitos, o correto para celular BR com DDI é `5564999866600`, 13 dígitos).
  Abrir esse link no WhatsApp resulta em número inválido / conversa que não
  abre. Troquei em **todos** os pontos de contato do site novo (header,
  hero, seção de contato, rodapé e botão flutuante) para o número correto
  informado pelo cliente: `5564999866600` → `https://wa.me/5564999866600`.
- **Telefone do rodapé corrigido.** O rodapé do site antigo mostra
  `(64) 99341-2358`, diferente do número principal `(64) 99986-6600` usado
  no resto do site (inclusive em outro link de WhatsApp na página
  `/arquitetura`, que usa um terceiro número, `5564993412358`). Ou seja, o
  site antigo tinha **três variações de telefone** coexistindo. O site novo
  usa um único número, em todo lugar: `(64) 99986-6600`.
- **Contador "pessoas envolvidas" removido.** Na home antiga, a seção
  "PREPARADOS PARA TE ATENDER" tem três contadores animados (pessoas
  envolvidas / projetos realizados / clientes satisfeitos) que deveriam
  contar até um número e ficaram travados em 0 — sinal de plugin quebrado
  sem manutenção. Em vez de inventar um número para "consertar" a seção,
  cortei o bloco inteiro. Prova social real ficou por conta da nota do
  Google (5,0 de 5, 22 avaliações) e dos depoimentos.
- **Página de teste removida.** O menu principal do site antigo tinha um
  item "onepage1", que leva a um embed do Canva — claramente uma página de
  teste que ficou publicada e linkada por engano. Ela não existe no site
  novo, nem no menu (que também deixou de existir — ver item de estrutura).
- **Estrutura reduzida de 5 páginas para 1.** O site antigo distribui pouco
  conteúdo real em Início / Sobre Nós / Arquitetura / Interiores / Obras —
  cada página feita no Elementor, pesada, repetindo o mesmo formulário e
  rodapé cinco vezes. Consolidei tudo em uma página só (hero → projetos →
  sobre → serviços → depoimentos → contato), como pede o padrão de redesign
  para escritórios pequenos: menos navegação, mais respiro por seção.
- **Tipografia e hierarquia novas.** Troquei a tipografia padrão do tema
  Elementor por Fraunces (títulos) + Inter Tight (corpo), com escala
  declarada e numerais de projeto como elemento de assinatura.
- **Performance e acessibilidade.** HTML/CSS puro em arquivo único (sem
  Elementor, sem jQuery, sem bibliotecas de ícone), `loading="lazy"` em
  todas as imagens abaixo da dobra, `width`/`height` declarados para evitar
  layout shift, foco de teclado visível (`:focus-visible`), uma única
  animação de revelação no scroll respeitando `prefers-reduced-motion`,
  Open Graph completo com imagem real de projeto, responsivo de 360px a
  1920px, botão de WhatsApp fixo e alcançável no mobile.

## Limitação técnica desta entrega (leia antes de publicar)

O ambiente usado para gerar este redesign roda em uma sandbox isolada, sem
acesso de rede geral — o download binário direto de `studionoas.com.br` (e
de qualquer outro domínio de terceiros) fica bloqueado por política de rede,
e a via alternativa teria exigido extrair as imagens como texto em base64 de
dentro do navegador, o que também é bloqueado por controle de segurança do
próprio ambiente (para evitar exfiltração de dados via texto). Ou seja: não
foi possível copiar os arquivos de imagem para dentro de `assets/` como
`.webp` local nesta rodada.

Para não travar a entrega nem inventar fotos, o `index.html` referencia as
imagens **diretamente da hospedagem atual do cliente** (URLs absolutas para
`studionoas.com.br/wp-content/uploads/...`) — são as fotos reais, exatamente
como estão publicadas hoje, sem nenhuma foto trocada ou gerada. A lista
completa de URLs de origem, com o nome de arquivo e a largura sugeridos para
quando alguém (com acesso normal à internet) baixar e converter para
`.webp`, está em `assets/imagens-fonte.md`. Depois disso, basta trocar os
`src` absolutos por relativos (`assets/nome-do-arquivo.webp`) — a marcação
(`width`/`height`/`loading`) já está pronta para isso.

O único asset gerado do zero é `assets/favicon-noas.svg`, um ícone de aba
vetorial simples (monograma "N"); não é uma foto e não substitui o logotipo
real do cliente, que é referenciado como está.

## Arquivos entregues

- `index.html` — site novo, uma página, HTML/CSS puro.
- `comparar.html` — antigo (iframe para `http://www.studionoas.com.br/`) e
  novo lado a lado, empilha em telas estreitas.
- `assets/favicon-noas.svg` — ícone de aba gerado.
- `assets/imagens-fonte.md` — mapa de URLs reais de origem para rehospedagem
  local em `.webp` na etapa de publicação.
- `NOTAS.md` — este arquivo.
