# Oral Vita — Radiologia Odontológica (Formosa-GO)

Redesenho de `https://oralvita.net` (WordPress + Elementor + Smart Slider 3) em uma
página única de HTML e CSS puros.

**Premissa que orientou tudo:** este lead não é clínica de tratamento. É um centro
de diagnóstico por imagem com dois públicos distintos — o dentista que encaminha e
o paciente que chega com um pedido de exame na mão. O site precisa responder três
perguntas em segundos: *vocês fazem esse exame?*, *quando fica pronto?*, *onde é?*
Nenhuma linha de "sorriso dos sonhos".

---

## O que foi mantido (regra zero)

- **Logotipo**, nas duas versões que o próprio site usa: `logo-oralvita2.png` no
  topo claro e `logo-oralvita.png` no rodapé escuro.
- **Fotos**: as quatro imagens reais do site (`Radiografias.jpeg`,
  `Tomografia-computadorizada.jpeg`, `documentacao-2.jpg`, `modelos2.jpg`).
  Nenhuma foto de banco de imagens.
- **Paleta**: azul-petróleo e turquesa derivados do logotipo. Nada de cor nova
  inventada.
- **Texto institucional com voz própria**, transcrito literalmente:
  "Somos uma radiologia odontológica especializada em imagens de alto padrão, com
  investimento constante em tecnologia e treinamento."
- **Lista de exames completa e literal** — os 27 itens publicados em
  `/exames/`, com os nomes exatos. Nada inventado, nada omitido.
- **Dados legais**: RT Fernando Ramos Jacintho de Almeida — CRO 8718/GO, e
  ORAL VITA CONSULTÓRIO ODONTOLÓGICO LTDA — EPAO 407-GO.
- **Links vivos do site atual** que continuam úteis: Resultados Online,
  Requisições Online e Convênios. Eles seguem apontando para as páginas
  existentes, então nada quebra no dia da troca.
- **Unidade Planaltina-DF**, com endereço e WhatsApp.
- **Depoimentos reais do Google**, com atribuição nominal.

---

## O que mudou, e por quê

| Antes | Agora | Motivo |
|---|---|---|
| Slider da home exibindo nomes de arquivo crus ("Cuidamos de tudo para você. (851 x 315 px)8", "Slide", "Cuidamosdetudoparavoc") | Herói tipográfico com uma promessa: *o exame sai hoje, com você ainda aqui* | O slider quebrado é o primeiro contato do paciente com a marca. Era o defeito mais caro do site. |
| Menu de 7 páginas, incluindo **Blog** parado desde 1/out/2024 | Página única com âncoras; o Blog sai do menu | Menu que promete conteúdo e entrega post de 2023 comunica abandono. Os posts continuam no ar nas URLs antigas — só deixam de ser navegação principal. |
| Quatro cards de categoria ("Documentação", "Radiografias", "Tomografia", "Modelos") levando todos para a mesma página `/exames/` | Índice completo dos 27 exames na própria home, agrupado em 4 blocos com contagem | O paciente chega com um nome específico escrito no pedido ("telerradiografia lateral"). Ele precisa reconhecer aquela palavra, não uma categoria genérica. Zero clique entre a dúvida e a resposta. |
| Diferenciais reais **ausentes** do site | Ficha de estrutura: entrega na hora, estacionamento próprio, ambiente climatizado, espaço com brinquedos, plano de saúde | São exatamente os motivos que os clientes citam nas avaliações do Google. Estavam invisíveis no site. |
| Nenhuma prova social | Nota 5,0 com 58 avaliações e três depoimentos nominais | Prova social existente e não utilizada. |
| Sem separação de público | Bifurcação logo abaixo da dobra: "Você tem um pedido do dentista" / "Você é dentista e encaminha pacientes" | Dois públicos com necessidades opostas. Sem essa bifurcação, os dois leem o texto do outro. |
| Endereço só no rodapé, sem CEP | Seção de localização com endereço completo, CEP, referência da prefeitura e link do Maps | Metade das buscas é "onde fica". |
| WhatsApp escrito como "9.98010881" | `(61) 99801-0881` clicável, com link `wa.me` no topo, no herói, nas duas rotas e em barra fixa no mobile | O número não era clicável nem legível. |
| E-mail ofuscado pelo Cloudflare (aparece como "[email protected]") | Removido do site; contato por WhatsApp e telefone | Endereço de e-mail quebrado é pior do que nenhum. O e-mail real pode ser reinserido assim que o cliente informar. |
| Elementor + Smart Slider + jQuery | Um arquivo HTML, CSS embutido, ~9 linhas de JS | Velocidade, e nada para quebrar. |

---

## Divergência encontrada (achado para a proposta)

**O site atual publica dois perfis de Instagram diferentes:**

- na **home**, o widget social aponta para `instagram.com/oralvitaradiologia`;
- no **rodapé de todas as páginas**, o ícone aponta para `instagram.com/oralvitafsa`.

Só um dos dois é o perfil ativo. Conforme orientação do levantamento, o redesenho
usa **@oralvitafsa** em todo o site. Vale confirmar com o cliente e corrigir (ou
remover) o outro — link social morto derruba a confiança justamente na hora em que
o paciente vai checar se a empresa é real.

Outra inconsistência menor: o site lista dois telefones para Planaltina-DF
(fixo (61) 3308-4507 e móvel 9.91291985). O redesenho usa o WhatsApp
(61) 99129-1985 informado no levantamento; convém confirmar o fixo antes de
publicar.

Terceira: a página `/exames/` lista **Guia Cirúrgico para Implantes** duas vezes
(em "Documentação" e em "Modelos | Moldagens | Placas"). Aqui ele aparece uma vez
só, em Documentação — daí a contagem de 27 e não 28.

---

## Pendências antes de publicar

1. **Baixar os assets para `assets/`.** As imagens e o logotipo estão sendo
   carregados diretamente de `oralvita.net/site2023/wp-content/uploads/...`
   (URLs estáveis do WordPress, usadas aqui para a demonstração). Na publicação
   definitiva: baixar, converter para `.webp`, gravar em `assets/` e trocar os
   `src`. São 5 arquivos:
   - `2023/03/logo-oralvita2.png` (topo)
   - `2023/03/logo-oralvita.png` (rodapé + og:image)
   - `2023/04/Radiografias.jpeg`
   - `2023/04/Tomografia-computadorizada.jpeg`
   - `2023/04/documentacao-2.jpg`
   - `2023/04/modelos2.jpg`
2. **Gerar `assets/og.png`** (1200×630) com o logotipo sobre fundo petróleo e
   trocar a `og:image`. Hoje ela aponta para o logotipo do domínio, que é
   quadrado e corta mal na prévia do WhatsApp.
3. **Auto-hospedar as fontes.** Newsreader e Inter Tight vêm do Google Fonts.
   Baixar os `.woff2` para `assets/` e declarar `@font-face` elimina a última
   dependência externa.
4. **Fotos que faltam.** Não existe no site nenhuma foto da recepção, do
   estacionamento nem do espaço infantil — justamente o que as avaliações mais
   elogiam. Três fotos do próprio local valeriam mais que qualquer texto nessa
   seção.
5. **Horário de funcionamento** não está publicado em lugar nenhum. Pedir ao
   cliente e inserir na seção de localização.
6. **E-mail de contato** real, para substituir o que o Cloudflare ofusca hoje.

---

## Decisões de design (para quando perguntarem)

- **Tema claro, frio.** A cena de uso é um consultório iluminado ou a calçada do
  Centro de Formosa ao meio-dia. Fundo escuro seria decisão estética contra a
  situação real de leitura.
- **Duas famílias, nenhuma de template.** Newsreader (serifada, com desenho) para
  título e citação; Inter Tight para corpo, rótulo e ficha técnica. Nada de
  Poppins, Montserrat ou Roboto.
- **O índice de exames não usa cards.** Cartões iguais escondem a informação em
  caixas. Lista tipográfica com régua de 1px mostra os 27 itens de uma vez —
  que é o argumento comercial.
- **Uma animação só.** No herói, a imagem "acende" como um negatoscópio sendo
  ligado: parte de um estado já visível, porém lavado, e ganha contraste em
  1,5s. O resto da página tem uma revelação discreta na entrada dos elementos do
  herói. Nada pisca, nada desliza em cada seção.
- **`prefers-reduced-motion` desliga tudo**, e o conteúdo aparece por padrão
  mesmo se o JavaScript falhar (o CSS só esconde depois que o script confirma
  que está rodando, com um `setTimeout` de 2,5s como rede de segurança).
- **Foco de teclado visível** em todos os links e botões, na ordem visual.

---

## Arquivos

```
oral-vita-radiologia/
├── index.html      # o site novo, um arquivo
├── comparar.html   # atual e proposta lado a lado, com "abrir em nova aba" nos dois painéis
├── assets/         # (vazio — ver pendência 1)
└── NOTAS.md
```
