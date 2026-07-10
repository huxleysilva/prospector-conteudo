# Notas do redesign — Flávia Goulart Arquitetura & Interiores

## Contexto importante: o domínio original caiu

`https://www.flaviagoulart.com.br/` está fora do ar — falha de DNS, não um
problema temporário de servidor. Todo o conteúdo abaixo foi extraído do
snapshot do Wayback Machine de **20/04/2025**:
`http://web.archive.org/web/20250420061321/https://www.flaviagoulart.com.br/`

O `comparar.html` usa esse mesmo snapshot no iframe "Antes", com um aviso
visível explicando a situação — não estou fingindo que o site antigo ainda
está no ar.

O rastreamento do Wayback para este domínio é raso: só a home ficou indexada
de forma navegável. Subpáginas como `/portfolio-fotos/`,
`/lista-obras-recentes/`, `/servicos/` e `/contato/` retornam "not archived".
Isso significa que **não existe, em nenhum lugar acessível, uma lista de
projetos com nome/metragem/ano** — essa informação nunca chegou a ser
arquivada. Não inventei nada para preencher essa lacuna; veja "O que mudou"
abaixo para como isso foi contornado.

## O que existia no site antigo (o que funciona)

- Logo em script elegante, com floreio ornamental — "Flávia Goulart /
  Arquitetura & Interiores", em branco sobre fundo escuro.
- Texto institucional real e específico: 21 anos de experiência, mais de 90
  obras residenciais em Brasília, formação em Arquitetura e Urbanismo,
  registro CAU A34792-2.
- Nomes e cargos reais da equipe: Gardênia Rocha (assistente técnica) e
  Arthur César (assistente técnico), com fotos.
- Retrato real da própria Flávia.
- 12 depoimentos reais de clientes, com nome e bairro/tipo de obra — cobrindo
  Setor Taquari, Sudoeste, Asa Sul, Jardins Mangueiral, entre outros. Textos
  com voz própria (ex.: o caso da piscina construída na cobertura de um
  prédio, relatado por Danielle Carrara).
- Paleta escura elegante (fundo quase-preto quente + branco), coerente com o
  tom "acolhedor e detalhista" que os próprios depoimentos descrevem.

O que **não** sobreviveu: o carrossel de fotos de projeto na home (Revolution
Slider, carregado via JavaScript) não foi capturado pelo Wayback — as URLs
das imagens existem no HTML mas retornam "not archived" quando acessadas
diretamente. Nenhuma foto de projeto/portfólio pôde ser recuperada. Detalhes
técnicos de onde vieram as 4 imagens que sobraram (logo, retrato, 2 fotos de
equipe) estão em `assets/FONTES-DAS-IMAGENS.md`.

## O que foi mantido

- Logo original (mesmo arquivo, via Wayback).
- Retrato real de Flávia e fotos reais de Gardênia e Arthur.
- Todos os nomes, cargos, número de CAU, anos de experiência e contagem de
  obras — exatamente como declarados pelo próprio site.
- Os 12 depoimentos originais (6 exibidos por espaço, na íntegra ou com corte
  de trecho repetitivo, sempre preservando autor e localização reais).
- O tom "acolhedor, detalhista, pontual" que aparece repetido nos
  depoimentos dos próprios clientes — isso guiou a direção de arte (ver
  plano de tokens abaixo), em vez de um "arquitetura minimalista" genérico.
- WhatsApp (61) 98126-7910, fornecido para este lead, usado como canal
  principal de contato — coerente com como os depoimentos descrevem o
  atendimento pessoal da Flávia.

## Plano de tokens (direção de arte)

Testei o plano perguntando "isso serviria para um nutricionista?" — a
resposta é não, e o motivo está amarrado a ativos reais da cliente:

- **Cores**
  - `#1C1A17` grafite-noturno — eco do fundo escuro do logo original.
  - `#F5EFE6` marfim — fundo principal, mais quente que branco puro.
  - `#B08968` terracota-areia — cor de destaque, puxada da luz quente da
    foto de retrato real da Flávia (ambiente de restaurante, luz âmbar).
  - `#C9A227` dourado-linha — usado só como hairline de 2px que abre cada
    seção; eco discreto do floreio ornamental do logo, sem repetir o
    floreio de forma literal (ficaria piegas em tela).
  - `#6B6B4F` verde-oliva — uso pontual em rótulos/CAU, nod às plantas
    visíveis no fundo da foto de retrato real.
  - `#2B2824` carvão-texto — corpo de texto, mais quente que preto puro.
- **Tipografia**: Fraunces (serif com curvas old-style, itálico nos títulos)
  para títulos — ponte para a elegância do logo em script sem usar uma
  script font (ilegível em mobile); Inter Tight para corpo/UI.
- **Conceito de layout em uma frase**: "Um dossiê de confiança — retrato,
  trajetória e vozes reais de quem já reformou com ela, respirando em blocos
  largos separados por linhas finas douradas, sem carrossel, sem ícone
  genérico."
- **Elemento assinatura**: a linha dourada de 64px que abre cada seção.

Esse plano não se sustentaria para nenhum outro nicho: a paleta terracota +
grafite quente + hairline dourado está amarrada à luz da foto real da
cliente e ao floreio do logo dela, não é uma paleta neutra de template.

## O que mudou (e por quê)

- **Estrutura**: de site institucional em 5 páginas esparsas (Página
  Inicial, Perfil, Portfólio, Serviços, Contato) para uma página única e
  longa. O escritório é pequeno — não há conteúdo real para sustentar 5
  páginas, e isso era parte do problema do site antigo (páginas vazias,
  navegação sem necessidade).
- **Seção "Projetos" virou seção "Depoimentos" reforçada**: o padrão-visual
  pede uma seção de 3–6 projetos com foto grande e ficha técnica. Essa
  informação (nome do projeto, metragem, ano) nunca foi arquivada em lugar
  nenhum acessível, e as fotos de projeto se perderam no Wayback. Em vez de
  inventar metragens ou usar fotos de banco de imagens — o que violaria a
  regra zero desta skill — o redesign apoia a prova social no que É real e
  abundante: 12 depoimentos verificáveis, com nome e bairro reais. É uma
  adaptação honesta a uma limitação de dados, não uma escolha estética.
- **Hero sem foto de projeto em tela cheia**: pela mesma razão acima — não
  há foto de projeto recuperável em resolução utilizável. O hero foi
  desenhado tipograficamente (fundo grafite + título grande em Fraunces
  itálico + estatísticas reais), em vez de forçar uma imagem de baixa
  resolução ou genérica em tela cheia.
- **Tipografia**: trocada de fontes de sistema/tema WordPress padrão para
  Fraunces + Inter Tight, com escala declarada.
- **Contato**: adicionado formulário nativo simples que monta a mensagem e
  abre o WhatsApp já preenchido (sem backend, sem e-mail inventado — o site
  antigo não tinha e-mail de contato arquivado).
- **Performance/acessibilidade**: HTML/CSS em arquivo único, imagens com
  `loading="lazy"` (exceto o logo, carregado eager por estar acima da
  dobra) e `width`/`height` declarados, skip-link, foco de teclado visível
  (`outline` customizado), `prefers-reduced-motion` respeitado na única
  animação (reveal on scroll), botão de WhatsApp fixo e acessível em mobile,
  Open Graph com imagem real para preview no WhatsApp.

## Pendência técnica conhecida

As 4 imagens usadas (logo, retrato, 2 fotos de equipe) estão referenciadas
por hotlink a URLs verificadas e ainda ativas (Wayback Machine e cache
Jetpack Photon do WordPress.com) — não foram baixadas e convertidas para
`.webp` localmente, porque o ambiente desta sessão não tinha uma rota de
rede disponível para trazer os bytes da imagem do navegador até a pasta de
saída. Isso está detalhado, com as URLs exatas, em
`assets/FONTES-DAS-IMAGENS.md`. Antes da publicação final, baixar essas 4
imagens, converter para `.webp` e apontar os `src` para arquivos locais —
única pendência para 100% de aderência ao padrão técnico (zero dependência
externa de imagem).
