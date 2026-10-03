---
name: dashboard-editorial-de-dados
description: Regras de design de informação, storytelling e interação para construir dashboards editoriais em um único arquivo HTML, que contam uma história com dados e deixam o leitor comparar o próprio recorte com o todo. Use sempre que for criar ou redesenhar um painel, especial de dados, relatório visual ou gráfico para público não especialista.
---

# Dashboard editorial de dados

## Quando usar

- Ao transformar uma base de dados em um painel HTML que precisa comunicar uma mensagem e permitir comparação entre recortes (todo → grupo → subgrupo → item).
- Ao redesenhar um painel que parece template, landing page, sistema corporativo ou "interface gerada automaticamente".
- Não use para painéis operacionais de monitoramento em tempo real, em que densidade importa mais que narrativa.

## Postura

- A visualização e a narrativa são o produto; o frontend é só o meio.
- O resultado deve parecer feito por jornalista de dados + designer de informação + analista + desenvolvedor de visualização, não por um gerador de interfaces.
- Entre efeito visual e clareza analítica, escolha clareza. Entre mais informação e melhor história, escolha a história.

## Antes de desenhar

1. Leia o dicionário de dados e a documentação da base.
2. Defina a unidade de análise e confira que nenhuma entidade é contada duas vezes. Registre as contagens de controle (total, únicos, soma das partes = todo).
3. Liste ausentes por coluna. Célula vazia nunca vira zero. Procure também **zeros suspeitos** (valores que deveriam ser positivos), que costumam indicar registros anulados ou inválidos. Exclua-os da análise afetada e diga isso no painel.
4. Escreva a definição operacional de cada categoria em uma frase, e outra frase sobre o que ela **não** mede.
5. Explore antes de escolher a história. Teste hipóteses que podem "não dar nada": uma ausência de diferença bem mostrada é um achado.
6. Escreva a mensagem central em até 2 frases com números.

## Arquitetura narrativa

- Organize por **pergunta → evidência → descoberta → nova pergunta**, nunca por "gráfico 1, gráfico 2".
- Arco: **início** (o quadro geral) → **tensão** (o número geral esconde diferenças) → **exploração** (onde estão as diferenças; onde estou eu) → **aprofundamento** (uma segunda dimensão, só se trouxer insight genuíno) → **resolução** (o que isso significa para o público) → **método**.
- Cada seção contém: (1) uma pergunta ou afirmação; (2) **uma** visualização dominante; (3) no máximo **um** elemento auxiliar; (4) uma conclusão curta.
- O estado inicial (sem seleção) conta a história inteira. A interação aprofunda, nunca é pré-requisito. Nunca abra com um painel vazio esperando escolha.
- A abertura tem só: sobrelinha, título com a descoberta, linha fina de 2 linhas, fonte curta e um fio. Sem KPIs, botões, ícones ou gráficos.
- Feche com uma frase forte e descritiva, mais 2 ou 3 observações em texto corrido. Não prescreva ação nem julgue o fenômeno.

## Títulos e textos

- **Teste da narrativa:** leia só o título principal, os títulos das seções e os títulos dos gráficos. Eles devem formar um resumo coerente. Se parecerem "Visão geral / Por região / Indicadores", reescreva.
- O título de seção afirma; o título do gráfico diz o achado; o subtítulo explica como ler; os eixos só informam a medida; as anotações explicam exceções. Não repita a mesma informação em título, subtítulo, legenda e tooltip.
- Ruim: "Distribuição por região". Bom: "Uma região concentra metade dos casos com 20% da população".
- Use linguagem descritiva e neutra: "a proporção observada é maior", "os dados mostram", "aparece associado a". Proibido "porque", "causa", "leva a" sem desenho causal. Em temas sensíveis, evite também "melhor", "pior", "sucesso", "fracasso", "domínio", "vitória".
- Textos curtos: linha fina de até 2 frases; conclusão de até 3.
- Textos dinâmicos se reescrevem com o recorte selecionado, com gramática correta (preposições e concordância), e usam só valores calculados.

## Grade e diagramação

- Grade de 12 colunas, largura útil de 1.180 a 1.280 px, alinhamento à esquerda.
- Três larguras: **narrow** (~7 colunas) para texto, **standard** (~9) para gráficos comparativos e **wide** (12) para a visualização principal. Anotações vão na margem (colunas 10–12). Nem tudo tem a mesma largura.
- Ritmo vertical: 96 a 128 px entre capítulos; cada capítulo abre com um fio fino e uma sobrelinha. A mudança de assunto deve ser percebida antes da leitura.
- Gráficos ficam direto na página, sem caixa. Containers só quando a separação semântica exigir.
- No celular, **recomponha**: margem vira bloco abaixo do gráfico, rótulos longos sobem para cima da linha, nomes longos viram siglas.

## Escolha de gráficos

| Pergunta | Use | Evite |
| --- | --- | --- |
| Parte → todo | barra 100% empilhada, larga, com rótulos diretos | pizza com muitas fatias, rosca decorativa |
| Comparar grupos num mesmo indicador | barras 100% alinhadas, ordenadas, com linha da referência | barras com eixos diferentes lado a lado |
| Posição de muitos itens em relação à média | barras divergentes a partir da referência (zero = média) | mapa quando a geografia não acrescenta |
| Recorte × referência em várias faixas | dumbbell (● recorte, ○ referência) | dois gráficos separados |
| Distribuição de dois grupos | histograma espelhado com medianas anotadas | média isolada, boxplot sem explicação para leigos |
| Fluxo real entre estados | Sankey | Sankey sem fluxo; radar; gauge; treemap sem hierarquia; 3D |

- **Teste do gráfico:** escreva PERGUNTA, EVIDÊNCIA e INSIGHT. Se um dos três não ficar claro, o gráfico não entra.
- Barras e áreas começam no zero. Não trunque escalas para dramatizar. Se a diferença em relação a uma referência é o ponto, faça a referência ser o zero.
- Ordene pelo valor, salvo quando há ordem natural (faixas, tempo).
- Mostre o n de cada grupo. Sinalize grupos pequenos com marca vazada ou esmaecida, e explique na anotação.
- Mapa só se a posição geográfica revelar algo. Se usar, mantenha também a versão ordenada.

## Anotação, eixos e grade

- Anote o achado diretamente no gráfico (linha + ponto + texto curto) ou na margem, alinhado a ele. Prefira rótulo direto a legenda.
- O gráfico deve ser compreensível sem tooltip.
- Linhas de grade finas e claras; eixos mínimos; nenhuma moldura em volta do gráfico.

## Cor

- A cor codifica significado, nunca decoração. **Teste da cor:** para cada cor, responda "que informação ela codifica?". "Combina" ou "dá destaque" não é resposta.
- Duas cores semânticas para as duas categorias centrais, com peso visual semelhante, e neutros para todo o resto.
- Paleta base (troque as duas cores de dados conforme o tema):
  - Categoria A: `#355C7D` (azul ardósia).
  - Categoria B: `#C9793A` (ocre); em texto, use `#9A5620` (contraste ≥ 4,5:1).
  - Texto `#20252B`; secundário `#66717D`; grade `#DCE1E5`; fundo `#F7F6F2`; superfície `#FFFFFF`.
  - Contexto não selecionado: `#AEB5BC` e `#DADDE1`.
- Não use pares com juízo de valor (verde = bom, vermelho = ruim) quando as categorias não forem boas ou ruins. Não use cores associadas a partidos, times ou marcas.
- A mesma cor significa a mesma coisa em todos os gráficos. Nunca reaproveite uma cor semântica para outra variável.
- Destaque = **contexto em neutro + objeto em cor**. Ao selecionar, os demais itens ficam cinza; o selecionado mantém a cor e ganha peso (negrito, sublinhado, espessura). Não introduza uma cor nova para seleção.
- Contraste: texto ≥ 4,5:1; marcas gráficas ≥ 3:1. Nada só por cor: sempre há rótulo, posição ou forma.

## Tipografia

- No máximo duas famílias, por exemplo uma serifada para títulos e texto corrido e uma sem serifa para gráficos e controles, sempre com fallback do sistema.
- Escala: sobrelinha 12–13 px (caixa alta, tracking moderado); título principal 44–58 px; linha fina 20–24 px; título de seção 28–36 px; título de gráfico 18–24 px; corpo 16–18 px; anotações 13–15 px; fonte/método 12–13 px. Nada abaixo de 12 px.
- Pouco negrito, nada de tudo em caixa alta, nada de centralizar por padrão, nada de monoespaçada decorativa.
- `font-variant-numeric: tabular-nums` em colunas de valores. Linhas de ~65–75 caracteres.

## Interação: coordenação

- Um **estado global** (todo → grupo → subgrupo) atualiza ao mesmo tempo títulos dinâmicos, números, destaques, comparações e textos. Nada de filtros soltos que mudam um gráfico só.
- **Teste da interação:** "que nova pergunta o leitor consegue responder com isso?". Se nenhuma, remova.
- Selecione em mais de um lugar: clique direto no gráfico, controle segmentado textual e um select compacto. Se fizer sentido, inclua uma busca de item que leve ao recorte que o contém.
- Mantenha sempre a referência geral visível e mostre "recorte × referência" com a diferença em p.p.
- Uma faixa de contexto fixa e discreta aparece **só** quando há seleção, com o recorte, o valor, a referência e "voltar ao geral". Use fundo sólido e fio fino, sem desfoque.
- Tooltip responde "o que estou vendo?": nome, valor de cada categoria, diferença para a referência e n. Funciona com mouse e foco por teclado. Nada essencial pode depender de hover (toque não tem hover).
- Animação só para explicar mudança de estado: 200–400 ms, só posição, largura, altura e opacidade. Sem bounce, elastic ou spin. Respeite `prefers-reduced-motion`.
- Estados vazios ou com poucos casos recebem frase explícita, nunca "NaN", "undefined" ou gráfico em branco.

## Proibido (anti "vibe coding")

- Glassmorphism, `backdrop-filter`, gradientes decorativos, neon, glow, sombras pesadas, fundos roxo/azul "estilo IA", blobs, partículas.
- Cards como estrutura principal, card dentro de card, bordas muito arredondadas, KPIs em quadrados iguais, grids estilo Bootstrap/Tailwind.
- Pills e badges em excesso, ícones ou emojis decorativos, texto com gradiente, números gigantes só para ocupar espaço, barras de progresso decorativas, gauges, velocímetros, 3D.
- **Teste da subtração:** para cada elemento, pergunte "se eu remover, a compreensão piora?". Se não piora, remova.

## Números

- Formate no padrão do público (ex.: `5.553`, `44,5%`, `+6,2 p.p.`) com `toLocaleString`.
- Uma casa decimal em percentuais; diferenças em p.p. com sinal, calculadas a partir dos valores arredondados exibidos, para o leitor conseguir refazer a conta.
- Calcule percentuais a partir das contagens no momento da exibição. Derive níveis superiores somando os inferiores, para que todos os gráficos batam.
- Mostre a contagem absoluta ao menos uma vez por seção.

## Acessibilidade e responsividade

- Use elementos nativos (`button`, `select`, `input`, `label`), foco visível, `aria-label` com valores nos gráficos, `aria-pressed` em seleções e `aria-live` nas regiões que mudam.
- Teste em 320, 375, 768, 1.024 e 1.280+ px: sem rolagem horizontal, sem rótulo cortado, texto ≥ 12 px.
- Gráficos em HTML/CSS com posições em %, ou SVG com `viewBox`, que se ajustam sem redesenho.

## Dados no arquivo

- Um único `.html` autocontido: CSS e JS embutidos; bibliotecas e fontes só por CDN, e só se agregarem valor.
- Agregue antes, com um script à parte, e embuta só o necessário. Nada de `fetch` de arquivos locais. Nada de dados pessoais que a história não usa.
- Gere o HTML a partir de um template + dados, para poder regerar sem editar números à mão.

## Checklist final

- [ ] A mensagem central está no título, com números, e o teste da narrativa passa.
- [ ] Cada seção tem uma visualização dominante, no máximo um auxiliar e uma conclusão curta.
- [ ] Teste do gráfico (pergunta, evidência, insight) passa em todos os gráficos.
- [ ] Teste da cor: cada cor tem significado único e constante.
- [ ] Teste da interação: cada controle responde a uma pergunta nova; o estado inicial conta a história sozinho.
- [ ] Teste da subtração aplicado; nenhum item da lista "Proibido" presente.
- [ ] Contagens de controle conferidas e números validados por script contra a base.
- [ ] Ausentes, zeros suspeitos e exclusões declarados perto do gráfico afetado e no método.
- [ ] Nenhuma frase causal ou valorativa.
- [ ] Seleção, reset, busca e tooltips testados; nenhum NaN em nenhum recorte.
- [ ] Console sem erros; abre direto do disco, sem servidor.
- [ ] Sem rolagem horizontal de 320 px em diante; contraste conferido; acentos corretos (UTF-8).
- [ ] Seção de método com fonte, unidade, filtros, definições, ausentes e limitações.
