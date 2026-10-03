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

Seguir a skill `painel-narrativo-institucional` (skill.md).

- **Arco narrativo em 8 blocos numerados:** retrato do país → território → porte → como se vence → quem chega → partidos → hipóteses → perguntas para a turma, com uma nota de método no final. O público começa no geral, é confrontado com a diversidade regional e termina refletindo sobre a própria realidade.
- **Títulos que já dizem a conclusão.** Quem só ler os títulos entende a história.
- **Alerta logo no início:** "novo" não quer dizer rejeição. O limite de dois mandatos torna parte da renovação obrigatória. É o principal cuidado contra a leitura errada.
- **Cores com papel fixo**, validadas para daltonismo e contraste nos modos claro e escuro: azul escuro `#2B63B0` para continuidade, azul claro `#6FA4E6` para renovação, cinzas para contexto e laranja `#E36A1E` só para destaques (média nacional, regiões extremas, os 195 sem adversário, "já na política").
- **Gráficos:**
  - Barra única dividida para a proporção nacional.
  - Barras horizontais ordenadas para UF, porte, ocupação e partido, com a linha de referência da média nacional.
  - Histograma agrupado para comparar as distribuições de votos.
  - Números de destaque para medianas e contagens.
  - Sem pizza, sem 3D, sem eixo duplo.
- **Interação a serviço do público:** o filtro por região destaca os estados da região escolhida e apaga os demais, para cada participante "encontrar a sua realidade". Há tooltip com valores absolutos em todas as marcas.
- **Rigor visível:** cada hipótese traz "a base mostra / a base não mostra". As associações não são apresentadas como causas. A nota de método e a tabela de dados ficam ao final.
- **Ficaram de fora:** o mapa coroplético (exigiria um GeoJSON pesado e não acrescenta à comparação ordenada) e a análise por gênero e raça (a taxa de reeleição praticamente não varia por gênero e esse recorte é de outros temas).
- **Técnica:** HTML único com CSS e JS embutidos, sem biblioteca externa, dados já agregados embutidos como JSON, layout responsivo (testado em 1200px e 390px), modo escuro e tabela acessível.

## Instruções para o Claude

- Responda e escreva o dashboard em português do Brasil, em linguagem de gestor público, sem jargão estatístico.
- Sempre filtre `cargo = Prefeito` antes de contar pessoas, municípios ou votos.
- Nunca chame "novo prefeito" de "derrota do incumbente": a base não tem candidatos derrotados.
- Diga "associação", nunca "causa". Toda hipótese deve dizer o que a base mostra e o que não mostra.
- Agregue os dados em Python e embuta só o JSON resultante no HTML. O HTML não pode ler o CSV.
- Use a paleta azul e cinza com laranja só para destaque. Valide as cores (daltonismo e contraste) antes de usar.
- Renderize e confira o dashboard em desktop e celular antes de entregar.
