# NOTAS — Redesign Odontoclin Especialidades (Luziânia-GO)

## O "antes"

O site atual é uma página improvisada no Google Sites chamada **"Whatsapp Aqui"**
(https://sites.google.com/view/whatsappaqui/odontoclin), com duas URLs cruas de
redirecionamento do Google coladas como texto — uma para o WhatsApp, outra para
o Instagram. Sem nome da clínica visível, sem endereço, sem serviços, sem
avaliações.

**O que funciona nele e foi preservado:** a intenção. A página inteira existe
para levar ao WhatsApp — e é assim que a clínica fecha agendamento. O site novo
mantém o WhatsApp como espinha dorsal de conversão: CTA no header, no hero
(acima da dobra em mobile), na seção de especialidades, no bloco de contato e em
botão flutuante no mobile.

## O que foi mantido (dados reais, nada inventado)

- WhatsApp confirmado do próprio site antigo: (61) 99947-3584 → wa.me/5561999473584
- Instagram: @odontoclinespecialidades
- Nome completo: Odontoclin Especialidades — Clínica Odontológica e Estética
- Endereço: R. São Paulo, Q15 – Lt 14, Sala 03 – Santa Luzia, Luziânia-GO, 72803-020
- Horário conhecido: seg–sex, fecha às 18h (só isso foi afirmado; o horário de
  abertura não é conhecido e por isso não foi escrito)
- Nota 5,0 no Google, 38 avaliações
- 3 depoimentos reais do Google, citados na íntegra com atribuição
  "— Nome, no Google" (Evanuse Viana Meireles Abreu, Crisnanda Silva,
  Catharina Kazmirczak)
- Dr. Lucas (na clínica desde pelo menos 2018, sisos e procedimentos complexos)
  e a secretária Alice — ambos citados nominalmente nas avaliações públicas
- O hábito da clínica de responder cada avaliação virou a linha "dono presente"
  na seção sobre

As três especialidades do site derivam apenas do que existe: "clínica geral e
prevenção" (famílias que voltam sempre — depoimento), "cirurgia oral" (sisos e
procedimentos complexos do Dr. Lucas — depoimento) e "estética do sorriso e
facial" (está no próprio nome da clínica; nenhum procedimento específico foi
inventado).

## Sobre fotos — decisão importante

**Não há fotos reais da clínica disponíveis.** Nenhuma foto de banco foi usada
fingindo ser da clínica. Em vez disso:

- Identidade gráfica forte carrega a página: verde pinho + marfim + rosa-gengiva,
  tipografia com desenho e o motivo recorrente do **arco de sorriso** (arcos
  concêntricos em SVG no hero, sob cada título de seção e no favicon/logo).
- A seção "sobre" tem um **slot de foto explícito e assumido**, com legenda
  "Espaço reservado para a foto da equipe e da clínica — entra assim que o
  material for enviado". Quando o cliente mandar fotos, é trocar um bloco.
- O logotipo é um wordmark tipográfico + símbolo de arcos, porque a página
  antiga não tem logo nenhum a preservar. Se a clínica tiver logo próprio
  (fachada/Instagram), ele substitui o wordmark sem mexer no layout.

## Plano de tokens (registrado)

- Cores: `--pinho #0F4C42` (principal), `--pinho-escuro #0A342E`,
  `--marfim #F6F2EA` (fundo, "aconchegante" em vez de branco estéril),
  `--esmalte #FFFFFF` (cartões), `--gengiva #C06A55` (acento quente, faz a
  ponte odontologia ↔ estética), `--tinta #172B27` (texto).
- Tipografia: **Fraunces** (display — curvas quentes, combina com a voz
  "aconchegante" dos depoimentos) + **Inter Tight** (corpo). Nada de
  Poppins/Montserrat/Roboto.
- Conceito em uma frase: *a recepção da clínica em forma de página — marfim
  calmo, verde profundo, e o WhatsApp sempre à mão como quem é recebido pela
  Alice.*
- Elemento assinatura: o **arco do sorriso** — arcos concêntricos finos que
  aparecem no hero, nos divisores de seção, no slot de foto e no favicon.
- Teste anti-genérico: pinho + marfim + serif serviria a um nutricionista; o que
  amarra ao nicho é o arco de sorriso como geometria recorrente, o branco
  "esmalte" dos cartões, o acento "rosa-gengiva" (em vez de terracota decorativa)
  e o copy inteiro ancorado em sisos, Dr. Lucas, Alice e recepção.

## O que mudou (e por quê)

| Antes | Depois | Por quê |
|---|---|---|
| Página "Whatsapp Aqui" sem nome da clínica | Marca, nome e localização no primeiro segundo | Quem recebe o link precisa saber onde chegou |
| URLs cruas coladas como texto | Botões de WhatsApp e links nomeados | URL crua parece golpe; botão com rótulo converte |
| Nenhuma prova social | Selo 5,0 + 3 depoimentos reais com atribuição | A nota 5,0 é o maior ativo da clínica e estava invisível |
| Nenhum endereço/horário | Endereço completo, "como chegar" e horário | Paciente novo decide por localização |
| Domínio sites.google.com/view/whatsappaqui | Página própria, um arquivo HTML, servível por qualquer nginx | Credibilidade e link limpo para bio do Instagram |

## Técnica

- HTML + CSS puros, um arquivo (`index.html`). Sem framework, sem build.
- Responsivo 360–1920px; CTA de WhatsApp acima da dobra em 360×640 e botão
  flutuante discreto no mobile.
- Reveal no scroll como progressive enhancement: classe `js` adicionada no
  `<head>`, padrão `[data-reveal]{opacity:1}`, IntersectionObserver e
  `setTimeout` de segurança de 2,5 s — nada fica invisível sem JS.
- `prefers-reduced-motion` respeitado (animações e smooth-scroll desligados).
- Foco de teclado visível em todos os elementos interativos.
- Open Graph com imagem própria gerada (`assets/og.png`, 1200×630, 41 KB).
  **Ao publicar, trocar `assets/og.png` por URL absoluta do domínio final** —
  WhatsApp não resolve caminho relativo no preview.
- Fontes via Google Fonts com `preconnect` e `display=swap`. Não foram
  embutidas para manter o entregável em um arquivo enxuto; ao publicar no
  servidor próprio, é possível self-hostear os woff2 em `assets/fonts/` se
  quisermos zerar dependências externas.
- `assets/` contém apenas `og.png`: o site original não tem nenhuma imagem a
  extrair (nem logo, nem fotos).
- `comparar.html`: iframes lado a lado (empilhados no mobile), ambos os painéis
  com link "abrir em nova aba ↗" — cobre o caso de o Google Sites recusar
  embed.

## Perguntas prováveis do cliente

- **"Cadê as fotos?"** — Não usamos foto de banco fingindo ser sua clínica.
  O slot está pronto: 1 foto da recepção/equipe já completa a página.
- **"Por que não tem lista grande de procedimentos?"** — Só publicamos o que
  podemos afirmar com o material existente. A lista completa entra em 10
  minutos quando você enviar.
- **"Posso continuar fechando pelo WhatsApp?"** — O site inteiro foi desenhado
  para isso; ele só faz o caminho até a mensagem parecer profissional.
