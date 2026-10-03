---
name: hud-neon-dataviz
description: Regras visuais e narrativas para dashboards em HTML com estética futurista (fundo escuro, acentos neon, tipografia técnica) e rigor de visualização de dados. Use sempre que for criar um painel, relatório visual ou gráfico em HTML autocontido, com qualquer base de dados.
---

# HUD Neon Dataviz

## Quando usar

Sempre que o pedido for um dashboard, painel ou relatório visual em HTML que precise:
contar uma história com dados, ser compreendido sem apresentador e ter aparência
futurista (interface de "HUD": escuro, luminoso, técnico) sem sacrificar legibilidade.
A estética é o invólucro; a leitura correta dos dados é o produto.

## Estrutura narrativa

- Abra com **uma pergunta norteadora** e **um número-herói** (≥ 84px) que já responde
  parte dela. Exatamente um número-herói por página.
- Logo abaixo, uma **linha de tiles** (3 a 6) com o retrato geral; nunca mais que 6
  por linha e nunca um tile órfão em segunda linha.
- Organize o resto em **atos numerados** (`01 — nome`, `02 — nome` …), cada um com:
  eyebrow em monoespaçada, título-afirmação (uma frase que já traz a conclusão), lede
  de 2 frases, um ou dois cards de gráfico, e um parágrafo de **leitura** com 2 ou 3
  números em negrito.
- Ordem dos atos: retrato geral → variação por escala → variação por lugar →
  mecanismo (como se produz) → quem (atores) → **a conta** (o que falta / o que
  muda). Fechar com uma frase de síntese e uma implicação para quem decide.
- Inclua um bloco **"O que a base permite / não permite dizer"** antes do primeiro
  ato. Correlação não vira causa no texto; autodeclaração não vira classificação.
- Rodapé obrigatório: fonte, data da extração, método de cada agregação, cuidados.

## Escolha de gráficos

- A forma vem **antes** da cor. Pergunte o que o leitor precisa fazer:
  comparar magnitudes → barras horizontais (rótulo longo cabe); comparar duas medidas
  por categoria → dumbbell; parte-a-todo pequeno → waffle 10×10 ou matriz; acima/abaixo
  de uma linha de base → barras divergentes; um número só → tile, não gráfico.
- **Um eixo por gráfico.** Nunca dois eixos Y. Duas medidas → dois gráficos.
- Barras ≤ 24px de espessura, ponta arredondada (4px), base reta. Entre marcas que se
  tocam, 2px da cor da superfície. Nenhuma borda em marca.
- Grade e eixos em hairline (1px) sólida, um tom acima da superfície. Nunca tracejado.
- Linhas de referência (média, população, meta) em hairline do acento, com rótulo
  monoespaçado em caixa alta; são o contexto que faz a barra significar algo.
- Rótulos diretos **seletivos**: extremos e o item da história; o resto fica no eixo,
  no tooltip e na tabela. Em listas ≤ 6 itens, rotular todos é aceitável.
- Rótulo nunca é cortado: se não cabe à esquerda, vai para a direita com a sigla da
  série; se não cabe dentro da barra, vai fora da barra.
- Com 2+ séries, **legenda sempre**; com 1 série, nenhuma (o título nomeia).
- Texto nunca veste a cor da série: valores e rótulos usam os tons de tinta; a
  identidade vem do ponto/retângulo ao lado.
- Todo gráfico tem **tooltip** (hover e foco de teclado, mesmo conteúdo) e um
  **"Ver como tabela"** com os mesmos números. Tooltip complementa; nunca é o único
  acesso ao valor.
- **Filtros em uma linha só**, acima de tudo o que eles escopam, fixada no topo ao
  rolar; nunca dentro de um card. Todo gráfico, tile e tabela abaixo responde ao
  mesmo recorte, e cada card mostra o recorte em uma linha (“Recorte: …”). O que
  está acima da linha de filtros (herói, retrato geral) é nacional e diz isso.
- **Seleção cruzada**: clicar numa barra, num tile de categoria ou numa área do mapa
  aplica o filtro correspondente (e clicar de novo desfaz); o item selecionado
  ganha brilho, os demais ficam a 30% de opacidade. O cursor e o tooltip avisam
  (“clique para filtrar”). Teclado: Enter/Espaço fazem o mesmo.
- Quando um filtro **não se aplica** a um gráfico (ex.: cargo numa comparação
  prefeito × vice), diga isso na legenda do card em vez de esconder o gráfico.
- Filtros operam sobre **agregados embutidos** (um cubo de contagens por dimensão),
  nunca sobre a base bruta; medianas e outras estatísticas não decomponíveis ficam
  nacionais e recebem a etiqueta “não filtra”.
- Textos narrativos descrevem o recorte nacional; ao filtrar, uma etiqueta “Texto:
  recorte nacional” aparece sobre cada parágrafo de leitura.
- **Mapa**: só quando a base traz uma chave geográfica (código IBGE, UF). A base
  não traz geometria: embuta uma malha oficial simplificada (IBGE) no próprio HTML
  e documente a origem; mapa municipal só se o peso e a leitura justificarem.
- Nunca mais de 7 classes de cor com significado. Nunca gere uma 9ª cor: agrupe em
  "Outras" ou faça pequenos múltiplos.

## Paleta de cores

Dois temas, **escuro (padrão)** e **claro**, construídos sobre a mesma paleta
monocromática de cinco azuis (“Beautiful Blues”, color-hex #1294). Tudo o que é dado
usa um desses cinco tons (ou um passo interpolado entre dois deles); só o fundo da
página é derivado. Os temas são definidos como *tokens* CSS em `:root` (escuro) e
`:root[data-theme="light"]` (claro); o código dos gráficos só usa tokens, nunca hex.

Escuro:
- Fundo da página `#010d20` (derivado) · Card `#011f4b` · Card secundário `#03396c`
- Hairline/grade: `#6497b1` a 16–28% · Eixo: `#6497b1` a 50%
- Tinta primária `#f3f7fb` · secundária `#b3cde0` · apagada `#6497b1` · forte `#fff`

Claro (papéis invertidos: o tom mais escuro vira tinta e foco):
- Fundo `#eef4f9` (derivado) · Card `#ffffff` · Card secundário `#b3cde0`
- Hairline/grade: `#03396c` a 10–18% · Eixo: `#03396c` a 35%
- Tinta primária `#011f4b` · secundária `#03396c` · apagada `#005b96` · forte `#011f4b`
- Medida/foco `#005b96` · contexto `#6497b1` · rampa `#8cb2c9 → #011f4b` (validada
  `--ordinal --mode light` sobre `#ffffff`) · identidade `#b3cde0 / #3279a4 / #011f4b`
  (ΔE 27 sob daltonismo; o tom claro fica abaixo de 3:1 e exige contorno + legenda +
  tabela, que são obrigatórios de qualquer modo).

Botão de tema no cabeçalho (☾ Escuro / ☀ Claro), com `aria-pressed`; a escolha é
salva em `localStorage` e, sem escolha salva, segue `prefers-color-scheme`. Um script
curto no `<head>` aplica o tema antes do primeiro paint para não piscar. A impressão
usa sempre os tokens claros.

Rampa sequencial (um matiz, claro = mais; no escuro o menor valor é o mais escuro):
`#005b96 → #3279a4 → #6497b1 → #8cb2c9 → #b3cde0` (dois passos intermediários
interpolados entre tons da paleta). Validada com `validate_palette.js --ordinal`
sobre `#011f4b`: luminosidade monótona, ΔL ≥ 0,06 entre passos, extremidade escura
≥ 2:1 contra a superfície.

Funções:
- **Medida única / foco**: `#b3cde0` (barras, ponto “foco” do dumbbell, linha de
  referência). **Contexto**: `#6497b1` (ponto “antes/população” do dumbbell).
- **Identidade** (3 classes no máximo, só quando indispensável): a paleta é
  monocromática, então a identidade é carregada por **luminosidade** —
  `#005b96`, `#6497b1`, `#b3cde0` — mais contorno fino, legenda com contagens e
  tabela. O validador categórico acusa, por construção, falha de banda e de croma
  (não há matiz para separar); a separação sob daltonismo (ΔE 17,6) e para visão
  normal (ΔE 18,7) passa. O tom mais claro vai para a classe **mais rara ou mais
  importante para a história** (ênfase), nunca para a “maior”; evite que a ordem
  de luminosidade reproduza uma hierarquia social.
- **Divergente**: sem polos quentes/frios disponíveis, a polaridade é dada pela
  direção da barra em torno do zero; o lado da história usa `#b3cde0` e o outro
  `#6497b1`, sempre com legenda. Linha de zero em `#6497b1`.
- **Mapa coroplético**: a rampa sequencial em 5 faixas fixas de 0–100%, legenda
  de rampa, UF sem valor em `#03396c`.
- **“Outras / sem informação”**: `#03396c` com contorno `#6497b1`.
- Status (bom/atenção/grave) não existe nesta paleta; não invente um — use ícone
  e texto.

Se trocar a paleta, substitua apenas este bloco e rode o validador de novo.

## Tipografia e layout

- Sans técnica para tudo, inclusive o número-herói: `"Space Grotesk", system-ui,
  sans-serif`. Monoespaçada só para eyebrows, ticks de eixo, tags e legendas de método:
  `"JetBrains Mono", ui-monospace, monospace`. Fontes via Google Fonts com fallback de
  sistema; sem outra biblioteca externa.
- Números grandes com algarismos proporcionais; `tabular-nums` apenas em colunas de
  tabela e ticks.
- Largura máxima 1080px; grid de 2 colunas para cards irmãos, 1 coluna abaixo de 860px.
- Cards com borda hairline, cantos 10px e dois "ticks" de canto em acento (sugestão de
  HUD). Fundo da página com grade sutil (≤ 3% de branco) e um glow radial no topo.
  Nada de scanlines, animações contínuas ou texturas sobre as marcas.
- Revelação ao rolar com `IntersectionObserver`, desligada em
  `prefers-reduced-motion`. Barra de progresso de leitura no cabeçalho fixo.
- Responsivo: SVGs redesenhados por largura (não só escalados); margens esquerdas
  proporcionais em telas estreitas; sem rolagem horizontal da página.
- Impressão: fundo branco e tinta escura via `@media print`.

## Checklist final

- [ ] A primeira tela já responde à pergunta norteadora com um número.
- [ ] Cada ato tem título-afirmação, gráfico e leitura com números em negrito.
- [ ] Nenhum gráfico com dois eixos; nenhuma pizza; nenhuma barra 3D.
- [ ] Paleta rodou no verificador e passou (ou o WARN foi coberto com rótulo direto).
- [ ] Legenda presente em todo gráfico com 2+ séries; ausente com 1.
- [ ] Rótulos diretos só nos extremos e no foco; nada cortado nem sobreposto.
- [ ] Tooltip no hover e no foco; "Ver como tabela" em todo gráfico.
- [ ] Textos de rótulo inseridos com `textContent`, nunca `innerHTML`.
- [ ] Dados agregados embutidos; o HTML abre com dois cliques e sem rede.
- [ ] Bloco "permite / não permite" e rodapé com fonte, data e método.
- [ ] Filtros numa linha só, acima dos gráficos; cada card mostra o recorte; seleção cruzada com desfazer.
- [ ] Tema claro e escuro conferidos um a um (herói, tiles, waffle, matriz, mapa, tooltip); nenhum hex fixo fora dos tokens.
- [ ] Testado em 1280px e em 390px; sem rolagem horizontal; sem erro no console.
