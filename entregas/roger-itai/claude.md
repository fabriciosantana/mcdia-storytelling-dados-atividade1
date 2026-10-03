## Qual história meu dashboard conta?

Quem governa os municípios brasileiros a partir de 2025 não é um retrato da população. Entre os
5.553 prefeitos eleitos em 2024, 13,2% são mulheres, 66% dos que declararam cor/raça são brancos
e só 2,3% são pretos. O painel faz um "espelho": compara quem governa com a população adulta
(21+ anos, Censo 2022) e mostra onde a distância é maior. Quem vê deve sair entendendo, em
poucos segundos, que o poder local tem um perfil muito específico, e com vontade de explorar a
sua própria cidade.

## Contexto do projeto

Pergunta norteadora: **"Quem governa os municípios?"** Base: `dados/eleitos.csv` (prefeitos e
vices eleitos em 2024, 11.106 pessoas), lida com o `dados/dicionario.md`, mais a população 21+
por UF, sexo e cor/raça do Censo 2022 (IBGE, tabela 9606) como referência de comparação. Cuidados
do dicionário aplicados: uma linha por município (prefeito e vice não são contados em dobro),
votos só do prefeito, célula vazia tratada como dado indisponível, códigos como texto e aviso de
que a base retrata a eleição de 2024, não o cargo hoje.

## Público-alvo

O cidadão comum num portal de transparência. Decide em poucos segundos se continua explorando,
então a linguagem é acessível sem perder precisão e a mensagem central vem logo no topo.

## Perguntas que os dados respondem

1. Quem são as pessoas que governam os municípios (gênero, idade, cor/raça, escolaridade, ocupação)?
2. Esse perfil se parece com a população que elas governam?
3. Em quais estados e recortes a distância é maior?
4. Quais partidos concentram as prefeituras?
5. Quem governa o meu município?

## Decisões de design

- **Ângulo do espelho:** cada comparação põe prefeitos e população lado a lado, com um índice
  (100 = espelho perfeito), para tornar a desigualdade visível sem explicá-la causalmente.
- **Cores:** azul `#1351B4` = quem governa; cinza = população. Mantidas em todos os gráficos.
- **Mapa por UF** para mostrar a geografia da distância; **barras** para rankings (partidos,
  ocupações); **busca por município** como fecho, para tornar o dado pessoal.
- **Fora do painel:** explicações causais. O painel descreve; não afirma por que a distância existe.
- **Skill seguida:** `skill.md` (regras genéricas de visualização e narrativa).

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos.
- Seguir a skill descrita em `skill.md`.
- Seguir as regras do dado e as verificações descritas abaixo.

---

## Notas técnicas do projeto original

O painel foi construído no Studio Console, num projeto chamado `transparencia`. Os caminhos
citados abaixo (`published/`, `pages/`, `sources/`, `scripts/`) pertencem a esse ambiente e não
fazem parte deste repositório; a entrega é o `dashboard.html` desta pasta.


Painel para um portal de transparência sobre quem foi **eleito prefeito em 2024** (mandato
2025–2028). Público: o cidadão comum, que decide em poucos segundos se continua explorando.
A linguagem é acessível sem perder precisão. Ângulo do painel: **o espelho**, que compara quem
governa com a população adulta que poderia governar.

- **Entrega:** arquivo único offline `published/transparencia/dashboard.html` (📦 snapshot da
  página `pages/dashboard.md`). O histórico dos pedidos está em `prompts.md`.
- **Fluxo do console:** vale a skill `montar-relatorio` e o `CLAUDE.md` da raiz. Este arquivo só
  traz o que é específico do projeto.

## Estrutura

```
bronze/      originais intocados: eleitos.csv, dicionario.md (LEIA antes de mexer nos dados),
             censo2022_tabela9606_21mais.json, manifest.json (origem + sha256)
scripts/preparar.mjs         bronze → sources (tipagem; --baixar rebaixa o Censo)
scripts/montar_dashboard.mjs gera pages/dashboard.md — SOBRESCREVE a página
sources/eleitos.parquet      as 72 colunas tipadas (11.106 pessoas)
sources/censo_21mais.csv     UF × sexo × cor/raça, população com 21+ anos
sources/10_prefeituras.sql   view prefeituras — 1 LINHA POR MUNICÍPIO (5.553), vice ao lado
sources/20_espelho.sql       view espelho — UF × gênero × cor: prefeitos e populacao_21mais
semantic/prefeituras.yaml    catálogo do perfil (fato prefeituras)
semantic/espelho.yaml        catálogo da comparação (fato espelho)
```

Comandos, com cwd = `studio-console/`:

```bash
node projects/transparencia/scripts/preparar.mjs
```

```bash
node projects/transparencia/scripts/montar_dashboard.mjs
```

## Regras do dado (os "cuidados" do pedido, já embutidos — não desfaça)

- **Nunca conte nada direto em `eleitos`.** Lá cada município aparece duas vezes (prefeito e
  vice) e os votos da chapa se repetem. Use a view `prefeituras`, onde uma linha é um município
  e os votos não duplicam.
- **Célula vazia não é zero nem "Não".** Cor/raça vazia vira o rótulo "Não informada" (16
  prefeitos), sem imputação. `bens` nulo (178) fica fora da mediana; 144 declararam zero.
- **Códigos são texto.** `codigo_municipio_tse` e `codigo_ibge` preservam os zeros à esquerda.
  O CSV usa `;` como separador e vírgula como decimal; o preparar.mjs converte.
- **Temporalidade:** a base é a eleição de 2024, não quem está no cargo hoje. Ela inclui 9
  chapas cassadas depois e 14 documentadas por fonte histórica (dimensão `validacao`). O aviso
  do topo da página é obrigatório.
- **Reeleição** = declaração ST_REELEICAO (`Sim` = prefeito em exercício que concorreu e venceu).
  `Não` não prova primeiro mandato.
- **Gênero do TSE ≠ sexo do Censo**: são campos distintos, comparados como cada órgão publica.
  "Pretos e pardos" segue a convenção do IBGE para população negra.

## O espelho (referência externa)

- **Fonte:** IBGE, Censo 2022, tabela 9606, população com **21 anos ou mais** (idade mínima
  para prefeito), por UF. O **DF fica fora** porque não tem prefeitura.
- **API do IBGE:** use `servicodados.ibge.gov.br/api/v3/agregados`. O `apisidra` cai em desafio
  Cloudflare. No SIDRA, `-` = zero absoluto; qualquer outro símbolo faz o script falhar de
  propósito.
- **`espelho`:** % entre prefeitos ÷ % na população × 100 (100 = espelho perfeito). O `total()`
  dele atravessa as UFs, então **não serve por UF**.
- **`espelho_pretos_pardos`:** o mesmo índice calculado DENTRO de cada recorte (usado no mapa
  por UF). O denominador dos prefeitos é só quem declarou cor/raça.
- **Blocos de cor/raça:** filtram as 5 categorias do IBGE (5.537 prefeitos). Os de gênero usam
  as 5.553 prefeituras.

## A página `pages/dashboard.md`

- **Formato:** página ARTESANAL com View Blocks de **dois catálogos**. O relatório spec-driven
  não serve aqui: aceita um catálogo só e põe a prosa só no topo.
- **SQL dos blocos:** sai do `compileSemanticBlock` (via montar_dashboard.mjs ou editor do
  console). Nunca edite o marcador `<!-- viewblock -->` nem o SQL de um bloco à mão.
- **Prosa:** é estática. Os números foram conferidos com a extração de 01/10/2026.
- **Ao mudar um número, catálogo ou view:** rode as queries da página e reconfira toda frase
  numérica. Denominador explícito; observado ≠ hipótese; **nenhuma afirmação causal** (o painel
  descreve, não explica).
- **Regenerar com o montar_dashboard.mjs** apaga ajustes feitos no editor. Para mudanças finas,
  edite a prosa e reedite os blocos pelo editor do console (▣/Σ/⚙).

Números-âncora (se mudarem, a prosa está desatualizada):

| Fato | Valor |
| --- | --- |
| Prefeituras / prefeitas / vice-prefeitas | 5.553 / 734 (13,2%) / 1.074 |
| Mulheres na população 21+ | 52,4% |
| Homens brancos: % pop. 21+ → % prefeitos → índice | 20,5% → 57,3% → 279 |
| Mulheres pretas: % pop. 21+ → prefeitas → índice | 5,4% → 20 (1 a cada 278) → 7 |
| Brancos / pardos / pretos entre prefeitos (cor declarada) | 66,0% / 31,3% / 2,3% |
| Chapas só de homens / só de mulheres | 3.864 (69,6%) / 119 (2,1%) |
| Idade na posse: p25 · mediana · p75 | 42 · 49 · 58 |
| Superior completo / reeleitos | 59,5% / 2.469 (44,5%) |
| PSD + MDB + PP | 2.500 (45,0%) |
| Chapas com 100% dos votos válidos / sem percentual | 288 / 9 |

## Armadilhas do console encontradas aqui

- **Barra deitada** (`orientation: horizontal`): o console desenha a 1ª linha EMBAIXO. Por isso
  as barras deitadas usam `order: asc`, para o maior ficar no topo. Nesse caso `limit` cortaria
  os maiores: as ocupações usam filtro com as 12 mais declaradas + `pct_todas_prefeituras`
  (`total(..., scope: all)`). Se o console for corrigido, volte ao `desc` padrão e ao `limit: 12`.
- **DataTable com mais de ~8 colunas** estoura a largura do cartão. A busca tem 7 colunas de
  ficha + % de votos; não acrescente colunas sem tirar outras.
- **Editar `sources/*.sql` não recarrega a view no servidor que está rodando.** Reexecute o
  `CREATE OR REPLACE VIEW` por `POST /api/query {sql, project: "transparencia"}` (primeiro
  `10_prefeituras`, depois `20_espelho`) ou reinicie a API.
- **O `<title>` do 📦 é o nome do arquivo** ("dashboard — Studio Console"), não o `title` do
  frontmatter.
- **O AreaMap gerado pelo compilador não tem rótulos** (só tooltip e legenda). O degradê sai da
  1ª cor da paleta.
- **Paleta do projeto** (`project.yaml`, preset govbr): 1ª série = azul `#1351B4` = QUEM GOVERNA;
  2ª = cinza = população. Nos gráficos de comparação, a métrica de prefeitos vem primeiro.

## Verificação antes de entregar

1. Rode todas as queries da página pela API (token em `server/.runtime/token`) e confira com a
   tabela de números-âncora.
2. Rode o lint (`lintEvidenceCompat` de `shared/evidenceLint.js`) e o `npm run audit:breaks`.
   Ambos devem sair sem aviso para `transparencia`.
3. Publique: `POST /api/projects/transparencia/publish {path: "dashboard.md", visibility: "public"}`.
4. **Inspeção visual:** o painel do navegador do app pode não desenhar (janela atrás). Use o
   Chrome headless contra o servidor estático (`published-static`, porta 4173) e recorte a
   imagem em faixas:

```bash
"/c/Program Files/Google/Chrome/Application/chrome.exe" --headless=new --disable-gpu --hide-scrollbars --user-data-dir="$TEMP/chrome-headless" --window-size=1280,7300 --virtual-time-budget=8000 --screenshot=full.png "http://localhost:4173/transparencia/dashboard.html"
```

5. Teste a busca: "Aracaju" deve trazer Emília Corrêa, PL, 57,5%.
