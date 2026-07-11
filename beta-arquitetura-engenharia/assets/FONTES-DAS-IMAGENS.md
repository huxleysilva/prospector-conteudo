# Origem das imagens usadas no redesign

Todas as imagens do `index.html` são fotos/renders reais do site antigo da
Beta (`betaarqeng.com`, Wix), referenciadas diretamente do CDN
`static.wixstatic.com` (hotlink) com parâmetros de redimensionamento e
qualidade ajustados (`w_`, `h_`, `q_85`, `enc_avif`). Nenhuma é imagem de
banco de imagens genérico.

Motivo do hotlink em vez de arquivo local `.webp`: o ambiente desta sessão
não tem saída de rede liberada para `curl`/`wget` baixarem bytes binários de
domínios externos (bloqueado pelo proxy da sandbox). A ferramenta de fetch de
página disponível só devolve HTML/texto, não o conteúdo binário da imagem.

## Lista de imagens e origem (media ID Wix / uso no site antigo)

| Uso no site novo | Media ID Wix | Onde aparecia no site antigo |
|---|---|---|
| Logo (header) | `359a63_aabd148fe8aa43aabc15e695bea523eb` | Cabeçalho de todas as páginas |
| Hero (topo) | `359a63_ca915001fd0940359a84542487d4298a` | Card "Projeto Residencial JA-04" na home |
| Projeto JA-04 | `359a63_7266d5fb19dd4bbfa4b320c5532deadf` | Topo da página `/projeto-1` |
| Projeto JA-30 | `359a63_de56d3aa6c9a4b36b45e494413b9a7ad` | Card JA-30 na home / topo `/projeto-2` |
| Projeto JA-21 | `359a63_f653f68247d040faab040bc4c86560ce` | Card JA-21 na home / topo `/projeto-4` |
| Projeto PC-06 | `359a63_4a861d1e040347b795c4e01a8c378ecd` | Card PC-06 na home / galeria `/projeto-5` |
| Retrato Ed Wilson | `359a63_cc61f84116954f2e9facf1366f3fecd6` | `/nossa-historia`, arquivo `ed.png` |
| Retrato Guilherme Oliveira Lima | `359a63_60e32226cd344791be2509e70246c361` | `/nossa-historia`, arquivo `guilherme.png` |
| Foto "Sobre"/contato | `359a63_5a39fecf189d4f73ae68db21b0f8ccb3` | Seção "Entre em Contato" na home, `EDITADO-01.png` |

## Pendência antes de publicar

Baixar essas 9 imagens (URL completa: `https://static.wixstatic.com/media/<ID>~mv2.<ext>`),
converter para `.webp` e salvar nesta pasta `assets/`, depois trocar os `src`
em `../index.html` e o `og:image` para os caminhos locais. Isso remove a
dependência do domínio `static.wixstatic.com` e completa o requisito de
"imagens otimizadas locais" do padrão técnico do redesign.
