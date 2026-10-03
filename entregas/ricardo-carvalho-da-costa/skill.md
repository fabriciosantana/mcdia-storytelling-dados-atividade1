---
name: dashboard-narrativo-html
description: Regras de estilo visual, estrutura narrativa e linguagem para construir dashboards em HTML que contam uma história para um público específico. Use sempre que for criar um painel, gráfico, relatório visual ou página de dados, especialmente quando o leitor tem pouco tempo e ninguém para explicar os números.
---

# Dashboard narrativo em HTML

## Quando usar

- Ao criar qualquer dashboard, painel ou página de gráficos em HTML a partir de uma tabela de dados.
- Antes de escolher cores, gráficos ou o texto dos títulos.
- Ao revisar um painel que mostra muitos números mas não diz o que concluir.

## Antes de desenhar

1. Escreva a história em uma frase: "O leitor deve sair sabendo que ___".
2. Defina o público: quanto tempo tem, o que já sabe, o que vai decidir. Ajuste o nível de detalhe e o vocabulário a ele.
3. Liste as 3 a 6 perguntas que a história responde, na ordem em que o leitor as faria.
4. Leia a documentação da base. Anote o que é unidade de contagem, o que significa dado ausente e o que a base **não** permite afirmar.

## Estrutura narrativa

- **Título é o achado, não o assunto.** Escreva "Metade dos pedidos vem de três cidades", não "Pedidos por cidade".
- **Topo:** título, uma frase de contexto e de 4 a 6 indicadores grandes. Quem ler só o topo já deve sair com a mensagem central.
- **Corpo:** uma seção por pergunta, em ordem de interesse. Cada seção tem título-frase com o número principal, uma linha de apoio e um gráfico.
- **Fechamento:** uma caixa "O que os dados mostram e o que não mostram", antes da fonte.
- **Rodapé:** fonte, data da extração e filtros usados.
- Corte o que não responde às perguntas. Menos gráficos, mais claros.

## Escolha de gráficos

- **Comparar categorias:** barras horizontais ordenadas por valor, com rótulo e valor ao lado. Ordene de forma decrescente, exceto categorias com ordem natural (faixas de idade, níveis de escolaridade).
- **Parte de um todo, com poucos grupos (2 ou 3):** barra empilhada de 100% ou "em cada 100" (quadradinhos). Evite pizza com mais de 3 fatias.
- **Um número que resume tudo:** indicador grande, sem gráfico.
- **Evolução no tempo:** linha, com no máximo 4 séries rotuladas direto.
- **Comparar com uma referência:** uma marca fina sobre a barra, com legenda dizendo de onde vem.
- **Evite:** eixo duplo, 3D, barras que não começam em zero, rosca com muitas fatias, rótulo em cima de cada ponto.
- Sempre que possível, ofereça os números em uma tabela dentro de um bloco recolhível.

## Paleta de cores

- Cor tem função, não enfeite. Use neutro por padrão e uma cor de destaque por vez.
- **Destaque principal:** azul `#2a78d6` (escuro: `#3987e5`).
- **Segundo destaque, para um grupo específico:** laranja `#eb6834` (escuro: `#d95926`).
- **Neutro (barras de apoio):** `#b9b7ae` (escuro: `#5c5b55`). **Trilho e grade:** `#ecebe6` (escuro: `#2a2a28`).
- **Fundo:** `#f6f5f2`, **cartão:** `#ffffff`, **texto:** `#14151a`, **texto secundário:** `#52514e` (escuro: fundo `#131312`, cartão `#1c1c1a`, texto `#f2f1ec`).
- Defina tudo como variáveis CSS em `:root` e redefina para o modo escuro com `prefers-color-scheme`.
- Texto nunca usa a cor da série. A cor identifica a barra, o texto fica em tinta neutra.
- Nunca dependa só da cor: o valor sempre aparece escrito.
- Cores de alerta (amarelo-claro) só para a caixa de limites.

## Tipografia e layout

- Fonte do sistema (`system-ui`), sem baixar fontes. Título entre 28 e 46 px (`clamp`), corpo de 15 a 16 px, notas de 13 px.
- Números com `font-variant-numeric: tabular-nums`.
- Largura máxima de 980 px, lateral de 16 px, cartões com borda fina e cantos de 12 a 14 px.
- Duas colunas no computador, uma no celular (quebra em 720 px). Sem rolagem lateral.
- Filtro em linha única, fixo no topo, com botões de pelo menos 36 px de altura e foco visível.
- Barras finas (cerca de 18 px), com a ponta arredondada.
- Respeite `prefers-reduced-motion`.

## Linguagem

- Frases curtas, voz ativa, sem jargão estatístico. Diga "metade" em vez de "mediana" e explique o termo entre parênteses quando precisar dele.
- Arredonde com critério: inteiro para valores acima de 10%, uma casa decimal abaixo disso.
- Diga sempre o denominador ("de 5.537 que declararam").
- Descreva sem julgar: mostre a distância entre grupos sem afirmar causa.

## Rigor com os dados

- Agregue em Python ou similar e embuta no HTML só os números agregados.
- Confira cada número exibido recalculando a partir da fonte.
- Dado ausente não é zero. Diga quantos casos ficaram de fora e por quê.
- Identifique qualquer dado externo à base como referência externa.
- Diga explicitamente o que o dado não permite concluir.

## Checklist final

- [ ] A história cabe em uma frase e o título do topo a entrega.
- [ ] Cada título de seção é um achado com número.
- [ ] Nenhum gráfico responde a uma pergunta que a história não faz.
- [ ] Todo gráfico tem valor escrito, não só cor.
- [ ] Barras partem de zero e os denominadores estão claros.
- [ ] Os limites da base estão visíveis na tela.
- [ ] Os números foram recalculados e batem.
- [ ] Testei em tela larga, em celular (390 px) e em modo escuro, sem erro de console nem rolagem lateral.
- [ ] O arquivo é único, abre com dois cliques e não depende de arquivos locais.
