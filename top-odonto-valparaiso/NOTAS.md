# Top Odonto — Clínica Integrada · notas do redesign

Valparaíso de Goiás-GO · Galeria Copacabana, Rua Japão Q. 12, 02B, loja 14A — Parque Esplanada III

---

## O que foi mantido (é do cliente)

- **Nome, endereço e telefone.** (61) 3205-5159 — o mesmo número que o site atual já usava nos links de WhatsApp, preservado em `wa.me/556132055159`.
- **Os tratamentos oferecidos**, com os nomes que a clínica usa.
- **Os depoimentos**, na íntegra e com atribuição a quem escreveu, todos vindos das avaliações públicas do Google.
- **Dr. Ronan**, citado nominalmente pelos pacientes, e o elogio recorrente à equipe da recepção.
- **A nota 4,9 com 29 avaliações** — conferida no perfil do Google.
- Os selos declarados no perfil: empresa que acolhe a comunidade LGBTQ+ e empresa de empreendedoras.

## O que mudou, e por quê

| Problema no site atual | O que foi feito |
|---|---|
| Contadores da home travados em **"0 K+ Sorrisos Restaurados"** e **"0 Especializações"** | Removidos. Número que mostra zero comunica o oposto do pretendido — e o padrão "herói-métrica" é um vício de template. A prova social agora vem dos depoimentos reais e da nota do Google, que são verificáveis. |
| **Imagem puxada do demo do tema** (`demo.bosathemes.com/...call-back-image.png`) servida como se fosse foto da clínica | Removida. Nenhuma imagem de terceiros ou de banco fingindo ser a clínica. No lugar, identidade gráfica própria e espaços reservados, rotulados, para as fotos reais. |
| **Botão de callback com link morto** (`href="#"`) | Todo botão da página agora executa uma ação real: abre o WhatsApp, liga, ou rola para a seção correspondente. |
| **Open Graph ausente** — link compartilhado no WhatsApp chega sem título, sem descrição e sem imagem | `og:title`, `og:description`, `og:image` (1200×630) e `og:locale` completos. É o achado central da proposta: a clínica é indicada boca a boca, e o link que circula chegava mudo. |
| **Typo no título da aba: "Espalanda"** em vez de "Esplanada" | Corrigido. Aparece na aba do navegador, nos favoritos e no resultado do Google. |
| Site respondia em **HTTP sem forçar HTTPS** (o certificado existe e é válido, só não redirecionava) | Nada a fazer no HTML — anotado como ajuste de servidor para o momento da publicação. |
| One-page sem navegação, difícil de percorrer | Estrutura com âncoras nomeadas (`#tratamentos`, `#clinica`, `#contato`) e ordem de leitura declarada. |

## Decisões de direção

**A clínica que responde.** A Top Odonto responde publicamente até as avaliações críticas, com tom transparente. Isso virou seção própria ("Uma clínica que responde") em vez de ficar escondido — para um paciente escolhendo dentista, saber que a clínica encara a crítica de frente vale mais que qualquer adjetivo sobre si mesma.

**Sem foto de banco.** A regra é firme: nada de stock fingindo ser a recepção deles. A página segura a composição com tipografia, cor e ritmo, e os espaços de foto estão explicitamente rotulados. Assim que a clínica enviar as imagens, entram sem retrabalho de layout.

**Contato acima da dobra em mobile.** Odontologia fecha por WhatsApp. O botão está no topo, aparece de novo ao longo da página e não some da tela em telas pequenas.

**Uma animação só.** Uma revelação autoral no scroll, com estado inicial já visível e rede de segurança em JavaScript — se o script falhar, a página aparece inteira do mesmo jeito. `prefers-reduced-motion` desliga tudo.

## Pendências para a publicação

1. **Fotos reais da clínica** (recepção, consultórios, equipe) para substituir os espaços reservados.
2. **Horário de abertura.** O Google só expõe o fechamento (12h). Não inventei o restante — confirmar com a clínica e completar.
3. **Instagram.** Não há perfil vinculado ao Google Maps. Se existir, entra no rodapé.
4. **`og:image` para URL absoluta** no momento da publicação (feito automaticamente pelo passo de publicar).
5. **Forçar HTTPS** no servidor, quando o site assumir o domínio definitivo.

## Arquivos

```
top-odonto-valparaiso/
├── index.html      # o site novo, arquivo único, HTML e CSS puros
├── comparar.html   # atual e proposta lado a lado, com "abrir em nova aba" nos dois painéis
├── assets/og.png   # imagem de compartilhamento, 1200×630
└── NOTAS.md
```
