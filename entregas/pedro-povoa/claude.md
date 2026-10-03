## Qual história meu dashboard conta?

Ninguém governa sozinho. Nas eleições municipais de 2024, nenhum partido ficou com sequer 1 em cada 5 prefeituras, só 5% dos prefeitos venceram sem coligação e em 3 de cada 4 chapas prefeito e vice são de partidos diferentes. O poder local brasileiro não se divide entre siglas que se enfrentam: é compartilhado por siglas que se combinam, e isso ajuda a entender a política nacional.

## Contexto do projeto

- **Disciplina:** PCDIA – Storytelling de Dados (IDP), Atividade 1.
- **Tema recebido:** O mapa partidário de 2025.
- **Pergunta norteadora:** Como o poder municipal ficou distribuído entre partidos e alianças após as eleições de 2024?
- **Briefing:** a editoria de política de um veículo de imprensa quer um dashboard como peça central de um especial sobre o resultado das eleições municipais. A história precisa se sustentar sozinha e ir além da contagem de vitórias: mostrar como o poder local se organizou entre partidos e alianças e o que isso diz sobre a política brasileira.
- **Base:** `dados/eleitos.csv` (TSE, 5.553 municípios, 11.106 linhas: prefeito e vice por município).
- **Cuidados do dicionário aplicados:**
  - contagens de partido usam só `cargo = Prefeito` (uma linha por município); votos e percentuais se repetem nas duas linhas da chapa, então nunca foram somados com o vice;
  - recorte completo (5.553 municípios), com nota sobre 23 municípios de situação judicial menos firme, porque a pergunta é sobre o resultado das urnas de 2024 e não sobre o ocupante atual;
  - células vazias tratadas como ausência de dado, não como zero;
  - "eleitorado governado" = votos válidos para prefeito no município, e não população;
  - federações (PT/PCdoB/PV e PSDB/Cidadania) contadas pelos partidos que as compõem.
- **Ideologia:** a base não traz classificação ideológica. Foi usada uma fonte externa e citada (survey ABCP 2018, Bolognesi, Ribeiro e Codato, *Dados*, 2023), restrita a um capítulo, com chave de sensibilidade para MDB, PSD e PSDB, que ficam a centésimos da fronteira.

## Público-alvo

Leitores gerais de um jornal: interessados em política, sem familiaridade com dados eleitorais. Leem em celular ou computador, em poucos minutos, sem ninguém para explicar. Precisam sair entendendo que o poder local é feito de alianças, e não de vitórias isoladas de partidos.

## Perguntas que os dados respondem

1. Quão pulverizado ficou o poder? Quais partidos lideram, e isso muda se a régua for eleitorado em vez de prefeituras?
2. Quanto do poder local é de partido sozinho e quanto é de coligação? Qual o tamanho típico de uma coligação?
3. Quem se alia com quem na chapa de prefeito e vice, e com que frequência a chapa atravessa campos ideológicos?
4. O desenho muda conforme o porte da cidade?
5. Como cada estado se organiza: quem lidera e quão pulverizado é?
6. Para onde pendeu o poder, segundo uma classificação ideológica publicada, e quão sensível é essa leitura?

## Decisões de design

- **Narrativa rolável em 6 capítulos**, cada um com título que diz a conclusão. A editora pediu uma história que se sustente sozinha, e um painel de filtros exige que o leitor já saiba o que procurar.
- **Ordem:** pulverização, aliança, dupla mista, porte, mapa, ideologia, e fecho com a leitura sobre a política brasileira. Vai do fato simples (quem ganhou) ao arranjo (como se organizou) e à interpretação.
- **Gráficos:** barras horizontais para ranking; colunas para distribuição do tamanho das coligações; barras com duas cores para pares de partidos; mapa de calor para partido por porte; cartograma de quadrados por UF (leve, sem geometria externa e legível em celular); barras empilhadas 100% para campos ideológicos. Sem pizza, sem eixo truncado.
- **Cores dos partidos:** identidade usada pelas siglas (Wikipédia pt, predefinição de cores), só para as 10 maiores; as demais em cinza. Como vários são azuis parecidos, toda barra e todo quadrado têm a sigla escrita (a cor nunca é o único canal). Os campos esquerda, centro e direita têm paleta própria, sem relação com as cores partidárias.
- **Interação mínima:** alternar prefeituras e eleitorado, tocar num estado, ligar a chave de sensibilidade. Tudo o mais é leitura direta.
- **O que ficou de fora:** perfil pessoal dos eleitos (gênero, raça, bens), por fugir da pergunta; mapa municipal completo, por exigir geometria externa.
- **Seguir a skill de `skill.md`.**

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos e sem CDN.
- Seguir a skill descrita em `skill.md`.
- Contar partidos só nas linhas de prefeito; nunca somar votos de prefeito e vice juntos.
- Toda afirmação numérica do texto precisa bater com os dados embutidos; recalcular antes de entregar.
- Citar a fonte e a ressalva de qualquer classificação externa (ideologia, cores) na própria tela.
- Escrever em português do Brasil, em tom jornalístico sóbrio, sem jargão eleitoral não explicado.
