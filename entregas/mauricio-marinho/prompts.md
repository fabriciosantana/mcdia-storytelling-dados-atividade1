# Diário de prompts

**Ferramenta:** Claude Code (Claude Opus 5.5), trabalhando direto no fork do repositório.

**Link compartilhado da conversa (opcional):** não disponível (sessão no terminal).

---

## Prompt 1

```
Hoje vamos fazer uma atividade da disciplina de storytelling com dados, do professor Danny de Castro, atividade em sala de aula. As instruções estão em https://ambientevirtual.idp.edu.br/courses/9582/assignments/44766 e o meu tema foi o 4 "Continuidade e renovação", o Briefing é o seguinte: Uma escola de governo vai abrir um curso para lideranças municipais e pediu um dashboard para a aula inaugural, sobre o contexto político em que essas lideranças vão atuar. A turma reúne gestores, servidores e assessores de diferentes regiões, que conhecem bem a própria realidade e pouco a dos outros municípios. Sua história deve levar essa turma a refletir sobre o equilíbrio entre quem permanece e quem chega ao poder municipal, e sobre o que pode estar por trás desse equilíbrio. Compreende? Analise a atividade, explique-me e compartilhe a estratégia para atender os requisitos definidos antes de iniciar os trabalhos ok?
```

**O que funcionou / o que mudei:** Pedir análise e estratégia antes de executar foi bom, mas o Claude não conseguiu abrir a página do AVA, porque ela exige login. A primeira estratégia partiu só do briefing e supôs dados que a base não tem (séries de 2016 a 2024, vereadores, candidatos derrotados). Aprendi a fornecer o enunciado e a base logo no primeiro prompt.

---

## Prompt 2

```
Salvei a pagina de instruções em /home/mauricio/Projetos/atividade-storytelling e o link do repositório do professor é https://github.com/prof-danny-idp/storytelling-dados-atividade1 a base completa está em https://github.com/prof-danny-idp/storytelling-dados-atividade1/raw/refs/heads/main/dados/eleitos.csv e o dicionário em https://github.com/prof-danny-idp/storytelling-dados-atividade1/blob/main/dados/dicionario.md
```

**O que funcionou / o que mudei:** Com o PDF, o dicionário e o workflow de validação do PR, a estratégia foi corrigida. A base tem só os eleitos de 2024, então a pergunta passou a ser "quem governa: reeleitos ou novos?", e não "quem venceu a disputa". O Claude também explorou os dados antes de propor a narrativa e encontrou os achados que viraram os blocos: a variação de RR a SC, o porte quase irrelevante, a votação folgada dos reeleitos, os 195 sem adversário e as ocupações dos novos. A cautela mais importante surgiu aqui: "novo" não quer dizer rejeição, por causa do limite de dois mandatos.

---

## Prompt 3

```
sim, mauricio-marinho, gh está autenticado, gostaria que, se tiveres que gerar qualquer dashboard, que seja em html com boas práticas sobre teoria das cores privilegiando tons e sobretons de azul e cinza, tons de laranja para destaques. Não precisa levar o tempo todo dado pelo professor, até 11:30, até porque todos já entregaram seus trabalhos, só falta eu.
```

**O que funcionou / o que mudei:** A restrição de cor deu identidade visual ao painel. Continuidade virou azul escuro, renovação azul claro, o contexto ficou em cinza e o laranja passou a marcar só a média nacional, os extremos e os pontos de atenção. O Claude validou a paleta com um script de daltonismo e contraste, e precisou de algumas iterações até os dois azuis ficarem distinguíveis também no modo escuro. Depois de renderizar o dashboard em 1200px e 390px, apareceu um bug: no celular, a linha "Brasil 44,5%" ficava deslocada, porque era calculada em pixels. A correção foi posicioná-la com CSS proporcional, e essa regra entrou na skill. Também revisei um título que sugeria causa ("a legenda importa mais…") e troquei por uma comparação descritiva. Além disso, conferi as frases com os números: o "PSD é o único partido de maioria reeleita" estava errado, porque o União tem 50,1%, e corrigi.

---

## Prompt 4

```
Carregue o dashboard no browser para eu ver, por favor.
```

**O que funcionou / o que mudei:** Ver o painel no navegador, e não só em imagens, mostrou que a história funcionava, mas que o painel era estático. Para uma turma que quer comparar a própria realidade com a dos outros, faltava poder explorar. Isso motivou o prompt seguinte.

---

## Prompt 5

```
Muito legal. GOstaria de fazer algumas modificações, gostaria de criar e utilizar um skill, como parte do projeto, que imprimisse minha personalidade. Gostaria que houvesse alguma interatividade nos gráficos, com agrupamentos e filtros sempre que possível, Utilizar tons e sobretons de azul e cinza e laranja para destaques. As interatividades devem ser suaves, com transição suave. Busco um dashboard de impacto com sofisticação. Podes gerar um skill que capture esta ideia, implantá-lo, atualizar o dashboard e a entrega em um novo pullrequest?
```

**O que funcionou / o que mudei:** O Claude criou a skill `assinatura-visual-marinho` com regras concretas, e não adjetivos:
- tokens de movimento (easing, 180/450/750ms);
- o padrão de filtro cruzado ("um gráfico destaca a própria dimensão, filtra pelas outras");
- reordenação FLIP;
- o hero azul-noite com números que contam até o valor;
- a regra "títulos descrevem o quadro geral, a leitura do recorte descreve o filtro".

A skill foi instalada em `~/.claude/skills/` e carregada pelo Claude Code antes de reconstruir o dashboard. Ajustes no caminho:
- O primeiro cubo de dados tinha quase uma linha por prefeito; foi dividido em três cubos menores para respeitar a regra de dados agregados.
- No celular, a barra de filtros colapsou e a pílula de leitura quebrava o texto em colunas; ambos foram corrigidos após as capturas de tela.
- O tooltip tratava a região "Norte" (índice 0) como "sem filtro"; o bug foi corrigido.
- Os exemplos da skill citavam números desta base e foram trocados por exemplos genéricos, para a skill servir a qualquer projeto.

Validei com um teste automatizado (Playwright): clicar em "Sul" leva o painel a 37,1% e 1.190 municípios; cruzar Sul, mais de 100 mil votos e PSD mostra o aviso de recorte pequeno (9 municípios); o clique na barra "Norte" sincroniza o filtro do topo. Não houve erros no console.
