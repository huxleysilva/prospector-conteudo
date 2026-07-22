# NOTAS — Redesign Oral Clínica (Luziânia-GO)

## Situação de partida

O "site" atual da clínica é `https://agenda.link/oralclinicaluziania`, que
redireciona para a **tela de login da Clinicorp** (software de gestão). Ou
seja: quem clica no link do Google cai numa tela de senha, não numa página da
clínica. Não havia layout, texto nem foto para preservar — o redesign partiu
dos dados públicos reais (Google Maps e avaliações).

O que **funciona** no cenário atual e foi aproveitado como matéria-prima:
a reputação. Nota 5,0 com 40 avaliações e depoimentos específicos (especialistas
por área, raio-X no local, limpeza, Dra. Adélia citada nominalmente). O site
novo é basicamente essa reputação organizada em página.

## O que foi mantido (dados reais, sem invenção)

- Nome: Oral Clínica.
- Nota 5,0 no Google, 40 avaliações — protagonista do hero.
- Endereço completo: Av. Alfredo Nasser, Quadra 01 – Lote 04, St. Mandu II,
  Luziânia-GO, CEP 72814-790.
- Telefone fixo (61) 3060-5029. **Não há WhatsApp confirmado**, então o CTA é
  "ligue e agende" — nenhum número de WhatsApp foi inventado.
- Horário: segunda a sexta, até as 18h10.
- Os 3 depoimentos reais do Google, na íntegra, com atribuição
  "— Nome, no Google" (Bruna Ribeiro, Mauricio Júnior, Dra. Bruna Vieira
  Vilarinho).
- Diferenciais citados nas avaliações: especialistas em cada área, radiografia
  periapical e panorâmica no local, clínica limpa/organizada, atendimento
  rápido, preço bom.
- Selo de acolhimento LGBTQ+ do Maps, citado de forma discreta no bloco de
  contato.
- **Não** foi criada lista de especialidades (implantes, ortodontia etc.)
  porque não há confirmação de quais a clínica oferece — só o que as
  avaliações comprovam.

## O que mudou

- **De tela de login para página institucional.** O link que a clínica divulga
  passa a apresentar a clínica antes de pedir qualquer coisa ao paciente.
- **Estrutura de página única:** hero com nota 5,0 → faixa de prova → 4 cartões
  de diferenciais (todos extraídos das avaliações) → destaque para o raio-X no
  local (diferencial técnico raro em clínica de bairro) → 3 depoimentos →
  contato com telefone em destaque, mapa e horário.
- **Contato acima da dobra no mobile:** telefone clicável no header fixo.

## Plano de tokens usado

- Conceito em uma frase: *a página é a sala de recepção da clínica — superfícies
  marfim limpas, verde profundo de confiança, e a nota 5,0 em âmbar como joia
  central.*
- Cores: `--papel #FAF7F2` (marfim quente, limpeza sem frieza hospitalar),
  `--pinho #0F3B33` (marca), `--pinho-2 #0A2B25`, `--menta #E2EEE7`,
  `--salvia #5E8677`, `--ambar #C0892F` (estrelas/detalhes), `--tinta #22302B`.
  Fugiu-se de propósito do azul-dentista de template.
- Tipografia: **Fraunces** (display, serifada com desenho — acolhimento) +
  pilha do sistema para corpo (zero dependência extra).
- Elemento assinatura: o **arco** — padrão SVG de semicírculos que evoca a
  arcada dentária/curva do sorriso, usado nos painéis do hero e do raio-X e no
  divisor da seção de contato.
- Teste anti-genérico: verde + marfim + serifa serviria para um nutricionista;
  o que ancora no nicho é o motivo da arcada, a nota dourada como protagonista,
  o painel de radiografia periapical/panorâmica e a faixa de horário estilo
  recepção. Sem esses quatro elementos o plano seria descartado.

## Fotos: política adotada

**Não há fotos reais da clínica disponíveis.** Nenhuma foto stock de
pessoas/consultórios foi usada fingindo ser da Oral Clínica — isso quebraria a
confiança que a página inteira tenta construir. No lugar:

- Dois painéis gráficos com o padrão de arcos da marca, cada um com um rótulo
  tracejado explícito: *"Espaço reservado — foto real entra aqui"* (recepção/
  equipe no hero; equipamento de radiografia na seção de estrutura).
- Quando o cliente enviar fotos reais, basta trocar o conteúdo do `.painel`
  por um `<img>` com `width`/`height` declarados e `loading="lazy"`.

## Técnica

- HTML + CSS puros, arquivo único, sem framework nem build.
- Responsivo de 360 a 1920 px (grid colapsa em 860 px; CTAs viram largura
  total abaixo de 420 px).
- Open Graph completo apontando para `assets/og.png` (1200×630, gerado com a
  identidade da marca — substituir por foto real quando existir).
- Foco de teclado visível (`:focus-visible` âmbar em tudo).
- `prefers-reduced-motion` respeitado: reveal e hovers desligam.
- Reveal no scroll com progressive enhancement: classe `.js` adicionada no
  head, conteúdo visível por padrão sem JS, e `setTimeout` de segurança que
  força tudo visível após 2,5 s.
- **Exceção documentada:** Fraunces carregada via Google Fonts (CDN). É a única
  dependência externa; se preferir zero CDN, dá para subsetar e embutir em
  woff2 na publicação.
- `comparar.html`: iframe duplo antes/depois. O painel "antes" (Clinicorp)
  provavelmente bloqueia embed por X-Frame-Options — por isso ambos os painéis
  têm link "abrir em nova aba ↗" e o painel antigo traz um aviso explicando o
  quadro em branco.
