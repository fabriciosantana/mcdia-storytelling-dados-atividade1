## Qual história meu dashboard conta?

Quem governa os municípios brasileiros não se parece com quem é governado. Em 2024, 65,8% dos prefeitos eleitos se declararam brancos, num país 43,5% branco; pessoas pretas são 2,3% dos prefeitos e 10,2% da população. O dashboard mostra que esse retrato se repete em todas as escalas — quanto maior a cidade, mais branca a prefeitura — e que a cor sobe com mais facilidade até a vice do que até a cabeça da chapa. Fecha com a conta: faltam 1.222 prefeituras para o poder municipal ter a cor do país.

## Contexto do projeto

**Pergunta norteadora:** Que retrato emerge das pessoas eleitas para governar os municípios brasileiros em 2024?

**Briefing:** um observatório da sociedade civil que acompanha a representação política vai lançar seu relatório anual e encomendou o dashboard que abre a publicação. Será compartilhado online e precisa ser compreendido sem alguém ao lado para explicá-lo. A história deve apresentar o retrato racial de quem governa os municípios e tratar o tema com rigor, respeitando o que a base permite e o que não permite afirmar.

**Base:** `dados/eleitos.csv` — 11.106 pessoas (5.553 prefeitos e 5.553 vices) eleitas nas eleições municipais ordinárias de 2024, consolidadas a partir dos repositórios abertos do TSE, extração de 01/10/2026. Lida com `sep=";"`, `encoding="utf-8-sig"`, `decimal=","`, códigos como texto.

**Cuidados do dicionário que foram aplicados:**
- Contagens de pessoas sempre filtradas por `cargo` (prefeito ou vice), nunca somadas.
- Votos e porte do município lidos uma vez por chapa (linha do prefeito).
- `raca_cor_autodeclarada` é **autodeclaração** no registro de candidatura; 16 prefeitos sem informação ficam fora dos percentuais por raça, mas dentro do total de 5.553. Não houve inferência por nome ou foto.
- "Negra" = preta + parda, conforme a convenção do IBGE; "preta" é sempre reportada separadamente.
- `candidato_a_reeleicao_tse` é declaração, não auditoria de mandato anterior — o texto diz "já eram prefeitos e buscaram a reeleição", não "foram reeleitos".
- Bens são valores nominais declarados ao TSE, sem auditoria; usei mediana, não média.
- A base descreve candidaturas e resultados de 2024; não é lista de ocupantes em exercício em 2026. O dashboard não fala em "prefeitos atuais".
- A comparação populacional usa o Censo 2022 (IBGE): branca 43,46%, parda 45,34%, preta 10,17%, indígena 0,60%, amarela 0,44%. "Esperado" = fatia no Censo × 5.553.
- Porte do município = `votos_validos_municipio_turno_atual_tse` (votos válidos para prefeito no turno decisivo), declarado como aproximação do eleitorado.
- Partidos só entram na comparação com 50+ prefeituras, para não exibir percentuais de bases minúsculas.

## Público-alvo

Pesquisadores, jornalistas, gestores públicos e cidadãos interessados em representação política. Têm entre 3 e 10 minutos, chegam por um link, podem estar no celular e não terão ninguém para explicar. Alguns conhecem o debate sobre representação racial; a maioria não conhece a base. Precisam sair sabendo (1) qual é o retrato, (2) onde ele é mais forte e (3) qual é o tamanho da distância para a população — e precisam confiar que os números foram lidos com cuidado.

## Perguntas que os dados respondem

1. Quem é a pessoa típica eleita para governar um município em 2024 (gênero, raça/cor, idade, escolaridade, estado civil, bens, continuidade)?
2. Quanto a composição racial dos prefeitos se afasta da composição da população brasileira, grupo a grupo?
3. O retrato muda com o porte do município? Quem governa as 100 maiores cidades?
4. Como a fatia de prefeitos negros varia entre regiões e unidades da Federação?
5. A cor declarada muda entre o cargo de prefeito e o de vice? Como as chapas se compõem?
6. Quais partidos elegem mais e menos prefeitos negros?
7. Quantas prefeituras a mais ou a menos cada grupo tem em relação ao que sua fatia na população previa?

## Decisões de design

- **Seguir a skill `skill.md` (hud-neon-dataviz).** Estética futurista em modo escuro, mas com as regras de dataviz do skill `dataviz` do Claude Code: forma antes da cor, um eixo por gráfico, marcas finas, legenda sempre que houver 2+ séries, tooltip + tabela em todo gráfico.
- **Número-herói único (65,8%)** abre a página e já responde parte da pergunta; abaixo, seis tiles com o "retrato-robô" para cobrir a pergunta norteadora em sua amplitude antes de aprofundar na cor.
- **Bloco "permite / não permite"** antes do primeiro ato, por exigência do briefing: a base descreve autodeclarações e resultados; não explica causas nem diz quem está no cargo hoje.
- **Seis atos** em ordem narrativa: espelho (quem) → escala (porte) → mapa (onde) → degrau (cargo) → partidos (quem leva) → conta (o que falta). Cada ato tem título-afirmação, gráfico, leitura.
- **Dumbbell** para população × prefeitos e para vice × prefeito: duas medidas por categoria, a distância entre os pontos é a mensagem.
- **Barras horizontais** para porte, UF e partido, com linhas de referência (população negra 55,5%; média 33,5%) para que cada barra tenha contexto. Rótulos diretos só nos extremos.
- **Waffle 10×10** para as 100 maiores cidades: 100 quadrados, uma prefeitura cada, com a única prefeitura preta destacada. Três cores de identidade (validadas em todos-os-pares) + cinza "outras".
- **Matriz 2×2** de chapas (prefeito × vice, branco/negro) com rampa sequencial — a célula mais clara é a mais frequente.
- **Barras divergentes** para "a conta": a sobra de um lado é a falta do outro.
- **Paleta “Beautiful Blues”** (color-hex #1294: `#011f4b · #03396c · #005b96 · #6497b1 · #b3cde0`), por pedido do briefing. É monocromática, então as funções de cor foram reorganizadas: `#b3cde0` = medida/foco, `#6497b1` = contexto, rampa `#005b96→#b3cde0` para mapa e matriz. No waffle, a identidade de raça/cor é por luminosidade e o tom mais claro vai para **preta** (a classe mais rara — ênfase), de propósito, para que a ordem de luminosidade não reproduza uma hierarquia de tons de pele. Rampa validada com `validate_palette.js --ordinal`; o teste categórico acusa falta de matiz por construção, e a separação (ΔE 17,6 sob daltonismo) passa.
- **Tema claro/escuro**: botão no cabeçalho; os dois temas usam os mesmos cinco azuis com papéis invertidos (no claro, `#005b96` é a medida e `#011f4b` a tinta). Os gráficos só usam tokens CSS, então a troca é instantânea e não redesenha nada. Rampa clara validada com o verificador em modo claro sobre branco. A preferência fica em `localStorage`; sem preferência, segue o sistema.
- **Filtros e seleção cruzada**: uma linha fixa de filtros (região, UF, porte, partido, cargo, gênero) acima dos seis atos. Todos os gráficos, tiles e tabelas recalculam a partir de um cubo de contagens embutido (UF × porte × cargo × gênero × raça/cor × partido, 3.398 células) e de um cubo de chapas (UF × porte × cor do prefeito × cor do vice). Clicar numa barra de porte/UF/partido, num tile de região ou numa UF do mapa aplica o filtro; clicar de novo desfaz. O herói e o retrato-robô ficam acima dos filtros e são nacionais; a mediana de bens não é decomponível e recebe a etiqueta “Brasil · não filtra”. Ao filtrar, os parágrafos de leitura ganham a etiqueta “Texto: recorte nacional”.
- **Mapa**: a base tem `codigo_ibge` e `uf`, mas nenhuma geometria ou coordenada. Um mapa por UF ficou viável embutindo a malha oficial do IBGE (API de malhas, qualidade mínima, simplificada para 60 KB) e juntando pelo código da UF; a origem está no rodapé. Mapa por município foi descartado: exigiria 5.570 polígonos (megabytes) e não leria melhor do que as 26 barras ordenadas.
- **Sem bibliotecas**: SVG gerado por JavaScript puro, dados agregados embutidos como JSON. Fontes do Google Fonts com fallback para o sistema; o arquivo abre offline.
- **O que ficou de fora**: ocupação declarada, escolaridade por raça e idade por raça (diferenças pequenas, não mudariam a história); mapa municipal (ver acima); comparação com 2020 (a base não permite); Censo por região/UF (não está na base; a comparação é sempre com o Censo nacional, e o rodapé diz isso).

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos. Não ler o CSV no navegador.
- Seguir a skill descrita em `skill.md`.
- Calcular todos os agregados em Python/pandas a partir de `dados/eleitos.csv` antes de escrever o HTML; conferir cada número citado no texto contra o agregado.
- Validar a paleta com `validate_palette.js` antes de usá-la; não estimar segurança para daltonismo a olho.
- Filtros só sobre agregados embutidos; cada card mostra o recorte ativo; o que não filtra diz que não filtra.
- Renderizar e olhar o resultado (desktop e 390px) antes de entregar; corrigir colisão de rótulos e rolagem horizontal.
- Nunca inferir raça por nome ou foto; usar apenas `raca_cor_autodeclarada`.
- Escrever em português do Brasil; separador decimal vírgula; milhar com ponto.
