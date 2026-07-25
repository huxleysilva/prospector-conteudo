# ION — Instituto Odontológico Neves · notas do redesign

Novo Gama-GO · Shopping Outlet Brasil, 2º piso, loja P15
Site atual: https://institutoodontologiconeves.meudoutor.com/

---

## O que o site atual já faz bem (e foi preservado)

- A lista de tratamentos é completa e correta. Todos os sete nomes foram mantidos
  literalmente: Ortodontia, Estética dental, Harmonização facial, Implantodontia,
  Prótese, Endodontia, Cirurgia. Inclusive as quatro modalidades de aparelho
  ("auto ligáveis, fixos, estéticos e alinhadores").
- A sigla **ION** já existia — aparece no `<title>` da plataforma. Ela virou o
  eixo da identidade em vez de ser descartada.
- Endereço completo e WhatsApp corretos. Foram mantidos ao caractere.
- Instagram @ion.odontologia mantido.

## O que mudou, e por quê

| Antes | Depois | Motivo |
|---|---|---|
| Título SSR genérico da plataforma | `ION — Instituto Odontológico Neves \| Shopping Outlet Brasil, Novo Gama-GO` | O nome e o endereço são o ativo. Precisam estar na aba e no Google. |
| Sem Open Graph | OG completo + imagem 1200×630 própria | **É o achado principal.** O link mandado no WhatsApp chegava sem nome, sem descrição e sem imagem. Agora chega como cartão. |
| Formulário-porteira (nome + telefone antes de liberar o WhatsApp) | Botão que abre a conversa direto, com mensagem já escrita | Cada campo antes do contato é gente desistindo. A página inteira diz isso em voz alta: "Sem formulário. Você clica e a conversa abre." |
| Banner de cookies de terceiro | Nenhum rastreador, nenhum banner | Não há o que consentir: a página não coleta nada. |
| Endereço escondido no rodapé | Endereço vira o argumento central da página | Estar dentro de um shopping é o diferencial real da clínica (estacionamento, segurança, horário, "cabe no mesmo passeio"). As avaliações citam "localização muito boa". |
| Equipe anônima | Dra. Jéssica Neves com nome, em bloco próprio | Ela é citada nominalmente em praticamente todas as avaliações. É o rosto da clínica; esconder isso era jogar fora a maior prova social que existe. |
| Copy institucional de template (idêntico ao de outras clínicas na mesma plataforma) | Copy reescrito na voz desta clínica | O texto antigo era o mesmo de qualquer cliente do "meudoutor". Todo texto novo saiu ou de fato verificável ou da linguagem das próprias avaliações. |

---

## Plano de tokens

**Cor — dominante quente, decidida (nenhum cinza puro na página)**

| Token | Hex | Papel |
|---|---|---|
| `--tinta` | `#2B1A28` | Aubergine-preto. Todo texto sobre claro. 15,1:1 sobre o papel. |
| `--ameixa` | `#5C2B50` | A cor da marca. Superfície escura e a placa de sinalização. Branco sobre ela: 11,1:1. |
| `--argila` | `#A8442A` | Terracota. **A ação**: CTA, links, marcadores. 5,5:1 sobre o papel. |
| `--argila-clara` | `#E8A98C` | Terracota clara, para acento *sobre* a ameixa. 5,4:1. |
| `--osso` | `#FAF5F0` | Papel quente. |
| `--bruma` | `#F0E6EC` | Malva pálido. Tinta de seção — substitui o "card branco". |
| `--fumo` | `#6B5462` | Taupe-ameixa. Texto secundário, 6,3:1. Neutro tingido com a matiz dominante. |

Sobre a superfície ameixa, o texto secundário é `#E0C8D9` — um tom da própria
matiz, nunca cinza — e compensa nos três eixos (entrelinha 1.78, tracking
+0.005em, peso mantido).

**Tipografia — duas famílias, papéis invertidos em relação ao clichê odontológico**

- **Bricolage Grotesque** (display, rótulos, botões, nomes de tratamento).
  Grotesca contemporânea com largura irregular; lê como letreiro de sinalização.
- **Spectral** (corpo, citações). Serifa desenhada para tela. Corpo serifado numa
  clínica é incomum e proposital: o argumento da página é "a gente explica", e
  serifa lê como explicação escrita por alguém, não como bula.

Escala: h1 `clamp(2.3rem, 6.1vw, 4.15rem)` / tracking −0.035em · h2 até 2.85rem
/ −0.03em · h3 1.35rem / −0.02em · corpo 1.0625rem / 1.72 · medida travada em
62ch (54ch nas linhas do diretório). Tracking nunca passa de −0.05em, e só na
sigla e no código da placa.

**Espaço — escala base 4**
`4 · 8 · 12 · 16 · 24 · 32 · 48 · 64 · 96 · 128`. Seções em
`clamp(72px, 8.5vw, 128px)`. Cada título de seção vem depois de um fio de 1px e
`32px` de respiro **acima**, contra `16px` abaixo — mais espaço acima do título
do que abaixo, sempre.

**Conceito de layout, em uma frase**
A página desce como um corredor de shopping: uma coluna alinhada à esquerda que
nunca centraliza, marcada por fios finos como as juntas do piso, com uma única
parada escura no meio.

**Elemento assinatura: o chanfro**
Um canto superior direito cortado a 45°, o formato de uma placa de sinalização
física. Aparece na placa "P15" do hero, nos espaços de foto, no bloco de
endereço, nos marcadores de lista e na tag do comparador. É forma, não
decoração: o mesmo corte em cinco escalas diferentes vira sistema.

---

## Tese espacial

- **Caminho de leitura primário:** sigla ION → a frase "Seu dentista fica no
  segundo piso do shopping" → botão do WhatsApp → placa P15 → e daí para baixo
  numa coluna única alinhada à esquerda.
- **O que fica junto, o que separa:** dentro de um grupo, 12–16px; entre linhas
  do diretório, 24px; entre grupos, 48px; entre seções, 72–128px. Os quatro fatos
  do shopping são um grupo apertado; a foto reservada ao lado é outro.
- **Quem lidera, quem apoia:** o bloco ameixa da Dra. Jéssica é a única massa
  escura da página e é o centro emocional — lidera. O diretório de tratamentos
  apoia: lê como textura de fios, denso de propósito.
- **Densidade e ritmo:** arejado no hero e no bloco escuro, denso no diretório.
  Um diretório *deve* ser denso; é o que faz ele parecer um quadro de lojas.
- **360px:** o hero vira coluna única e a placa sobe para o topo (`order:-1`),
  virando identificador compacto; o diretório colapsa de duas colunas para nome
  acima e explicação abaixo; o nome extenso some do cabeçalho e fica só "ION";
  os botões viram largura total.
- **1920px:** conteúdo travado em 1160px, mas o bloco ameixa sangra de borda a
  borda para a coluna não ficar encalhada no meio do branco.
- **Teste do squint:** desfocando, vê-se primeiro a mancha do h1, depois o
  retângulo ameixa, depois a textura listrada do diretório. Ordem correta.

---

## Como este redesign se distingue do da MEC Odontológica

As duas clínicas rodam na mesma plataforma e tinham o mesmo texto de template.
Nenhum elemento foi reaproveitado:

| | MEC (irmão) | ION (este) |
|---|---|---|
| Paleta | Aqua/teal + marfim (fria) | Ameixa + terracota + osso (quente) |
| Tipografia | Fraunces (serifa display) + Inter Tight (sans corpo) | Bricolage Grotesque (grotesca display) + Spectral (serifa corpo) — papéis invertidos |
| Elemento assinatura | Arco do sorriso | Chanfro de placa de sinalização |
| Serviços | Quatro frentes agrupadas e nomeadas | Diretório de sete linhas com fio, tradução ao lado, uma linha-guia maior |
| Tese | Percurso clínico (da triagem ao resultado) | Geografia (o dentista dentro do shopping) |
| Hero | Grade foto + texto, rótulo em caixa alta | Frase longa + placa de endereço, sem foto |
| Movimento | Reveal no scroll seção a seção | Nenhum reveal. Um único gesto no carregamento |
| Rótulos | Eyebrow em caixa alta em toda seção | Rótulo existe só dentro das placas e do rodapé |

---

## Movimento: um único momento autoral

Ao carregar, a placa do hero **corta o próprio canto** (`clip-path` animando de
retângulo para chanfro, 640ms, `cubic-bezier(.16,1,.3,1)`) enquanto o código
"P15" assenta o tracking de `.11em` para `-.05em`. É um gesto só, parte de um
estado já visível (o conteúdo nunca fica invisível esperando JS) e some inteiro
sob `prefers-reduced-motion: reduce`.

**Não há reveal no scroll.** Sem JavaScript de animação, sem `opacity:0` em
lugar nenhum. Se o JS falhar, nada acontece — porque não há JS.

---

## Status dos assets

| Asset | Situação |
|---|---|
| **Logotipo oficial** | ❌ **Não obtido.** A URL do S3 da plataforma (`simplesanuncios.s3.amazonaws.com/prd/388052/...`) não devolveu arquivo — é URL assinada com expiração. **Não foi hotlinkada** (quebraria em produção) e **nenhum logo foi inventado**. No lugar, um lockup tipográfico "ION · Instituto Odontológico Neves" em Bricolage Grotesque. **Pedir o arquivo original ao cliente** (de preferência SVG ou PNG com fundo transparente). |
| **Capa do tema "preto"** | ❌ Não obtida, mesma origem/mesmo motivo. Não foi usada. |
| **`assets/og-ion.jpg`** | ✅ Criado aqui. 1200×630, 43 KB, JPEG progressivo. Composição tipográfica com a ameixa da marca, a sigla ION e a placa P15. É o que aparece no preview do WhatsApp. |
| **Fotos da clínica** | ⚠️ **Três fotos reais em uso, vindas do perfil público da própria clínica no Google Maps** (fotos que o próprio negócio publicou lá). Nenhuma foto de banco de imagem. Estão **hotlinkadas** de `lh3.googleusercontent.com` — ver ressalva abaixo. |
| **Retrato da Dra. Jéssica Neves** | ❌ Não obtido. O espaço no bloco ameixa continua rotulado como reservado — é honesto e desenhado, não uma imagem quebrada. |

### Fotos reais integradas (atualização)

A página deixou de ser 100% tipográfica. Três fotos do **perfil público do Google
Maps do próprio Instituto Odontológico Neves** foram distribuídas assim:

| Onde | Papel |
|---|---|
| Faixa de abertura, logo abaixo do hero (`21/9`) | Dá rosto à clínica antes da primeira dobra terminar. `fetchpriority="high"`, sem `lazy`. |
| Seção "Onde ficamos" (`4/3`) | Ocupa o antigo espaço reservado da fachada, ao lado dos quatro fatos do shopping. `loading="lazy"`. |
| Seção de contato / "Como chegar" (`3/2`) | Acima do bloco de endereço, fechando o argumento geográfico. `loading="lazy"`. |

Tratamento visual: `object-fit:cover`, `width`/`height` declarados, **canto
reto** (nenhum `border-radius`), **nenhuma sombra difusa**. A foto é recortada
pelo mesmo chanfro da placa P15 — ela entra no sistema em vez de flutuar sobre
ele. O `aspect-ratio` está no CSS, então não há layout shift.

**Alt text deliberadamente prudente.** Não sei com precisão o que cada foto
mostra, então nenhum alt descreve pessoas, ambientes ou equipamentos
específicos: todos dizem apenas "Instituto Odontológico Neves, no Shopping
Outlet Brasil, Novo Gama-GO". Não afirmar o que não se confirma.

**Pendência obrigatória antes da publicação definitiva:** as três URLs são
hotlinks do CDN do Google (`lh3.googleusercontent.com`), estáveis mas fora do
nosso controle. **Baixar os três arquivos para `assets/`, converter para `webp`
(fallback `jpg`) e trocar os `src` por caminhos locais.** Enquanto forem
hotlink, cada visita vaza referrer para o Google e a página depende de um
domínio de terceiro.

O `og:image` **não foi alterado**: continua `assets/og-ion.jpg`, a imagem própria
gerada aqui, que é a certa para o preview do WhatsApp.

### O que pedir ao cliente antes de publicar

1. **Arquivo do logotipo (SVG ou PNG transparente) — ainda pendente.** A URL do
   S3 da plataforma retorna `AccessDenied`, então não há como recuperá-lo por
   fora. Precisa vir do cliente. Até lá, o lockup tipográfico "ION" segura.
2. **Fotos da Dra. Jéssica Neves e da equipe.** Retrato vertical dela para o
   bloco ameixa (hoje ainda é espaço reservado) e, se possível, uma foto da
   equipe. As avaliações citam a Dra. nominalmente; o rosto dela vale mais que
   qualquer foto de ambiente.
3. Fotos próprias em alta resolução da fachada da loja P15 e do interior, para
   substituir as do Google Maps por arquivos que a clínica controla.
4. Horário completo de atendimento (o Google só mostrou "fecha às 12h" no
   período consultado; a página diz isso literalmente em vez de inventar).
5. Lista dos convênios aceitos, se houver — hoje a página só diz "atendemos
   convênio", que é o que dá para afirmar com segurança.

Ao publicar em domínio próprio, trocar `og:image` para a **URL absoluta**
(`https://dominio/assets/og-ion.jpg`) — WhatsApp e Facebook não resolvem caminho
relativo.

---

## Checagens técnicas

- **Contraste:** todos os pares de texto verificados ≥ 4,5:1 (o menor é
  `--argila` sobre `--bruma`, 4,9:1). Nenhum texto usa o terracota escuro sobre
  a ameixa — esse par reprova, e por isso o terracota só aparece ali como barra
  decorativa.
- **Foco de teclado:** contorno terracota de 3px com offset 3px em tudo que é
  focável, na ordem visual. Link "pular para o conteúdo" no topo.
- **Responsivo:** 360 → 1920. Sem scroll horizontal (`overflow-x:hidden` no
  body como rede de segurança, mas não há estouro).
- **Peso:** um arquivo HTML, zero JavaScript, zero framework, uma imagem de
  43 KB carregada só como OG. A única dependência externa são as duas fontes do
  Google Fonts, com `preconnect` e `display=swap`. Se o cliente quiser
  dependência zero, os `.woff2` podem ser embutidos localmente na publicação.
- **Dados estruturados:** JSON-LD do tipo `Dentist`, com endereço, telefone e
  `aggregateRating` 4,9/35 — para o Google entender a ficha.
- **Nenhum rastreador, nenhum cookie, nenhum banner de consentimento.**

---

## Defaults de categoria recusados de propósito

- Grade de cards iguais com ícone + título + texto. Trocada por linhas de
  diretório com fio.
- Eyebrow em caixa alta acima de toda seção.
- Numeração 01/02/03. Os únicos números da página — P15, 2º piso, 4,9, 35 — são
  informação real.
- Texto em gradiente, glassmorphism, `border-left` colorida, sombra difusa.
- Herói-métrica (número gigante + label). A nota 4,9 aparece pequena, dentro da
  seção de avaliações, onde ela é verificável.
- Foto de banco de imagem com dentista sorrindo de jaleco.
- Avatar redondo recortado ao lado de depoimento.
