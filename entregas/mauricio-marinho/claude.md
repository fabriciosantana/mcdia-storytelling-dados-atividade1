## Qual história meu dashboard conta?

Nas eleições de 2024, 44,5% dos prefeitos eleitos foram reconduzidos e 55,5% chegaram ao cargo agora. Esse equilíbrio muda muito de lugar para lugar: vai de 67% de continuidade em Roraima a 31% em Santa Catarina, e o Sul é a região que mais renova. Quem permanece costuma vencer com folga; quem chega raramente se declara político de profissão. O dashboard convida lideranças municipais a olhar para além do próprio município e a se perguntar o que sustenta esse equilíbrio: a vantagem de quem governa, o limite de dois mandatos, a falta de competição ou a cultura política regional.

## Contexto do projeto

- **Tema 4: Continuidade e renovação.** Pergunta norteadora: *O que as eleições de 2024 revelam sobre continuidade e renovação no comando das prefeituras?*
- **Briefing:** uma escola de governo vai abrir um curso para lideranças municipais e pediu um dashboard para a aula inaugural sobre o contexto político em que essas lideranças vão atuar. A história deve levar a turma a refletir sobre o equilíbrio entre quem permanece e quem chega ao poder municipal, e sobre o que pode estar por trás desse equilíbrio.
- **Base:** `dados/eleitos.csv` (11.106 linhas, 72 colunas, 5.553 municípios), com o dicionário em `dados/dicionario.md`.
- **Cuidados de leitura aplicados:**
  - Filtrar `cargo = Prefeito` (uma linha por município) e contar municípios por `codigo_municipio_tse`.
  - "Reeleito" é a declaração `candidato_a_reeleicao_tse` (ST_REELEICAO). Não houve auditoria individual do mandato anterior.
  - Votos e percentuais vêm só da linha do prefeito, para não contar em dobro. Uso `percentual_validos_chapa_atual_tse`, que reflete o reprocessamento atual.
  - Célula vazia não é zero: as 9 chapas sem percentual ficaram fora do histograma.
  - Estão incluídas as 9 chapas cassadas e as 14 eleições históricas, porque a pergunta é sobre o resultado das urnas. Conferi que, considerando só `ELEITO_ATUAL_TSE`, a taxa continua em 44,5%.
  - A base retrata 2024, não quem governa hoje. Não tem candidatos derrotados, vereadores nem eleições anteriores.

## Público-alvo

Gestores, servidores e assessores municipais de várias regiões, na aula inaugural de uma escola de governo.
- Conhecem bem a própria realidade e pouco a dos outros municípios. O dashboard precisa tirá-los do "caso local" e mostrar o país.
- Têm vivência política, mas não necessariamente familiaridade com análise de dados. A linguagem deve ser direta, sem jargão estatístico.
- A ocasião é de abertura e reflexão, não de decisão. O dashboard termina com perguntas para debate, não com recomendações.

## Perguntas que os dados respondem

1. Quanto das prefeituras ficou com quem já governava e quanto mudou de mãos? (44,5% e 55,5%)
2. Esse equilíbrio é igual no país inteiro? (Não: há 35 pontos de diferença entre RR e SC, e o Sul renova mais.)
3. O tamanho do município faz diferença? (Pouca: a taxa fica entre 44% e 47% em todos os portes até 100 mil votos.)
4. Como vence quem permanece e como vence quem chega? (Reeleitos: mediana de 65% dos votos, 38% acima de 70% e 195 sem adversário. Novos: mediana de 54%.)
5. De onde vêm os novos prefeitos? (Só 8% se declararam com cargo eletivo; predominam profissionais liberais e empresários.)
6. O partido se associa ao padrão? (Entre os maiores, a continuidade vai de 35% no PSDB a 52% no PSD.)
7. O que a base permite e o que não permite afirmar sobre as causas?

## Decisões de design

Seguir a skill `assinatura-visual-marinho` (skill.md), a minha assinatura pessoal para dashboards: impacto na primeira dobra, sofisticação nos detalhes e movimento com propósito. Ela está instalada em `~/.claude/skills/assinatura-visual-marinho/` e foi carregada pelo Claude Code para construir esta versão.

- **Versão 2, interativa.** A primeira versão (PR #9) era estática. Esta mantém a mesma história e os mesmos títulos, mas transforma cada gráfico em algo explorável. O público conhece a própria realidade, e os filtros permitem que cada gestor coloque a sua região, o seu porte ou o seu partido ao lado do país.
- **Hero de impacto:** faixa azul-noite com o título-mensagem em serifa editorial (Source Serif 4) e 4 números-chave que contam até o valor e se atualizam com os filtros: % de reeleitos, municípios no recorte, reeleitos sem adversário e % dos novos vindos da política.
- **Filtros globais cruzados** numa barra fixa no topo: região, porte e partido. Cada gráfico aplica os filtros das outras dimensões e **destaca** (em vez de filtrar) a própria dimensão, para não perder a comparação. Clicar em uma barra (região, estado, porte ou partido) filtra o painel inteiro, e clicar de novo desfaz. "Limpar filtros" volta ao Brasil.
- **Agrupamentos e alternâncias**, com um controle segmentado de indicador deslizante:
  - bloco 01: recorte inteiro ou por região;
  - bloco 02: região ou estado, e % ou nº de prefeitos (barras empilhadas de reeleitos e novos);
  - bloco 03: % ou nº;
  - bloco 04: % do grupo ou nº;
  - bloco 05: novos ou reeleitos;
  - bloco 06: % ou nº, ordenado por % ou por tamanho.
- **Movimento suave:** todas as mudanças usam o mesmo easing (`cubic-bezier(.22,1,.36,1)`).
  - As barras crescem e mudam de largura em 750ms.
  - As listas se reordenam deslizando (técnica FLIP).
  - Os números contam do valor anterior até o novo.
  - Os blocos entram com fade em cascata.
  - Tudo é desligado com `prefers-reduced-motion`.
- **Os títulos descrevem o país e não mudam com os filtros.** Abaixo de cada gráfico, uma "leitura do recorte" com ponto laranja descreve o filtro ativo e mostra o n. Com n < 30, aparece o aviso "recorte pequeno, interprete com cautela".
- **Cores com papel fixo**, validadas para daltonismo e contraste nos dois modos:
  - azul `#2B63B0` para continuidade e azul claro `#6FA4E6` para renovação;
  - cinzas para itens fora de foco;
  - laranja `#E36A1E` só para a média de referência, os "sem adversário", o "já na política" e o foco do teclado.
- **Histograma com faixa própria para "sem adversário"** (≈100% dos votos), rotulada em laranja, para que as vitórias sem disputa apareçam como fenômeno distinto.
- **Rigor:** as hipóteses trazem "a base mostra / não mostra". O alerta "novo ≠ rejeição" fica no primeiro bloco. Método e limites ficam no final, com uma tabela por UF que segue os filtros.
- **Dados embutidos agregados em três cubos de contagem**, cada um com as dimensões de filtro (região ou UF, porte, partido, situação) mais uma dimensão de análise (UF, faixa de votação ou ocupação). Não há nomes nem identificadores. Partidos com menos de 150 prefeitos entram como "Outros". Testei antes um cubo único com todas as dimensões, mas ele tinha 4.162 células, 3.344 delas com n = 1 (praticamente a base linha a linha), e foi descartado.
- **Ficaram de fora:** mapa coroplético (GeoJSON pesado; a comparação ordenada com filtro cumpre melhor o papel) e recortes por gênero e raça (a taxa de reeleição praticamente não varia por gênero, e esses recortes são de outros temas).
- **Técnica:** HTML único com CSS e JS embutidos, sem biblioteca de gráficos e com fontes do Google Fonts (há fallback para fontes do sistema). Testado com Playwright em 1280px e 390px e no modo escuro, sem erros no console e sem rolagem horizontal. Os números conferem com a versão 1 (Brasil 44,5%, Sul 37,1%, Norte 50,8%).

## Instruções para o Claude

- Responda e escreva o dashboard em português do Brasil, em linguagem de gestor público, sem jargão estatístico.
- Sempre filtre `cargo = Prefeito` antes de contar pessoas, municípios ou votos.
- Nunca chame "novo prefeito" de "derrota do incumbente": a base não tem candidatos derrotados.
- Diga "associação", nunca "causa". Toda hipótese deve dizer o que a base mostra e o que não mostra.
- Agregue os dados em Python e embuta só o JSON resultante no HTML. O HTML não pode ler o CSV.
- Siga a skill `assinatura-visual-marinho`: paleta azul e cinza com laranja só para destaque, filtros cruzados, agrupamentos e transições suaves.
- Os títulos descrevem o país; o que muda com o filtro vai na leitura do recorte.
- Renderize e confira o dashboard em desktop e celular antes de entregar.
