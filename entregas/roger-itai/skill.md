---
name: dashboard-narrativo
description: Regras visuais e narrativas para dashboards em HTML que contam uma história com dados. Use sempre que for criar um gráfico, painel ou relatório visual, ou revisar um que já existe.
---

# Dashboard narrativo

Um dashboard não é um painel de números: é um argumento. Cada bloco responde a uma pergunta, e a ordem dos blocos leva o leitor de uma mensagem a uma ação.

## Quando usar

- Ao criar um dashboard, painel, relatório visual ou gráfico isolado em HTML.
- Ao revisar um painel que mostra muitos números e pouca mensagem.
- Quando o público é leigo ou tem pouco tempo para decidir se continua lendo.

## Antes de desenhar

1. Escreva a mensagem central em **uma frase**. Se não couber, o painel ainda não tem história.
2. Defina o público e o tempo que ele tem. Quem decide em 10 segundos precisa da conclusão no topo.
3. Liste as perguntas que o painel responde, na ordem em que a história as apresenta.
4. Leia a documentação da base (dicionário, notas de método) e registre os cuidados de leitura: unidade de contagem, valores vazios, período coberto, duplicidades.

## Estrutura narrativa

- **Abertura:** a mensagem principal como título, em linguagem afirmativa ("Mulheres são 13% dos prefeitos"), não descritiva ("Prefeitos por gênero"). Logo abaixo, 3 a 4 números-âncora em cartões.
- **Desenvolvimento:** um bloco por pergunta, do panorama para o detalhe. Cada bloco tem um título que diz a conclusão e uma frase de contexto.
- **Contraste:** compare sempre com uma referência (população, meta, período anterior). Um número sozinho não diz nada.
- **Fecho:** um convite à ação ou à exploração (busca, filtro, recorte pessoal) ou a conclusão que o leitor leva.
- **Aviso de método:** um parágrafo curto e visível com fonte, período e limites dos dados. Não esconda no rodapé.
- Descreva o que os dados mostram; não afirme causas que eles não provam.

## Escolha de gráficos

- **Comparar categorias:** barras horizontais ordenadas do maior para o menor, com rótulo de valor. Rótulos longos pedem barras horizontais.
- **Evolução no tempo:** linha. Poucos pontos (até 5): colunas.
- **Composição de um todo:** barra empilhada a 100% ou um único número em destaque. Evite pizza com mais de 3 fatias.
- **Distribuição:** histograma ou faixas (percentis), com a mediana marcada.
- **Geografia:** mapa coroplético só quando a localização é a mensagem. Use escala sequencial de uma cor e legenda. Caso contrário, prefira barras ordenadas.
- **Dois grupos lado a lado** (ex.: observado × referência): barras agrupadas com as mesmas cores em todo o painel.
- **Detalhe:** tabela com busca, no máximo 7 colunas.
- Evite: 3D, eixo duplo, gráficos de área sobrepostos, rosca com muitas categorias, barras com eixo que não começa em zero.

## Paleta de cores

- **Destaque (o foco da história):** `#1351B4`.
- **Referência/neutro:** `#8A94A6`.
- **Texto principal:** `#1F2937`; **texto secundário:** `#6B7280`.
- **Fundo:** `#FFFFFF`; **superfície/cartões:** `#F4F6FA`; **linhas e grades:** `#E3E7EE`.
- **Alerta/negativo (uso raro):** `#C0392B`.
- Regras: cada cor tem **um** significado e não muda entre gráficos. No máximo 5 cores por gráfico. Não use cor como única forma de informação: combine com rótulo, posição ou padrão. Contraste mínimo de 4,5:1 para texto. Use escalas sequenciais de uma cor para intensidade, não arco-íris.

## Tipografia e layout

- Fonte sem serifa legível (`system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`); no máximo 2 pesos.
- Escala: título principal 28–36 px; títulos de bloco 20–24 px; texto 16 px; notas 13–14 px.
- Largura máxima de leitura de 1100 px, centralizado; espaçamento generoso entre blocos.
- Responsivo: grade que passa de várias colunas para uma em telas estreitas (`@media (max-width: 720px)`). Gráficos redimensionam com a janela.
- Cartões de número: valor grande, rótulo curto embaixo e a unidade explícita.
- Tooltips mostram valor e denominador. Eixos com rótulos legíveis e sem poluição de grades.

## Dados e arquivo

- Entregue **um único HTML autocontido**: CSS e JS embutidos, ou bibliotecas por CDN. Não leia arquivos locais; embuta os dados já agregados.
- Agregue antes de embutir: o HTML leva só o que os gráficos usam.
- Indique sempre o denominador ("% dos 5.000 que informaram") e trate valores vazios como indisponíveis, nunca como zero.
- Formate números no padrão do público (separador de milhar, vírgula decimal, percentuais com uma casa).
- Inclua `<title>`, `lang` e `meta viewport`. Dê `aria-label` ou texto alternativo aos gráficos.

## Checklist final

- [ ] A mensagem central aparece no topo, em uma frase.
- [ ] Cada título de bloco diz a conclusão, não só o assunto.
- [ ] Cada gráfico tem referência de comparação e denominador explícito.
- [ ] Os tipos de gráfico combinam com a pergunta e nenhum eixo distorce a escala.
- [ ] Cada cor tem um único significado em todo o painel.
- [ ] O aviso de método (fonte, período, limites) está visível.
- [ ] Nenhuma afirmação causal sem evidência.
- [ ] Funciona em tela estreita e em tela larga.
- [ ] O arquivo abre com dois cliques, sem erros no console e sem depender de outros arquivos.
