# Diário de prompts

Diário das rodadas com o Claude (Claude Code), em ordem cronológica. Os prompts originais eram longos. Abaixo de cada um está o texto essencial, com objetivo, restrições e pedidos mantidos fielmente.

---

## Prompt 1 — Auditoria exploratória em modo somente leitura

```
Antes de qualquer implementação, faça somente uma análise em modo leitura deste repositório.
NÃO altere, crie, mova ou exclua nenhum arquivo. NÃO faça commit nem push. NÃO gere o dashboard ainda.

1. Leia integralmente o README.md e dados/dicionario.md.
2. Inspecione a estrutura de dados/eleitos.csv sem modificá-lo.
3. Leia os quatro arquivos de entregas/_modelo e confirme a existência de entregas/marcio-barbosa.

Meu tema é: Tema 3 — O mapa partidário de 2024.
Pergunta norteadora: "Como o poder municipal ficou distribuído entre partidos e alianças após as eleições de 2024?"
Público: leitor de veículo de imprensa interessado em política, que não conhece a estrutura da base.

Atenção às regras do dicionário: diferencie Prefeito e Vice-Prefeito; não duplique votos ou municípios;
use id_chapa e codigo_municipio_tse; diferencie partido do prefeito, partido do vice, coligação,
federação e tipo_agremiacao; considere classificacao_validacao; não trate a base como lista de
ocupantes em 2026; não faça inferências ideológicas.

Responda com números verificáveis: municípios representados; prefeitos por partido e %; distribuição
por região e por UF; chapas como partido isolado, coligação ou federação; o que os dados permitem
afirmar sobre alianças; diferença entre partido do prefeito e composição da chapa; 5 a 8 achados.
Não escolha a história, cores nem gráficos. Ao final: metodologia, verificações de qualidade,
tabelas-resumo, achados (fatos × interpretações) e limitações.
```

**O que funcionou / o que mudei:** A restrição de somente leitura funcionou: nenhum arquivo foi alterado.

A auditoria confirmou a estrutura da base:
- 11.106 linhas, com 5.553 prefeitos e 5.553 vices;
- uma chapa por município e 23 chapas fora de `ELEITO_ATUAL_TSE`;
- `federacao` é atributo da pessoa, não da chapa;
- `composicao_coligacao` registra federações como bloco, o que exigiu cuidado ao separar as siglas.

O achado mais promissor foi o contraste entre o partido do prefeito (PSD lidera) e a presença nas chapas vencedoras (MDB, PP e PSD praticamente empatados). Por isso, no prompt seguinte pedi alternativas narrativas em vez de ir direto ao dashboard.

---

## Prompt 2 — Três alternativas de narrativa

```
Continue em modo SOMENTE LEITURA. Não altere arquivos, não escolha cores.
Use exclusivamente os resultados verificados na análise anterior.

Proponha 3 alternativas de narrativa jornalística. Para cada uma: mensagem central em uma frase;
título factual e neutro; subtítulo; sequência narrativa; pergunta de cada bloco; dado que sustenta
cada afirmação; visualização mais adequada; anotações; limitações; pontos fortes e limitações
como storytelling.

Pelo menos uma alternativa deve explorar o contraste "quem encabeça a prefeitura" × "quem participa
da chapa vencedora".

Evite: coleção de gráficos independentes; linguagem de torcida; classificar partidos
ideologicamente; chamar presença em coligação de domínio, influência ou poder sem explicar a
métrica; tratar municípios como eleitores; sugerir causalidade; escolher narrativa só por estética.
Não faça ranking das alternativas. Ao final, tabela comparativa (foco, pergunta, abertura,
revelação, papel da geografia, complexidade, nº de visualizações).
```

**O que funcionou / o que mudei:** Vieram três alternativas comparáveis:
- **A:** "Ninguém governa sozinho".
- **B:** "Quem encabeça × quem participa".
- **C:** "Um país, vários mapas".

Pedir para não ranquear me obrigou a escolher conscientemente. A alternativa B responde às duas palavras da pergunta ("partidos" e "alianças"), mas deixava a geografia de fora; a C tinha a geografia, mas pouco das alianças. Decidi combinar B como espinha dorsal com a geografia de C como capítulo final.

---

## Prompt 3 — Arquitetura narrativa definitiva (B + geografia de C)

```
Continue em modo SOMENTE LEITURA. Não gere dashboard, claude.md, skill.md ou prompts.md.
Direção escolhida: alternativa B como espinha dorsal + dimensão geográfica da C como capítulo final.

Construa uma arquitetura narrativa definitiva com começo, virada, aprofundamento e fechamento:
1. fotografia nacional; 2. virada; 3. alianças (94,33% coligações; 77,5% prefeito e vice de partidos
diferentes); 4. segunda fotografia (presença nas chapas vencedoras); 5. contraste encabeça × integra;
6. parceiros de composição; 7. geografia (regiões e UFs); 8. fechamento com limites.

Para cada bloco: objetivo, pergunta, métrica exata, transição, visualização e por quê, título,
anotação, risco de interpretação e como evitá-lo.

Regras: sem torcida ou julgamento; sem classificação ideológica; não usar "poder", "influência",
"domínio" ou "força" para presença sem explicar; deixar claro que integrar é presença na composição,
não peso político, e que a soma pode passar de 100%; não dramatizar a diferença MDB/PP/PSD; não
tratar municípios como população; não explicar causas regionais; base = resultado de 2024
consolidado em 2026. Geografia: tile map ou matriz, não coroplético. Entre 5 e 6 visualizações.
Ao final: tabela da sequência, título e subtítulo gerais, mensagem central, métricas a validar e
blocos removíveis.
```

**O que funcionou / o que mudei:** A arquitetura ficou com 6 visualizações (V1 a V6). Duas decisões evitaram redundância:
- o gráfico de halteres (V3) serve aos blocos 4 e 5;
- o bloco 6 mede uma proporção (encabeça ÷ integra), não outra contagem.

A arquitetura listou as métricas que ainda precisavam ser recalculadas antes de implementar, principalmente a razão encabeça ÷ integra, que só tinha sido derivada de contas anteriores. Isso levou à rodada de validação.

---

## Prompt 4 — Validação numérica final e sistema visual

```
Continue em modo SOMENTE LEITURA.
PARTE 1: recalcule diretamente de dados/eleitos.csv todas as métricas listadas para validação
(totais, prefeitos por partido, recorte só ELEITO_ATUAL_TSE, tipo_agremiacao, prefeito × vice,
separação de composicao_coligacao preservando federações, presença, encabeça por federação, razão
encabeça ÷ integra, exemplo de Acrelândia, regiões, maior participação por UF com empates, UFs
abaixo de 20%). Se algum número anterior estiver errado, diga valor anterior, valor recalculado e
causa. Não esconda divergências.

PARTE 2: proponha um sistema visual editorial/jornalístico, genérico o bastante para virar skill.
Evitar: dashboard corporativo, template de BI, estética de IA, cards arredondados, gradientes,
sombras, laranja/creme, roxo/rosa, arco-íris. Cor com função narrativa; não favorecer partido;
não usar vermelho/azul como oposição nem verde/vermelho como bom/ruim.
Compare: A) uma cor por partido; B) neutro com cor só para a métrica; C) híbrido.
Proponha tokens HEX com função, tipografia, escala, largura, espaçamento, celular, anotações,
fonte/metodologia, tooltips, acessibilidade e anti-chartjunk. No halteres, diferenciar as DUAS
MÉTRICAS, não os partidos. No tile map, distinguir partidos sem mosaico caótico.
Ao final: relatório de validação, sistema visual, paleta em tabela, regras para skill.md,
decisões para claude.md e checklist visual.
```

**O que funcionou / o que mudei:** A validação encontrou e explicitou divergências reais:
- top 3 e top 5 eram 45,02% e 64,94%, não 45,03% e 64,95% (eu tinha somado percentuais já arredondados);
- no AC há empate no 2º lugar entre REPUBLICANOS e PL;
- PRD e SOLIDARIEDADE têm 9,8% e 9,7%, e não "~10%";
- os números em destaque devem ter a mesma precisão (94,3% e 77,5%).

No sistema visual, a comparação das estratégias de cor levou à opção B: nenhuma cor por partido; "encabeça" em tinta escura, "integra" em petróleo. Medi os contrastes WCAG da paleta.

Aprovei a troca da V5 (barras regionais empilhadas) por uma matriz em escala neutra, porque as barras exigiriam 10 cores categóricas.

---

## Prompt 5 — Preenchimento de claude.md e skill.md

```
Agora saímos do modo somente leitura. Edite SOMENTE entregas/marcio-barbosa/claude.md e skill.md.
Não faça commit nem push. Use exclusivamente números recalculados e validados; prevalecem as
correções da validação (45,0%, 64,9%, 94,3%, 77,5%, PRD 9,8%, SOLIDARIEDADE 9,7%, empate no 2º lugar
do AC, arredondamentos que podem não somar 100%). V5 aprovada como matriz.

claude.md: primeira seção exatamente "## Qual história meu dashboard conta?"; contexto, perguntas,
estrutura narrativa (9 blocos, V1–V6), decisões de design específicas (cor não representa partido,
encabeça = tinta, integra = petróleo, Source Serif 4 + Libre Franklin, 680/960px, tabelas
acessíveis), regras metodológicas e limitações.

skill.md: GENÉRICA, nome editorial-data-storytelling, sem partidos, eleição, TSE ou números deste
trabalho; seções do modelo com regras imperativas, tokens genéricos com HEX, acessibilidade e
checklist operacional.

Depois: mostre o diff, git status --short e confirme que nenhum outro arquivo foi alterado.
```

**O que funcionou / o que mudei:** Os dois arquivos foram preenchidos.

- **Correção ainda na mesma rodada:** o `claude.md` dizia "partido mais votado na UF", o que é incorreto porque a métrica conta prefeituras, não votos. O texto foi trocado antes de eu ver o resultado.
- **Rodada seguinte de higiene:** pedi a remoção de restos do template. A verificação mostrou que não havia resíduos: as linhas do modelo que eu tinha visto estavam no diff como linhas removidas. Nada foi alterado.
- **Ponto anotado para depois:** o exemplo da skill ("X concentra 45% do total") repetia um número deste trabalho. Ficou para a rodada seguinte.

---

## Prompt 6 — Implementação do dashboard e registro final da entrega

```
Implemente a entrega. Edite SOMENTE skill.md, prompts.md e dashboard.html (claude.md aprovado, não
alterar). Não faça commit nem push.

1. skill.md: troque apenas o exemplo "X concentra 45% do total" por um exemplo genérico.
2. dashboard.html: arquivo único e autocontido, sem ler eleitos.csv, JSON, JS ou CSS locais; dados
   agregados embutidos. Narrativa: abertura (5.553 municípios, eleição de 2024, consolidado em
   01/10/2026, não representa quem ocupa os cargos hoje); V1 barras "PSD, MDB e PP encabeçam 45% das
   prefeituras"; bloco "uma prefeitura, vários partidos" com o exemplo de Acrelândia; V2 KPIs 94,3% e
   77,5% + barra 100%; V3 halteres "Encabeçar e integrar contam histórias diferentes"; parceiros de
   composição; V5 matriz regional neutra; V6 tile map com cor = faixa da maior participação, sigla
   como texto, DF sem eleição municipal; blocos "Como os números foram calculados" e "O que os dados
   mostram e o que não mostram".
   Sistema visual aprovado (tokens, Source Serif 4 + Libre Franklin, sem sombras/gradientes/pizza),
   lang pt-BR, SVG com role/aria-label, tabelas em <details>, prefers-reduced-motion, sem rolagem
   horizontal em 360/768/1280px.
3. prompts.md: diário cronológico das rodadas realmente realizadas, sem inventar ações.
4. Testes: existência, ausência de leitura local e de fetch/XMLHttpRequest, placeholders, validade
   estrutural, dados embutidos, números principais, responsividade, acessibilidade, git diff --check,
   git status --short; abrir em navegador headless se disponível.
```

**O que funcionou / o que mudei:** A avaliação final desta rodada será preenchida e ajustada depois dos testes desta implementação.

Registro técnico desta rodada, para referência:
- **Como o HTML foi gerado:** por um script de build fora do repositório, que lê o CSV e confere 19 grupos de números contra os valores aprovados antes de escrever o arquivo. Os dados ficam embutidos no HTML.
- **Correção 1 (arredondamento do AP):** o teste mostrou o AP com 56,3% em vez dos 56,2% validados. O valor exato é 9/16 = 56,25, e o build arredondava "metade para cima", diferente da validação. O build passou a usar arredondamento "metade para o par" (ABNT NBR 5891), igual à validação.
- **Correção 2 (título regional):** o título "Cada região tem um partido diferente…" da arquitetura era impreciso, porque Norte e Nordeste têm o MDB com a maior participação. Ficou "Quatro partidos diferentes têm a maior fatia das prefeituras nas cinco regiões".
- **Correção 3 (matriz no celular):** ajustei a matriz regional para não ter texto transbordando em 360px.
