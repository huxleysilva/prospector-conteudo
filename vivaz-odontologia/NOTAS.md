# Vivaz Clínica Odontológica — notas do redesign

Formosa-GO · Setor Central · site atual: https://sites.google.com/view/vivazodonto

---

## O que foi mantido (é do cliente, não se mexe)

- **A frase-posicionamento**: "Atendemos urgência todos os dias" é do próprio site atual.
  Ela não foi reescrita — foi promovida a título da página.
- **Os nomes dos serviços, exatamente como estão hoje**: Especialista em Endodontia
  (canal), Lentes em resina, Aparelho invisível, Restaurações, Prótese, Clareamento e
  Limpeza, Odontopediatria, Cirurgia Oral. Nenhum foi renomeado, agrupado ou cortado.
- **Dr. Victor**, nominalmente, e a especialidade dele (endodontia).
- **Os três depoimentos do Google**, na íntegra e com o nome de quem escreveu
  (Joel Borges, Walter Augusto, Gabryellah Costa), atribuídos como "no Google".
- **Nota 5,0 e 44 avaliações**, endereço completo (Edifício Ebenezer — R. Herculano
  Lobo, 255, Setor Central, 73801-260), telefone, Instagram @vivaz__odontologia,
  e o fechamento às 20h.
- **A matiz verde** da identidade. Ela continua sendo a cor da marca; só foi levada
  para um verde mais profundo e assentada sobre um fundo quente, em vez do branco
  puro do template do Google Sites.

## O que mudou

**Hierarquia.** No site atual a urgência e o horário estão no meio do texto corrido.
Aqui, a promessa de urgência é o `h1` e o horário virou informação viva, no alto da
página. Quem chega com dor às 19h40 não deveria precisar caçar isso.

**O quadro de plantão (elemento assinatura).** Um bloco escuro no topo que lê a hora
do próprio visitante e escreve o estado em português: "São 19h12. Ainda dá tempo hoje:
fechamos às 20h." / "São 22h40. Já passou das 20h — mas urgência é todos os dias." A
régua de 24 tiques abaixo marca a hora atual; as horas depois das 20h são âmbar (a cor
reservada ao estado "urgência"). O texto nunca afirma horário de abertura, porque esse
dado não estava disponível — se o cliente informar, entra em uma linha.

**A única animação.** Os 24 tiques da régua assentam uma vez, em cascata da manhã para
a noite (ease-out exponencial, 14 ms de atraso por tique). Não há fade-in por seção.
`prefers-reduced-motion` desliga tudo, e o estado padrão da página já é o estado final —
sem JavaScript, a régua aparece inteira e a frase estática continua correta.

**Âncoras quebradas.** O Google Sites atual renderiza códigos crus como
`#h.w2iyspqkgp19` no meio do conteúdo, resto de link interno quebrado. Não existem no
site novo.

**WhatsApp.** O encurtador `wa.link/xn56zc` foi trocado pelo link canônico
`wa.me/5561996546259`, com mensagem pré-escrita ("Olá, vim pelo site e preciso de
atendimento."). Encurtador é uma dependência a mais que pode cair; `wa.me` é do próprio
WhatsApp. O botão está no cabeçalho, no herói, na ficha de contato, no rodapé e em uma
barra fixa na base da tela no celular.

**Serviços sem grade de cards.** Endodontia ganhou uma faixa própria — é a
especialidade da casa e o que traz as urgências. Os outros sete viraram uma lista de
duas colunas separada por régua de 1px, nome em serifa à esquerda e uma frase à direita.
Sem ícone genérico, sem numeração 01/02/03, sem oito cartõezinhos iguais.

**Depoimentos sem avatar.** Citação em serifa, régua de 2px acima, atribuição embaixo.
Nada de foto de perfil recortada nem card com sombra.

**Responsivo de verdade.** Testado no raciocínio de layout para 360px e 1920px: em
360px tudo vira coluna única, a régua de horas reduz para tiques de ~10px e a barra
de contato fica fixa na base; em 1920px o conteúdo trava em 1180px e o herói abre em
duas colunas (7/5), com o quadro de plantão à direita.

**Técnico.** HTML e CSS puros, um arquivo, sem framework. Open Graph completo com
imagem da própria recepção da clínica (1200×900 — ver "Fotos"), JSON-LD `Dentist` com endereço, telefone,
serviços e a nota agregada. Foco de teclado visível em todos os links (âmbar sobre as
superfícies escuras). Nenhum script bloqueante.

## Plano de tokens

| token | hex | papel |
|---|---|---|
| `--tinta` | `#16241E` | texto principal e rodapé — neutro tingido de verde, não cinza |
| `--tinta-suave` | `#3E4E46` | texto secundário sobre claro (≈6:1) |
| `--pinheiro` | `#1E4B3B` | superfície escura funcional (plantão, barra fixa) e botão primário |
| `--vivaz` | `#3FA97A` | acento gráfico da marca — só em elementos ≥3px, nunca texto pequeno |
| `--areia` | `#F2EEE5` | fundo da página, quente |
| `--papel` | `#FBF9F5` | superfície clara elevada (faixa de prova, destaque) |
| `--lampiao` | `#E3A75E` | sinal com significado: depois das 20h / urgência |

Dominante quente (areia do cerrado), acento verde da marca, âmbar reservado a um
estado — nunca decorativo. Cinza puro não aparece em lugar nenhum.

**Tipografia:** Fraunces (display, títulos, citações, nomes de serviço) e Inter Tight
(corpo, labels, metadados). Duas famílias, quatro papéis declarados. Nada de Poppins,
Montserrat ou Roboto. Corpo em 17px, medida de 46–62ch.

**Espaço:** escala base 4 (`--s1` 4px … `--s9` 96px). Grupos internos apertados
(8–16px), separação entre seções generosa (96px). Sempre mais espaço acima de um
título do que abaixo.

## Fotos — status

**Os slots vazios saíram; entraram três fotos reais da clínica.** Elas vêm do **perfil
público da Vivaz no Google Maps** — são fotos do próprio estabelecimento (uma delas
publicada pelo proprietário), não banco de imagem. Estão no site nesta ordem:

1. **Letreiro "VIVAZ" na recepção** — seção "Quem vai te atender", em retrato `4:5`.
   É também a `og:image` (1200×900): é a foto que melhor representa a marca no preview
   de WhatsApp e redes.
2. **Consultório** — faixa `16:9` na seção "O que fazemos", entre a endodontia em
   destaque e a lista de serviços.
3. **Fachada do Edifício Ebenezer** — coluna da direita em "Onde ficamos", ao lado do
   endereço. Quem nunca foi reconhece o prédio antes de sair de casa.

Todas com `alt` descritivo e honesto, `width`/`height` declarados (sem layout shift),
`loading="lazy"` — nenhuma está acima da dobra, então não há `fetchpriority="high"`.
Sem canto arredondado, sem sombra difusa, `object-fit:cover` na proporção reservada.

**Pendência para a publicação definitiva:** hoje as três estão **hotlinkadas** em
`lh3.googleusercontent.com`. Antes de publicar de verdade, **baixe os três arquivos
para `assets/`, converta para `.webp`** (largura ~1600px, qualidade 80) e troque os
`src` por caminhos locais. URL do Google não é hospedagem — pode mudar sem aviso, e
cada foto vira uma requisição a um domínio de terceiro.

**Pedir ao cliente:** retrato do Dr. Victor e foto da equipe (não existem no perfil
público). O retrato entra direto no slot `4:5` da seção "Quem vai te atender" e a foto
atual da recepção desce para a galeria de "Onde ficamos". Vale pedir também os
originais em alta das três fotos acima, para não depender do recorte do Google.

O logotipo também não estava disponível em arquivo. O wordmark atual é tipográfico
(Fraunces + ponto verde) e é substituível por um `<img>` no mesmo lugar, no cabeçalho
e no rodapé.

## Arquivos

```
vivaz-odontologia/
├── index.html      site novo
├── comparar.html   antigo × novo, iframe duplo, ambos com "abrir em nova aba ↗"
├── assets/og.png   1200×630, gerada com os tokens do site
└── NOTAS.md        este arquivo
```

O `comparar.html` avisa, dentro do painel da esquerda, que o Google Sites pode
recusar a exibição em iframe — com o link para abrir em nova aba ao lado.
