## Qual história meu dashboard conta?

O poder municipal eleito em 2024 é majoritariamente branco: dois em cada três prefeitos se declararam brancos, e só 128 dos 5.553 se declararam pretos. O retrato muda de região para região — 94% de brancos no Sul, 62% de pardos no Norte — e fica um pouco mais diverso apenas na cadeira de vice. O dashboard mostra esse retrato e diz com clareza o que a base permite e não permite afirmar sobre ele.

## Contexto do projeto

**Tema:** 2. A cor do poder municipal.
**Pergunta norteadora:** Que retrato racial emerge das pessoas eleitas para governar os municípios brasileiros em 2024?

**Base:** `dados/eleitos.csv` — 11.106 linhas, uma por pessoa (5.553 prefeitos e 5.553 vices), de 5.553 municípios, extraída do TSE em 01/10/2026. Separador `;`, vírgula decimal, UTF-8 com BOM. Ler `dados/dicionario.md` antes de qualquer análise.

**Cuidados de leitura considerados:**

- `raca_cor_autodeclarada` é declaração da própria pessoa no registro da candidatura. Não é verificada e não houve inferência por nome ou imagem.
- 42 registros (0,4%), de 29 municípios, estão sem raça/cor. Entram como “sem informação”; não são redistribuídos nem tratados como zero.
- Prefeito e vice são contados separadamente (filtro por `cargo`). A dupla é unida por `id_chapa`.
- O recorte é o resultado de 2024, não os ocupantes atuais: inclui 9 chapas cassadas e 14 confirmadas por registro histórico. Restringir a `ELEITO_ATUAL_TSE` não altera os percentuais (65,8% / 31,2% / 2,3% entre prefeitos).
- 16 dos 5.569 municípios ficaram fora; o Distrito Federal não elege prefeito.
- Etnia indígena e pertencimento quilombola têm campos próprios e não equivalem a raça/cor.
- `genero_tse` é o gênero do cadastro, não identidade de gênero.
- Votos da chapa aparecem nas duas linhas: para o porte do município, usar só a linha do prefeito.
- A base contém apenas eleitos. Não há candidatos derrotados nem dados de população.

## Público-alvo

Leitores do relatório anual de um observatório da sociedade civil. Público amplo, on-line, que lê sozinho, sem ninguém para explicar, possivelmente no celular. Não domina estatística nem o vocabulário eleitoral. Precisa sair com uma imagem clara de quem foi eleito e com a noção exata de até onde os dados vão — para não repetir uma conclusão que a base não sustenta.

## Perguntas que os dados respondem

1. Como se declararam, em raça ou cor, os prefeitos eleitos em 2024?
2. O retrato muda entre o cargo de prefeito e o de vice?
3. Como é a composição racial da dupla eleita em cada município?
4. O retrato é o mesmo em todas as regiões e estados?
5. O que acontece quando se cruza raça com gênero?
6. O tamanho da disputa muda o retrato?
7. O que esta base permite e não permite afirmar?

## Decisões de design

- **Skill:** seguir `skill.md` (`narrativa-visual-com-rigor`), baseada em *Storytelling with Data* (Knaflic) e *A psicologia das cores* (Heller).
- **Formato de leitura guiada, não painel de filtros.** O público lê sozinho; a página é uma coluna única, de cima para baixo, com oito passos numerados. Cada título de seção afirma o achado, de modo que os títulos sozinhos contam a história.
- **Ordem do geral ao específico:** retrato nacional → cargo → chapa → território → gênero → porte → limites → fecho.
- **Cores que não imitam tons de pele.** Usar branco, marrom e preto para as categorias reforçaria estereótipo e deixaria a categoria “branca” invisível no fundo claro. Cinza marca a maioria branca como pano de fundo; azul, cor associada a confiança e sobriedade, marca pardos (claro) e pretos (escuro) — mesmo matiz porque as duas categorias formam, na convenção do IBGE, a população negra. Violeta e verde ficam para amarela e indígena, sem ligação literal. “Sem informação” usa hachura: ausência não é uma categoria como as outras. Vermelho ficou de fora para não emitir julgamento.
- **Grade de 100 quadrados na abertura,** porque “de cada 100 prefeitos, 66…” é a forma mais direta de explicar proporção a quem não lê gráficos com frequência.
- **Barras 100% empilhadas para região, estado e porte,** porque a pergunta é de composição dentro de cada grupo. Ordenadas pela fatia branca, salvo as faixas de porte, que têm ordem natural.
- **Barras pareadas para prefeito e vice,** na mesma escala e partindo do zero, para que a diferença entre 2,3% e 4,5% de pretos apareça sem exagero.
- **Pretos e pardos são mostrados separados** sempre que cabem. O agrupamento só aparece em chapas e em gênero, onde seis categorias cruzadas ficariam ilegíveis — e a página avisa quando agrupa.
- **Limites em seção própria, não em rodapé.** A exigência de rigor do público vira conteúdo: duas listas, “permite” e “não permite”.
- **Um único dado externo:** a composição da população no Censo 2022, marcada como fora da base e com a ressalva de que a comparação é indicativa. Sem ela, o leitor não tem referência; com ela sem aviso, pareceria que a base mede sub-representação.
- **Interação mínima:** uma alternância prefeitos/vices no bloco territorial, dica ao passar o mouse ou tocar e tabelas recolhidas com os números exatos.
- **Sem bibliotecas externas.** HTML, CSS e JavaScript puros, fontes do sistema: o arquivo abre sem internet.
- **Ficou de fora:** partido, escolaridade, idade, bens e reeleição. São recortes possíveis, mas desviam da pergunta norteadora.

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos. Não ler o CSV nem outros arquivos a partir do HTML.
- Seguir a skill descrita em `skill.md`.
- Ler `dados/dicionario.md` antes de analisar e respeitar os cuidados listados acima.
- Usar os termos do TSE para as categorias: branca, parda, preta, amarela, indígena. Escrever “se declarou” ou “autodeclarado”, nunca “é”.
- Calcular percentuais sobre o total do grupo, incluindo os registros sem informação.
- Mostrar o total de cada grupo comparado e sinalizar os grupos pequenos.
- Não afirmar causa nem “sub-representação” a partir da base sozinha. Qualquer número externo deve ser identificado como tal.
- Conferir cada número do texto contra os agregados antes de entregar.
- Escrever em português do Brasil, em linguagem direta, sem jargão eleitoral ou estatístico.
- Testar a página em largura de celular e de computador; não pode haver rolagem horizontal nem erro no console.
