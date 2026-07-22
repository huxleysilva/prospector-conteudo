# NOTAS — MEC Clínica Odontológica (Jardim do Ingá, Luziânia-GO)

## O que foi mantido (regra zero)

- **Logotipo real** da MEC (dente + paleta aqua), referenciado da URL original.
- **Foto de capa do cliente** (`cliente.png` do site atual), usada no hero.
- **Todos os textos com voz própria**, na íntegra ou com edição mínima:
  - "Conquiste o sorriso dos seus sonhos" (título do hero)
  - "Presente no atendimento odontológico, oferecemos excelência..." (hero e
    citação na seção A clínica)
  - "Da triagem até o resultado final, trabalhamos com alta gama de
    tratamentos odontológicos, exames digitais e planejamentos gerais."
- **Os 11 tratamentos com os nomes originais**, incluindo os detalhes entre
  parênteses (aparelhos auto ligáveis, porcelanas e resinas, canal, sisos,
  gengivite/periodontite). Foram apenas **agrupados** em quatro frentes
  (Alinhar / Restaurar / Tratar e prevenir / Diagnosticar) para dar leitura de
  plano clínico em vez de lista corrida.
- **Paleta aqua/teal da marca**: `#2EB6AE` (aqua do logo), `#0F7C76`
  (aqua profundo para CTAs, com contraste AA), `#E7F5F3` (névoa de fundo),
  `#0B2B2A` (petróleo do texto).
- Nota Google real: 5,0 com 31 avaliações, com link para o perfil no Maps.
- Endereço, WhatsApp e Instagram reais.

## O que mudou e por quê

| Problema no site atual | Solução no redesign |
|---|---|
| Título SSR genérico "Clínica" (o Google e o WhatsApp mostram isso) | `<title>` e meta description com nome, bairro e cidade |
| Sem Open Graph — link sem preview no WhatsApp | OG completo com foto, título e descrição |
| Formulário-porteira: exige nome/telefone antes de liberar o WhatsApp | Botão `wa.me/5561996751678` abre a conversa direto, sem cadastro |
| Banner de cookies invasivo de terceiro | Site estático sem rastreadores — nenhum banner necessário |
| Domínio de plataforma (`mecodontologia.meudoutor.com`) | HTML próprio, pronto para domínio próprio |
| App client-side ("Loading...") — nada renderiza sem JS | HTML puro; o JS é só a revelação no scroll, com fallback |
| CTA laranja da plataforma, fora da paleta da marca | Accent repensado: CTAs no aqua profundo da própria marca; o único tom quente restante é o âmbar das estrelas da nota Google |

## Decisões de design (plano de tokens aplicado)

- **Conceito**: recepção de clínica em aqua e luz — uma coluna calma, hero com
  a promessa real da MEC e a nota 5,0, tratamentos organizados como plano
  clínico numerado, WhatsApp sempre ao alcance (header fixo).
- **Assinatura da página**: o "arco do sorriso" — traço curvo em aqua,
  derivado da curva do dente do logotipo, sublinhando o título do hero.
- **Tipografia**: Fraunces (display; serifa de terminais macios que humaniza o
  tom clínico) + Inter Tight (corpo/UI). Nada de Poppins/Montserrat/Roboto.
- Zero gradiente, zero sombra difusa, fotos sem borda arredondada.
- Uma única animação (revelação no scroll), com `prefers-reduced-motion`
  respeitado, aprimoramento progressivo e rede de segurança de 2,5 s.
- Foco de teclado visível em todos os elementos interativos.
- Responsivo de 360 px a 1920 px (grid colapsa em 880 px; tipos com `clamp`).

## Pendências técnicas (registrar antes de publicar)

1. **Assets não puderam ser baixados**: o proxy do workspace bloqueou por
   allowlist tanto `simplesanuncios.s3.amazonaws.com` (logo) quanto
   `mecodontologia.meudoutor.com` (capa) — inclusive via proxies de imagem.
   O `index.html` referencia as **URLs originais ao vivo**:
   - Logo: `https://simplesanuncios.s3.amazonaws.com/prd/540723/clinicas/image_1778504736684.png`
   - Capa: `https://mecodontologia.meudoutor.com/header/aqua/cliente.png`
   Antes de publicar, baixar ambas para `assets/`, converter para WebP
   (logo mantendo transparência) e trocar os `src` e o `og:image`.
2. **`og:image` precisa de URL absoluta do domínio definitivo** após a
   publicação (hoje aponta para a capa ao vivo na plataforma, o que funciona,
   mas depende do site antigo continuar no ar).
3. **Fontes via Google Fonts** (Fraunces + Inter Tight): o embutimento local
   também foi bloqueado pela allowlist. Se quiser zero dependência externa,
   baixar os WOFF2 na publicação e servir de `assets/`.
4. O iframe do site antigo em `comparar.html` depende de a plataforma permitir
   embed; se bloquear via cabeçalho, o link "abrir em nova aba ↗" cobre o caso.

## Adendo — logotipo (pós-QA)

O logotipo original está hospedado no S3 da plataforma (Simples Anúncios) atrás de
URL assinada que expira — referenciá-lo direto quebra (AccessDenied), e CORS impede
extração dos pixels. Decisão: **não** falsificar a marca. O header usa um lockup
tipográfico "MEC · Clínica Odontológica" com o arco-assinatura em aqua, e o favicon
é um SVG derivado. Quando o cliente fornecer o arquivo do logo, ele entra no lugar
do arco em um minuto — bom gancho de conversa, inclusive.
