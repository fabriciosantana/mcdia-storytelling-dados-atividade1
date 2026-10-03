## Qual história meu dashboard conta?

As eleições municipais de 2024 não produziram um vencedor, e sim um condomínio. Seis partidos de centro e centro-direita (PSD, MDB, PP, União, PL e Republicanos) passaram a governar quase 3 em cada 4 prefeituras do país. Quase ninguém venceu sozinho: 95% dos prefeitos se elegeram em coligações, e em 3 de cada 4 chapas o vice é de outro partido. O poder local brasileiro é negociado, fragmentado entre siglas, mas concentrado num mesmo bloco pragmático, que muda de dono conforme a região.

## Contexto do projeto

- **Pergunta norteadora:** como o poder municipal ficou distribuído entre partidos e alianças após as eleições de 2024?
- **Briefing:** a editora de política de um veículo de imprensa prepara um especial sobre o resultado das eleições municipais. O dashboard é a peça central da matéria e precisa se sustentar sozinho, indo além da contagem de vitórias.
- **Base:** `dados/eleitos.csv` (prefeitos e vices eleitos em 2024, TSE, extração de 01/10/2026), com 5.553 municípios.
- **Cuidados de leitura seguidos (do dicionário):**
  - Cada município tem duas linhas (prefeito e vice). As contagens de prefeituras usam somente `cargo = Prefeito`.
  - Os votos da chapa se repetem nas duas linhas e só são somados para prefeitos.
  - O recorte inclui 9 chapas cassadas e 14 eleições históricas documentadas. Elas são mantidas, porque a pergunta é sobre o resultado da eleição e não sobre quem governa hoje, e isso é dito em nota.
  - 16 municípios ficaram fora da base, o que também é informado.
  - Não há população na base. O "tamanho" do município é aproximado pelo total de votos válidos para prefeito, e isso é dito no dashboard.
  - A presença de um partido em alianças é contada pela coluna `composicao_coligacao`. Partidos federados (PT/PCdoB/PV e PSDB/Cidadania) aparecem juntos, por isso a sua presença como membro fica inflada, o que é avisado em nota.

## Público-alvo

Leitor geral de jornal: interessado em política, mas sem familiaridade com dados eleitorais. Lê no celular ou no computador, em poucos minutos, e precisa entender a mensagem sem legenda técnica. Não sabe o que é "federação", "turno decisivo" ou "coligação", então esses termos precisam ser explicados em uma linha.

## Perguntas que os dados respondem

1. Quem ganhou mais prefeituras? (PSD 890, MDB 860, PP 750, União 589, PL 517, Republicanos 437; os 6 somam cerca de 73%.)
2. Ganhar mais cidades significa governar mais gente? (Não exatamente: o PP tem 13,5% das prefeituras, mas só cerca de 10% dos votos válidos; o PL cresce nas cidades grandes, onde chega a cerca de 20% das prefeituras.)
3. Alguém venceu sozinho? (Quase ninguém: só 278 prefeitos se elegeram por partido isolado; a aliança típica tem 4 partidos e algumas passam de 15.)
4. Quem se alia com quem? (Em 77,5% das chapas o vice é de outro partido; as duplas mais comuns combinam PSD, MDB, PP, União e PL entre si.)
5. Esse poder é igual no país todo? (Não: o União domina o Centro-Oeste, o PP o Sul, o MDB o Norte, o PSD o Sudeste, e PSB e PT têm seu peso concentrado no Nordeste.)
6. Conclusão: o que esse arranjo diz sobre a política brasileira? (Poder local pulverizado em siglas, mas concentrado num bloco de centro pragmático que governa por meio de alianças amplas.)

## Decisões de design

- **Título-manchete com a conclusão**, não com o tema ("Seis partidos, três em cada quatro prefeituras"), porque o leitor de jornal precisa da mensagem antes do gráfico.
- **Ordem da narrativa:** quem venceu → peso real (cidades × eleitores) → ninguém vence sozinho → quem se alia com quem → geografia do poder → conclusão. Assim começa no que o leitor espera (contagem) e vai além dela, como pede a editora.
- **Gráficos:**
  - barras horizontais ordenadas para o ranking de partidos;
  - barras pareadas para comparar a fatia de prefeituras com a fatia de eleitores;
  - histograma para o tamanho das alianças;
  - tabela de calor partido × região para a geografia.
  - Sem pizza, sem 3D, sem mapa coroplético (mapa exigiria arquivo de geometria externo e não ajuda a comparar partidos).
- **Cor:** os seis partidos do bloco dominante em um tom de destaque e os demais em cinza, porque a história é "o bloco versus o resto", e não 24 cores diferentes.
- **Ficou de fora:** perfil pessoal (gênero, raça, idade, patrimônio), que é outra história.
- Seguir a skill descrita em `skill.md`.

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos como JSON no próprio HTML. Nunca ler o CSV.
- Seguir a skill descrita em `skill.md`.
- Fazer os cálculos em Python a partir de `dados/eleitos.csv`, respeitando os cuidados de leitura acima, e conferir os totais (5.553 prefeituras).
- Textos em português do Brasil, linguagem de jornal, sem jargão; explicar "coligação" e "federação" em uma frase.
- Cada gráfico tem um título que afirma o achado, e não só descreve o eixo.
- Funcionar bem no celular (cerca de 400px) e no computador.
- Rodapé com fonte (TSE, eleições municipais 2024) e as notas metodológicas.
