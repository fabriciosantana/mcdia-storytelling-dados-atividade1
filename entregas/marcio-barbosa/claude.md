## Qual história meu dashboard conta?

Na eleição municipal de 2024, nenhum partido encabeçou mais de 17% das prefeituras: PSD (890), MDB (860) e PP (750) somam 45,0% dos 5.553 municípios da base. Mas o partido do prefeito mostra só uma dimensão do resultado: 94,3% das chapas vencedoras foram coligações e, em 77,5% delas, prefeito e vice são de partidos diferentes. Quando se conta a presença na composição das chapas vencedoras, MDB, PP e PSD aparecem, cada um, em cerca de 4 de cada 10 prefeituras, e várias siglas surgem quase só como integrantes — presença que indica participação na chapa, não peso político. O quadro muda bastante entre regiões e estados, e o dashboard termina explicitando o que esses dados de 2024 não permitem afirmar.

## Contexto do projeto

- **Tema:** Tema 3 — O mapa partidário de 2024.
- **Pergunta norteadora:** "Como o poder municipal ficou distribuído entre partidos e alianças após as eleições de 2024?"
- **Base:** `dados/eleitos.csv` (prefeitos e vice-prefeitos eleitos nas eleições municipais ordinárias de 2024), lida segundo `dados/dicionario.md`.
- **Cobertura:** 5.553 municípios representados, em 26 UFs e 5 regiões (o DF não tem eleição municipal).
- **Referência temporal:** resultado da eleição de 2024, com dados consolidados em 01/10/2026.
- **Cuidado central:** a base **não** é uma lista dos ocupantes atuais dos cargos. Cassações, renúncias, eleições suplementares e trocas de partido posteriores não estão refletidas. O dashboard deve sempre falar em "prefeituras conquistadas em 2024", nunca em "quem governa hoje".

## Público-alvo

Leitor de veículo de imprensa interessado em política, sem conhecimento técnico sobre dados eleitorais. Sabe o que é prefeito, vice e partido, mas não necessariamente o que são coligação e federação, nem como a base foi estruturada. Lê em poucos minutos, muitas vezes no celular. Precisa sair entendendo:

- como as prefeituras se distribuíram entre os partidos;
- por que contar só o partido do prefeito é incompleto;
- como a distribuição varia no território;
- e o que os dados **não** dizem.

## Perguntas que os dados respondem

Na ordem em que a história as apresenta:

1. Quantas prefeituras cada partido encabeça?
2. Como as chapas vencedoras foram formadas (coligação, partido isolado, federação; prefeito e vice do mesmo partido ou não)?
3. Qual a diferença entre encabeçar uma prefeitura e integrar a chapa vencedora?
4. Em quantas chapas vencedoras cada partido ou federação aparece?
5. Como a distribuição das prefeituras encabeçadas varia entre as regiões?
6. Como varia entre as UFs, e onde um partido concentra ou o quadro é mais repartido?
7. Quais são os limites da interpretação desses dados?

## Estrutura narrativa

Sequência aprovada (começo → virada → aprofundamento → fechamento):

| # | Bloco | Pergunta | Visualização |
|---|---|---|---|
| 1 | Fotografia nacional | Quem encabeça as prefeituras? | **V1** — barras horizontais |
| 2 | "Uma prefeitura, vários partidos" | Por que só o partido do prefeito não basta? | Esquema explicativo (exemplo de Acrelândia), não é gráfico de dados |
| 3 | Alianças | Com que frequência as chapas vencedoras foram alianças? | **V2** — KPIs + barra 100% de `tipo_agremiacao` |
| 4 | Presença nas chapas vencedoras | Em quantas chapas cada sigla/federação aparece? | **V3** — halteres, primeira etapa (só "integra") |
| 5 | Contraste encabeça × integra | O que muda entre as duas contagens? | **V3** — halteres completo |
| 6 | Parceiros de composição | Quem aparece muito mais como integrante do que como cabeça? | **V4** — barras 100% encabeça × só integra |
| 7 | Geografia: regiões | A distribuição muda por região? | **V5** — matriz regional (tabela de calor) |
| 8 | Geografia: UFs | Qual partido tem a maior participação em cada UF? | **V6** — tile map das UFs |
| 9 | Metodologia e limitações | O que dá e o que não dá para afirmar? | Texto |

São 6 visualizações principais (V1 a V6). V3 é um único gráfico revelado em duas etapas, para não duplicar o mesmo dado.

### Números de referência (validados diretamente em `dados/eleitos.csv`)

**Bloco 1 — prefeitos por partido (n = 5.553)**
- PSD 890 (16,03%), MDB 860 (15,49%), PP 750 (13,51%), UNIÃO 589 (10,61%), PL 517 (9,31%), REPUBLICANOS 437 (7,87%), PSB 311 (5,60%), PSDB 275 (4,95%), PT 252 (4,54%).
- Outros 15 partidos somam 672 (12,10%). São 24 partidos com ao menos um prefeito.
- Top 3: 45,02% (exibir como 45,0%). Top 5: 64,94% (exibir como 64,9%). Nenhum partido chega a 17%.

**Bloco 2 — exemplo de Acrelândia (AC)**
- Prefeito do REPUBLICANOS, vice do UNIÃO.
- Composição da coligação: REPUBLICANOS / PL / UNIÃO.
- Conta como 1 prefeitura encabeçada (REPUBLICANOS) e 3 presenças em chapa vencedora (REPUBLICANOS, PL e UNIÃO).

**Bloco 3 — alianças**
- `tipo_agremiacao`: coligação 5.238 (94,33%), partido isolado 278 (5,01%), federação sem coligação 37 (0,67%).
- Prefeito e vice de partidos diferentes: 4.301 (77,45%); do mesmo partido: 1.252 (22,55%).
- Exibir os KPIs como **94,3%** e **77,5%**.
- Coligações têm mediana de 3 siglas/federações (máximo de 17).

**Blocos 4–5 — integra × encabeça, por sigla/federação, em % de 5.553**

| Sigla/federação | Integra | Encabeça |
|---|---|---|
| MDB | 2.245 (40,4%) | 860 (15,5%) |
| PP | 2.168 (39,0%) | 750 (13,5%) |
| PSD | 2.166 (39,0%) | 890 (16,0%) |
| UNIÃO | 1.874 (33,7%) | 589 (10,6%) |
| REPUBLICANOS | 1.723 (31,0%) | 437 (7,9%) |
| PL | 1.569 (28,3%) | 517 (9,3%) |
| Fed. PSDB/Cidadania | 1.342 (24,2%) | 308 (5,5%) |
| PSB | 1.334 (24,0%) | 311 (5,6%) |
| PODE | 1.130 (20,3%) | 127 (2,3%) |
| Fe Brasil | 1.118 (20,1%) | 285 (5,1%) |

- A soma das presenças é 21.016, o equivalente a 378,5% de 5.553. **É não aditiva.**
- Composição das federações que encabeçam:
  - Fe Brasil 285 = PT 252 + PC do B 19 + PV 14;
  - Fed. PSDB/Cidadania 308 = PSDB 275 + CIDADANIA 33;
  - Fed. PSOL/Rede 4 = REDE 4.

**Bloco 6 — % encabeça ÷ integra (21 unidades)**
- PSD 41,1; MDB 38,3; PP 34,6; PL 33,0; UNIÃO 31,4
- Fe Brasil 25,5; REPUBLICANOS 25,4; PSB 23,3; Fed. PSDB/Cidadania 23,0
- AVANTE 18,7; PDT 15,7; NOVO 12,5; PODE 11,2
- PRD 9,8; SOLIDARIEDADE 9,7; MOBILIZA 9,3
- Fed. PSOL/Rede 3,9; PMB 1,7; AGIR 1,2; DC 0,9; PRTB 0,7
- Exemplos: DC integra 223 e encabeça 2; AGIR integra 250 e encabeça 3.

**Bloco 7 — partido com maior participação em cada região**

| Região | Municípios | Maior participação |
|---|---|---|
| Sudeste | 1.656 | PSD 355 (21,4%) |
| Sul | 1.190 | PP 278 (23,4%) |
| Centro-Oeste | 467 | UNIÃO 155 (33,2%) |
| Norte | 449 | MDB 111 (24,7%) |
| Nordeste | 1.791 | MDB 282 (15,7%), seguido de perto por PSD 275 (15,4%) |

- PSD tem 8 prefeituras no Centro-Oeste.
- O Nordeste concentra 67,5% das prefeituras do PT e 68,8% das do PSB.

**Bloco 8 — UFs**
- Oito partidos têm a maior participação em ao menos uma UF: PSD 6, UNIÃO 5, MDB 3, PL 3, PP 3, PSB 3, PSDB 2, REPUBLICANOS 1. Não há empate no 1º lugar.
- UFs onde a maior participação de um partido é mais alta: AL 63,7% (MDB), AC 63,6% (PP), PA 58,7% (MDB), AP 56,2% (UNIÃO), MS 55,7% (PSDB).
- Abaixo de 20%: MG 16,7% (PSD; 23 partidos com prefeito), PE 17,5% (PSDB), MA 18,4% (PL).
- **AC:** há empate no 2º lugar entre REPUBLICANOS e PL (2 prefeituras cada).
- Faixas do tile map:

  | Faixa | UFs |
  |---|---|
  | <20% | MG, PE, MA |
  | 20–30% | RJ, RN, BA, ES, PI |
  | 30–40% | SC, RO, PB, SP, RS, SE, CE, GO, AM |
  | 40–50% | TO, PR, MT, RR |
  | ≥50% | MS, AP, PA, AC, AL |

Percentuais arredondados podem não somar exatamente 100%. Inclua essa nota onde houver distribuição completa.

## Decisões de design

Seguir a skill descrita em `skill.md` (editorial-data-storytelling). Decisões específicas deste dashboard:

### Aparência geral
- **Aparência editorial/jornalística**, fundo branco, muito espaço em branco. A narrativa conduz e os gráficos ficam integrados ao texto.
- **Sem cards decorativos, gradientes ou sombras.** Sem estética de dashboard corporativo, template de BI ou interface de IA. As seções se separam por espaço e fios finos.

### Cor
- **Cor não representa partido.** Partidos são identificados principalmente por **rótulos diretos e ordem estável**. Motivos:
  - são 24 partidos e 3 federações, o que exigiria uma paleta categórica ilegível;
  - cores partidárias carregam associação simbólica;
  - a história é sobre *como se conta*, não sobre "times".
- **"Encabeça" usa a família tinta/cinza escuro** (`--ink` #1A1F24 e escala sequencial de cinzas).
- **"Integra" e o conceito de aliança usam a família petróleo** (`--accent` #0E7470; `--accent-light` #9FCFCB, sempre com borda #0E7470).
- **Tons neutros representam contexto** (`--context` #8A939C).
- Nenhuma cor sugere aprovação ou reprovação política. Sem vermelho × azul como oposição e sem verde × vermelho como bom × ruim.

### Tipografia e layout
- **Tipografia:**
  - *Source Serif 4* (fallback: Georgia, serif) para títulos e narrativa;
  - *Libre Franklin* (fallback: system-ui, -apple-system, "Segoe UI", sans-serif) para gráficos, números e interface, com `tabular-nums`.
- **Layout:** coluna de texto de cerca de 680px; gráficos de até cerca de 960px.
- Responsivo a partir de 360px, **sem rolagem horizontal no celular**.
- **Tabelas equivalentes acessíveis** (em `<details>`) para todos os gráficos.

### Por visualização
- **V1:** PSD, MDB e PP em `--ink`, demais partidos em `--context`. Valores na ponta das barras. "Outros 15 partidos" por último, com nota.
- **V2:** KPIs 94,3% e 77,5% em `--accent`. Na barra 100%:
  - coligação em `--accent`;
  - partido isolado em cinza médio;
  - federação em `--ink-2`;
  - o segmento de 0,67% tem largura mínima visível e rótulo externo com fio-guia.
- **V3:** a diferença entre as **duas métricas** é feita por cor + luminância + forma + rótulo direto.
  - Encabeça: ponto/quadrado cheio em `--ink`.
  - Integra: ponto em `--accent` com anel branco.
  - Conector em `--rule-strong`. Partidos todos em tinta, sem cor própria.
  - Ordenado por "integra". Escala de 0 a 50% dos municípios.
- **V4:** parte "encabeça" em `--ink`; parte "só integra" em `--accent-light` com borda `--accent`. Total de presenças (n) ao lado de cada barra.
- **V5 — matriz regional (substitui as barras 100% empilhadas multicoloridas):**
  - regiões nas colunas (com n no cabeçalho);
  - 9 maiores partidos + "outros" nas linhas;
  - **percentual escrito em cada célula**, sobre escala sequencial **neutra** (cinzas);
  - a maior célula de cada região é marcada com **borda de 2px em tinta e número em negrito**, sem depender só da cor;
  - no celular, a matriz é transposta (partidos nas linhas, colunas N, NE, CO, SE, S).
- **V6 — tile map:**
  - **quadrados de mesmo tamanho**, um por UF, em posição geográfica aproximada;
  - a cor representa a **faixa percentual da maior participação na UF** (<20, 20–30, 30–40, 40–50, ≥50%), em escala de cinzas, e **não o partido**;
  - a **sigla do partido escrita diretamente** no quadrado, junto com o %;
  - **DF indicado como "sem eleição municipal"** (quadrado vazio com borda tracejada);
  - **n de municípios** exibido (tooltip/tabela, e marcador de "n pequeno" em RR, AP e AC);
  - controle opcional "destacar partido" usando contorno e negrito, não cor partidária;
  - tabela ordenável como alternativa no celular.

### Anotações e tooltips
- **Anotações:** no máximo 2 por gráfico, texto sans em `--ink-2`, fio-guia de 1px, sem caixas.
- **Tooltips** no formato fixo: número absoluto, denominador e percentual. Por exemplo: "MDB · integra 2.245 de 5.553 chapas vencedoras (40,4%) · encabeça 860 (15,5%)".

## Regras metodológicas específicas

### Unidade e contagem
- **Unidade principal:** município/prefeito. Base: **5.553 municípios**.
- Usar **uma linha de prefeito por chapa** (`cargo = Prefeito`) para evitar dupla contagem.
- `id_chapa` vincula prefeito e vice; `codigo_municipio_tse` identifica o município.
- **Votos não são necessários** para a narrativa principal e não devem ser somados como "votação do partido".

### Definições
- **"Encabeça"** = o partido do prefeito (`partido` na linha do prefeito). Nos blocos 4–6, esse partido é mapeado para a sua federação, quando pertencer a uma.
- **"Integra"** = a sigla ou federação aparece em `composicao_coligacao` da chapa vencedora.
- **A presença é não aditiva:** a mesma chapa conta para todos os seus integrantes, e a soma passa de 100%. Nunca empilhar nem fazer pizza com essa métrica.
- **Federações são tratadas como bloco** quando a composição da chapa assim as registra; não é possível saber qual partido federado atuou.
  - Nos blocos 1, 7 e 8, a contagem é **por partido**.
  - Nos blocos 4–6, é **por sigla/federação**.
  - Avisar essa mudança no texto.
- `federacao`/`sigla_federacao` descrevem o partido **da pessoa**, não a chapa: não usar como atributo da chapa.

### O que não afirmar
- **Município não equivale a população nem eleitorado.** Escrever "% dos 5.553 municípios" junto a cada gráfico.
- A base contém **apenas chapas vencedoras**: não falar em taxa de sucesso, desempenho de derrotados nem "estratégia vencedora".
- **Não inferir ideologia** nem agrupar partidos em campos políticos.
- **Não inferir causalidade**, inclusive explicações regionais ou estaduais.
- **Presença na chapa não mede peso, influência, cargos nem permanência da aliança.** Não usar "poder", "domínio", "influência" ou "força" para essa métrica. Usar "presença", "integra", "maior participação".
- Não dramatizar a diferença entre MDB (2.245), PP (2.168) e PSD (2.166) na métrica de presença.

### Limitações a exibir (bloco 9 e notas próximas aos gráficos)
1. A base cobre 5.553 dos 5.569 municípios com eleição em 2024; **16 municípios ficaram fora** por insuficiência de confirmação.
2. **23 chapas** estão em categorias de validação diferentes de `ELEITO_ATUAL_TSE` (9 `CHAPA_CASSADA_TSE` e 14 `ELEICAO_HISTORICA_DOCUMENTADA`). Foram mantidas.
   - O efeito delas é de **no máximo cerca de 0,05 ponto percentual** nas participações verificadas (maior variação: 0,043 ponto).
   - O ranking dos 10 maiores partidos não muda.
3. É uma **fotografia da eleição de 2024 consolidada em 01/10/2026**, não dos ocupantes atuais.
4. A **filiação partidária refere-se à candidatura de 2024.**
5. Presença na composição não mede peso político; federações aparecem como bloco.
6. Contagens são de municípios, não de eleitores ou habitantes.
7. Só há chapas vencedoras.
8. Não há classificação ideológica na base.
9. Percentuais arredondados podem não somar exatamente 100%.

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos (não ler `eleitos.csv` nem outros arquivos locais). Fontes e eventuais bibliotecas apenas via CDN.
- Seguir a skill descrita em `skill.md`.
- Usar **somente** os números da seção "Números de referência". Texto, gráficos, tabelas e tooltips devem ler do **mesmo objeto de dados agregados**.
- Manter a precisão decimal consistente: 1 casa nos gráficos e textos (2 casas apenas em notas/tabelas quando necessário).
- Cada bloco termina com uma frase de transição para o seguinte; nenhum gráfico solto sem pergunta.
- Exibir junto a cada gráfico: base ("% dos 5.553 municípios"), fonte ("TSE, eleição municipal de 2024, consolidado em 01/10/2026") e nota da métrica quando necessária.
- Linguagem factual, neutra e acessível; sem adjetivos valorativos sobre partidos.
- Testar em 360, 768 e 1280px; verificar contraste, foco de teclado, `aria-label` dos SVGs e `prefers-reduced-motion`.
