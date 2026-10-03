---
name: dashboard-narrativo
description: Regras de narrativa, escolha de gráficos, cor, tipografia e acessibilidade para dashboards em HTML que contam uma história com dados. Use sempre que for criar um dashboard, painel, gráfico ou peça visual de dados para um público não especialista.
---

# Dashboard narrativo

## Quando usar

- Sempre que o pedido for um dashboard, painel, infográfico ou relatório visual em HTML.
- Principalmente quando o público é amplo (leitores, gestores, cidadãos) e não domina a base de dados.
- Não use para análises exploratórias internas, em que velocidade importa mais que narrativa.

## Estrutura narrativa

- **Abra com a conclusão.** O título é uma manchete que afirma o achado principal em uma frase ("X concentra três quartos de Y"), e não o tema ("Análise de Y").
- Logo abaixo, um **linha fina** de 1 a 2 frases com o contexto mínimo: o que é a base, de quando é, qual a pergunta.
- Em seguida, **3 a 4 números-chave** (cartões grandes) que resumem a história antes de qualquer gráfico.
- Organize o corpo em **capítulos numerados**, do mais esperado ao mais revelador: primeiro o que o leitor já imagina, depois o que contraria ou aprofunda essa expectativa.
- Cada capítulo tem: título que afirma o achado, 1 a 3 frases de texto explicando o que olhar, um gráfico e, se necessário, uma nota curta.
- **Feche com uma conclusão explícita**, chamada "O que isso significa", ligando os capítulos e respondendo à pergunta inicial.
- Termine com rodapé: fonte, data dos dados, notas metodológicas e limitações.
- Explique todo termo técnico na primeira vez em que aparece, em uma frase simples.

## Escolha de gráficos

- **Ranking / comparação de categorias:** barras horizontais, ordenadas do maior para o menor, com rótulo do valor na ponta.
- **Comparar duas medidas da mesma categoria** (ex.: participação em A × participação em B): barras pareadas ou gráfico de halteres (dois pontos ligados por uma linha). Nunca use dois eixos Y.
- **Distribuição de uma quantidade:** histograma (colunas com espaço mínimo entre si).
- **Duas dimensões categóricas cruzadas:** tabela de calor (matriz) com uma única cor em gradiente claro → escuro e o valor escrito na célula.
- **Evolução no tempo:** linha. **Parte de um todo com 2–3 partes:** barra empilhada única de 100%.
- **Um número que importa sozinho:** cartão com número grande, e não um gráfico.
- **Evite:** pizza com mais de 3 fatias, 3D, gráficos de radar, eixos que não começam em zero em barras, mapas quando o objetivo é comparar categorias, mais de 8 cores no mesmo gráfico.
- Se houver categorias demais, mostre as principais e agrupe o resto em "Outros".

## Paleta de cores

A cor serve à mensagem: **destaque o que importa e deixe o resto em cinza.**

| Papel | Claro | Escuro | Uso |
|---|---|---|---|
| Destaque principal | `#2a78d6` | `#3987e5` | O protagonista da história |
| Destaque secundário | `#eb6834` | `#d95926` | Contraponto, segunda série de uma comparação |
| Neutro (contexto) | `#b4b2aa` | `#5f5e59` | Categorias que não são o foco |
| Fundo da página | `#f6f5f1` | `#141413` | Fundo |
| Superfície (cartões) | `#fcfcfb` | `#1f1f1d` | Cartões e gráficos |
| Texto principal | `#1b1b19` | `#f2f1ec` | Títulos e corpo |
| Texto secundário | `#5d5c57` | `#b9b8b0` | Legendas, notas, eixos |

- Escalas sequenciais (tabelas de calor): uma só cor, do claro (`#eaf2fd`) ao escuro (`#104281`). Valores mais altos são mais escuros.
- A cor acompanha a entidade, e não a posição: se o item X é azul num gráfico, é azul em todos.
- Nunca use vermelho e verde como único par de contraste. Nunca dependa só da cor: sempre há rótulo, legenda ou texto.
- Os textos usam as cores de texto, nunca a cor da série.
- Ofereça modo escuro respeitando `prefers-color-scheme`.

## Tipografia e layout

- Fonte do sistema (`system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`); sem fontes externas, se não forem necessárias.
- Título de 32–44px, em negrito; títulos de capítulo de 20–24px; texto de 16–17px com entrelinha 1,6; notas de 13px.
- Uma coluna centralizada com largura máxima de ~1000px para leitura confortável; gráficos podem usar a largura toda dessa coluna.
- Números no padrão brasileiro: ponto para milhar, vírgula para decimal (`toLocaleString('pt-BR')`), e `%` colado ao número.
- Grades e eixos discretos (linhas finas e claras); sem bordas pesadas nem sombras fortes.
- Responsivo: tudo tem que funcionar em 400px de largura; matrizes largas ficam em contêiner com rolagem horizontal própria.

## Interação

- Todo gráfico tem dica flutuante (tooltip) ao passar o mouse ou tocar, com o valor exato e o contexto.
- Interação é complemento: a mensagem precisa estar legível sem passar o mouse.
- Não use animações longas nem elementos que se movem sozinhos.

## Técnica

- Um único arquivo HTML autocontido: CSS e JS embutidos; bibliotecas apenas por CDN, se forem mesmo necessárias (prefira SVG/HTML puro).
- Dados já agregados embutidos como JSON no próprio arquivo; nunca ler arquivos locais.
- Calcule os agregados com um script reproduzível antes de escrever o HTML e confira os totais.

## Checklist final

- [ ] O título afirma a conclusão principal em uma frase.
- [ ] Existe uma conclusão explícita no fim, que responde à pergunta.
- [ ] Cada gráfico tem título-achado e texto curto dizendo o que observar.
- [ ] Barras começam em zero; não há eixo duplo, 3D nem pizza com muitas fatias.
- [ ] A cor destaca o protagonista e o resto está em cinza; nada depende só da cor.
- [ ] Os números estão no formato brasileiro e os totais conferem com a fonte.
- [ ] Os termos técnicos estão explicados.
- [ ] O arquivo abre com dois cliques, sem erros no console e sem ler arquivos locais.
- [ ] Funciona em 400px de largura e no modo escuro.
- [ ] O rodapé tem a fonte, a data e as limitações.
