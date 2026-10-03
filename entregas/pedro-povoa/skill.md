---
name: dashboard-narrativo-html
description: Regras narrativas, de gráficos, cor, tipografia e acessibilidade para dashboards em HTML que contam uma história para público não especialista. Use sempre que for criar um painel, relatório visual ou peça de dados para leitura em jornal, apresentação ou web.
---

# Dashboard narrativo em HTML

## Quando usar

Ao criar qualquer dashboard, painel ou página de gráficos cujo objetivo é fazer o leitor entender uma mensagem, e não apenas consultar números. Aplique também ao revisar um dashboard existente.

## Estrutura narrativa

- Comece pela mensagem principal em uma frase, como título (ex.: "A maioria faz X, e quase ninguém faz Y"). Logo abaixo, um parágrafo de abertura e de 2 a 4 números-âncora grandes.
- Divida o corpo em 4 a 7 capítulos numerados. Cada capítulo tem: um título que enuncia a conclusão (e não o assunto), uma frase de leitura que diz o que olhar, um gráfico e uma nota curta com a definição da medida.
- Ordene do simples ao interpretativo: primeiro o fato básico, depois o arranjo ou a causa, por fim a leitura sobre o que isso significa.
- Feche com um bloco de síntese que responde à pergunta do projeto e diz "e daí?". Nunca termine num gráfico.
- Coloque uma nota metodológica no rodapé: fonte, recorte, definições, limitações e qualquer classificação externa com sua origem.
- Cada capítulo deve se sustentar sozinho: quem ler só um deve entender a conclusão dele.

## Escolha de gráficos

- Ranking ou comparação entre categorias: barras horizontais ordenadas, com rótulo e valor ao lado. Limite a 10 itens e agrupe o resto em "Outros (N)".
- Distribuição de uma quantidade: colunas por faixa, com a faixa de destaque em cor de ênfase.
- Parte do todo entre poucos grupos: barra empilhada 100%. Evite pizza e rosca.
- Duas dimensões categóricas: mapa de calor com valor escrito em cada célula.
- Geografia: se não houver geometria confiável embutível, use cartograma de quadrados com a sigla e o valor dentro; evite mapas que exijam arquivos externos.
- Barras sempre começam em zero. Não use eixo duplo, 3D nem escala truncada.
- Quando uma medida pode ser lida de duas formas (ex.: contagem e peso), ofereça alternância entre elas e rotule cada uma.
- Se uma conclusão depende de um limiar ou de uma classificação discutível, inclua uma chave de sensibilidade que mostre como ela muda.

## Paleta de cores

- Parta de uma paleta de interface com poucas cores e papéis claros: fundo, cartão, texto, texto secundário, linhas, uma cor de ênfase e um neutro para "o restante". Defina cada uma por variável CSS.
- Se o projeto pedir identidade nacional, use as cores da bandeira do Brasil: azul `#002776` (faixa de abertura, botões, bloco final), verde `#009C3B` (números-âncora e rótulos de capítulo; use `#00662a` quando for texto sobre fundo claro, por contraste) e amarelo `#FFDF00` (destaques e kicker sobre azul). Fundo claro levemente esverdeado `#f7f9f4`, texto `#14213d`, neutro `#b9bfc7`.
- Sem pedido de identidade, escolha uma paleta sóbria de uma única cor de ênfase.
- Use cor de categoria só para os 6 a 10 itens principais; os demais ficam no neutro. Mais de 10 cores deixa o gráfico ilegível.
- Se as cores vierem de uma identidade externa (marcas, siglas), mantenha-as, mas nunca use a cor como único canal: escreva o nome em cada elemento, porque cores parecidas (vários azuis) confundem.
- Escalas de grupos analíticos (ex.: categorias ordenadas) usam paleta própria, diferente de qualquer identidade de marca, para não gerar associação errada.
- Defina todas as cores como variáveis CSS e redefina-as para `prefers-color-scheme: dark`. Contraste mínimo de 4,5:1 entre texto e fundo.

## Tipografia e layout

- Títulos em serifa (`Georgia, "Times New Roman", serif`), texto e rótulos em `system-ui`. Corpo de 17px, entrelinha 1,6, largura de texto até 680px.
- Coluna central de até 880px, margem lateral de 16px, sem rolagem horizontal. Teste em 360px de largura.
- Números grandes em serifa para âncoras. Rótulos de gráfico de no mínimo 12px.
- Gráficos em HTML, CSS e SVG simples, sem dependência de rede; se usar biblioteca, carregue por CDN e mantenha o conteúdo legível sem ela.
- Interação mínima e óbvia: botões de alternância, toque em um item para detalhe. Todo controle tem rótulo e é acessível por teclado.

## Dados e integridade

- Embuta no HTML apenas os dados já agregados. Nada de ler arquivos locais.
- Defina cada medida na primeira vez que aparecer; não use jargão do domínio sem explicar.
- Todo número no texto deve ser derivado dos dados embutidos; recalcule antes de entregar. Prefira escrever "menos de 1 em cada 5" quando o valor exato for 16%.
- Informe o tamanho do recorte e o que ficou de fora.
- Não afirme causa onde só há associação.

## Checklist final

- [ ] O título principal diz a conclusão, e cada capítulo também.
- [ ] A história se sustenta lida de cima a baixo, sem filtros.
- [ ] Todo número do texto bate com os dados.
- [ ] Barras começam em zero; sem pizza, 3D ou eixo duplo.
- [ ] Nenhuma informação depende só de cor; siglas e valores estão escritos.
- [ ] Notas de fonte, recorte e definições estão no rodapé; classificações externas estão citadas.
- [ ] Funciona em 360px sem rolagem horizontal e em modo escuro.
- [ ] O arquivo abre com dois cliques, sem erros no console e sem dependência de arquivos locais.
- [ ] Há um bloco final que responde à pergunta do projeto.
