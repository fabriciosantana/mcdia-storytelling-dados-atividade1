---
name: dashboard-narrativo-html
description: Regras de estrutura narrativa, estilo visual, animação e linguagem para construir dashboards executivos em HTML que contam uma história para um público específico. Use sempre que for criar um painel, gráfico, relatório visual ou página de dados, especialmente quando o leitor tem pouco tempo, vai decidir algo a partir dali e não tem ninguém para explicar os números.
---

# Dashboard narrativo em HTML

## Quando usar

- Ao criar qualquer dashboard, painel ou página de gráficos em HTML a partir de uma tabela de dados.
- Antes de escolher cores, gráficos ou o texto dos títulos.
- Ao revisar um painel que mostra muitos números mas não diz o que concluir.
- Ao adaptar um painel existente para um público novo.

## Antes de desenhar

1. Escreva a história em uma frase: "O leitor deve sair sabendo que ___".
2. Defina o público: quanto tempo tem, o que já sabe, o que vai decidir. Ajuste o nível de detalhe e o vocabulário a ele. Trocar o público é refazer a narrativa, não trocar a paleta.
3. Liste as 3 a 6 perguntas que a história responde, na ordem em que o leitor as faria.
4. Leia a documentação da base. Anote o que é unidade de contagem, o que significa dado ausente e o que a base **não** permite afirmar.
5. **Confronte a estrutura pedida com o que a base tem.** Antes de montar as seções, verifique se existem série temporal, meta, grupo de controle e medida de resultado. O que não existir não vira seção.

## Estrutura narrativa executiva

Para um leitor que vai decidir, use esta ordem:

1. **Cabeçalho:** título que é o achado, mais período analisado, unidade de contagem e data de extração. O leitor precisa saber "de quando é isso" antes de perguntar.
2. **Resumo executivo:** uma caixa destacada com a mensagem principal em 2 ou 3 frases. Quem ler só isso já sai com a conclusão e com o aviso do que a base não cobre.
3. **Indicadores essenciais:** de 4 a 6 cards. Cada um traz valor, rótulo, **unidade e período**, e uma **linha de comparação** quando houver uma legítima.
4. **Comparações disponíveis:** evolução no tempo e desempenho contra meta, se existirem. Se não existirem, use a melhor comparação que a base oferece (contra uma referência externa identificada, ou entre os recortes da própria base) e diga qual é.
5. **O que explica a diferença:** mostre onde os valores variam e onde não variam, quantificando a amplitude. Descreva o contraste; não afirme a causa.
6. **Pontos de atenção:** cada um é um número com a sua leitura direta. Marque o que é distância entre grupos e o que é contraste entre duas medidas.
7. **Fechamento:** "O que estes dados não respondem", antes da fonte.
8. **Rodapé:** fonte, data da extração, recorte e unidade.

Corte o que não responde às perguntas. Menos gráficos, mais claros.

### Seções que a base não sustenta

- Nunca preencha uma seção pedida com valor inventado, meta estimada, projeção ou comparação fabricada.
- Quando faltar o dado, **substitua a seção pela comparação legítima mais próxima** e diga na tela por que a troca aconteceu.
- Recomendação só é permitida quando a base mede resultado. Se ela só descreve, troque "Recomendações" por "O que estes dados não respondem" e aponte qual base seria necessária para decidir.
- Um painel que mostra onde o dado acaba é mais confiável que um que preenche o vazio.

## Títulos e afirmações

- **Título é o achado, não o assunto.** Escreva "Metade dos pedidos vem de três cidades", não "Pedidos por cidade".
- Cada seção tem um título-frase com o número principal.
- **Não fixe no texto qual categoria é a maior.** Apure a categoria majoritária do recorte em exibição: ela muda quando o filtro muda, e um texto fixo vira afirmação falsa.
- Quando as duas primeiras categorias estiverem a menos de 1,5 ponto percentual, trate como empate e diga "em proporções praticamente iguais", em vez de eleger uma vencedora.

## Escolha de gráficos

- **Comparar categorias:** barras horizontais ordenadas por valor, com rótulo e valor ao lado. Ordem decrescente, exceto em categorias com ordem natural (faixas de idade, níveis de escolaridade).
- **Comparar dois valores por categoria (observado x referência):** gráfico de distância (dumbbell) — dois pontos ligados por uma linha, com a diferença escrita ao lado. Mostra a distância melhor que duas barras lado a lado.
- **Parte de um todo, com poucos grupos (2 ou 3):** barra empilhada de 100% ou **"em cada 100"**: cem figuras iguais que a pessoa consegue contar sem saber ler percentual. É a melhor escolha quando o público pode não ter familiaridade com gráficos. Use figuras de tamanho idêntico, distinga os grupos só por **cor abstrata** — nunca por tom de pele, formato ou qualquer traço que carregue estereótipo — e diga na tela que o número é arredondado. Evite pizza com mais de 3 fatias.
- **Observado contra uma referência, para público amplo:** duas barras empilhadas uma sobre a outra, **com os dois percentuais escritos na própria linha** e uma frase curta dizendo o tamanho da diferença. Não dependa de legenda distante nem de passar o mouse: informação essencial não pode exigir interação.
- **Um número que resume tudo:** indicador grande, sem gráfico.
- **Evolução no tempo:** linha, com no máximo 4 séries rotuladas direto. Só use se houver mais de um período na base.
- **Comparar o mesmo indicador entre recortes:** pequenos múltiplos, um painel por indicador, sempre com os mesmos recortes e com a **amplitude** (maior menos menor) escrita no painel. É o que transforma "varia conforme o recorte" em um número.
- **Evite:** eixo duplo, 3D, barras que não começam em zero, rosca com muitas fatias, rótulo em cima de cada ponto.
- Ofereça os números em uma tabela dentro de um bloco recolhível.

## Paleta de cores

- Cor tem função, não enfeite. Use neutro por padrão e uma cor de destaque por vez.
- **Base institucional:** azul escuro na faixa do cabeçalho, azul médio como destaque principal, cinza-azulado como neutro de apoio, branco e cinzas muito claros no fundo.
- **Segundo destaque, para um grupo específico ou para o item selecionado:** laranja. Nunca use laranja sem critério: ele marca uma coisa por vez.
- Defina tudo como variáveis CSS em `:root` e redefina para o modo escuro com `prefers-color-scheme`, **inclusive as cores que não são texto nem fundo** (faixa, tooltip, pílulas). Uma cor fixa no CSS quebra um dos dois modos.
- Texto nunca usa a cor da série. A cor identifica a marca, o texto fica em tinta neutra.
- Nunca dependa só da cor: o valor sempre aparece escrito.
- Cores de alerta (amarelo-claro) só para a caixa de limites.

## Tipografia e layout

- Fonte do sistema (`system-ui`), sem baixar fontes. Título entre 25 e 40 px (`clamp`), corpo de 16 px, notas de 12,5 a 13 px. Nada abaixo de 12 px: o painel pode ser projetado.
- Números com `font-variant-numeric: tabular-nums`.
- Largura máxima de 1180 px para projeção, lateral de 24 px, cartões com borda fina, cantos de 10 px e sombra sutil.
- **Grades de cartões com número fixo de colunas por faixa de largura, não `auto-fit`.** Com `auto-fit`, 6 cartões viram 5 + 1 órfão. Defina as colunas de forma que a última linha nunca fique com um cartão sozinho.
- Filtro fixo no topo, com botões de pelo menos 36 px de altura e foco visível.
- Barras finas (cerca de 18 px). Sem rolagem lateral em nenhuma largura.

## Animação

- Anime só a entrada e a troca de filtro. **Nunca em loop.**
- Duração entre 400 e 800 ms, com aceleração suave. Escalone marcas irmãs em 40 a 60 ms, com teto de uns 350 ms: o conjunto inteiro termina rápido.
- Prefira `transform` (`scaleX`, `translate`, `opacity`) a animar largura ou posição: é mais suave e não recalcula o leiaute.
- Contagem crescente nos indicadores **termina sempre no valor exato formatado**. Animar nunca muda precisão, unidade nem valor final.
- **Ao trocar um filtro, o número transita do valor anterior para o novo**, não de zero. Reiniciar em zero a cada clique esconde justamente o que o usuário quer ver: o tamanho da mudança.
- Guarde o valor final em um atributo e **congele todos os números antes de imprimir**: a impressão não espera a animação terminar e capturaria um valor intermediário, que sai errado no papel.
- Respeite `prefers-reduced-motion: reduce`: todo o conteúdo aparece no estado final, imediatamente. Teste nesse modo — o painel tem que ficar legível sem nenhuma animação.

## Comparações: a regra que mais se erra

- **Nunca compare um subconjunto com a referência do conjunto inteiro.** Se a referência externa é do todo, a comparação é do todo. Comparar um recorte contra ela produz uma leitura falsa, mesmo que os dois números estejam certos.
- Para comparar um recorte, use o **mesmo indicador** entre o recorte e o conjunto, ou uma referência do mesmo nível, se existir.
- Aplique essa regra em **todos** os lugares, não só no gráfico principal: cartões de destaque, títulos e textos de resumo erram com a mesma facilidade e são menos revisados.
- Antes de ligar um filtro, percorra cada visualização e classifique: acompanha o recorte, ou é fixa? Depois verifique se o dado permite que a fixa passe a acompanhar — muitas vezes permite, e isso é melhor que um aviso.

## Interação

- Ofereça filtro só para dimensões que existem na base.
- Um filtro atualiza **tudo** que depende dele: cards, gráficos, títulos e textos de resumo.
- **Toda visualização que não acompanha o filtro recebe um selo visível** dizendo isso, junto ao gráfico. Não basta mencionar em nota de rodapé, e nunca afirme que o painel inteiro acompanha a seleção.
- **Cada visualização declara o próprio recorte e o próprio denominador**, com os casos sem informação contados à parte.
- Mostre o filtro ativo em texto e ofereça um botão de limpar, desabilitado quando nada estiver filtrado.
- Trate o recorte sem registros com uma mensagem própria, não com gráficos vazios.
- Ofereça **tema claro e escuro manuais**, mantendo a identidade nos dois, e um **modo apresentação** com fontes maiores e menos texto por tela, para projeção.
- Tooltip com rótulo, valor absoluto, denominador e percentual, formatados no idioma do leitor.
- Tudo que o mouse alcança, o teclado também: marcas focáveis, rótulo acessível com o valor, dica que aparece no foco. Estados de foco sempre visíveis.
- Não crie botão ou controle sem função.

## Impressão

- Esconda filtros e controles, e **imprima o recorte aplicado como texto** — a folha não tem estado.
- Fundo branco, sem sombra, cartões inteiros sem quebra no meio (`break-inside: avoid`), mas **sem travar a quebra de seções inteiras**, senão sobra meia página em branco.
- Abra os blocos recolhíveis antes de imprimir e garanta que os gráficos apareçam completos.

## Linguagem

- Frases curtas, voz ativa, sem jargão estatístico. Diga "metade" em vez de "mediana" e explique o termo entre parênteses quando precisar dele.
- Formate números, datas, percentuais e moeda no padrão local do leitor.
- Use uma casa decimal nos percentuais e mantenha a mesma precisão no painel inteiro. Misturar "87%" e "86,8%" na mesma tela parece erro.
- Diga sempre o denominador ("de 5.537 que declararam").
- Descreva sem julgar: mostre a distância entre grupos sem afirmar causa.

## Rigor com os dados

- Agregue em Python ou similar e embuta no HTML só os números agregados.
- **Confira cada número exibido recalculando a partir da fonte**, e compare de forma automatizada, não a olho.
- Dado ausente não é zero. Diga quantos casos ficaram de fora e por quê.
- Identifique qualquer dado externo à base como referência externa, e **não aplique uma referência de um nível a um recorte de outro** (uma média do conjunto todo não serve de parâmetro para um subconjunto isolado).
- Diga explicitamente o que o dado não permite concluir.
- Não use logotipo, nome ou identidade visual de instituição real, nem apresente o painel como sistema oficial, a menos que ele seja de fato daquela instituição.

## Checklist final

- [ ] A história cabe em uma frase e o título do topo a entrega.
- [ ] Cada título de seção é um achado com número.
- [ ] Nenhuma seção foi preenchida com dado que a base não tem.
- [ ] Nenhum texto fixa uma categoria que muda com o filtro.
- [ ] Nenhuma comparação põe um recorte contra a referência do conjunto inteiro — inclusive nos cartões e títulos.
- [ ] Toda visualização fixa tem selo visível, e nenhuma frase afirma que o painel inteiro acompanha o filtro.
- [ ] Toda visualização mostra o seu recorte e o seu denominador.
- [ ] A concordância dos textos gerados foi conferida em todos os recortes, não só no padrão.
- [ ] Nenhum gráfico responde a uma pergunta que a história não faz.
- [ ] Todo gráfico tem valor escrito, não só cor.
- [ ] Barras partem de zero e os denominadores estão claros.
- [ ] O filtro atualiza tudo que depende dele, e o que não é filtrável está marcado.
- [ ] As animações terminam no valor exato e somem com `prefers-reduced-motion`.
- [ ] Tudo que o mouse alcança, o teclado também alcança.
- [ ] Os limites da base estão visíveis na tela.
- [ ] Os números foram recalculados contra a fonte e batem.
- [ ] Testei em tela larga, em projetor, em celular (390 px) e em modo escuro, sem erro de console nem rolagem lateral.
- [ ] Testei a pré-visualização de impressão.
- [ ] O arquivo é único, abre com dois cliques e não depende de arquivos locais.
