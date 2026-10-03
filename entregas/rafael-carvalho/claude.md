## Qual história meu dashboard conta?

Nas eleições municipais de 2024, mulheres são 13,2% dos prefeitos e 19,3% dos vices nos 5.553 municípios cobertos. Homens ocupam os dois cargos em 69,6% das chapas. A presença feminina varia entre territórios, oferecendo pontos de atenção para uma audiência pública sobre participação política, sem atribuir causas que a base não permite demonstrar.

## Contexto do projeto

Atividade individual de Storytelling de Dados, Mestrado em Administração Pública do IDP. Tema 1: Mulheres e homens no comando das prefeituras. Pergunta norteadora: como mulheres e homens estão presentes no comando dos municípios brasileiros eleitos em 2024? Trabalho produzido com Codex por solicitação direta do estudante. Este documento registra o contexto consolidado durante a conversa, sem alegar ter sido carregado previamente como configuração.

## Público-alvo

Comissão do Legislativo em audiência pública: parlamentares, assessorias técnicas e representantes da sociedade civil, com pouco tempo e opiniões formadas. Apresentar uma mensagem principal imediatamente, seguida de evidências e perguntas para aprofundamento.

## Perguntas que os dados respondem

- Qual a participação de mulheres e homens em cada cargo?
- Como a participação feminina varia entre regiões e estados?
- Quantas chapas têm mulheres na prefeitura, na vice, em ambos ou em nenhum cargo?
- A leitura muda ao restringir o universo a chapas marcadas como ELEITO na extração do TSE?

## Recorte e rigor

Fonte: https://github.com/prof-danny-idp/storytelling-dados-atividade1/blob/main/dados/eleitos.csv e respectivo dicionário. Extração de referência: 01/10/2026. CSV UTF-8, separador ponto e vírgula. Preservar identificadores como texto.

Recorte principal histórico: 5.553 municípios, incluindo 9 chapas com cassação e 14 com eleição histórica documentada. Filtro alternativo: 5.530 municípios marcados como ELEITO_ATUAL_TSE. Não identificar o resultado como lista de governantes atuais. Há 16 municípios fora da cobertura.

Separar os cargos e identificar municípios por codigo_municipio_tse. Associar as duas pessoas por id_chapa. Percentual feminino = mulheres no cargo e território / total do mesmo cargo e território. Não calcular médias simples de percentuais estaduais. Não usar votos neste trabalho. Não transformar ausência de dados em zero. O campo genero_tse está preenchido em todas as linhas e é uma classificação cadastral, sem inferência de identidade de gênero.

## Decisões de design

- Ordem: panorama, diferença entre cargos, territórios, composição das chapas e implicações para o debate.
- Cores solicitadas pelo estudante: azul-marinho #171a4a para homens e roxo #4c007d para mulheres, com #000020, #2f2c79 e #7f00b2 como apoio. Texto e contagens acompanham a cor. Tipografia e espaçamento preservados.
- Barras com escala de 0 a 100%, contagens e percentuais com uma casa decimal. Sem gráfico de pizza ou escala truncada.
- Mapa por estado com malha simplificada do IBGE, embutida no HTML. Controle para visualizar participação de mulheres (roxo) ou homens (azul-marinho). Escala fixa de 0 a 100% compartilhada entre gêneros, cargos e recortes. Comparar estados sem afirmar que um estado inteiro ou cada município tem o mesmo resultado.
- Estados fora da região selecionada aparecem em cinza, assim como o Distrito Federal, que não tem eleição municipal. Consulta por clique, toque e teclado mostra percentuais e contagens de ambos os gêneros. A tabela e as barras complementam o mapa.
- Filtros de região, cargo e critério. O título mantém a referência nacional; os demais indicadores seguem o território selecionado, explicitado na tela.
- CSS, JavaScript e dados agregados embutidos. Sem CDN, fontes externas ou requisições de dados.
- Tabela de estados para consulta, notas metodológicas abertas e apresentação responsiva.

## Limites e verificação

Não inferir tendência, causalidade, chance de vitória ou representatividade frente à população. A base só contém pessoas incluídas no recorte de eleitos. Cada município tem peso igual. Conferir unicidade, pares prefeito/vice, soma das composições e consistência entre agregados nacionais, regionais e estaduais. Testar todos os filtros no navegador offline.

## Revisão do título e pictogramas

Título escolhido pelo estudante: O Brasil precisa de mais mulheres! É uma posição normativa do estudante; a evidência descritiva aparece no subtítulo: Mulheres ocupam apenas 13,2% das prefeituras no recorte nacional, com percentual atualizado pelo critério de inclusão. Não apresentar a frase do título como conclusão causal ou como indicador calculado.

Pictogramas usam roxo vivo #a600d9 e azul-marinho #303b68 para aumentar a distinção visual. Cada cartão tem 100 símbolos, com preenchimento parcial correspondente à casa decimal do percentual exibido. A nota de leitura é compartilhada entre os três cartões e explicita as diferentes unidades: pessoas nos dois primeiros, municípios no terceiro.

O mapa alterna mulheres e homens por dois botões com indicação de estado ativo. Selecionar um estado preenche sua área em roxo #7f00b2 ou azul-escuro #000020. Os demais ficam com 50% de opacidade no modo mulheres e 30% no modo homens. Um segundo clique, Enter ou espaço no mesmo estado desfaz a seleção; o botão Limpar seleção também está disponível. A nota distingue destaque visual de valor percentual. O DF pode receber destaque de seleção, mantendo o aviso de ausência de eleição municipal e sem inventar valores.


## Identificação e formato da entrega

Estudante: Rafael Carvalho. GitHub: rafael7carvalho. Este arquivo de contexto do Codex é entregue como claude.md por orientação do professor confirmada pelo estudante na conversa. O nome é uma exigência de entrega; o trabalho foi produzido com Codex.

