## Qual história meu dashboard conta?

Em 2024, continuidade e renovação dividiram as prefeituras quase ao meio: em 44,5% dos municípios o eleito era o prefeito que disputava a reeleição; em 55,5%, houve troca de titular. O equilíbrio muda com o território (de 31,2% de continuidade em SC a 66,7% em RR), mas quase não muda com o porte da cidade. Onde houve continuidade, a votação do eleito tendeu a ser mais alta.

## Contexto do projeto

- **Tema 4 — Continuidade e renovação.** Pergunta norteadora: *"O que as eleições de 2024 revelam sobre continuidade e renovação no comando das prefeituras?"*
- **Base:** `dados/eleitos.csv` (11.106 pessoas: 5.553 prefeitos e 5.553 vices, em 5.553 municípios de 26 UFs), lida conforme `dados/dicionario.md`. Extração de 01/10/2026.
- **Cuidados do dicionário aplicados e conferidos por script:**
  - Unidade de análise = prefeito (`cargo = Prefeito`): 5.553 linhas, 5.553 `codigo_municipio_tse` distintos, 5.553 `id_chapa`. Nenhum município contado duas vezes; os votos da chapa são lidos só na linha do prefeito.
  - Códigos lidos como texto (todos os `codigo_municipio_tse` têm 5 dígitos).
  - `classificacao_validacao`: 5.530 `ELEITO_ATUAL_TSE`, 9 `CHAPA_CASSADA_TSE`, 14 `ELEICAO_HISTORICA_DOCUMENTADA`. As contagens de continuidade usam os 5.553 (retrato do resultado de 2024); só com os 5.530, o percentual nacional também é 44,5%.
  - **Votos:** nos 23 municípios que não são `ELEITO_ATUAL_TSE`, os votos da chapa aparecem anulados (14 com 0%) ou ausentes (9 vazios) na extração atual. Por isso a análise de votação usa só os 5.530. Esse problema foi encontrado na revisão: a primeira versão contava os 14 zeros como "vitórias com menos de 50%".
  - **Porte:** 9 municípios com zero voto válido registrado ficam fora da análise por porte (5.544 considerados).
  - `reeleito_declaracao_tse` coincide com `candidato_a_reeleicao_tse` nos 5.553 prefeitos.
  - A base descreve o resultado de 2024, não os ocupantes atuais.

### Definição operacional

- **Continuidade:** prefeito eleito com `candidato_a_reeleicao_tse = Sim`. Ele declarou ao TSE concorrer à reeleição, ou seja, já era o prefeito.
- **Renovação do titular:** prefeito eleito com `candidato_a_reeleicao_tse = Não`.
- **O que isso não mede:**
  - Renovação do titular não significa estreante nem primeiro mandato. 73 eleitos nessa situação declararam a ocupação "PREFEITO".
  - Não mede continuidade de grupo político ou de partido. Em 232 municípios, o novo prefeito teve como vice alguém que disputava a reeleição para vice.
  - Não é taxa de sucesso de quem tentou se reeleger: a base só tem eleitos.
  - Não informa quantos prefeitos estavam impedidos de concorrer por estarem no segundo mandato.

## Público-alvo

Turma da aula inaugural de uma escola de governo: gestores, servidores e assessores de diferentes regiões. Conhecem bem o próprio município e pouco os demais. Precisam, em poucos minutos:

1. entender o panorama nacional;
2. perceber que ele esconde diferenças;
3. localizar a própria região ou UF;
4. comparar com o país;
5. sair com uma síntese.

Não são estatísticos: o texto usa linguagem direta, explica "p.p." e não usa jargão.

## Perguntas que os dados respondem (na ordem da história)

1. **Qual o equilíbrio nacional?** Continuidade em 44,5% (2.469) e renovação do titular em 55,5% (3.084).
2. **O número nacional esconde diferenças?** Sim. Norte 50,8%, Centro-Oeste 49,7%, Nordeste 47,5%, Sudeste 43,3%, Sul 37,1%: 13,7 p.p. entre os extremos. O Norte é a única região acima de 50%.
3. **Onde estão as maiores diferenças?** Entre estados, de 31,2% (SC) a 66,7% (RR): 35,5 p.p., mais que o dobro da diferença entre regiões. Entre UFs com 30 municípios ou mais, os extremos são SC (31,2%) e PA (54,5%). 17 das 26 UFs ficam acima da média nacional.
4. **Como o meu território se posiciona?** A seleção de região ou UF compara o recorte com o Brasil. Por porte, o Brasil varia só de 40,1% a 46,5% (6,4 p.p.).
5. **Alguma outra variável contextualiza?** Sim, a votação.
   - Medianas de votos válidos: 65,1% na continuidade e 54,4% na renovação.
   - Entre eleitos com menos de 50% dos votos válidos, 20,1% eram de continuidade (166 de 825).
   - Entre eleitos com 70% a 99,9%, eram 75,0% (744 de 992).
   - É uma associação, não uma causa.
6. **O que isso revela?** Não há um Brasil municipal único. O equilíbrio depende mais do território do que do tamanho da cidade.

## Decisões de design

### Narrativa

- **Arquitetura início → tensão → exploração → aprofundamento → resolução:**
  - **Início:** retrato nacional.
  - **Tensão:** regiões, depois estados.
  - **Exploração:** "A sua realidade".
  - **Aprofundamento:** votação.
  - **Resolução:** síntese, seguida do método.
- **Regra de composição de cada seção:** pergunta ou afirmação → visualização dominante → no máximo um elemento auxiliar → conclusão curta.
- **Títulos que formam um resumo quando lidos em sequência:**
  1. "Continuidade e renovação dividem as prefeituras quase ao meio, mas o equilíbrio muda conforme o território"
  2. "Um país dividido quase ao meio"
  3. "Entre Norte e Sul, 13,7 pontos percentuais de distância"
  4. "Entre os estados, a distância é mais que o dobro da observada entre regiões"
  5. "Pequeno ou grande, o município tem proporção de continuidade parecida"
  6. "Onde houve continuidade, a votação do eleito tendeu a ser mais alta"
  7. "Não há um Brasil municipal único"
- **Hierarquia de texto:** título de seção = afirmação; título do gráfico = achado; subtítulo = como ler; eixos = só medidas; anotações na margem = exceções e extremos.
- **Estado inicial (Brasil) conta a história inteira.** A interação acrescenta camadas sem ser necessária.

### Visualizações (pergunta → evidência → insight)

- **Barra proporcional nacional, larga, com rótulos e definições alinhados a cada segmento.**
  - Pergunta: qual o equilíbrio?
  - Insight: quase metade e metade.
  - Com uma seleção ativa, aparece uma segunda barra (recorte × Brasil).
- **Barras 100% empilhadas por região, ordenadas, com linha vertical do Brasil.**
  - Pergunta: o equilíbrio se repete?
  - Insight: o Norte passa de 50%; o Sul fica bem abaixo.
- **Barras divergentes por UF em relação ao Brasil, em p.p.**
  - O zero é a média nacional: o comprimento codifica o desvio e começa em zero, sem escala truncada.
  - Azul à direita = mais continuidade que o país; ocre à esquerda = mais renovação. Como renovação = 100 − continuidade, o desvio de uma é o espelho da outra, e a cor mantém o significado.
  - UFs com menos de 30 municípios aparecem com barra vazada.
  - A escolha foi preferida a um mapa: 26 valores próximos se comparam melhor por posição do que por área.
- **Dumbbell por porte do município (escala 0–100%).**
  - No estado Brasil, mostra só os pontos nacionais, e o achado é visual: todos perto de 45%.
  - Com uma seleção, liga o recorte (●) ao Brasil (○) em cada faixa.
  - Faixas com menos de 10 municípios aparecem esmaecidas.
- **Histograma espelhado da votação do eleito** (continuidade para cima, renovação para baixo; % do grupo, faixas de 5 p.p.).
  - As medianas são anotadas diretamente no gráfico.
  - Com uma seleção, traços pretos marcam a distribuição do Brasil.
  - Escolhido porque mostra a distribuição inteira, e não só uma média.

### Interação (coordenação, não filtros soltos)

- **Um único estado global (Brasil → região → UF) repercute em todo o painel:**
  - segunda barra no capítulo 1;
  - destaque da região no capítulo 2;
  - destaque das UFs no capítulo 3, com as demais em cinza;
  - dumbbell, leitura e conclusão do capítulo 4;
  - histograma, medianas e notas do capítulo 5;
  - faixa fixa de contexto no topo, que só aparece com seleção ativa e traz "Voltar ao Brasil".
- **Onde se seleciona:**
  - clique direto nas barras de região e de UF (clicar de novo volta ao Brasil);
  - controle segmentado textual e um select compacto no capítulo 4;
  - busca por município, que seleciona a UF dele.
- **Tooltips** respondem "o que estou vendo?": continuidade, renovação, diferença em relação ao Brasil e municípios considerados. São aprofundamento: toda informação essencial também está em rótulos.
- **Transições** de 240 a 320 ms, só de posição, largura, altura e opacidade. Respeitam `prefers-reduced-motion`.

### Sistema visual

- **Grade editorial de 12 colunas (largura útil de 1.240 px) com três larguras:**
  - **narrow** (7 colunas): texto;
  - **standard** (9 colunas): gráficos;
  - **wide** (12 colunas): retrato nacional.
  - As anotações ficam na margem (colunas 10–12). No celular, a página é recomposta em uma coluna.
- **Cores semânticas não partidárias:**
  - continuidade `#355C7D` (azul ardósia);
  - renovação `#C9793A` (ocre); em texto, `#9A5620` para contraste;
  - texto `#20252B`; texto secundário `#66717D`; grade `#DCE1E5`; fundo `#F7F6F2`.
  - O contexto não selecionado usa cinzas (`#AEB5BC` e `#DADDE1`); a seleção usa espessura e sublinhado, sem cor nova.
  - Não há par "bom/ruim" (verde/vermelho): continuidade e renovação não são julgadas.
- **Tipografia:** Source Serif 4 (títulos, texto corrido) e Source Sans 3 (gráficos, rótulos, controles), com alinhamento à esquerda e pouco negrito.
- **Tecnologia:** HTML, CSS e JavaScript puros, sem biblioteca de gráficos. Os gráficos são elementos HTML posicionados em %, o que os torna responsivos sem redesenho; só as fontes vêm por CDN.
- **Dados embutidos:**
  - agregados por UF (contagens por faixa de votos e de porte);
  - uma lista compacta dos 5.553 municípios (nome IBGE, UF, continuidade, % de votos, turno, critério de inclusão), sem nomes de pessoas, usada na busca e nas medianas e histogramas por recorte.
  - Brasil e regiões são somas das UFs, o que garante consistência.
- **Removido no redesenho:**
  - cards e caixas com borda arredondada;
  - grade de 100 quadrados, redundante com a barra;
  - números gigantes e caixas de mediana coloridas;
  - pílulas e barra fixa com desfoque (backdrop blur);
  - os quatro cartões de KPI da síntese;
  - o gráfico de composição da chapa: o achado virou uma frase no método;
  - o dot plot de eixo truncado, trocado por barras divergentes que começam em zero;
  - a paleta verde-petróleo/ocre, trocada por azul/ocre de peso semelhante.
- Skill seguida: `skill.md` desta pasta.

## Limitações

- Renovação do titular ≠ novato, ≠ mudança de grupo político, ≠ mudança de partido.
- Não há perdedores na base: os números não são taxa de sucesso de quem tentou a reeleição.
- A declaração de reeleição não foi auditada individualmente; sucessões e eleições suplementares podem afetar casos específicos.
- Porte medido por votos válidos para prefeito no turno decisivo, como aproximação do eleitorado (não é população).
- A seção de votação exclui 23 municípios com votos da chapa anulados ou ausentes na extração atual.
- Todas as comparações são descritivas; nenhuma diferença é apresentada como causa.

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos (nunca ler o CSV em tempo de execução).
- Seguir a skill descrita em `skill.md`.
- Usar sempre `cargo = Prefeito` como unidade; contar municípios por `codigo_municipio_tse`; nunca somar votos de prefeito e vice.
- Em análises de votos, usar só `classificacao_validacao = ELEITO_ATUAL_TSE` e declarar a exclusão.
- Calcular todo número exibido a partir da base e conferir somas (regiões e UFs = 5.553) antes de publicar. Diferenças em p.p. são calculadas a partir dos valores arredondados exibidos, para que o leitor possa refazer a conta.
- Usar os termos "continuidade" e "renovação do titular", sempre com a definição operacional; nunca "novato" ou "estreante".
- Linguagem descritiva e neutra: sem "melhor", "pior", "sucesso", "fracasso", "domínio" ou causalidade.
- Não modificar arquivos fora de `entregas/tiago-cardoso/`.
