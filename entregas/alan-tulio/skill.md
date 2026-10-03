---
name: narrativa-visual-com-rigor
description: Regras de narrativa, escolha de gráficos, cor e tipografia para dashboards e relatórios visuais em HTML que contam uma história com dados para público amplo. Use sempre que for criar ou revisar um gráfico, painel, infográfico ou página de dados, com qualquer base.
---

# Narrativa visual com rigor

Duas referências sustentam esta skill. De *Storytelling with Data*, de Cole Nussbaumer Knaflic, vem o método: entender o contexto, escolher o visual adequado, eliminar a saturação, dirigir a atenção, pensar como designer e contar uma história. De *A psicologia das cores*, de Eva Heller, vem o cuidado com a cor: nenhuma cor tem significado sozinha; o efeito depende do contexto e das cores que a acompanham.

## Quando usar

Use ao criar ou revisar qualquer peça que mostre dados para alguém ler sem você por perto: dashboard, relatório, infográfico, página de resultados. Siga as seções na ordem. A cor vem por último.

## Antes de desenhar: contexto

Responda por escrito, antes do primeiro gráfico:

1. **Quem lê?** Nomeie um público específico. Registre o que ele já sabe, quanto tempo tem e o que precisa compreender ou decidir.
2. **Qual é a grande ideia?** Escreva uma única frase completa, com sujeito e verbo, que afirme um ponto de vista e diga o que está em jogo. Se não couber em uma frase, a análise ainda não terminou.
3. **Qual é a história em três minutos?** Se só for possível dizer isso, o que precisa ficar?
4. **O que os dados não permitem dizer?** Liste as limitações antes de escrever conclusões.

Separe análise exploratória de explicação. Explore tudo; mostre só o que sustenta a grande ideia. Corte o que é interessante mas não serve à mensagem.

## Estrutura narrativa

- Organize em três atos. **Começo:** a mensagem principal já no título da página, com o contexto mínimo. **Meio:** as evidências, uma por seção, da mais geral para a mais específica. **Fim:** o que fica e o que fazer com isso.
- Escreva títulos que afirmam, não que descrevem. Use “Vendas caíram 12% depois da mudança de preço”, não “Vendas por mês”.
- Teste a **lógica horizontal**: lidos em sequência, sozinhos, os títulos das seções devem contar a história inteira.
- Teste a **lógica vertical**: em cada seção, título, texto e gráfico devem dizer a mesma coisa.
- Dê a cada seção uma única ideia e, de preferência, um único gráfico.
- Abra cada seção com o achado em palavras; o gráfico vem depois, como prova.
- Coloque os números de destaque no texto, com a unidade e o total de referência (“128 de 5.000”, não só “2,3%”).
- Repita a mensagem central no início e no fim, com palavras diferentes.
- Feche com uma chamada: uma decisão, uma pergunta em aberto ou o próximo dado a buscar.

## Rigor: o que os dados permitem afirmar

- Descreva antes de explicar. Não escreva “porque”, “causa” ou “leva a” sem um desenho de análise que sustente causalidade.
- Inclua uma seção visível, não uma nota de rodapé, com duas listas: o que a base permite afirmar e o que não permite.
- Informe em toda peça: fonte, data de extração, unidade de análise, cobertura e tratamento dos valores ausentes.
- Mostre os ausentes como categoria própria. Nunca os redistribua nem os trate como zero.
- Mostre o total (n) de cada grupo comparado. Sinalize grupos pequenos, em que poucos casos mudam o percentual.
- Se usar um número de fora da base, identifique-o como externo, cite a fonte e explique por que a comparação é imperfeita.
- Use os termos da fonte para as categorias. Se agrupar categorias, diga qual foi o critério.
- Verifique cada número do texto contra os dados embutidos antes de entregar.

## Escolha de gráficos

Escolha pela comparação que o leitor precisa fazer:

| O leitor precisa ver | Use | Evite |
| --- | --- | --- |
| Um ou dois números | Texto grande com uma frase de contexto | Gráfico para um único número |
| Categorias entre si | Barras horizontais, ordenadas pelo valor | Pizza, rosca, barras em 3D |
| Partes de um todo em vários grupos | Barras 100% empilhadas, com no máximo cinco ou seis partes | Várias pizzas lado a lado |
| Uma proporção para público leigo | Grade de 100 unidades (“de cada 100…”) | Velocímetros e medidores |
| Evolução no tempo | Linha | Barras para séries longas |
| Dois momentos ou dois grupos | Barras pareadas ou gráfico de inclinação | Dois eixos verticais |
| Relação entre duas medidas | Dispersão | Linha ligando pontos sem ordem |
| Valores exatos para consulta | Tabela, como apoio ao gráfico | Tabela no lugar do gráfico principal |

Regras que valem sempre:

- Comece o eixo das barras no zero. Barras truncadas distorcem a comparação.
- Use a mesma escala em gráficos que serão comparados.
- Nunca use dois eixos verticais. Separe em dois gráficos.
- Ordene categorias pelo valor, salvo quando a categoria tem ordem natural (faixas, datas).
- Rotule diretamente as barras e linhas. Use legenda só quando o rótulo direto não couber, e ponha-a acima do gráfico.
- Escreva rótulos na horizontal. Se o nome é longo, vire a barra, não o texto.
- Ofereça os valores exatos em tabela recolhida abaixo do gráfico.
- Em HTML, mostre o valor e o total ao passar o mouse ou tocar em cada marca.

## Eliminar a saturação

Cada elemento na tela custa atenção. Remova o que não informa:

- Tire bordas de gráfico, linhas de grade, marcadores de ponto e fundos coloridos, salvo quando ajudam a ler.
- Elimine casas decimais sem significado. Uma casa decimal basta para percentuais.
- Alinhe textos à esquerda e elementos em uma grade. Evite texto centralizado em blocos.
- Preserve o espaço em branco. Não preencha vazios com mais gráficos.
- Use proximidade e alinhamento para mostrar o que pertence junto, em vez de caixas e linhas.
- Deixe eixos, notas e rótulos secundários em cinza; eles apoiam, não competem.

## Paleta de cores

Princípios:

- **Cinza é o padrão; cor é a exceção.** Desenhe tudo em tons neutros e aplique cor só onde o leitor deve olhar primeiro. Se tudo é destacado, nada é destacado.
- **Cada cor tem uma função e a mantém** em todos os gráficos da peça. A mesma categoria tem sempre a mesma cor.
- **O significado vem do conjunto.** Avalie a combinação, não cada cor isolada: a mesma cor muda de efeito conforme as vizinhas e o tema.
- **Cor nunca é o único canal.** Acompanhe sempre com rótulo, posição ou textura.

Paleta-base, com a função de cada cor:

| Função | Cor | Hex | Por quê |
| --- | --- | --- | --- |
| Fundo da página | Branco quente | `#FBFAF7` | Branco puro ofusca em tela; o tom quente descansa a leitura |
| Superfície dos gráficos | Branco | `#FFFFFF` | Separa o gráfico do texto sem precisar de borda forte |
| Texto principal | Quase preto | `#1F1D1A` | Preto puro pesa; o tom atenuado mantém o contraste e suaviza |
| Texto secundário | Cinza escuro | `#55514A` | Hierarquia sem trocar de matiz |
| Notas e eixos | Cinza médio | `#6F6A62` | Recua para o segundo plano e continua legível |
| Linhas e divisores | Cinza claro | `#E4E0D8` | Estrutura quase invisível |
| Dado de contexto | Cinza neutro | `#A8A39A` | Cinza é a cor da neutralidade: informa sem chamar atenção |
| Destaque principal | Azul profundo | `#1B4FA8` | Azul é a cor mais associada a confiança e sobriedade; sustenta um tom institucional |
| Destaque secundário | Azul claro | `#4A90D9` | Mesmo matiz, menor intensidade: indica parentesco com o destaque principal |
| Categoria adicional 1 | Violeta | `#8A5FBF` | Distinta do azul sem carregar sentido de alerta |
| Categoria adicional 2 | Verde | `#12935F` | Tom calmo, de leitura neutra |
| Aviso e limitação | Âmbar | `#9A6700` sobre `#FFF8E6` | Amarelo é a cor da advertência; reservada a ressalvas |
| Sem informação | Hachura cinza | `#C9C4BA` sobre branco | Textura, não cor: ausência não é uma categoria como as outras |

Regras de uso:

- Use no máximo um matiz de destaque por gráfico e, no total da peça, cinco cores de categoria.
- Reserve vermelho para erro ou perigo real. Vermelho carrega paixão, agressão e proibição; fora desses contextos, ele julga o dado.
- Não use verde e vermelho como par de oposição: é a confusão mais comum no daltonismo e traz o julgamento “bom contra mau”.
- Evite marrom e laranja saturado como cores principais: tendem a ser lidas como antiquadas ou pouco sérias em contexto institucional.
- Para magnitude, use um único matiz do claro ao escuro. Para opostos, dois matizes com ponto médio neutro. Nunca arco-íris.
- **Dados sobre grupos de pessoas:** não use cores que imitem ou evoquem estereótipos do grupo (tom de pele, rosa e azul para gênero, cores de bandeira ou de partido sem necessidade). Use cores convencionais e diga na peça que são convenções.
- Garanta contraste mínimo de 4,5:1 para texto e 3:1 para marcas contra o fundo. Onde a marca for clara demais, dê rótulo direto.
- Teste a paleta em simulação de daltonismo e em escala de cinza. Se duas categorias vizinhas se confundirem, mude a intensidade ou acrescente textura.
- Escreva o texto sempre em tons de texto, nunca na cor da série.

## Tipografia e layout

- Use duas famílias, no máximo: uma serifada para títulos (`Georgia, serif`) e uma sem serifa para texto e gráficos (`system-ui, sans-serif`). Fontes do sistema dispensam downloads e abrem sem internet.
- Hierarquia por tamanho e peso, não por cor: título da página de 30 a 46 px; títulos de seção de 23 a 30 px; texto de 16 a 17 px com entrelinha 1,6; notas de 13 a 14 px.
- Limite a linha de texto a cerca de 70 caracteres.
- Use coluna única, com largura máxima de 860 px, lida de cima para baixo. O ponto mais importante fica no alto, à esquerda.
- Dê a cada gráfico um título curto e um subtítulo que diga a unidade e o denominador.
- Use numerais tabulares em tabelas e rótulos de valor. Formate números no padrão do idioma do leitor.
- Faça a página responsiva: em telas estreitas, empilhe as colunas, ponha rótulos acima das barras e deixe tabelas largas rolarem dentro da própria caixa. A página nunca rola na horizontal.
- Entregue um único arquivo HTML, com CSS, JavaScript e dados agregados embutidos. Não leia arquivos locais. Se usar biblioteca externa, carregue por CDN e confirme que a página continua legível se ela falhar.
- Acessibilidade: defina o idioma da página, dê descrição textual a cada gráfico, mantenha foco visível nos controles e respeite a preferência por menos movimento.

## Checklist final

- [ ] A grande ideia cabe em uma frase e está no título da página.
- [ ] Os títulos das seções, lidos em sequência, contam a história com começo, meio e fim.
- [ ] Cada gráfico responde a uma pergunta e o título dele afirma a resposta.
- [ ] Barras começam no zero; não há dois eixos, pizza nem 3D.
- [ ] Tirei bordas, grades e decimais que não informam.
- [ ] Ao olhar de relance, o olho cai primeiro no que importa.
- [ ] Cada cor tem uma função, é a mesma em toda a peça e não é o único canal.
- [ ] Nenhuma cor imita ou estereotipa um grupo de pessoas.
- [ ] Contraste e leitura em daltonismo foram testados.
- [ ] Há uma seção visível sobre o que os dados permitem e não permitem afirmar.
- [ ] Fonte, data, unidade de análise, cobertura e ausentes estão informados.
- [ ] Nenhuma frase afirma causa sem sustentação.
- [ ] Todos os números do texto foram conferidos contra os dados embutidos.
- [ ] O arquivo abre com dois cliques, sem erros no console e sem ler arquivos locais.
- [ ] A página funciona em tela de celular e de computador, sem rolagem horizontal.
