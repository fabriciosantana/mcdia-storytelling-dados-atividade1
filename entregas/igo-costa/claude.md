## Qual história meu dashboard conta?

A maioria das pessoas incluídas como eleitas para prefeito e vice-prefeito em 2024 se autodeclarou branca: 7.084 de 11.106, ou 63,8%. Esse total esconde diferenças entre cargos e regiões. Pessoas pretas aparecem proporcionalmente mais entre os vices, enquanto a categoria parda é a mais frequente no Norte e no Nordeste no recorte histórico completo. O dashboard descreve esse retrato sem atribuir causas ou medir a distância em relação à população.

## Contexto do projeto

Tema: **A cor do poder municipal**.

Pergunta norteadora: **Que retrato racial emerge das pessoas eleitas para governar os municípios brasileiros em 2024?**

Um observatório da sociedade civil encomendou um dashboard para abrir seu relatório anual de representação política. Ele será compartilhado on-line e deve ser compreensível sem mediação. Esta entrega foi preparada com auxílio do Codex. O nome do arquivo segue o enunciado, mas não indica uso efetivo do Claude.

## Público-alvo

Pesquisadores, jornalistas, gestores públicos e cidadãos interessados. Usar português claro, explicar os denominadores e apresentar método e limites no próprio dashboard.

## Perguntas que os dados respondem

- Qual a composição racial autodeclarada das pessoas incluídas no recorte?
- Como essa composição varia entre prefeitos e vice-prefeitos?
- Como as distribuições diferem entre regiões e UFs?
- O retrato muda ao restringir aos registros marcados como ELEITO na extração atual do TSE?

## Dados e regras de análise

Fonte: `eleitos.csv` e `dicionario.md` fornecidos na atividade. Separador ponto e vírgula, UTF-8 com BOM e vírgula decimal. Extração de referência: 01/10/2026.

Cada linha é uma pessoa. Contar por `id_candidato_tse`, separar `cargo` para comparar cargos e usar uma linha de prefeito por chapa para contar municípios. Preservar todas as cinco categorias publicadas em `raca_cor_autodeclarada`; células vazias viram categoria analítica “Sem informação”, sem inferência racial.

Recorte padrão: 11.106 pessoas, 5.553 municípios, 26 UFs, cinco regiões. Inclui 11.060 pessoas marcadas ELEITO no TSE, 18 pessoas de chapas cassadas e 28 pessoas de eleições históricas documentadas. Permitir restringir a `classificacao_validacao = ELEITO_ATUAL_TSE`, que reúne 5.530 municípios. Não apresentar a base como relação de governantes em exercício em 2026.

Percentuais usam todas as pessoas do respectivo recorte, incluindo os registros sem informação. Para comparar cargos, cada cargo tem seu próprio denominador. Calcular diferenças em pontos percentuais com valores não arredondados. Exibir uma casa decimal e contagens inteiras. Pessoas negras significa a soma de pretas e pardas, explicitada junto ao indicador e sem suprimir as categorias originais.

Não calcular taxa de sucesso eleitoral: não há candidaturas derrotadas. Não medir sub ou sobrerrepresentação populacional: não há base demográfica comparável. Não concluir evolução histórica, causalidade, discriminação individual ou identidade racial por nome, imagem ou pertencimento quilombola/indígena.

## Decisões de design

- Narrativa: composição nacional, comparação de cargos, distribuição regional e conclusão com limites.
- Layout editorial com fundo claro, títulos em Georgia, texto em fonte de sistema e contraste alto.
- Barras horizontais com escala fixa de 0 a 100% para composição e comparação de cargos. Barras empilhadas de 100% para regiões.
- Cores distinguem categorias e não reproduzem cores de pele; rótulos e tabela evitam depender apenas de cor.
- Filtros por território, cargo e inclusão. A comparação mantém ambos os cargos. O destaque e a conclusão nacional permanecem fixos e são identificados como referência do recorte completo.
- Tabela consultável, exportação CSV do recorte e impressão. Layout adaptado a telas pequenas.
- HTML autocontido, sem CDN, leitura de CSV externo ou fontes remotas. Incorporar somente contagens agregadas, sem nomes e identificadores pessoais.

## Validação e pendências de entrega

Foram conferidas a unicidade das 11.106 candidaturas e 5.553 chapas, as somas das categorias e o recorte TSE. No Chrome, foram verificadas 192 combinações de filtros sem erros de JavaScript, a limpeza de filtros, a geração do conteúdo CSV e a impressão em PDF. Capturas de desktop (1.440 px) e celular (390 px) foram revisadas, sem transbordamento horizontal. A gravação efetiva do download foi cancelada pelo navegador de teste; o conteúdo gerado foi validado separadamente.

A entrega está na pasta `entregas/igo-costa`, usando o nome Igo Costa configurado no Git e o padrão de nome e sobrenome exigido pelo validador. O enunciado pede uso do Claude: a autoria assistida pelo Codex deve ser tratada com transparência antes da submissão. Não inventar prompts ou atribuir esta conversa ao Claude.
