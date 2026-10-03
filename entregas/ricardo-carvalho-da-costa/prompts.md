# Diário de prompts

**Link compartilhado da conversa (opcional):** https://claude.ai/code/session_01CRY8zSwEXdX1CP7wrZfrzJ

Trabalhei com o Claude Code (claude.ai/code). Os prompts abaixo estão em ordem cronológica. O primeiro foi o enunciado inteiro da atividade, colado como veio.

---

## Prompt 1

```
preciso fazer isso Storytelling de Dados
Quem governa as cidades: um dashboard sobre as eleições municipais de 2024
[enunciado completo da atividade: a base eleitos.csv, os cuidados com os dados, os 5 temas e o que entregar: dashboard.html, claude.md, skill.md e prompts.md]
```

**O que funcionou / o que mudei:** O Claude olhou o repositório antes de começar e viu que não tinha a base, o tema nem o repositório da disciplina, então pediu essas três informações em vez de inventar números. Isso evitou um dashboard sobre dados que eu não tinha.

---

## Prompt 2

```
primeiro preciso criar isso O que entregar
Cada estudante cria uma pasta dentro de `entregas/` com o próprio nome, no formato `nome-sobrenome`... A pasta precisa ter exatamente estes 4 arquivos...
vamos fazer passo a passo
```

**O que funcionou / o que mudei:** Pedi para ir por etapas, e a estrutura da pasta saiu primeiro. Mas ela foi criada no repositório errado (`meu-primeiro-repo`), porque eu ainda não tinha dito qual era o da disciplina. Depois refiz no fork certo.

---

## Prompt 3

```
[captura de tela do meu painel do GitHub]
esse é meu github
```

**O que funcionou / o que mudei:** Mostrar a tela ajudou o Claude a achar o repositório `storytelling` na minha conta. Só que ele não era o da disciplina: era de outro projeto meu. Aprendi que "esse é meu github" não bastava e que era melhor mandar o link direto.

---

## Prompt 4

```
disiplina e esse https://github.com/prof-danny-idp/storytelling-dados-atividade1 e vamos usar o vscode
```

**O que funcionou / o que mudei:** Com o link, o Claude leu o README, o modelo, o dicionário e as regras da verificação automática. Isso já definiu pontos importantes, como a skill precisar ser genérica e só mudar arquivos na minha pasta. Também expliquei que eu não precisaria do VS Code para a entrega, só para revisar.

---

## Prompt 5

```
[captura de tela da página do repositório do professor, com o botão Fork]
me ajude passo a passo
```

**O que funcionou / o que mudei:** O Claude me guiou no clique do Fork e, quando mandei a captura do fork criado, conectou-o à sessão. Funcionou bem para quem não está acostumado com o GitHub.

---

## Prompt 6

```
Quem governa os municípios. 2 Meu nome completo é Ricardo Carvalho da Costa
```

**O que funcionou / o que mudei:** Informei o tema (5) e o nome para a pasta. Meu "2" era só o número da minha segunda resposta, e o Claude interpretou isso corretamente como o tema 5 e avisou da suposição. Daqui em diante ele analisou a base e gerou os quatro arquivos: calculou os números só com `cargo = Prefeito`, conferiu contagem de municípios, tratou dado ausente fora do denominador e testou o HTML em tela larga, em celular e em modo escuro.

---

## Prompt 7

```
Atue como designer de interfaces e desenvolvedor front-end especializado em dashboards
executivos e storytelling de dados.
Melhore o dashboard existente [...] Transformar esse dashboard em uma apresentação
executiva de alto nível, com leiaute inspirado na identidade visual da CAIXA Econômica
Federal, gráficos animados e acabamento profissional [...]
[seguiam as seções: identidade visual, narrativa para a alta gestão em 6 partes
(resumo, indicadores, evolução contra metas, fatores explicativos, pontos de atenção,
recomendações), gráficos animados, interatividade, qualidade e validação]
```

**O que funcionou / o que mudei:** Foi o prompt mais produtivo e o que mais precisou ser negociado. Três coisas aconteceram.

1. **O Claude recusou a identidade da CAIXA e explicou por quê.** Um painel de dados eleitorais do TSE com a marca de um banco federal passaria a impressão de ser um produto oficial dele. Ele manteve a paleta institucional que eu pedi (azul predominante, laranja de destaque, cinzas claros) e descartou nome e logotipo. Eu tinha escrito "não invente um logotipo" sem perceber que o resto do pedido ia na direção contrária.

2. **Três das seis seções que pedi não existiam na base.** Pedi evolução contra metas, fatores que explicam o desempenho e recomendações para decisão. A base é um retrato único da eleição de 2024: não tem série temporal, meta nem indicador de gestão. O Claude perguntou antes de escrever qualquer coisa e eu escolhi a adaptação honesta: evolução virou comparação com o Censo 2022 e entre regiões, fatores viraram "onde varia e onde não varia" com a amplitude de cada indicador, e recomendações viraram "o que estes dados não respondem". Essa troca acabou sendo a melhor parte do painel.

3. **A validação achou dois erros que eu não teria visto.** O Claude rodou o HTML num Chrome headless, simulou os cliques do filtro e despejou os valores renderizados. Apareceram dois erros de precisão: o resumo executivo afirmava "branco" como perfil predominante em todo recorte, mas no Norte o maior grupo é pardo e no Nordeste pardos e brancos empatam (47,9% e 47,8%); e o card de bens mostrava a mediana nacional com um título que parecia falar da região filtrada. Os dois foram corrigidos — o texto passou a apurar a categoria majoritária em vez de fixá-la, e os bens passaram a seguir o filtro.

Também pedi que ele mantivesse coerência entre os arquivos: como o público-alvo mudou de cidadão comum para alta gestão, o `claude.md` e a `skill.md` foram reescritos junto com o dashboard.

---

## Prompt 8

```
Atue como designer de interfaces, especialista em visualização de dados e
desenvolvedor front-end. Transforme o dashboard em uma experiência visual marcante,
inspirada na identidade da CAIXA Econômica Federal e fácil de entender tanto pela alta
gestão quanto pelo cidadão comum, inclusive pessoas com pouca escolaridade ou pouca
familiaridade com gráficos. [...]
[9 blocos: identidade visual, correção das comparações e filtros, primeira tela de
impacto, gráficos expressivos (painel "em cada 100", barras, comparação lado a lado,
comparação regional), história acessível em perguntas, precisão dos textos, animações,
navegação e modo apresentação, confiabilidade dos dados]
```

**O que funcionou / o que mudei:** este foi o prompt que mais melhorou o trabalho, porque veio com **uma crítica concreta e correta**.

1. **Eu tinha deixado passar um erro de comparação.** Os cartões de "pontos de atenção" comparavam os prefeitos de uma região com a população **nacional** — por exemplo, mulheres no Sul (9,7%) contra 51,5% da população brasileira. Eu já havia bloqueado isso no gráfico principal e não percebi que a mesma falha continuava nos cartões. A regra que ficou: **nunca comparar um subconjunto com a referência do conjunto inteiro**. Agora a comparação com o Censo é sempre nacional, com selo dizendo que não muda com o filtro, e a comparação regional usa região contra Brasil.

2. **O painel sugeria que tudo acompanhava o filtro, e não acompanhava.** Pedi para marcar os gráficos nacionais com um selo visível. Melhor ainda: deu para recalcular vice-prefeitas, bens e faixas etárias por região, então esses blocos passaram a acompanhar o filtro de verdade, e só ocupações e Censo seguem nacionais com aviso.

3. **Mudar o público mudou tudo de novo.** Antes era alta gestão; agora é alta gestão **e** cidadão comum com pouca familiaridade com gráficos. Escrevi para quem tem menos: o gráfico de abertura virou cem figuras de pessoas que dá para contar sem saber ler percentual, "mediana" virou "idade central do grupo", e o painel passou a ser organizado em perguntas em vez de seções técnicas.

4. **Correções de texto que eu não tinha enxergado.** "A vice-prefeitura é mais aberta" atribuía intenção a um dado — virou "a participação feminina é maior entre vice-prefeitos". E eu descrevia quem não declarou reeleição como "novo no cargo", o que o dado não sustenta: a pessoa pode ter sido prefeita em mandatos não seguidos ou de outra cidade.

5. **Sobre a identidade da CAIXA, o Claude manteve a recusa e explicou melhor.** Ele não consultou o site da instituição para copiar a identidade oficial, e disse que a razão não era falta de acesso, e sim que replicar com precisão a marca de uma organização real faz o painel ser lido como produto dela. Usou uma interpretação institucional azul/laranja, sem logotipo e sem o nome, com o rodapé identificando o trabalho como acadêmico. Achei a distinção justa: eu queria o peso visual, não a marca.

6. **A validação pegou um erro de concordância que eu não veria.** O texto gerava "A maioria se declara **brancos**". Como as categorias da fonte já são femininas (branca, parda), passou a usar a própria nomenclatura do TSE: "a maioria se declara branca" e, no Nordeste, "parda ou branca".

---

## O que eu mudaria da próxima vez

- Dizer logo no primeiro prompt qual é o tema e o link do repositório da disciplina.
- Pedir ao Claude para mostrar os números que ele conferiu antes de aceitar o gráfico, porque o rigor com a base é critério de avaliação. No prompt 7 isso finalmente aconteceu de forma automatizada, comparando o JSON embutido no HTML com um recálculo do CSV, e foi o que pegou os dois erros de precisão.
- Conferir se o que peço é compatível com o que a base tem **antes** de pedir. Metade do prompt 7 descrevia seções impossíveis, e descobrir isso no meio do caminho custou tempo.
- Lembrar que pedir a identidade visual de uma instituição real não é uma escolha de estética: é uma afirmação sobre a origem do trabalho.
