## Qual história meu dashboard conta?

Nas eleições municipais de 2024, 734 mulheres e 4.819 homens foram eleitos prefeitos nos 5.553 municípios da base: 13,2% de prefeitas. Essa proporção não é uniforme no território: varia de 9,2% no Sudeste a 18,5% no Nordeste entre as regiões, e de 2,6% (ES) a 26,7% (RR) entre as UFs, o que indica onde olhar com mais atenção. Como recorte complementar, a escolaridade declarada diferencia os dois grupos: 80,8% das prefeitas e 56,3% dos prefeitos têm superior completo. O dashboard descreve, não recomenda: a audiência tira as próprias conclusões.

## Contexto do projeto

- **Tema:** "Mulheres e homens no comando das prefeituras".
- **Pergunta norteadora:** "Como mulheres e homens estão presentes no comando dos municípios brasileiros eleitos em 2024?"
- **Base:** `dados/eleitos.csv` (11.106 linhas, 72 colunas: prefeito e vice de 5.553 municípios) e `dados/dicionario.md`. Os arquivos soltos na raiz do projeto não foram usados.
- **Cuidados do dicionário considerados:** separador `;` e decimal `,`; códigos lidos como texto; célula vazia não é zero nem "Não"; votos repetidos nas linhas de prefeito e vice; a base descreve a eleição de 2024 (extração em 01/10/2026) e não os ocupantes atuais dos cargos; gênero é o campo `genero_tse` do cadastro do TSE, sem inferência por nome ou imagem.
- **Resultado dos números:** todos calculados do CSV por um script de agregação; só os agregados estão embutidos no HTML.

## Público-alvo

Comissão do Legislativo sobre participação política, em audiência pública: parlamentares, assessorias técnicas e sociedade civil. São pessoas com pouco tempo e opiniões já formadas, que precisam sair com uma leitura clara e fundamentada. Por isso: resposta principal na primeira tela, texto curto, títulos que dizem o achado, linguagem descritiva e nenhuma recomendação política.

## Perguntas que os dados respondem

1. Quem está no comando das prefeituras eleitas em 2024? (13,2% de prefeitas e 86,8% de prefeitos, em 5.553 municípios)
2. Essa distribuição é igual em todo o país? (não: de 9,2% a 18,5% entre as cinco regiões)
3. Onde estão as diferenças que merecem atenção? (entre as 26 UFs, de 2,6% a 26,7%; 16 acima e 10 abaixo da média nacional)
4. Há uma dimensão complementar que diferencie os dois grupos? (escolaridade declarada)

## Recorte e metodologia

- **Universo:** `cargo = Prefeito`: 5.553 pessoas, uma por município. Vice-prefeitos excluídos.
- **Unidade de análise:** a pessoa eleita prefeita ou prefeito; municípios contados por `codigo_municipio_tse` (5.553, sem duplicidade; `id_chapa` também único).
- **Indicador:** % de prefeitas = prefeitas ÷ prefeituras do recorte (nacional, região ou UF). Cálculo com precisão total; arredondamento só na exibição (formato brasileiro).
- **Universo mantido por inteiro:** inclui chapas com cassação registrada ou eleição documentada historicamente (23 municípios). Teste de sensibilidade: usando só `ELEITO_ATUAL_TSE` (5.530), a proporção seria 13,25%, praticamente igual a 13,2%.
- **Escolaridade:** `escolaridade` agrupada em Superior completo, Superior incompleto, Médio completo e Médio incompleto ou menos (inclui fundamental e "lê e escreve"). Sem células vazias nesta coluna entre os prefeitos.
- **Exploração que não entrou:** idade (média de 49 anos nos dois grupos), candidatura à reeleição (13,0% a 13,5%), raça/cor (grupos pequenos e 16 vazios), partido (muitas siglas, sem pergunta clara), porte do município e votos (não acrescentavam resposta à pergunta; votos não foram usados).
- **Validação:** recomputação independente com o módulo `csv` do Python, comparada com os dados embutidos: total, municípios, mulheres + homens, soma de regiões e de UFs, escolaridade.

## Decisões de design

- Peça editorial de leitura vertical: abertura escura com números grandes, seções com muito espaço em branco, fechamento escuro.
- Paleta fornecida: `#27424B` para títulos, texto e fundos de destaque; `#6399AE` e `#67A5BF` para os dados; `#859EB6` e `#DBD9D6` para apoio. Sem rosa/azul estereotipado: mulheres e homens são distinguidos por posição, rótulos, valores e intensidade.
- Texto sempre em `#27424B` sobre fundo claro ou branco sobre `#27424B`, para manter o contraste; as cores azuis ficam em barras e superfícies, sem texto pequeno sobre elas (rótulos e valores ficam fora das barras).
- Tipografia sans-serif do sistema, títulos grandes, corpo de 17 a 18 px.
- Sem bibliotecas externas: HTML, CSS e JavaScript em um só arquivo, com os dados agregados embutidos.
- Interação mínima e útil: tooltip por barra (também por foco de teclado) e botões que destacam as UFs de uma região. A história funciona sem clicar.
- Responsivo: testado em 1366, 820 e 375 px de largura, sem rolagem horizontal.

## Decisões de visualização

- **Panorama:** o 13,2% é o número dominante da abertura (título "A cada 100 prefeituras, 13 são comandadas por mulheres"), com 5.553 municípios, 734 prefeitas e 4.819 prefeitos em segundo plano e uma barra de composição 100% com rótulos fora da barra: resposta visível sem tooltip.
- **Regiões:** barras horizontais com o percentual de prefeitas, ordenadas, com eixo de 0 a 30% (o mesmo das UFs) e linha da média nacional. O rótulo mostra "prefeitas de municípios" para deixar o denominador claro. Uma nota alerta que número absoluto não equivale à presença relativa.
- **UFs:** 26 barras horizontais ordenadas por percentual, com número de prefeitas e total de municípios. UFs com menos de 30 municípios (RR, AP, AC) são marcadas com asterisco e nota explicativa, porque o percentual é sensível a poucos casos (a hachura da primeira versão foi retirada para deixar o gráfico mais limpo).
- **Escolaridade:** duas barras horizontais simples comparando só a proporção com superior completo (80,8% das prefeitas e 56,3% dos prefeitos), com a diferença de 24,5 pontos percentuais destacada. As demais categorias ficam em tabela acessível recolhida e no tooltip, para não competirem com a mensagem principal.
- **Descartados:** mapa (não melhorava a resposta; as barras ordenadas comparam melhor as UFs e o mapa daria destaque visual a UFs pequenas); pizza para as UFs; gráficos de idade, reeleição, partido e votos; qualquer filtro que não ajudasse a narrativa.
- **Títulos** reescritos depois dos resultados e revisados na segunda rodada: "A proporção muda quando olhamos para o território", "A diferença aumenta quando olhamos estado por estado" e "A escolaridade declarada também difere entre os grupos". O texto usa "municípios analisados" e "prefeitos eleitos", sem dizer que prefeituras foram eleitas.

## Limitações dos dados

- A base descreve a eleição de 2024 (consulta em 01/10/2026). Não é uma fotografia de quem ocupa o cargo hoje: há chapas com cassação registrada ou eleição documentada historicamente.
- 16 dos 5.569 municípios com eleição em 2024 ficaram fora da base por falta de confirmação; o DF não tem eleição municipal (26 UFs).
- Gênero é o do cadastro do TSE (`genero_tse`), e não identidade de gênero. Escolaridade é declarada no registro de candidatura.
- UFs com poucos municípios geram percentuais instáveis.
- A análise é descritiva: não mede causas e não permite explicar as diferenças entre regiões, UFs ou escolaridade.
- Os dados de votos, patrimônio e raça/cor existem na base mas não foram usados.

## Instruções para o Claude

- Gerar um único `dashboard.html`, autocontido, com os dados agregados embutidos; nunca ler o CSV em tempo de execução.
- Seguir a skill descrita em `skill.md`.
- Filtrar `cargo = Prefeito`, contar municípios por `codigo_municipio_tse` e não somar votos das duas linhas.
- Linguagem descritiva e neutra: sem causalidade não demonstrada, sem recomendação política e sem julgamento sobre homens ou mulheres.
- Sempre indicar que os dados são de 2024.
