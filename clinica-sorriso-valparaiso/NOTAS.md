# Clínica Sorriso — Valparaíso de Goiás-GO
## Notas do redesign

Refação completa. A versão anterior desta pasta foi reprovada com razão: era uma
página 100% tipográfica, sem o logo e sem nenhuma foto real da clínica, e ainda
em paleta bege/terracota que não é a da marca. Isso violava a regra zero
(logo, fotos e paleta do cliente não se substituem). Esta versão parte das
imagens reais do site atual.

---

## O que foi mantido (é do cliente, não se troca)

- **Logo original** (`logo_sorriso.png`), no cabeçalho e no rodapé, sem recorte,
  sem recolorir, sem "modernizar".
- **Paleta azul da marca**, tirada do próprio logo. Nada de bege ou terracota.
- **Fotos reais da clínica**: recepção (`IMG_6727`), consultório (`IMG_6771`) e
  sala de radiologia (`IMG_4152`).
- **Retratos reais da equipe**: Marcelo, Thaynara e Marlúcia, com nome e
  especialidade exatamente como o cliente descreve.
- **Fotos de tratamento** do site atual: ortodontia, implantodontia, endodontia
  e harmonização facial.
- **Selo Invisalign**, que é credenciamento real e argumento de venda.
- **Voz do texto institucional**: "a arte de fazer você sorrir", "fundada em
  2006", "tendo como foco principal você, paciente" — reaproveitado quase
  literal no herói.
- **Depoimentos reais do Google**, com atribuição, sem avatar inventado.
- **Endereço com a referência que o paciente usa**: "acima do Banco Santander".
- **Horário completo real**, incluindo a observação de sábados alternados.
- Telefone, WhatsApp, Instagram, Facebook e YouTube existentes.

## O que mudou, e por quê

| Antes | Agora | Motivo |
|---|---|---|
| Rodapé "© 2021" | Ano calculado no navegador | Site que se diz de 2021 parece abandonado |
| Popup "SORRISO DAY 11/11/2023" | Removido | Promoção vencida há três anos recebendo o visitante |
| Faixa "a partir de maio/25" | Removida | Vencida há mais de um ano |
| Menu com páginas que não abrem e link `?page_id=183` | Página única com âncoras | Nenhum link morto; o conteúdo real cabe em uma página |
| Agendamento em popup de formulário | WhatsApp direto, com mensagem pré-escrita | É por onde o paciente já fala com a clínica |
| Imagens de 2560px servidas brutas | `loading="lazy"`, `width`/`height` e `aspect-ratio` declarados | Sem layout shift e sem travar 4G |
| "19 anos de tradição" escrito à mão | "desde 2006" | Número fixo envelhece sozinho; a data não |
| Sedação e Invisalign perdidos no meio dos serviços | Duas seções próprias, a sedação em superfície escura logo abaixo do herói | São os diferenciais raros no interior, e o medo é o motivo nº 1 de adiar tratamento |
| Sem Open Graph | OG completo com foto da recepção | O link circula por WhatsApp |

## Decisões de design

- **Tipografia**: Fraunces (display, serif com desenho) e Inter Tight (corpo).
  Duas famílias, papéis fixos. Nada de Poppins/Montserrat/Roboto.
- **Cor**: azul da marca `#0B5FA5`, superfície escura `#072E4A`, fundo gelo
  `#EDF3F8`, filete `#C6D9E6`, tinta `#0E1F2C`. Os neutros são tingidos de azul —
  não há cinza puro. O ouro `#9A6B00` aparece só nas estrelas do Google.
- **Elemento assinatura**: a régua de horário. Os dias de atendimento viram
  barras posicionadas numa escala real de 07h a 19h, mostrando de relance que a
  clínica abre cedo e fecha tarde, e que sábado é meio período. É informação do
  cliente desenhada, não decoração.
- **Animação única**: essas barras abrem da esquerda quando a seção entra na
  tela (ease-out exponencial). O resto da página só tem uma revelação discreta.
  `prefers-reduced-motion` desliga tudo; sem JavaScript, tudo nasce visível.
- **Sem grade de cards idênticos, sem eyebrow em toda seção, sem numeração
  01/02/03, sem gradiente em texto, sem glassmorphism, sem border-left colorida
  e sem herói-métrica.** A nota 4,9 é uma linha de rodapé do herói, não um
  número gigante.
- **CTA de WhatsApp** no cabeçalho, no herói, na seção de sedação, no contato e
  fixo no rodapé em telas de até 640px.
- Responsivo de 360px a 1920px; foco de teclado visível em todas as superfícies,
  inclusive nas escuras.

## Pendência antes de publicar

As imagens estão **hotlinkadas do domínio atual** (`clinicasorriso.com/wp-content/...`)
para que a demo funcione sem depender de arquivos locais. Na publicação
definitiva:

1. Baixar as 11 imagens usadas para `assets/`.
2. Converter para `webp` (fotos de ambiente com largura máxima de 1600px, os
   retratos com 1000px, o logo e o selo mantendo PNG com transparência).
3. Trocar os `src` absolutos por caminhos `assets/…` e conferir os
   `width`/`height` reais de cada arquivo.
4. Confirmar com a clínica: os sábados alternados de fato começam 07:40, e se o
   canal preferido de agendamento continua sendo o WhatsApp (61) 98290-7900.
