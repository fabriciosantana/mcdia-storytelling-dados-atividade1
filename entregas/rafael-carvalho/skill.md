---
name: narrativa-publica-com-dados
description: Orienta o Codex a criar dashboards acessíveis e verificáveis para públicos que precisam compreender evidências rapidamente.
---

# Dashboards com narrativa para debate público

## Estrutura narrativa

1. Identificar pergunta, público, unidade de análise, período e recorte antes de escolher gráficos.
2. Começar com uma conclusão sustentada pelos dados. Usar um título descritivo e uma frase que explique a implicação.
3. Organizar o percurso em panorama, comparações, aprofundamento e questões para discussão.
4. Incluir apenas indicadores que ajudem a responder à pergunta. Distinguir observação, interpretação e hipótese.

## Rigor

- Validar chaves, duplicidades, cobertura, unidades e dados ausentes.
- Definir numerador e denominador de cada taxa. Mostrar contagens ao lado de percentuais.
- Calcular proporções agregadas a partir de contagens, evitando médias simples de taxas com denominadores distintos.
- Separar categorias que representam funções ou populações diferentes.
- Declarar exclusões, período de referência, fonte e limitações.
- Não inferir causas, tendências ou probabilidades sem evidência adequada.

## Linguagem e apresentação

- Usar frases curtas e termos familiares ao público, explicando conceitos técnicos indispensáveis.
- Usar uma paleta contida e consistente, com cores neutras no fundo e cores semânticas nos dados.
- Ao comparar homens e mulheres, representar homens em azul-marinho (#171a4a, com #000020 para variações mais escuras) e mulheres em roxo (#4c007d, com #7f00b2 para destaques). Reservar #2f2c79 para transições ou apoio, sem confundir as categorias. Essa associação deve permanecer constante em gráficos, mapas, legendas e indicadores.
- Manter cores consistentes entre gráficos, com rótulos que permitam entender os valores sem depender de cor.
- Usar fonte de sistema no corpo, títulos com hierarquia clara e texto de leitura confortável.
- Priorizar barras para comparar categorias. Partir de zero, manter escalas comuns e expor unidades.
- Ordenar categorias por valor quando isso favorecer a comparação; preservar ordem temporal quando pertinente.
- Evitar elementos tridimensionais, excesso de cores e decoração sem função informativa.

## Análises territoriais e mapas

- Incluir mapa sempre que a análise comparar diferentes cidades ou outros territórios. Usar a unidade geográfica correspondente à pergunta: municípios para cidades, estados ou regiões para agregados territoriais.
- Utilizar malhas de fonte identificada e associar os dados por códigos geográficos, conferindo correspondências e territórios sem dados. Não inventar contornos ou atribuir um agregado a cada cidade como se fosse um resultado municipal.
- Ao comparar homens e mulheres no mapa, usar azul-marinho e roxo conforme a paleta semântica. Para proporções, oferecer mapas comparáveis ou alternância explícita entre as categorias, com intensidades dentro da família de cor correspondente. Não usar roxo apenas para indicar valores acima da média, pois isso pode sugerir maioria feminina inexistente.
- Preferir percentuais a contagens brutas quando o objetivo for comparar a composição de territórios com tamanhos diferentes. Exibir também numerador e denominador na consulta.
- Manter a mesma escala para ambos os gêneros e todos os filtros. Informar o significado das tonalidades e distinguir claramente maior participação relativa de maioria absoluta.
- Usar cinza e uma legenda explícita para ausência de dados ou territórios fora do recorte. Nunca confundir essas situações com zero.
- Permitir consulta por toque, mouse e teclado, com rótulos e tabela equivalentes. Preservar as barras como complemento quando elas ajudarem a comparar valores com precisão.
- Declarar que áreas maiores no mapa não significam maior população, maior número de municípios ou maior peso no indicador.

## Interação e acessibilidade

- Rotular controles e indicar o recorte ativo. Atualizar coerentemente métricas, textos e gráficos.
- Garantir navegação por teclado, foco visível, contraste adequado e estrutura semântica.
- Oferecer contagens em texto ou tabela além dos gráficos.
- Adaptar a leitura a telas pequenas sem reduzir o texto a tamanhos desconfortáveis.
- Usar arquivo autocontido quando a entrega exigir abertura local, incluindo os dados necessários e sem dependências externas.

## Verificação final

- Reconciliar totais com a fonte e conferir cálculos por uma segunda abordagem.
- Testar controles, recortes, casos vazios e arredondamentos.
- Verificar visualmente telas grandes e pequenas, corrigindo cortes e sobreposição.
- Registrar honestamente o processo e as limitações de qualquer teste não realizado.

## Destaques de seleção e pictogramas

- Nos mapas de comparação entre homens e mulheres, o contorno ao passar o mouse, selecionar ou focar um território deve acompanhar o gênero visualizado: roxo #7f00b2 para mulheres e azul-escuro #000020 para homens.

- Ao selecionar um território em mapas comparativos de gênero, preencher sua área com roxo para mulheres ou azul-escuro para homens e reduzir os demais a 50% de opacidade no modo mulheres e 30% no modo homens. O segundo clique no território deve limpar a seleção, além de oferecer um botão de limpeza. Para alternar entre apenas duas categorias, preferir botões com indicação explícita do estado ativo e suporte a teclado. Explicar que o preenchimento sólido indica seleção e não valor máximo da escala.

- Para comunicar proporções, usar uma grade ilustrativa de 100 pictogramas quando isso ajudar o público. Destacar a quantidade equivalente ao percentual e preencher parcialmente o último ícone para a casa decimal. Mostrar também o percentual e a contagem reais. Explicitar a unidade representada, sem sugerir que os ícones são indivíduos da base.
- Territórios sem dado podem receber destaque de seleção, mas devem manter uma mensagem clara de indisponibilidade e nunca receber um percentual inventado.

- Em pictogramas pequenos, aumentar a diferença de luminosidade entre as cores das categorias: roxo vivo #a600d9 para mulheres e azul-marinho moderadamente claro #303b68 para homens. Quando várias grades usam o mesmo princípio, reunir a explicação em uma nota compartilhada, explicitando as diferentes unidades.
