---
name: painel-narrativo-institucional
description: Regras de narrativa, visualização, cor e linguagem para dashboards em HTML que contam uma história com dados para públicos do setor público e institucional. Use sempre que for criar ou revisar um dashboard, painel, gráfico ou relatório visual em HTML.
---

# Painel narrativo institucional

## Quando usar

- Ao criar ou revisar qualquer dashboard, painel ou relatório visual em HTML, com qualquer base de dados.
- Quando o objetivo for **levar um público específico a uma conclusão ou reflexão**, e não só exibir números.
- Não use para análises exploratórias internas, em que a velocidade importa mais que a narrativa.

## Antes de desenhar: três perguntas

1. **Quem vai ler, e o que essa pessoa já sabe?** Escreva o público em uma frase e não perca isso de vista.
2. **Qual é a mensagem central em uma frase?** Se não couber em uma frase, a história ainda não está pronta.
3. **O que a base permite e o que não permite afirmar?** Liste os limites (recorte, ausências, variáveis declaradas e não auditadas) antes de escrever qualquer título.

## Estrutura narrativa

- **Abra com a mensagem principal** como título do painel. Logo abaixo, um parágrafo de 2 a 3 frases que situa o leitor.
- **Do geral para o particular, e de volta ao leitor:** retrato geral → onde ele varia → como ele se manifesta → quem está por trás → hipóteses → pergunta ou chamada final ligada à realidade do público.
- **Numere os blocos** (1, 2, 3…) com um rótulo curto em caixa alta acima do título. Assim o leitor sabe onde está no percurso.
- **Cada título de bloco é uma conclusão, não um assunto.** Use "O Sul renova mais que o Norte", não "Dados por região". Lendo só os títulos, o leitor deve entender a história.
- **Logo na abertura, coloque um alerta contra a leitura errada mais provável** (caixa com ícone e borda de destaque).
- **Separe fato de hipótese.** Hipóteses ficam em um bloco próprio. Cada uma traz "o que os dados mostram" e "o que os dados não mostram".
- **Feche com perguntas ou próximos passos** para o público, nunca com um gráfico solto.
- **Termine com uma nota de método:** fonte, recorte, definições, exclusões e uma tabela com os dados dos gráficos.

## Escolha de gráficos

| Para mostrar | Use | Evite |
|---|---|---|
| Um número que resume tudo | Número de destaque grande + barra única dividida | Gráfico de pizza, velocímetro |
| Comparar categorias | Barras horizontais **ordenadas por valor** | Barras em ordem alfabética, 3D |
| Comparar com uma referência | Barras + linha tracejada de referência rotulada | Cores diferentes para acima e abaixo sem legenda |
| Comparar duas distribuições | Histograma agrupado, cada grupo normalizado para 100% | Sobrepor contagens absolutas de grupos de tamanhos diferentes |
| Evolução no tempo | Linha com no máximo 4 séries | Barras empilhadas no tempo |
| Pares de valores-chave | Cartões com dois números lado a lado | Tabelas longas no meio da narrativa |

- **Nunca use eixo duplo.** Medidas de escalas diferentes vão em gráficos separados.
- **Eixos de barras começam em zero.** Linhas de grade quase invisíveis. Rótulo do valor no fim de cada barra.
- **Sempre exiba o n** (base de cálculo) no tooltip ou no rodapé. Avise quando um grupo for pequeno e o percentual instável.
- **Rótulos curtos** (siglas ou nomes abreviados), com o nome completo no tooltip.

## Paleta de cores

A cor tem função, não decoração. Até 2 cores de série, cinzas para contexto e 1 cor de destaque.

| Papel | Claro | Escuro | Uso |
|---|---|---|---|
| Série principal | `#2B63B0` | `#2E61B2` | A categoria central da história |
| Série secundária | `#6FA4E6` | `#6497DA` | A categoria em contraste com a principal |
| Destaque | `#E36A1E` | `#E2671F` | Referências, extremos e o que o leitor **precisa** ver. No máximo 1 ou 2 elementos por bloco |
| Texto de destaque | `#B34F10` | `#F29A5E` | Números em laranja (contraste de texto garantido) |
| Fundo destaque | `#FDF0E6` | `#2E2016` | Caixas de alerta e cartões em evidência |
| Texto principal | `#142235` | `#EEF2F7` | Títulos e valores |
| Texto secundário | `#47566B` | `#B9C4D2` | Parágrafos e rótulos |
| Texto auxiliar | `#6B7889` | `#8E9BAB` | Eixos, notas, fontes |
| Marca neutra | `#C3CCD8` | `#3D4A5B` | Barras fora do foco (filtro ativo) |
| Linhas | `#DBE1E9` | `#2B3644` | Bordas e eixos |
| Fundo da página / cartão | `#F3F5F8` / `#FFFFFF` | `#0F141B` / `#18202A` | Superfícies |

- **Uma categoria tem sempre a mesma cor** em todos os gráficos do painel.
- **O laranja nunca vira uma terceira série.** Ele marca exceção ou referência.
- **Texto nunca usa a cor da série.** O valor fica na cor de texto, e a cor aparece em uma amostra (quadradinho) ao lado.
- **Valide toda paleta nova** para daltonismo (protanopia, deuteranopia, tritanopia) e contraste com o fundo, nos dois modos. Se o contraste de uma cor com o fundo ficar abaixo de 3:1, ofereça rótulos diretos e uma tabela.
- **Modo escuro com tons escolhidos para ele**, não uma inversão automática. Ofereça um botão de alternância e respeite `prefers-color-scheme`.

## Tipografia e layout

- Fonte do sistema (`system-ui`). Título do painel com 28 a 44px (`clamp`), títulos de bloco com 21 a 27px, texto com 16 a 17px e notas com 13px.
- Números tabulares (`font-variant-numeric: tabular-nums`) em valores e tabelas.
- Coluna de leitura com até 760px de largura para parágrafos. Largura máxima do painel entre 1000 e 1100px.
- Cada bloco em um cartão com cantos arredondados (12 a 14px), padding generoso e sombra mínima.
- **Responsivo:** teste em 390px e em 1200px. No celular, grades viram 1 ou 2 colunas, rótulos de eixo são reduzidos e nenhum elemento gera rolagem horizontal na página.
- Posicione linhas de referência em unidades proporcionais (CSS `calc` com %), nunca em pixels calculados uma vez só.

## Interação

- **Tooltip em toda marca de dado**, com o rótulo completo, o valor absoluto, o percentual e o n. Precisa funcionar com mouse, toque e teclado (foco).
- **Filtros em uma única linha acima do gráfico**, como botões com `aria-pressed`. Filtrar **destaca e esmaece**; não remove as outras categorias, para preservar a comparação.
- Sem animações longas; respeite `prefers-reduced-motion`.

## Linguagem para o público

- Escreva para quem decide e não para quem analisa: frases curtas, voz ativa, números arredondados no texto (44,5% → "quase metade") e precisos nos gráficos.
- Formato numérico do idioma do público (pt-BR: `44,5%`, `5.553`).
- **Nunca transforme associação em causa.** Use "está associado a", "coincide com", "pode indicar".
- Nomeie limites com honestidade: "a base não permite saber…".
- Evite jargão estatístico ("mediana" pode aparecer, mas acompanhada de uma explicação do que significa).

## Requisitos técnicos

- Um único arquivo HTML. CSS e JS embutidos. Bibliotecas, se houver, só por CDN.
- **Os dados entram já agregados**, como um objeto JSON embutido. O painel nunca lê arquivos locais.
- Faça a agregação em um script separado e reprodutível. Confira os totais (linhas, chaves únicas) com `assert` antes de exportar.
- Inclua `lang`, `viewport`, `title`, `aria-label` nos gráficos e uma tabela de dados em `<details>` como alternativa acessível.

## Checklist final

- [ ] A mensagem central aparece no título e é sustentada por todos os blocos?
- [ ] Lendo só os títulos, a história faz sentido?
- [ ] Todo número no texto confere com o dado agregado?
- [ ] Os limites da base estão explícitos e nenhuma frase afirma uma causa?
- [ ] O laranja aparece só onde precisa?
- [ ] O painel foi aberto e conferido no desktop, no celular e no modo escuro, sem erros no console?
