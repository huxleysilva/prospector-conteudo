# NOTAS — Redesign Vogar Arquitetura

## O que o site antigo tinha de errado (achados no site ao vivo)

1. **Banner "Casa Milano" com texto de template não editado.** Na home,
   o card da Casa Milano mostra literalmente "Give customers details
   about the banner image(s) or content on the template." — o texto
   padrão do tema Shopify (Dawn), nunca substituído. Isso está publicado
   e visível para qualquer visitante.
2. **Página "Sobre nós" publicada e vazia.** `vogar.arq.br/pages/sobre-nos`
   existe, está no menu principal, mas não tem nenhum parágrafo — só o
   bloco de newsletter do rodapé. Um lead que clica em "Sobre nós" para
   conhecer a arquiteta não encontra nada.
3. **Descrição de projeto reciclada sem edição.** A meta description
   "SOBRE O PROJETO... vista para o lago..." é idêntica em produtos que
   não têm nada a ver com lago — inclusive no VISAGE SALON, um salão de
   beleza comercial. É outro texto de template copiado e nunca ajustado
   por projeto.
4. Site cheio de estrutura de e-commerce Shopify (carrinho, seletor de
   país/moeda com +200 países, "Preço normal $0.00", "Esgotado") em um
   site que não vende produto nenhum — é um portfólio de arquitetura
   fantasiado de loja.

## O que funcionava e foi preservado

- **Nome e wordmark**: "Vogar Arquitetura" — não existe logo gráfico no
  site atual, o cabeçalho já usa o nome em texto. O redesign preserva
  isso, apenas tipografa o wordmark; não inventamos um símbolo novo.
- **Fotos reais de projeto**: usadas exatamente as mesmas fotos do
  portfólio do cliente (ver `assets/imagens-fonte.txt` para a lista
  completa de URLs de origem). Nenhuma foto foi gerada ou trocada.
- **Nomes dos projetos**: Casa Náutico, Casa Verona, Casa Mar-a-Lago,
  Casa Branca, Visage Salon — nomes exatamente como estão no site e no
  Shopify admin do cliente.
- **A citação da fundadora**: "Não basta criar algo único. A arquitetura
  precisa ser sentida com a alma." — Vanessa Portes, junto com a foto
  dela (o recorte em PNG que já era usado no banner da home). Essa é a
  peça central da seção "Sobre" no site novo.
- **Tagline institucional real**: "Nós pensamos além dos espaços, nós
  pensamos em você." — usada como texto de apoio no hero, exatamente
  como aparecia na home antiga.
- **Categorias reais de atuação**: o `<title>` do site antigo é
  "VOGAR | ARQUITETURA E INTERIORES" e o menu já separava
  Residenciais/Comerciais. A seção "Serviços" do site novo (Arquitetura
  residencial / Arquitetura comercial / Design de interiores) vem
  diretamente dessa estrutura real, não foi inventada.
- **WhatsApp, redes sociais e contato**: número (62) 99182-9272, link
  wa.me usado no botão "Fale conosco" do site antigo, Instagram
  @vogararquitetura, Facebook, Pinterest e YouTube — todos copiados tal
  qual do rodapé original.

## O que NÃO inventamos (e por quê)

- **Metragens, ano de entrega e localização exata de cada projeto**: não
  existe essa informação em nenhuma página do site antigo (nem nos
  produtos, nem nas coleções, nem em metadados). Em vez de inventar
  "180m² · 2023 · Caldas Novas" como muitos templates fazem, cada bloco
  de projeto no site novo traz só nome, categoria (residencial/comercial)
  e uma frase descritiva honesta. Se o cliente quiser, dá pra completar
  a "ficha técnica" depois — mas com dado real vindo dele.
- **Texto da seção "Sobre"**: como a página "Sobre nós" original está
  vazia, o parágrafo institucional do site novo foi escrito só a partir
  de fragmentos que já existiam de fato no site (a citação, a tagline, o
  nome da arquiteta, a cidade). Não inventamos formação, tempo de
  mercado, número de projetos entregues ou equipe — porque nada disso
  está disponível em nenhuma página pública. Recomendo pedir esse texto
  direto para a Vanessa antes de publicar.
- **Depoimentos de clientes**: não há nenhum depoimento em texto no site
  antigo. Em vez de simular uma frase de "cliente satisfeito", a seção
  de prova social usa apenas o dado real e verificável: nota 5,0 com 19
  avaliações no Google Maps (informação repassada pelo lead), mais links
  diretos para Instagram/Facebook/Pinterest/YouTube reais.

## O que mudou estruturalmente

- Site antigo: menu de 4+ páginas (Projetos com submenu, Sobre, Contato)
  rodando em cima de infraestrutura de e-commerce Shopify. Site novo:
  uma página só, com âncoras internas (`#projetos`, `#sobre`,
  `#contato`) — sem carrinho, sem seletor de moeda, sem nada que sugira
  loja.
- Tipografia trocada de fonte de tema genérico do Shopify para
  **Fraunces** (títulos e nomes de projeto, com peso editorial) +
  **Inter Tight** (corpo). Nenhuma das duas é Poppins/Montserrat/Roboto.
- Paleta nova, construída a partir da fotografia real dos projetos
  (concreto claro, água do lago, madeira, metal escovado), não da
  identidade visual antiga (que era só preto/branco de tema padrão):
  `--bg #F4F0E7` (papel areia), `--bg-alt #EAE3D6`, `--ink #1B2420`
  (verde muito escuro), `--sage #6E7B5E` (verde eucalipto, usado em
  rótulos/tags), `--brass #9C7A46` (latão, usado em hover/CTA), `--line
  #C9C2B2` (linha fina divisória).
- Elemento assinatura: uma linha fina horizontal cor de latão abaixo de
  cada nome de projeto, referenciando a linha d'água/horizonte do lago —
  o motivo visual central do portfólio (Casa Náutico, Casa Mar-a-Lago).
- Um projeto por bloco, foto grande alternando esquerda/direita, sem
  carrossel, sem ícone genérico nos "serviços".
- Uma única animação: revelação suave no scroll (fade + leve translação),
  respeitando `prefers-reduced-motion`.
- Botão de WhatsApp sempre acessível: fixo no cabeçalho no desktop e
  botão flutuante no canto inferior direito em mobile.

## Limitação técnica do ambiente (leia antes de publicar)

O ambiente onde este redesign foi gerado não tem acesso de rede no nível
do shell (todo tráfego HTTP fora da ferramenta de leitura de páginas foi
bloqueado por allowlist). Isso significa que **não foi possível baixar os
bytes das fotos** para convertê-las em `.webp` e hospedá-las localmente
em `assets/`. O `index.html` entregue referencia as fotos diretamente do
CDN público do próprio site do cliente (`vogar.arq.br/cdn/shop/...`) —
são as mesmas imagens reais, só que carregadas por hotlink em vez de
cópia local.

Antes de publicar de verdade: baixar cada imagem listada em
`assets/imagens-fonte.txt`, converter para `.webp` (~75-80% de
qualidade), salvar em `assets/` com os nomes já sugeridos no manifesto, e
trocar os `src` do `index.html` para os caminhos locais. Isso também
resolve a dependência de o site novo continuar de pé só enquanto o
Shopify antigo estiver no ar.

Pelo mesmo motivo, as fontes (Fraunces e Inter Tight) estão carregadas
via Google Fonts CDN em vez de embutidas — ideal seria baixar os arquivos
`.woff2` e servir localmente na publicação final.

## Arquivos entregues

```
vogar-arquitetura/
├── index.html                    # site novo
├── comparar.html                 # antigo x novo, iframe duplo
├── assets/
│   └── imagens-fonte.txt         # manifesto com URLs reais de cada foto usada
└── NOTAS.md                      # este arquivo
```
