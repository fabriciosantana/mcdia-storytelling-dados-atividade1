## Prompt 1 — Análise, narrativa e implementação inicial

O prompt original tem cerca de 44 seções e é muito extenso; abaixo está o resumo fiel das suas instruções, não o texto integral.

```
Você é o agente responsável por executar integralmente minha atividade de Storytelling de Dados. NÃO quero apenas sugestões: inspecione o projeto, leia as instruções, analise a base, faça a análise exploratória, identifique a narrativa, construa o dashboard, crie os arquivos obrigatórios, valide os dados e o HTML e deixe a entrega pronta para revisão.

- Diretório de trabalho: Trabalhos\Grafico - 03102026 (raiz do projeto Git; remote = meu fork storytelling-dashboard-3h). Se não for o projeto correto, NÃO altere nada e informe. Sem push, PR, merge ou comandos destrutivos.
- Tema: "Mulheres e homens no comando das prefeituras". Pergunta: "Como mulheres e homens estão presentes no comando dos municípios brasileiros eleitos em 2024?"
- Briefing: audiência pública de comissão do Legislativo (parlamentares, assessorias, sociedade civil), pouco tempo, opiniões formadas. O dashboard informa; não recomenda voto, partido ou política, e não julga grupos.
- Entrega: entregas/fabiana-milhomem/ com claude.md (começando por "## Qual história meu dashboard conta?"), skill.md (genérica), prompts.md e dashboard.html (arquivo único, autocontido, só dados agregados embutidos).
- Dados: universo cargo = Prefeito; municípios por codigo_municipio_tse; vazio não é zero nem "Não"; nunca somar votos das duas linhas; tratar o dado como eleição de 2024, não como situação atual.
- Fazer análise exploratória real (totais, gênero, região, UF e variáveis complementares) sem forçar tese; incluir uma dimensão complementar só se acrescentar à história.
- Narrativa: panorama nacional → regiões (percentual, denominador claro) → UFs (barras horizontais ordenadas) → dimensão complementar opcional → síntese factual; títulos orientados por mensagem; sem mapa nem pizza para UFs sem necessidade analítica.
- Visual: paleta #6399AE #27424B #DBD9D6 #67A5BF #859EB6, editorial, sem rosa/azul estereotipado, acessível, responsivo, números no padrão brasileiro.
- Validar: auditoria independente dos cálculos, teste do HTML em navegador, revisão da narrativa e checklist final de arquivos. Relatório final sem commit, push ou PR.
```

**O que funcionou / o que mudei:** O prompt foi detalhado o bastante para dispensar perguntas sobre o conteúdo (universo, regras da base, narrativa, paleta). Ao executá-lo, o agente parou na primeira verificação: o diretório indicado não era um repositório Git e não tinha o `README`, o `_modelo/` nem os dados, o que levou ao Prompt 2. Os números do prompt original não foram usados; tudo foi recalculado do CSV.

---

## Prompt 2 — Integração segura do repositório

```
Escolha a opção 1, mas com uma adaptação importante: o diretório Grafico - 03102026 deve ser a RAIZ DEFINITIVA do projeto Git, não uma subpasta. Clone o fork numa pasta temporária fora do diretório final, inspecione o conteúdo (README, entregas/_modelo, dados, configurações, histórico), integre ao diretório existente preservando dicionario.md, eleitos.csv e Tema.jpeg (compare antes de qualquer coincidência de nome), não faça commit, push nem PR e apresente estrutura, arquivos integrados, arquivos preservados, git status, remote e branch.
```

**O que funcionou / o que mudei:** A integração funcionou: o `.git` do clone foi copiado para a raiz e os arquivos versionados foram restaurados sem sobrescrever os arquivos locais. A comparação revelou que o `eleitos.csv` da raiz era idêntico ao de `dados/`, mas o `dicionario.md` da raiz era uma página HTML do GitHub salva como `.md`. Por isso, no Prompt 3 a fonte oficial passou a ser apenas `dados/`.

---

## Prompt 3 — Desenvolvimento completo com as regras reais do repositório

```
Pode iniciar agora o desenvolvimento completo. Antes de criar qualquer arquivo, leia as regras reais do repositório e da validação automática (README, entregas/_modelo, .github/workflows/validar-entrega.yml). Use EXCLUSIVAMENTE dados/eleitos.csv e dados/dicionario.md; não toque nos arquivos soltos da raiz nem em nada fora de entregas/fabiana-milhomem/. Faça a análise exploratória, construa o dashboard HTML autocontido, claude.md, skill.md genérica e prompts.md, valide dados e visual (navegador headless), execute a validação do repositório, deixe a pasta com exatamente os 4 arquivos e entregue o relatório final, sem commit, push ou PR.
```

**O que funcionou / o que mudei:** A leitura prévia do workflow mostrou o que é checado (pasta em minúsculas com hífen, os 4 arquivos preenchidos e diferentes do modelo, `<html>` completo, seção "Qual história…" no `claude.md` e cabeçalho `name`/`description` na `skill.md`). A exploração mostrou 13,2% de prefeitas no país, de 9,2% a 18,5% entre as regiões e de 2,6% a 26,7% entre as UFs; a escolaridade foi a única dimensão complementar com contraste claro, e idade e reeleição foram descartadas por serem quase iguais entre os grupos. Durante a validação no navegador encontrei um erro de layout: no celular (375 px) havia rolagem horizontal de 24 px, porque variáveis de largura definidas inline sobrepunham o CSS responsivo. Corrigi com `!important` na regra da tela pequena e repeti os testes (0 px de overflow em 1366, 820 e 375 px, sem erros de console). Uma auditoria independente com o módulo `csv` confirmou todos os números embutidos.

---

## Prompt 4 — Refinamento editorial e visual

Na minha numeração da conversa este foi o quarto prompt; ele corresponde à "segunda rodada" do dashboard (o prompt original o chamava de "Prompt 2"). Abaixo está o resumo fiel das instruções, não o texto integral.

```
A primeira versão está tecnicamente funcional e validada. NÃO vamos reconstruir o projeto: esta rodada é só de refinamento editorial, storytelling, hierarquia visual, precisão textual e leitura. Modifique somente entregas/fabiana-milhomem/dashboard.html e registre este prompt em prompts.md (claude.md e skill.md só se for necessário para manter a coerência, informando antes do relatório). Sem commit, push ou PR; não mexa em dados/, README, _modelo, outras entregas, .github, scripts nem nos três arquivos soltos da raiz.

- Abertura: H1 "A cada 100 prefeituras, 13 são comandadas por mulheres"; subtítulo "5.553 municípios analisados nas eleições municipais de 2024"; o 13,2% como protagonista visual, com 5.553 / 734 / 4.819 em segundo plano; novo texto de abertura que conduz à pergunta territorial. Não usar "prefeituras eleitas".
- Regiões: título "A proporção muda quando olhamos para o território", com texto sobre a variação (9,2% a 18,5%) e a comparação por percentual.
- UFs: passo "3 · As diferenças entre as UFs", título "A diferença aumenta quando olhamos estado por estado", sem "onde olhar com mais atenção"; manter filtro de região ("Clique em uma região para destacar suas UFs"); manter asterisco e nota para UFs com menos de 30 municípios, reduzindo a dependência da hachura.
- Escolaridade: refazer como duas barras simples (superior completo: prefeitas 80,8% e prefeitos 56,3%), destacando a diferença de 24,5 p.p.; demais categorias em tooltip/tabela/nota; valores escritos na tela; sem inferência causal; manter a observação metodológica.
- Fechamento: "O que os dados mostram", três mensagens (13,2%; 9,2–18,5%; 2,6–26,7%), sem recomendação.
- Metodologia: deixar claro que são 26 UFs com municípios (DF não tem eleição municipal) e reescrever o universo de 5.553 municípios com a observação sobre os 5.569 como nota secundária.
- Contraste: manter a paleta, priorizar #27424B para texto e usar os azuis em barras e superfícies, sem texto pequeno sobre eles.
- Não adicionar mapa, novos gráficos nem cards. Testar 1366×820, 1280×800 e 375×812, console, tooltips, filtro e escolaridade; recalcular e confirmar os números antes de alterar o HTML.
```

**O que funcionou / o que mudei:** Todos os números foram recalculados do CSV antes de alterar o HTML e conferiram (5.553; 734; 4.819; 13,2% e 86,8%; regiões de 9,2% a 18,5%; RR 26,7% e ES 2,6%; escolaridade 80,8% e 56,3%, diferença de 24,5 p.p.). O que mudou no `dashboard.html`:
- **Abertura:** novo título e subtítulo; o 13,2% passou a ser o maior elemento da tela, e 5.553, 734 e 4.819 viraram números secundários. O rótulo da barra de composição saiu de dentro da barra para baixo dela, para não ficar texto sobre azul.
- **Regiões e UFs:** títulos e textos novos; o passo da UF virou "As diferenças entre as UFs"; o texto do filtro foi trocado; a hachura das UFs pequenas foi retirada e ficaram o asterisco, a nota e o tooltip.
- **Escolaridade:** as barras empilhadas deram lugar a duas barras simples de "superior completo", com os valores escritos na tela e a diferença de 24,5 p.p. destacada. As demais categorias foram para uma tabela recolhida e para o tooltip.
- **Fechamento e fonte:** o título passou a "O que os dados mostram". A metodologia ganhou o texto do Distrito Federal e uma redação mais clara do universo, com os 5.569 municípios como observação secundária.
- **Terminologia:** o texto não usa mais "prefeituras eleitas"; ficaram "municípios analisados" e "prefeitos eleitos".
- **Testes:** problema encontrado no teste de celular: o rótulo "+24,5 p.p." ficava cortado dentro da faixa da diferença em 375 px, então ele some na tela pequena e a diferença segue na caixa logo abaixo. Também retirei o `aria-hidden` do 13,2% da abertura, para que leitores de tela leiam o número.
- **`claude.md`:** ajustei os trechos que descreviam as barras empilhadas, a hachura e os títulos antigos, para refletir o dashboard final. A `skill.md` não foi alterada.

---

## Prompt 5 — Ajuste final de precisão terminológica

```
Faça apenas um ajuste editorial final em dashboard.html, sem alterar dados, cálculos, gráficos, paleta, tipografia, layout, estrutura narrativa, interatividade, responsividade, acessibilidade, escolaridade, regiões, UFs, fechamento, skill.md ou claude.md. Alterar o H1 para "Em cada 100 municípios, 13 elegeram mulheres para a prefeitura" e a legenda do 13,2% para "dos municípios analisados elegeram mulheres para a prefeitura", para alinhar a abertura à unidade de análise e à temporalidade. Verificar quebras visuais no desktop e no mobile e repetir as validações (números contra o CSV, console, 375 px, rolagem horizontal, autocontenção, ausência de "prefeituras eleitas" e de afirmações causais).
```

**O que funcionou / o que mudei:** Ajuste exclusivamente editorial. O H1 passou a 'Em cada 100 municípios, 13 elegeram mulheres para a prefeitura' e a legenda do 13,2% passou a 'dos municípios analisados elegeram mulheres para a prefeitura'. Os dados, cálculos, gráficos e estrutura permaneceram inalterados. As validações numéricas, de navegador, responsividade e autocontenção passaram novamente.
