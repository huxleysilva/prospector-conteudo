# Origem das imagens usadas no redesign

O domínio `flaviagoulart.com.br` está fora do ar (DNS morto). O rastreamento do
Wayback Machine para este site também é raso: só a home foi indexada de forma
navegável, e o carrossel de fotos de projeto (Revolution Slider, imagens
carregadas via JavaScript) não ficou preservado em nenhum snapshot — as
tentativas de resolver `wp-content/uploads/2020/07/sliderhomenovo*.jpg` e
`.../2022/01/home_slider_mobile_*.jpg` direto no Wayback retornam "not
archived", mesmo aparecendo no HTML da home.

As únicas fotos reais recuperáveis e verificadas (abrindo cada URL e
confirmando visualmente o conteúdo) vieram de duas fontes que ainda respondem:

1. **Logo** — preservado no Wayback (snapshot de 08/2022, redirecionado
   automaticamente a partir da URL pedida):
   `https://web.archive.org/web/20220802025616im_/https://www.flaviagoulart.com.br/wp-content/uploads/elementor/thumbs/flavialogo_8-pkvzypxandkyrwrdn7i6v2k7ygl4iqzoumvz25tx54.png`

2. **Retrato de Flávia Goulart** (usado em "Sobre") e **fotos da equipe**
   (Gardênia Rocha e Arthur César) — ainda servidas pelo cache do Jetpack
   Photon do WordPress.com (`i0.wp.com`), que mantém cópia de imagens já
   visitadas mesmo com o site de origem fora do ar:
   - `https://i0.wp.com/www.flaviagoulart.com.br/wp-content/uploads/elementor/thumbs/foto_home2-pkvzyiekvxjhyqweujtflbuv2ogpbzwxhxume9cn08.jpg?ssl=1`
   - `https://i0.wp.com/www.flaviagoulart.com.br/wp-content/uploads/2019/06/gardenia_assistente_arq-1-e1661394382387.jpg?ssl=1`
   - `https://i0.wp.com/www.flaviagoulart.com.br/wp-content/uploads/2021/12/arthur_assistente_tecnico-e1661394421875.jpg?ssl=1`

`index.html` referencia essas três fotos e o logo diretamente por essas URLs
(hotlink), porque o ambiente de trabalho desta sessão não tem saída de rede
para baixar e reencodar os arquivos localmente em `.webp` — apenas o
navegador conectado tem acesso à internet, e não há um caminho de arquivo
disponível para trazer os bytes da imagem do navegador até esta pasta.

**Antes de publicar de verdade (skill `publicar`/`deploy-servidor`):**
baixar essas 4 imagens, converter para `.webp`, e trocar os `src` em
`index.html` para arquivos locais em `assets/`. Isso resolve a única pendência
técnica em relação ao padrão-visual (imagens locais otimizadas, sem
dependência de terceiros).

Nenhuma foto de projeto/portfólio foi inventada. Onde a foto real não pôde
ser recuperada, a seção correspondente foi redesenhada ao redor do que É real
(depoimentos, números, retrato) em vez de preencher com imagem genérica de
banco de imagens.
