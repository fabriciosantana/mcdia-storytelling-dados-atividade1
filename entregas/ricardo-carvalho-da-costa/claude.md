## Qual história meu dashboard conta?

De cada 100 pessoas eleitas prefeitas em 2024, cerca de **13 são mulheres**. A maioria se declara branca, tem 49 anos e curso superior completo. Esse retrato muda de região para região — e muda sobretudo em raça/cor: no Sul, 93,9% dos prefeitos se declaram brancos; no Norte, 33,2%. O que quase não muda é a ausência de mulheres: mesmo na região com mais prefeitas elas não passam de 18,5%. O dashboard entrega essa mensagem em poucos segundos, com cem figuras que qualquer pessoa consegue contar, e deixa explorar o resto por região.

## Contexto do projeto

- **Tema recebido:** 5. Quem governa os municípios.
- **Pergunta norteadora:** quem são as pessoas que governam os municípios brasileiros a partir de 2025?
- **Base:** `dados/eleitos.csv` (11.106 linhas, 5.553 municípios, prefeitos e vices eleitos em 2024) e `dados/dicionario.md`.
- **Cuidados do dicionário que apliquei:**
  - Todas as contas de pessoas usam só `cargo = Prefeito` (5.553 linhas, um por município). Os vice-prefeitos entram apenas na comparação de gênero.
  - Município é contado por `codigo_municipio_tse`.
  - Célula vazia não é zero nem "Não": raça/cor ausente em 16 prefeitos e bens ausentes em 178 ficam fora do denominador. Cada gráfico mostra na tela o denominador que usou e quantos casos ficaram de fora.
  - Os dados retratam a **eleição de 2024**, não o ocupante atual: 9 chapas cassadas e 14 de eleição histórica documentada seguem na base.
  - Reeleição é a declaração feita no registro de candidatura, não uma auditoria do mandato anterior.
  - A idade usada é `idade_posse_2025`.
- **Referência externa:** Censo 2022 (IBGE), usado só como parâmetro de comparação nacional para gênero e raça/cor. Não está na base e vem identificado como referência.

## Público-alvo

**Duas pessoas ao mesmo tempo: a alta gestão em uma reunião e o cidadão comum em um portal.** O que elas têm em comum é o pouco tempo e a ausência de alguém para explicar. O que as separa é a familiaridade com gráficos — e a resposta foi escrever para quem tem menos.

Isso definiu quase todas as escolhas: a conclusão principal vem em uma frase curta na primeira tela, o gráfico de abertura são cem figuras de pessoas que dá para contar sem saber ler percentual, todo valor aparece escrito ao lado da barra, e termos como "mediana" viraram "idade central do grupo", com a explicação completa guardada em "Sobre os dados". O modo apresentação atende especificamente a reunião e projeção: aumenta as fontes e esconde as notas secundárias.

## A história, em perguntas

O painel é organizado como uma sequência de perguntas, e não como um catálogo de gráficos:

1. **Quem foi eleito?** — raça/cor, escolaridade, idade e ocupação.
2. **Quantas mulheres e quantos homens?** — prefeitura e vice-prefeitura lado a lado.
3. **Como esse perfil se compara à população?** — a única comparação externa que a base permite.
4. **O que muda entre as regiões?** — um indicador por vez, cinco regiões na mesma escala.
5. **Como se distribuem partidos e reeleição?**
6. **O que esses dados permitem concluir?** — limites, glossário e tabela completa.

## O que a base não permite, e o que fiz no lugar

A base é um retrato único da eleição de 2024: **não tem série temporal, meta institucional nem indicador de desempenho de gestão.** Nada disso foi inventado. Onde um painel executivo normalmente traria evolução e metas, entra a comparação com o Censo 2022 e a comparação entre regiões — as duas únicas comparações legítimas disponíveis. Onde traria recomendações, entra "O que esses dados permitem concluir", que diz explicitamente qual outra base seria necessária para decidir.

## Decisões de design

- **Identidade institucional, sem instituição.** Azul institucional na faixa e nos gráficos, laranja só para o que está em destaque, branco e cinzas claros nas áreas de leitura. **Não usei logotipo, nome nem marca de nenhuma instituição real**, e não consultei a identidade oficial de nenhuma delas para copiá-la: um painel de dados eleitorais com a identidade precisa de outra organização se lê como produto oficial dela, mesmo com aviso. O rodapé identifica o trabalho como acadêmico e declara que não é sistema oficial de ninguém.
- **Primeira tela com uma pergunta respondida, não um resumo longo.** Título, uma frase de conclusão, quatro números grandes e o gráfico protagonista. Sem parágrafo antes do gráfico.
- **Cem figuras de pessoas** para a participação feminina, todas do mesmo tamanho, distinguidas só por cor abstrata — nunca por tom de pele ou formato que sugira estereótipo. O arredondamento está dito na tela.
- **Cada gráfico declara o seu recorte e o seu denominador** ("Recorte: Nordeste · 1.791 prefeitos · 1.787 declararam raça/cor").
- **Selo "Brasil · não muda com o filtro"** nos dois blocos que permanecem nacionais: ocupações e comparação com o Censo. Antes o painel sugeria que tudo acompanhava o filtro, o que não era verdade.
- **A comparação com a população só existe no recorte Brasil.** A referência do Censo é nacional; usá-la contra uma região isolada produziria uma leitura falsa. Quando há região selecionada, o bloco continua no Brasil e explica o porquê.
- **Comparação lado a lado, com os dois percentuais escritos**, sem depender de legenda distante nem de passar o mouse, e com uma frase curta dizendo o tamanho da diferença.
- **Comparação regional com seletor de indicador**, as cinco regiões sempre na mesma escala e a região do filtro destacada em laranja. O título diz o resultado observado, nunca a causa.
- **Nada de categoria fixada no texto.** A categoria majoritária é apurada no recorte, porque ela muda: no Norte a maioria se declara parda, e no Nordeste pardos e brancos empatam tecnicamente (47,9% e 47,8%) — caso em que o texto diz "praticamente empatados" em vez de eleger um vencedor.
- **Animações de 620 ms**, só na entrada e na troca de filtro. Ao mudar o recorte, os números transitam do valor anterior para o novo, em vez de reiniciar em zero. Com `prefers-reduced-motion` tudo aparece pronto, e na impressão os valores são congelados no número final.
- **Tema claro e escuro manuais**, com a mesma identidade nos dois, e **modo apresentação** com fontes maiores e menos texto por tela.
- **Impressão limpa:** sem filtros nem controles, com o recorte impresso como texto e os cartões inteiros.

## Precisão dos textos: o que corrigi

- "A vice-prefeitura é mais aberta" → **"A participação feminina é maior entre vice-prefeitos"**. A primeira versão atribuía uma intenção; a segunda descreve o dado.
- "O que explica a diferença entre os recortes" → **"O que muda entre as regiões"**. O painel mostra variação, não explicação.
- **"Não concorreram como reeleição" não é "novo no cargo".** A base registra apenas a declaração feita nesta eleição: a pessoa pode ter governado o município em mandatos não seguidos ou ter sido prefeita de outra cidade. O texto anterior afirmava mais do que o dado sustenta.
- **As características foram medidas separadamente.** Dizer que a maioria é branca, tem superior e é homem não significa que sejam as mesmas pessoas. O painel mostra, por recorte, quantos reúnem as três ao mesmo tempo (33,7% no Brasil, 48,5% no Sul, 16,5% no Norte).
- **Mediana** aparece como "idade central do grupo" e **pontos percentuais** ganharam exemplo no glossário.

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos. Não ler o CSV no navegador.
- Seguir a skill descrita em `skill.md`.
- Para falar de prefeitos, filtrar `cargo = Prefeito`. Para contar municípios, usar `codigo_municipio_tse`. Nunca somar votos das duas linhas da chapa.
- Tratar célula vazia como dado indisponível, nunca como zero ou "Não", e mostrar na tela o denominador e quantos casos ficaram de fora.
- **Nunca comparar um subconjunto com a referência do conjunto inteiro.** Se a referência externa é nacional, a comparação é nacional.
- **Marcar com selo visível todo gráfico que não acompanha o filtro**, e não afirmar que o painel inteiro acompanha.
- Apurar a categoria majoritária do recorte em vez de fixá-la no texto, e tratar diferença menor que 1,5 ponto como empate.
- Não inferir nada além do declarado: sem causa, sem meta, sem projeção, sem recomendação de política pública.
- Não usar logotipo, nome ou identidade visual de instituição real, nem apresentar o painel como sistema oficial.
- Escrever para quem tem menos familiaridade com gráficos, sem infantilizar: linguagem simples, valor sempre escrito, termo técnico explicado.
- Antes de entregar, conferir cada número recalculando a partir do CSV e testar filtros, temas, modo apresentação, impressão, celular e tela grande.
