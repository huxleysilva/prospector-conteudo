# Imagens usadas no redesign — fonte real e conversão pendente

O `index.html` deste redesign referencia as imagens **diretamente da hospedagem
atual do cliente** (`studionoas.com.br/wp-content/uploads/...`), em vez de
cópias locais em `.webp`. Isso foi uma decisão técnica, não de design — ver
`NOTAS.md` para o motivo (o ambiente de sandbox usado para gerar este redesign
bloqueia download binário de domínios externos).

Nenhuma foto foi inventada. Todas as imagens abaixo são reais, do site atual
do cliente, conferidas uma a uma abrindo a página ao vivo.

Quando este site for publicado (etapa `/publicar`), baixar cada URL abaixo e
salvar em `assets/` já convertida para `.webp`, mantendo os nomes sugeridos —
depois só trocar o `src` no HTML de absoluto para relativo.

| Uso no site          | URL de origem (real, do cliente)                                                                                                   | Nome local sugerido        | Largura alvo |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------|-----------------------------|--------------|
| Logo (header)         | https://studionoas.com.br/wp-content/uploads/2024/04/NOAS_MARCA-01_VERDE-horizontal.png                                             | logo.webp                  | 480px        |
| Hero                  | https://studionoas.com.br/wp-content/uploads/2022/06/CASA-PORTUGAL-CALDAS-NOVAS-GO-3.jpg                                            | hero-casa-portugal.webp    | 1800px       |
| Projeto 01            | https://studionoas.com.br/wp-content/uploads/2022/06/ALDEIA-DAS-THERMAS-CALDAS-NOVAS-GO.jpg                                         | aldeia-das-thermas.webp    | 1400px       |
| Projeto 02            | https://studionoas.com.br/wp-content/uploads/2022/06/CASA-L2-CALDAS-NOVAS-01.jpg                                                    | casa-l2.webp               | 1400px       |
| Projeto 03            | https://studionoas.com.br/wp-content/uploads/2022/06/RESIDENCIA-AR-CALDAS-NOVAS-GO-4.jpg                                            | residencia-ar.webp         | 1400px       |
| Projeto 04            | https://studionoas.com.br/wp-content/uploads/2022/06/ARENA-BEACH-TENNIS-APARECIDA-DE-GOIANIA-resize.jpg                             | arena-beach-tennis.webp    | 1400px       |
| Projeto 05            | https://studionoas.com.br/wp-content/uploads/2022/06/PET-CENTER-CALDAS-NOVAS-02.jpg                                                 | pet-center.webp            | 1400px       |
| Sobre (fundadores)    | https://studionoas.com.br/wp-content/uploads/2022/06/002-1.jpg                                                                       | fundadores.webp            | 1200px       |
| Open Graph (og:image) | https://studionoas.com.br/wp-content/uploads/2022/06/CASA-PORTUGAL-CALDAS-NOVAS-GO-3.jpg                                            | (mesma do hero)            | 1200px       |

`favicon-noas.svg`, nesta mesma pasta, é o único asset gerado do zero — um
monograma vetorial simples ("N" em terracota sobre verde), usado só como
ícone de aba. Não substitui o logotipo real do escritório, que continua sendo
a arte original do cliente (linha "Logo" na tabela acima).
