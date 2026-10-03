## Qual história meu dashboard conta?

Quem governa os municípios brasileiros é, na maioria das vezes, um homem branco, de 49 anos, com ensino superior: 87% dos prefeitos eleitos em 2024 são homens, 66% se declaram brancos e 60% têm curso superior completo. Mas esse retrato muda muito de região para região e não é o único: há 13% de prefeitas, 31% de prefeitos pardos e 44% de prefeitos reeleitos. O dashboard mostra o retrato médio em poucos segundos e deixa a pessoa explorar as diferenças.

## Contexto do projeto

- **Tema recebido:** 5. Quem governa os municípios.
- **Pergunta norteadora:** quem são as pessoas que governam os municípios brasileiros a partir de 2025?
- **Base:** `dados/eleitos.csv` (11.106 linhas, 5.553 municípios, prefeitos e vices eleitos em 2024) e `dados/dicionario.md`.
- **Cuidados do dicionário que apliquei:**
  - Todas as contas de pessoas usam só `cargo = Prefeito` (5.553 linhas, um por município). O vice entra apenas na comparação de gênero.
  - Município é contado por `codigo_municipio_tse`.
  - Célula vazia não é zero nem "Não": raça/cor ausente em 16 prefeitos e bens ausentes em 178 ficam fora do denominador, e isso está dito na tela.
  - Os dados retratam a **eleição de 2024**, não o ocupante atual. Por isso há um aviso visível sobre as 9 chapas cassadas e as 14 de eleição histórica documentada, mantidas na base.
  - Reeleição é a declaração `ST_REELEICAO`, não uma auditoria do mandato anterior.
  - A idade usada é `idade_posse_2025`.
  - Importei tudo como texto e converti só as colunas numéricas, com vírgula decimal.
- **Referência externa:** o Censo 2022 (IBGE), usado apenas como marca de comparação para gênero e raça/cor. Ele não está na base e vem identificado como referência.

## Público-alvo

Cidadão comum, em um portal de transparência. Decide em poucos segundos se continua explorando, não conhece dados eleitorais e não tem ninguém para explicar. Precisa de linguagem simples, números grandes no topo e precisão sem jargão.

## Perguntas que os dados respondem

1. Qual é o perfil mais comum de quem governa os municípios (gênero, raça/cor, idade, escolaridade)?
2. Quanto esse perfil é maioria absoluta e quanto ele deixa de fora (mulheres, pessoas pardas e pretas, jovens)?
3. A vice-prefeitura é mais diversa que a prefeitura?
4. Quais partidos concentram as prefeituras e quantos prefeitos estão em continuidade (reeleitos)?
5. O retrato muda de uma região para outra?
6. Que ocupações e que patrimônio declarado esses prefeitos têm?

## Decisões de design

- **Título como achado:** o `h1` já entrega a conclusão ("homem branco de 49 anos, com ensino superior"), porque o público decide em segundos. Cada seção também tem como título uma frase com o número principal.
- **Seis indicadores no topo:** quem lê só o topo já sai com o retrato. Os números são os mesmos que as seções detalham.
- **"Em cada 100 prefeitos" (waffle) para gênero:** transforma 13% em 13 quadrados, mais fácil para quem não lida com estatística. Para os demais assuntos uso barras horizontais ordenadas, com a categoria destacada em azul e as demais em cinza.
- **Marca da população (Censo 2022) nas barras de raça/cor:** mostra a distância entre quem governa e a população, sem afirmar causa. Só aparece no recorte Brasil, porque a referência é nacional.
- **Filtro por região (chips):** é a interação principal. Muda gênero, raça/cor, idade, escolaridade, partidos e reeleição. A seção "O Brasil muda de região" fica fixa para comparar as cinco regiões lado a lado.
- **Cores:** azul para destaque geral, laranja só para mulheres e cinza para o resto, com modo escuro. Nada depende só da cor: todo valor aparece em texto.
- **Aviso de limites em caixa própria**, antes do rodapé, em vez de nota de pé de página, porque o público não tem quem explique os limites da base.
- **Tabela com os números** em um `<details>`, para quem prefere ler os valores ou usa leitor de tela.
- **O que ficou de fora:** votação, mapa por município e bens por região. Eles aumentariam o tempo de leitura sem responder à pergunta "quem são".
- **Autocontido:** HTML, CSS e JavaScript sem bibliotecas externas, com os dados já agregados embutidos. Abre com dois cliques.
- Seguir a `skill.md` desta pasta.

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos. Não ler o CSV no navegador.
- Seguir a skill descrita em `skill.md`.
- Para falar de prefeitos, filtrar `cargo = Prefeito`. Para contar municípios, usar `codigo_municipio_tse`. Nunca somar votos das duas linhas da chapa.
- Tratar célula vazia como dado indisponível, nunca como zero ou "Não", e dizer na tela quantos casos ficaram de fora.
- Lembrar que a base é a eleição de 2024, não os ocupantes atuais.
- Não inferir nada além do declarado: sem relação causal, sem palpite sobre identidade.
- Antes de entregar, conferir cada número exibido recalculando a partir do CSV e abrir o HTML em tela larga, em tela de celular e em modo escuro.
