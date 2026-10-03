# Diário de prompts

**Link compartilhado da conversa (opcional):** não há (sessão no Claude Code, terminal local).

---

## Prompt 1

````
Você está trabalhando como meu agente principal de desenvolvimento e análise de dados neste repositório.

Sua responsabilidade é executar de ponta a ponta a atividade acadêmica existente neste projeto, e não apenas me dar instruções.

IMPORTANTE:
- Trabalhe diretamente nos arquivos do repositório.
- Inspecione o projeto antes de implementar qualquer coisa.
- Não me peça para explicar arquivos, colunas ou estrutura que você mesmo possa descobrir no repositório.
- Tome decisões técnicas e de design justificáveis.
- Não invente resultados, estatísticas, relações ou interpretações.
- Sempre calcule os números a partir da base fornecida.
- Revise e teste sua própria implementação antes de considerar o trabalho concluído.
- Se encontrar alguma ambiguidade, consulte primeiro README.md, dados/dicionario.md, os arquivos em entregas/_modelo e a própria base.
- Execute scripts, análises e testes necessários autonomamente.
- Quero um trabalho acadêmico de alta qualidade, não apenas algo que cumpra minimamente o checklist.

==================================================
1. CONTEXTO DA ATIVIDADE
==================================================

Esta é uma atividade de Storytelling de Dados do Mestrado em Administração Pública do IDP.

O objetivo é construir um dashboard HTML baseado na base de eleições municipais brasileiras de 2024.

Meu tema designado é:

TEMA 4 — CONTINUIDADE E RENOVAÇÃO

Pergunta norteadora:

"O que as eleições de 2024 revelam sobre continuidade e renovação no comando das prefeituras?"

Público:

Turma da aula inaugural de uma escola de governo.

São gestores, servidores e assessores de diferentes regiões do Brasil. Essas pessoas conhecem relativamente bem a realidade do próprio município ou região, mas conhecem pouco a realidade dos demais municípios brasileiros.

Portanto, o dashboard deve permitir que alguém compreenda o panorama nacional e, ao mesmo tempo, consiga comparar diferentes realidades territoriais.

==================================================
2. SUA PRIMEIRA TAREFA: ENTENDER O REPOSITÓRIO
==================================================

Antes de programar:

1. Leia integralmente:
   - README.md
   - dados/dicionario.md
   - entregas/_modelo/claude.md
   - entregas/_modelo/skill.md
   - entregas/_modelo/prompts.md
   - entregas/_modelo/dashboard.html

2. Inspecione:
   - dados/eleitos.csv
   - estrutura das colunas
   - tipos dos dados
   - valores faltantes
   - categorias relevantes
   - particularidades indicadas pelo dicionário.

3. Confirme tecnicamente os cuidados da base, principalmente:
   - cada município possui prefeito e vice;
   - análises de prefeito precisam usar cargo = Prefeito;
   - votos da chapa não podem ser duplicados;
   - células vazias não significam zero ou "Não";
   - códigos devem ser tratados corretamente;
   - a base representa o resultado das eleições de 2024 conforme os critérios documentados, e não necessariamente os ocupantes dos cargos hoje.

Não implemente a narrativa antes de analisar os dados.

==================================================
3. DIRETÓRIO DA MINHA ENTREGA
==================================================

Minha entrega deve ficar em:

entregas/tiago-cardoso/

Se ainda não existir, copie entregas/_modelo para esse diretório.

Ao final, dentro de entregas/tiago-cardoso devem existir EXATAMENTE os quatro arquivos exigidos:

- dashboard.html
- claude.md
- skill.md
- prompts.md

Não coloque scripts auxiliares, CSVs, imagens, JSON ou qualquer outro arquivo dentro dessa pasta.

Você pode criar arquivos temporários fora dela para fazer análises, mas eles não fazem parte da entrega.

==================================================
4. ANÁLISE DE DADOS
==================================================

Faça uma análise exploratória real da base antes de decidir a história.

Para este tema, use como unidade principal de análise os PREFEITOS eleitos.

Comece investigando principalmente:

- candidato_a_reeleicao_tse
- reeleito_declaracao_tse
- regiao
- uf
- codigo_municipio_tse
- municipio
- partido
- turno_decisivo
- percentual_validos_chapa_atual_tse
- classificacao_validacao

Mas não se limite mecanicamente a essas variáveis caso outras colunas da base tragam evidência relevante para a pergunta.

IMPORTANTE SOBRE A INTERPRETAÇÃO:

Não trate automaticamente quem NÃO aparece como candidato à reeleição como:
- político novo;
- estreante;
- pessoa sem experiência política;
- primeira vez como prefeito.

A base não necessariamente permite essas conclusões.

Defina operacionalmente continuidade e renovação de maneira rigorosa, apoiada no que a base realmente mede, e explique essa limitação metodológica no dashboard e no claude.md.

Não transforme associações observacionais em relações causais.

Exemplos de afirmações proibidas sem evidência causal:
- "prefeitos são reeleitos porque..."
- "a região X causa maior renovação..."
- "o partido Y produz mais continuidade..."

Prefira formulações descritivas:
- "a proporção observada é maior..."
- "os dados mostram..."
- "entre os municípios da região..."
- "há diferença na distribuição observada..."

==================================================
5. DESCUBRA A HISTÓRIA; NÃO A PRESUMA
==================================================

A pergunta central é:

"O que as eleições de 2024 revelam sobre continuidade e renovação no comando das prefeituras?"

Quero que você descubra a resposta analisando os dados.

Não comece assumindo que houve muita continuidade ou muita renovação.

Depois da análise, defina uma mensagem central factual que possa ser sustentada pelos dados.

A narrativa deve seguir uma progressão semelhante a:

1. panorama nacional;
2. descoberta principal;
3. diferenças territoriais;
4. aprofundamento;
5. comparação entre contextos;
6. síntese útil para gestores públicos.

Não transforme o dashboard em uma coleção aleatória de gráficos.

Cada visualização deve responder uma pergunta da narrativa.

==================================================
6. QUERO UM DASHBOARD FORA DO COMUM
==================================================

Não quero um dashboard estático convencional composto apenas por cards e gráficos independentes.

Quero uma experiência de exploração narrativa interativa.

O usuário deve poder interagir com o dashboard e perceber que os gráficos fazem parte de um mesmo sistema.

Use JavaScript dentro do próprio dashboard.html.

É permitido carregar bibliotecas de visualização por CDN, caso realmente agreguem valor.

Exemplos possíveis:
- D3.js
- Plotly.js
- Chart.js
- Apache ECharts
- outras bibliotecas estáveis e apropriadas.

Escolha você a tecnologia mais adequada.

Não use frameworks pesados sem necessidade.

==================================================
7. PRINCÍPIO DE INTERAÇÃO
==================================================

Quero utilizar o conceito:

"do Brasil para a minha realidade"

A experiência deve começar apresentando o Brasil e depois permitir que o usuário explore regiões e UFs.

O dashboard deve possuir interações reais, não apenas filtros decorativos.

Considere implementar elementos como:

- seleção de região;
- seleção de UF;
- comparação da seleção com o Brasil;
- atualização coordenada de números e gráficos;
- tooltips informativos;
- destaques ao selecionar categorias;
- transições suaves;
- textos narrativos que possam mudar conforme a seleção;
- gráficos conectados entre si;
- possibilidade de voltar ao panorama nacional.

Exemplo conceitual:

Brasil
→ Região
→ UF

Quando o usuário selecionar uma região ou UF, diferentes partes do dashboard devem reagir.

Por exemplo:

"Brasil: X% de continuidade"
"UF selecionada: Y%"
"Diferença: +Z pontos percentuais em relação ao país"

Mas calcule os valores reais.

==================================================
8. VISUALIZAÇÕES
==================================================

Quero visualizações sofisticadas, mas justificadas.

"Revolucionário" não significa usar gráficos exóticos sem função.

Significa oferecer uma experiência visual que revele padrões que uma tabela simples não revelaria.

Considere, depois de olhar os dados, combinações como:

- barras proporcionais interativas;
- ranking dinâmico de UFs;
- dumbbell chart;
- slope chart;
- dot plot;
- beeswarm;
- distribuição;
- pequenos múltiplos;
- matriz;
- mapa apenas se ele realmente contribuir;
- Sankey apenas se houver uma relação apropriada;
- outras formas visuais justificadas.

EVITE:
- excesso de gráficos de pizza;
- velocímetros;
- 3D;
- efeitos meramente decorativos;
- gráficos difíceis de interpretar;
- arco-íris de cores;
- excesso de indicadores;
- dashboards que pareçam uma tela genérica de Power BI.

Cada gráfico deve possuir uma pergunta ou insight associado.

==================================================
9. EXPERIÊNCIA NARRATIVA
==================================================

O dashboard deve funcionar em duas camadas:

CAMADA 1 — LEITURA PASSIVA

Se a pessoa apenas rolar a página, deve compreender toda a história.

CAMADA 2 — EXPLORAÇÃO

Se a pessoa quiser investigar mais, deve conseguir comparar:
- Brasil;
- regiões;
- UFs;
- outros recortes relevantes que você descobrir.

Assim, interação complementa storytelling; não substitui storytelling.

==================================================
10. DESIGN
==================================================

Quero aparência editorial, contemporânea e institucional.

Referências conceituais:
- especiais jornalísticos de dados;
- visualizações editoriais;
- dashboards de organizações de pesquisa;
- apresentação adequada a uma escola de governo.

Evite aparência de:
- template administrativo;
- sistema ERP;
- dashboard financeiro;
- trabalho escolar genérico.

Priorize:

- bastante espaço em branco;
- hierarquia tipográfica forte;
- poucas cores;
- uma cor principal para continuidade;
- outra para renovação;
- neutros para contexto;
- contraste acessível;
- excelente leitura;
- responsividade;
- títulos que comuniquem insights, não simplesmente nomes das variáveis.

Não associe automaticamente cores partidárias ou ideológicas às categorias.

==================================================
11. RESPONSIVIDADE E ACESSIBILIDADE
==================================================

O dashboard precisa funcionar bem:
- desktop;
- notebook;
- tablet;
- celular.

Teste diferentes larguras.

Garanta:
- textos legíveis;
- tooltips utilizáveis;
- controles claros;
- contraste adequado;
- teclado quando aplicável;
- atributos ARIA quando úteis;
- nenhuma informação essencial exclusivamente por cor.

==================================================
12. ARQUITETURA DO dashboard.html
==================================================

O arquivo deve ser único e abrir diretamente no navegador.

Pode possuir:

<style>
...
</style>

<script>
...
</script>

Também pode carregar bibliotecas por CDN.

Porém:

TODOS OS DADOS utilizados pelo dashboard devem estar agregados e incorporados no próprio HTML/JavaScript.

O dashboard NÃO deve:
- abrir eleitos.csv em runtime;
- depender de um servidor local;
- fazer fetch do CSV;
- depender de Python após a geração;
- depender de arquivos locais externos.

Faça a análise previamente e grave no HTML somente os agregados necessários.

Evite embutir as 11 mil linhas se não houver necessidade.

==================================================
13. PERFORMANCE
==================================================

O dashboard deve abrir rapidamente.

Portanto:
- agregue os dados previamente;
- minimize estruturas desnecessárias;
- não faça processamento pesado no navegador;
- não carregue bibliotecas redundantes;
- reutilize os mesmos dados agregados para diferentes visualizações quando possível.

==================================================
14. ESTRUTURA NARRATIVA SUGERIDA
==================================================

Não trate isto como estrutura obrigatória. Depois da análise, melhore-a se os dados indicarem outro caminho.

Uma possibilidade:

SEÇÃO 1
Pergunta / mensagem principal.

SEÇÃO 2
Brasil:
qual o equilíbrio observado entre continuidade e renovação?

SEÇÃO 3
Território:
isso ocorre da mesma forma em todas as regiões?

SEÇÃO 4
Estados:
onde estão as maiores diferenças?

SEÇÃO 5
Exploração:
escolha uma região/UF e compare com o Brasil.

SEÇÃO 6
Aprofundamento:
alguma outra variável disponível ajuda a contextualizar a diferença observada?

SEÇÃO 7
Síntese para gestores:
o que este retrato revela sobre a diversidade do contexto municipal brasileiro?

SEÇÃO FINAL
Fonte, metodologia e limitações.

==================================================
15. TEXTOS DO DASHBOARD
==================================================

Não escreva textos longos.

Use:
- headline;
- subtítulo curto;
- pequenas anotações;
- insights diretamente associados aos gráficos.

Escreva para gestores públicos, e não para estatísticos.

Quando houver conceito metodológico necessário, explique em linguagem acessível.

==================================================
16. claude.md
==================================================

Preencha completamente:

entregas/tiago-cardoso/claude.md

A primeira seção precisa continuar exatamente:

## Qual história meu dashboard conta?

Nela, escreva de 2 a 4 frases com a história REAL encontrada nos dados.

Depois documente:
- contexto;
- público;
- perguntas respondidas;
- decisões narrativas;
- decisões de visualização;
- limitações;
- instruções utilizadas.

Não deixe placeholders.

==================================================
17. skill.md
==================================================

Crie uma skill REALMENTE reutilizável.

Ela NÃO pode mencionar:
- eleições;
- TSE;
- prefeito;
- reeleição;
- esta base;
- este trabalho específico.

A skill deve ser genérica para criação de dashboards narrativos interativos.

Inclua:

- name;
- description;
- quando usar;
- princípios narrativos;
- regras de escolha de gráficos;
- princípios de interação;
- uso de cores;
- tipografia;
- layout;
- acessibilidade;
- responsividade;
- tratamento de números;
- títulos orientados a insight;
- regras contra chartjunk;
- checklist final.

Use instruções acionáveis.

==================================================
18. prompts.md
==================================================

Registre apenas prompts que realmente foram enviados por mim.

NÃO invente prompts intermediários.

Como estou lhe dando este grande prompt inicial, registre-o como Prompt 1.

Na seção:

"O que funcionou / o que mudei"

descreva objetivamente que o prompt estabeleceu:
- autonomia de análise;
- narrativa;
- interatividade;
- rigor;
- estrutura de entrega.

Se posteriormente eu enviar outros prompts nesta sessão, acrescente-os cronologicamente.

==================================================
19. VALIDAÇÕES NUMÉRICAS OBRIGATÓRIAS
==================================================

Antes de finalizar:

1. valide número de prefeitos analisados;
2. valide número de municípios;
3. confirme que não contou prefeito + vice como duas prefeituras;
4. confira percentuais;
5. confira somas por região;
6. confira somas por UF;
7. verifique valores faltantes;
8. verifique classificacao_validacao;
9. confira arredondamentos;
10. verifique que percentuais exibidos correspondem aos números agregados.

Crie verificações automatizadas temporárias se necessário.

==================================================
20. TESTES DO HTML
==================================================

Antes de encerrar:

- abra ou renderize dashboard.html;
- procure erros de JavaScript;
- teste todos os filtros;
- teste reset de filtros;
- teste tooltips;
- teste atualização coordenada dos gráficos;
- teste estados sem dados, caso existam;
- teste responsividade;
- verifique overflow horizontal;
- verifique console;
- verifique caracteres acentuados;
- verifique que o dashboard funciona abrindo diretamente como arquivo HTML.

Corrija os problemas encontrados.

Não considere concluído antes disso.

==================================================
21. AUTONOMIA PARA ITERAÇÃO
==================================================

Quero que você trabalhe como agente.

Portanto faça autonomamente este ciclo:

ANALISAR
→ formular hipótese narrativa
→ validar nos dados
→ escolher visualizações
→ implementar
→ abrir/testar
→ avaliar criticamente
→ corrigir
→ testar novamente
→ finalizar.

Se o primeiro design ficar genérico, melhore.

Se um gráfico não acrescentar informação, remova.

Se uma interação parecer gratuita, substitua.

Se descobrir um insight melhor durante a implementação, ajuste a narrativa.

==================================================
22. CRITÉRIO MAIS IMPORTANTE
==================================================

O objetivo não é demonstrar quantas tecnologias você consegue usar.

O objetivo é que um gestor público termine a experiência entendendo algo que não era óbvio antes de olhar os dados.

Quero que seja visualmente memorável, mas metodologicamente defensável.

Entre "efeito visual impressionante" e "clareza analítica", escolha clareza analítica.

Entre "mais informação" e "melhor história", escolha melhor história.

==================================================
23. NÃO FAÇA
==================================================

Não:
- invente estatísticas;
- invente causalidade;
- invente dados de 2020;
- pesquise valores externos para completar buracos da base sem necessidade;
- altere dados originais;
- modifique arquivos fora da minha pasta de entrega, exceto arquivos temporários locais necessários para análise;
- altere README.md;
- altere dados/;
- altere entregas/_modelo;
- altere trabalhos de outros alunos;
- faça commit ainda;
- faça push ainda;
- abra Pull Request ainda.

Eu farei a parte final de Git depois de revisar.

==================================================
24. RESULTADO ESPERADO
==================================================

Ao terminar, quero encontrar:

entregas/tiago-cardoso/
├── claude.md
├── dashboard.html
├── prompts.md
└── skill.md

Todos completos.

Depois de terminar a implementação, faça uma última revisão como se você fosse o professor avaliando pelos critérios:

1. narrativa;
2. visualizações e rigor;
3. qualidade da skill;
4. qualidade do claude.md;
5. registro dos prompts;
6. funcionamento do HTML.

Corrija qualquer ponto fraco identificado.

Finalmente, no terminal, me apresente somente um resumo curto contendo:

- história encontrada nos dados;
- principais números;
- visualizações implementadas;
- interações implementadas;
- arquivos criados;
- testes executados;
- eventuais limitações metodológicas.

Agora comece lendo o repositório e execute o trabalho completo.
````

**O que funcionou / o que mudei:** O prompt estabeleceu **autonomia de análise** (o Claude leu README, dicionário e modelos, explorou a base e conferiu sozinho os cuidados: 5.553 prefeitos = 5.553 municípios = 5.553 chapas, votos só na linha do prefeito, 9 percentuais vazios mantidos como ausentes); **narrativa** (a história foi descoberta nos dados e não presumida: quase empate 44,5% × 55,5%, forte variação territorial, associação com a margem de votos e, como achado inesperado, quase nenhuma variação por porte de município); **interatividade** (o princípio "do Brasil para a minha realidade" virou uma seleção global Brasil → região → UF → município que reconfigura todos os gráficos e textos); **rigor** (a proibição de tratar "não candidato à reeleição" como estreante levou às categorias "recondução" e "troca de titular" e a uma seção de limitações no próprio painel); e **estrutura de entrega** (pasta com exatamente quatro arquivos, dados agregados embutidos, testes de navegador e validações numéricas). Por ser muito detalhado, o prompt dispensou rodadas de esclarecimento; o ajuste veio no prompt seguinte, por causa do prazo.

---

## Prompt 2

```
o prazo é agora. preciso terminar urgente, não vai respeitar prazos que estejam no trabalho
```

**O que funcionou / o que mudei:** Enviado durante a execução, depois que o Claude avisou que o prazo do README (03/10/2026, 11h30) estava próximo. Mudou a prioridade de "explorar várias alternativas" para "fechar a entrega": o Claude manteve a análise e as validações, mas descartou ideias mais caras (mosaico com os 5.553 municípios, biblioteca de gráficos externa) em favor de gráficos em HTML/CSS puro, mais rápidos de construir e testar, e escreveu os arquivos de documentação em paralelo aos testes.

---

## Prompt 3

````
Quero que você redesenhe a experiência visual deste dashboard com foco rigoroso em DATA VISUALIZATION, INFORMATION DESIGN e STORYTELLING COM DADOS.

O problema atual não é funcional.

O problema é de direção de arte e linguagem visual: o resultado está com aparência de "vibe coding", landing page de SaaS ou interface gerada por IA.

Quero eliminar completamente essa aparência.

A partir deste momento, atue prioritariamente como:

- Data Visualization Designer;
- Information Designer;
- Editorial Designer;
- especialista em Storytelling com Dados;
- especialista em interfaces analíticas para o setor público.

O frontend é apenas o meio de implementação.

A visualização dos dados e a narrativa são o produto.

==================================================
1. PRINCÍPIO FUNDAMENTAL
==================================================

Este NÃO é:

- um SaaS;
- uma landing page;
- um painel administrativo;
- uma aplicação de startup;
- um dashboard financeiro;
- uma demonstração de frontend;
- uma interface "futurista";
- uma peça de marketing.

Este é um:

DASHBOARD EDITORIAL DE DADOS

destinado a uma aula inaugural de uma escola de governo.

O resultado deve parecer produzido por uma equipe formada por:

jornalista de dados
+
designer de informação
+
analista de políticas públicas
+
desenvolvedor de visualização.

Não por um gerador automático de interfaces.

==================================================
2. TEMA E PERGUNTA
==================================================

Tema:

CONTINUIDADE E RENOVAÇÃO

Pergunta norteadora:

"O que as eleições de 2024 revelam sobre continuidade e renovação no comando das prefeituras?"

Público:

gestores, servidores e assessores públicos de diferentes regiões brasileiras.

Eles conhecem relativamente bem sua realidade local, mas pouco sobre os demais municípios.

Portanto, a experiência deve ajudá-los a:

1. compreender o panorama nacional;
2. perceber que existem diferenças territoriais;
3. localizar sua região/UF dentro desse panorama;
4. comparar sua realidade com outras;
5. sair com uma síntese clara.

==================================================
3. STORYTELLING: NÃO ORGANIZE POR GRÁFICOS
==================================================

NÃO pense:

"primeiro gráfico"
"segundo gráfico"
"terceiro gráfico"

Pense:

PERGUNTA
→ EVIDÊNCIA
→ DESCOBERTA
→ NOVA PERGUNTA

Cada seção deve provocar naturalmente a seguinte.

A página precisa possuir progressão narrativa.

Use como arquitetura conceitual:

INÍCIO
→ apresentar o equilíbrio nacional.

TENSÃO
→ revelar que o número nacional esconde diferenças territoriais.

EXPLORAÇÃO
→ permitir descobrir onde essas diferenças estão.

APROFUNDAMENTO
→ mostrar características relevantes encontradas nos dados.

RESOLUÇÃO
→ devolver ao gestor uma leitura sobre a diversidade do contexto municipal brasileiro.

O usuário que simplesmente rolar a página deve compreender a história inteira.

A interação deve aprofundar a história, e não ser necessária para entendê-la.

==================================================
4. REGRA CENTRAL DE COMPOSIÇÃO
==================================================

Cada seção deve possuir:

1. uma pergunta ou afirmação;
2. uma visualização dominante;
3. no máximo um elemento auxiliar;
4. uma conclusão curta.

Evite:

visualização + visualização + visualização + visualização.

Crie ritmo.

Algumas áreas devem ser densas.

Outras devem respirar.

Use espaço em branco como elemento de design.

==================================================
5. NÃO USE O PADRÃO "CARD DASHBOARD"
==================================================

Evite estruturar tudo dentro de caixas.

Especialmente evite:

- dezenas de cards independentes;
- card dentro de card;
- grandes caixas com bordas arredondadas;
- KPIs em quatro quadrados iguais;
- grid de cards como estrutura principal;
- cada gráfico dentro de uma "caixinha";
- dashboard estilo Bootstrap;
- dashboard estilo Tailwind template;
- painel estilo sistema corporativo.

Gráficos podem existir diretamente na composição editorial.

Use containers somente quando a separação semântica realmente exigir.

A página precisa parecer diagramada, não encaixotada.

==================================================
6. PROIBIÇÕES ESTÉTICAS — ANTI VIBE CODING
==================================================

NÃO USE:

- glassmorphism;
- backdrop blur;
- gradientes decorativos;
- neon;
- glow;
- sombras exageradas;
- fundos roxos/azuis "AI style";
- blobs decorativos;
- partículas;
- elementos flutuantes sem função;
- ícones decorativos em todo título;
- emojis como decoração;
- badges/pills em excesso;
- border-radius gigantes;
- animações gratuitas;
- números gigantes apenas para ocupar espaço;
- texto com gradient;
- efeitos 3D;
- pseudo-dashboard futurista;
- barras de progresso decorativas;
- gauges;
- velocímetros.

Se algum elemento existir apenas para "ficar bonito", remova.

==================================================
7. LINGUAGEM EDITORIAL
==================================================

A referência conceitual é:

reportagem visual
+
especial de dados
+
relatório de instituto de pesquisa
+
visualização editorial.

Não copie nenhuma publicação específica.

Use princípios editoriais:

- hierarquia;
- ritmo;
- alinhamento;
- contraste;
- proximidade;
- repetição controlada;
- precisão;
- contenção visual.

A página deve transmitir:

seriedade,
clareza,
curiosidade,
credibilidade.

==================================================
8. GRID E DIAGRAMAÇÃO
==================================================

Construa um grid editorial consistente.

Desktop:

- largura útil aproximada: 1180–1280px;
- conteúdo textual principal mais estreito;
- gráficos podem ultrapassar a largura da coluna textual;
- alinhamentos devem se repetir verticalmente.

Use uma grade baseada aproximadamente em 12 colunas.

Não é obrigatório implementar framework de grid.

É uma regra de composição.

Utilize três larguras conceituais:

NARROW
texto narrativo.

STANDARD
gráficos comparativos.

WIDE
visualizações territoriais ou visualizações principais.

Não deixe todos os elementos com exatamente a mesma largura.

==================================================
9. RITMO VERTICAL
==================================================

Use bastante espaço entre capítulos.

Uma mudança de assunto deve ser percebida visualmente antes mesmo da leitura.

Exemplo de ritmo:

headline

espaço

contexto

visualização

anotação

grande espaço

nova pergunta

visualização

Não compacte tudo.

O dashboard deve poder ser longo.

Scrolling faz parte da narrativa.

==================================================
10. TIPOGRAFIA
==================================================

Tipografia deve ser editorial e discreta.

Use no máximo:

- uma família tipográfica principal;
- eventualmente uma família complementar.

Prefira fontes legíveis.

Se usar fontes externas, carregue por CDN de fonte confiável.

Hierarquia sugerida:

EYEBROW
12–13px
uppercase ou small caps
tracking moderado.

HEADLINE PRINCIPAL
aprox. 44–58px desktop
forte, mas não extravagante.

SUBTÍTULO
20–24px.

TÍTULO DE SEÇÃO
28–36px.

TÍTULO DE GRÁFICO
18–24px.

BODY
16–18px.

ANOTAÇÕES
13–15px.

FONTE/METODOLOGIA
12–13px.

Evite:

- excesso de bold;
- tudo em caixa alta;
- títulos centralizados por padrão;
- múltiplas fontes;
- fonte monospace decorativa.

Alinhamento preferencial:

à esquerda.

==================================================
11. HIERARQUIA DO TEXTO
==================================================

Não escreva:

"Continuidade por região"

quando os dados permitirem escrever algo como:

"Entre as regiões, a proporção de continuidade varia em X pontos percentuais"

ou outra afirmação REAL sustentada pelos dados.

Títulos de gráfico devem comunicar descobertas.

Subtítulos explicam como ler.

Eixos apenas informam medidas.

Anotações explicam exceções ou achados.

Não repita a mesma informação em:

título
+
subtítulo
+
legenda
+
tooltip.

==================================================
12. SISTEMA DE CORES
==================================================

As cores possuem função semântica.

Não são decoração.

Precisamos representar principalmente:

CONTINUIDADE
RENOVAÇÃO
CONTEXTO

Utilize uma paleta deliberadamente não partidária.

Sugestão inicial:

CONTINUIDADE:
#355C7D

RENOVAÇÃO:
#C9793A

TEXTO PRINCIPAL:
#20252B

TEXTO SECUNDÁRIO:
#66717D

LINHAS / GRID:
#DCE1E5

FUNDO:
#F7F6F2

SUPERFÍCIE:
#FFFFFF

Você pode ajustar tonalidades para melhorar contraste e acessibilidade, mas preserve a lógica.

IMPORTANTE:

continuidade e renovação devem possuir peso visual semelhante.

Não use uma cor "boa" e outra "ruim".

Não associe:

verde = bom
vermelho = ruim

porque não existe julgamento normativo sobre continuidade ou renovação.

==================================================
13. USO DE DESTAQUE
==================================================

Utilize a regra:

contexto em neutro
+
objeto analisado em cor.

Exemplo:

ao selecionar uma UF:

todas as demais UFs → cinza;
UF selecionada → cor;
Brasil → marcador neutro forte.

Isso reduz ruído.

Não pinte todas as categorias com cores diferentes se cor não tiver significado analítico.

==================================================
14. COR COMO INTERAÇÃO
==================================================

A mesma semântica de cor deve permanecer em todo o dashboard.

Se azul representa continuidade no primeiro gráfico:

azul representa continuidade em TODOS os gráficos.

Se laranja representa renovação:

mantenha o significado.

Nunca reutilize essas cores para outra variável.

Seleção pode utilizar:

stroke
espessura
opacidade
marcador

em vez de introduzir uma nova cor.

==================================================
15. ESCOLHA DE GRÁFICOS
==================================================

Escolha o gráfico pela pergunta.

PARTE → TODO:
barra 100% empilhada.

RANKING:
barra horizontal ou dot plot.

COMPARAÇÃO ENTRE DUAS MEDIDAS:
dumbbell.

DISTRIBUIÇÃO:
histograma, boxplot, beeswarm ou strip plot.

TERRITÓRIO:
mapa somente quando posição geográfica acrescentar informação.

COMPARAÇÃO ENTRE MUITAS UFs:
dot plot ou barras ordenadas geralmente são superiores a mapa para precisão.

EVITE:
pizza com muitas categorias;
donut decorativo;
radar;
gauge;
3D;
treemap sem hierarquia real;
Sankey sem fluxo real.

==================================================
16. GRÁFICOS DEVEM TER UMA CAMADA DE ANOTAÇÃO
==================================================

Não espere que o usuário descubra tudo sozinho.

Quando houver uma descoberta relevante:

anote diretamente na visualização.

Exemplo:

linha
+
ponto
+
texto curto.

Prefira anotação direta à legenda quando possível.

O gráfico deve poder ser compreendido mesmo sem tooltip.

Tooltip é aprofundamento, não explicação principal.

==================================================
17. EIXOS E GRIDLINES
==================================================

Reduza tinta não informacional.

Gridlines:
sutis.

Eixos:
mínimos.

Bordas:
raramente necessárias.

Não desenhe moldura ao redor do gráfico.

Evite eixo Y quando valores puderem ser rotulados diretamente sem poluição.

Em barras:

comece em zero quando comprimento codificar magnitude.

Não trunque escala para dramatizar diferenças.

==================================================
18. FORMATAÇÃO NUMÉRICA
==================================================

Use:

43,7%

e não:

43.700000%

Use pontos percentuais quando comparar percentuais:

+6,2 p.p.

Números inteiros:

5.553

Não use precisão falsa.

Normalmente:
uma casa decimal para percentuais é suficiente.

==================================================
19. INTERAÇÃO: PRINCÍPIO DE COORDENAÇÃO
==================================================

Não quero filtros independentes que apenas atualizam gráficos.

Quero VISUALIZAÇÕES COORDENADAS.

Estado global sugerido:

Brasil
Região selecionada
UF selecionada

Quando a seleção mudar:

- headline contextual pode mudar;
- KPI contextual muda;
- gráfico territorial muda destaque;
- ranking muda destaque;
- comparação Brasil × seleção muda;
- texto interpretativo muda;
- tooltips permanecem consistentes.

Uma única escolha deve repercutir pela narrativa.

==================================================
20. INTERAÇÃO NÃO PODE DESTRUIR A HISTÓRIA
==================================================

Estado inicial:

Brasil.

Este estado precisa contar a história sozinho.

Interação:

é uma camada adicional.

Nunca deixe o dashboard inicialmente vazio esperando o usuário selecionar alguma coisa.

==================================================
21. CONTROLES
==================================================

Controles devem ser discretos e editoriais.

Evite:

grandes dropdowns estilo formulário corporativo.

Considere:

segmented control;
select compacto;
botões textuais;
clicar diretamente na visualização.

Sempre inclua:

Brasil

como maneira clara de voltar ao contexto nacional.

==================================================
22. MICROINTERAÇÕES
==================================================

Animação somente para explicar mudança de estado.

Use:

200–400ms.

Pode animar:

posição;
altura;
largura;
opacidade.

Evite:

bounce;
elastic;
spin;
efeitos chamativos.

A transição deve ajudar o usuário a perceber:

"o gráfico mudou porque minha seleção mudou".

==================================================
23. TOOLTIP
==================================================

Tooltip deve responder:

"O que estou vendo?"

Não repita apenas o eixo.

Exemplo conceitual:

TOCANTINS

Continuidade
XX,X%

Renovação
YY,Y%

Diferença em relação ao Brasil
+Z,Z p.p.

N municípios considerados

Use valores reais.

==================================================
24. COMPARAÇÃO COM O BRASIL
==================================================

Este deve ser um dos princípios centrais da experiência.

Quando região ou UF estiver selecionada, sempre que fizer sentido mostrar:

LOCAL
versus
BRASIL.

Isso conversa diretamente com o público da escola de governo.

A pergunta implícita deve ser:

"Como minha realidade se posiciona dentro do país?"

==================================================
25. PROPOSTA DE ESTRUTURA VISUAL
==================================================

Analise os dados antes de usar esta estrutura literalmente.

CAPÍTULO 0 — ABERTURA

eyebrow:
ELEIÇÕES MUNICIPAIS 2024

headline:
uma conclusão real encontrada nos dados.

deck:
2 linhas de contexto.

fonte curta.

Nada além disso.

-------------------------------------

CAPÍTULO 1 — O RETRATO NACIONAL

Uma grande composição mostrando:

continuidade | renovação

Evite dois cards gigantes.

Considere:

barra horizontal proporcional dominante,
com números diretamente associados.

Objetivo:
responder a pergunta mais básica imediatamente.

-------------------------------------

CAPÍTULO 2 — O NÚMERO NACIONAL ESCONDE DIFERENÇAS

Mostre as cinco regiões.

Preferência inicial:

barras 100% empilhadas alinhadas.

Ordene de forma analiticamente útil.

Anote extremos ou padrões relevantes.

-------------------------------------

CAPÍTULO 3 — 26 REALIDADES

Visualização dominante das UFs.

Considere:

dot plot ordenado
ou
barras ordenadas.

Inclua marcador da média Brasil.

Permita clique.

Ao clicar em UF:
todo o dashboard entra no contexto dela.

-------------------------------------

CAPÍTULO 4 — EXPLORE SUA REALIDADE

Área explicitamente interativa.

Controle:

Brasil
→ Região
→ UF

Exiba uma composição comparativa:

SELEÇÃO
versus
BRASIL.

Não crie apenas KPIs.

Considere dumbbell, slope ou outra representação de diferença.

-------------------------------------

CAPÍTULO 5 — APROFUNDAMENTO

Utilize uma segunda dimensão SOMENTE se os dados produzirem insight genuíno.

Exemplos possíveis:

turno decisivo;
votação;
partido;
ou outra variável relevante.

Não inclua uma variável apenas porque existe.

Pergunta:

"Isso acrescenta algo à história sobre continuidade e renovação?"

Se não acrescentar, elimine.

-------------------------------------

CAPÍTULO 6 — FECHAMENTO

Uma frase forte, mas descritiva.

Sem prescrição política.

Sem julgamento sobre ser melhor continuar ou renovar.

Apresente o significado administrativo da diversidade encontrada.

-------------------------------------

CAPÍTULO 7 — METODOLOGIA

Pequeno e transparente.

Informe:

- unidade de análise;
- filtro utilizado;
- definição operacional de continuidade;
- definição operacional de renovação;
- número de municípios;
- tratamento de ausentes;
- limitação da variável de reeleição;
- fonte.

==================================================
26. ESTILO DE ABERTURA
==================================================

A abertura NÃO deve conter:

4 KPIs;
3 badges;
2 gráficos;
botões;
ícones.

Ela deve respirar.

Exemplo estrutural:

ELEIÇÕES MUNICIPAIS 2024

[HEADLINE COM A DESCOBERTA]

[DUAS LINHAS EXPLICANDO O QUE SERÁ EXPLORADO]

────────────────────

A primeira visualização começa depois.

==================================================
27. DENSIDADE DA INFORMAÇÃO
==================================================

Use progressive disclosure.

Mostre primeiro o essencial.

Detalhes aparecem via:

tooltip;
seleção;
hover;
nota;
exploração.

Não coloque tudo simultaneamente na tela.

==================================================
28. RESPONSIVIDADE
==================================================

Não apenas reduza desktop para mobile.

Recomponha.

Desktop:
pode usar gráficos lado a lado.

Mobile:
empilhe.

Labels precisam continuar legíveis.

Interações devem funcionar por toque.

Hover nunca pode ser obrigatório.

==================================================
29. ACESSIBILIDADE
==================================================

Garanta:

contraste WCAG razoável;
navegação por teclado nos controles;
focus visível;
ARIA quando necessário;
informação não codificada somente por cor;
tooltips acessíveis quando possível.

==================================================
30. MAPAS
==================================================

Não use mapa do Brasil apenas porque existem UFs.

Pergunte primeiro:

"a geografia ajuda a responder a pergunta?"

Se usar:

mapa = descoberta espacial.

Nunca:

mapa = decoração.

Se valores muito próximos forem difíceis de comparar no mapa, mantenha também uma visualização quantitativa ordenada.

==================================================
31. ELEMENTOS TEXTUAIS DINÂMICOS
==================================================

Quando o usuário selecionar território, permita que alguns textos mudem.

Exemplo estrutural:

Estado inicial:

"No Brasil, X% dos prefeitos eleitos estavam em situação de reeleição."

Selecionando região:

"No Nordeste, a proporção é Y%, Z p.p. em relação ao país."

Selecionando UF:

"Em Tocantins, ..."

Use apenas interpretações calculadas.

Nunca gere linguagem causal.

==================================================
32. MÉTODO DE TRABALHO
==================================================

Antes de editar HTML:

FASE 1
faça uma auditoria visual do dashboard atual.

Liste internamente:
- o que parece template;
- o que parece vibe coding;
- excesso de cards;
- falta de hierarquia;
- inconsistência de cores;
- redundâncias;
- gráficos inadequados;
- problemas narrativos.

FASE 2
defina um design system mínimo:
- grid;
- spacing;
- tipografia;
- cores;
- escala visual;
- padrões de gráfico;
- interação.

FASE 3
faça wireframe da narrativa antes da implementação.

FASE 4
implemente.

FASE 5
renderize e observe o resultado.

FASE 6
remova tudo que pareça decorativo ou artificial.

FASE 7
reavalie a página perguntando:

"isso parece uma visualização editorial de dados ou uma landing page feita por IA?"

Se parecer landing page, continue refinando.

==================================================
33. TESTE DE SUBTRAÇÃO
==================================================

Para cada elemento visual, pergunte:

"Se eu remover isso, a compreensão piora?"

Se a resposta for NÃO:

remova.

==================================================
34. TESTE DE GRÁFICO
==================================================

Para cada gráfico, escreva internamente:

PERGUNTA:
o que este gráfico responde?

EVIDÊNCIA:
qual informação ele mostra?

INSIGHT:
o que o usuário deve perceber?

Se você não conseguir responder claramente aos três:

o gráfico não deve existir.

==================================================
35. TESTE DE COR
==================================================

Para cada cor presente:

"qual informação essa cor codifica?"

Se a resposta for:

"é bonita",
"combina",
"dá destaque",

isso não basta.

Reduza ou elimine.

==================================================
36. TESTE DE INTERAÇÃO
==================================================

Para cada interação:

"qual nova pergunta o usuário consegue responder com isso?"

Se a resposta for nenhuma:

remova.

==================================================
37. TESTE DE STORYTELLING
==================================================

Leia somente:

headline principal
+
títulos das seções
+
títulos dos gráficos.

Sem olhar os gráficos.

Eles devem formar um resumo coerente da história.

Se parecer uma lista como:

"Visão geral"
"Dados por região"
"Dados por estado"
"Análise"
"Indicadores"

os títulos estão errados.

Eles precisam formar narrativa.

==================================================
38. NEUTRALIDADE
==================================================

Este é um tema eleitoral.

O design não deve sugerir que:

continuidade é positiva;
renovação é positiva;
continuidade é negativa;
renovação é negativa.

Evite linguagem como:

melhor;
pior;
sucesso;
fracasso;
domínio;
vitória da renovação;
resistência à mudança.

Descreva padrões observados.

==================================================
39. RESULTADO VISUAL ESPERADO
==================================================

Quero que alguém abra o dashboard e pense:

"isso parece um especial de dados profissional."

E não:

"alguém pediu para uma IA gerar um dashboard."

A sofisticação precisa surgir de:

hierarquia;
proporção;
tipografia;
dados;
anotações;
interação;
comparação;
ritmo;
espaço em branco.

Não de efeitos.

==================================================
40. IMPLEMENTAÇÃO
==================================================

Você pode:

- reutilizar os cálculos existentes;
- reutilizar dados agregados corretos;
- alterar profundamente HTML e CSS;
- alterar a estrutura da página;
- refazer gráficos;
- substituir biblioteca de visualização;
- reorganizar JavaScript.

Mantenha:

- um único dashboard.html;
- dados necessários embutidos;
- bibliotecas externas somente via CDN;
- funcionamento direto no navegador.

Não altere números corretos apenas para adaptar ao design.

==================================================
41. ENTREGA
==================================================

Agora:

1. audite o dashboard atual;
2. analise novamente a história sustentada pelos dados;
3. desenhe mentalmente o sistema visual;
4. refatore profundamente a página;
5. implemente visualizações coordenadas;
6. renderize;
7. teste desktop e mobile;
8. corrija problemas;
9. faça uma segunda rodada de refinamento visual;
10. faça o teste "anti vibe coding";
11. entregue a versão final.

NÃO pare para me explicar o que pretende fazer.

Faça o trabalho.

Ao terminar, me mostre apenas:

- a narrativa visual adotada;
- quais visualizações foram escolhidas e por quê;
- quais interações existem;
- quais elementos do design anterior foram removidos;
- eventuais limitações.
````

**O que funcionou / o que mudei:** A primeira versão funcionava, mas tinha aparência de template: cards com bordas arredondadas, pílulas, barra fixa com desfoque, grade de 100 quadrados redundante com a barra, números gigantes, quatro cartões de KPI e paleta verde-petróleo. O prompt trocou o papel do Claude de desenvolvedor para designer de informação e deu critérios verificáveis:

- uma visualização dominante por seção;
- grade de 12 colunas com larguras narrow, standard e wide;
- cor semântica constante e "contexto em neutro + objeto em cor";
- estado global coordenado;
- testes de subtração, de gráfico, de cor, de interação e de títulos;
- neutralidade.

O resultado foi refeito do zero: barra nacional larga, barras 100% por região, barras divergentes por UF a partir da média do Brasil (sem eixo truncado), dumbbell recorte × Brasil por porte e histograma espelhado da votação. Também ganhou uma faixa de contexto que só aparece com seleção, e o gráfico da chapa virou uma frase no método. A reanálise pedida no item 41 também corrigiu um erro de dados da versão anterior: 14 chapas cassadas ou históricas têm votos anulados (0%) e eram contadas como "vitórias com menos de 50%". A seção de votação passou a usar só os 5.530 eleitos na extração atual. A paleta sugerida foi mantida; só o ocre ganhou uma versão mais escura para texto, por contraste.

---

## Prompt 4

````
Estamos na ETAPA FINAL desta atividade.

Já existe uma versão implementada do trabalho. A partir de agora, NÃO quero uma nova exploração criativa nem uma reconstrução gratuita do projeto.

Sua missão é:

AUDITAR → CORRIGIR → REFINAR → VALIDAR → ENTREGAR.

Trabalhe autonomamente até a entrega estar concluída.

==================================================
1. CONTEXTO
==================================================

Atividade:
Storytelling de Dados — Eleições Municipais de 2024

Tema:
CONTINUIDADE E RENOVAÇÃO

Pergunta norteadora:

"O que as eleições de 2024 revelam sobre continuidade e renovação no comando das prefeituras?"

Público:
gestores, servidores e assessores de diferentes regiões em uma aula inaugural de uma escola de governo.

Minha pasta de entrega:

entregas/tiago-cardoso/

Arquivos obrigatórios:

- dashboard.html
- claude.md
- skill.md
- prompts.md

==================================================
2. REGRA PRINCIPAL DESTA ETAPA
==================================================

PRESERVE o que estiver funcionando bem.

Não refaça o projeto apenas por preferência estética.

Faça alterações somente quando elas melhorarem objetivamente:

- narrativa;
- legibilidade;
- visualização;
- interação;
- rigor metodológico;
- responsividade;
- acessibilidade;
- funcionamento;
- conformidade com a atividade.

Se encontrar algo com aparência de "vibe coding", corrija.

O resultado final deve parecer:

visualização editorial de dados
+
storytelling jornalístico
+
design de informação
+
análise para gestão pública.

E NÃO:

landing page;
template SaaS;
dashboard administrativo genérico;
frontend demonstrativo feito por IA.

==================================================
3. PRIMEIRO: AUDITE A VERSÃO ATUAL
==================================================

Leia novamente:

- README.md
- dados/dicionario.md
- entregas/tiago-cardoso/claude.md
- entregas/tiago-cardoso/skill.md
- entregas/tiago-cardoso/prompts.md
- entregas/tiago-cardoso/dashboard.html

Inspecione também dados/eleitos.csv quando necessário para validar os resultados.

Avalie a versão atual segundo:

1. narrativa;
2. rigor;
3. visualizações;
4. interação;
5. direção de arte;
6. diagramação;
7. uso de cores;
8. responsividade;
9. acessibilidade;
10. requisitos formais da entrega.

Não me apresente o diagnóstico antes de agir.

Corrija diretamente os problemas encontrados.

==================================================
4. STORYTELLING
==================================================

Confira se a página responde claramente:

"O que as eleições de 2024 revelam sobre continuidade e renovação no comando das prefeituras?"

A narrativa precisa possuir progressão.

Idealmente:

PANORAMA NACIONAL
→ DIFERENÇAS TERRITORIAIS
→ REGIÕES
→ UFs
→ COMPARAÇÃO COM A REALIDADE SELECIONADA
→ APROFUNDAMENTO
→ SÍNTESE.

O usuário que apenas rolar a página deve compreender a história.

A interação deve aprofundar a análise, não ser necessária para entender o argumento central.

Faça o seguinte teste:

leia apenas:
- headline;
- títulos das seções;
- títulos dos gráficos.

Eles precisam formar uma narrativa coerente.

Se forem apenas:

"Visão geral"
"Por região"
"Por estado"
"Indicadores"

melhore-os.

Use títulos orientados a descobertas reais dos dados.

==================================================
5. RIGOR DOS DADOS
==================================================

Revalide TODOS os números relevantes diretamente na base.

Obrigatoriamente confira:

- filtro cargo = Prefeito;
- quantidade de prefeitos;
- quantidade de municípios;
- continuidade;
- renovação;
- Brasil;
- regiões;
- UFs;
- percentuais;
- pontos percentuais;
- totais;
- dados faltantes;
- classificacao_validacao;
- arredondamentos;
- agregações utilizadas nos gráficos.

Não conte vice-prefeito como outra prefeitura.

Não duplique votos da chapa.

Não transforme célula vazia em zero ou "Não".

==================================================
6. DEFINIÇÃO DE CONTINUIDADE E RENOVAÇÃO
==================================================

Garanta que o dashboard NÃO sugira que alguém que não aparece como candidato à reeleição seja necessariamente:

- estreante;
- novo na política;
- sem experiência anterior;
- primeiro mandato da vida.

Use uma definição operacional sustentada pela base.

Explique brevemente essa limitação na metodologia.

Não invente informação histórica que não esteja disponível.

==================================================
7. NEUTRALIDADE
==================================================

Não apresente continuidade ou renovação como:

melhor;
pior;
positivo;
negativo;
sucesso;
fracasso.

As cores também não devem produzir esse julgamento.

Não use:

verde = bom
vermelho = ruim.

Use linguagem descritiva.

==================================================
8. DIREÇÃO VISUAL
==================================================

Faça uma última revisão estética usando princípios de information design.

REMOVA OU REDUZA:

- excesso de cards;
- card dentro de card;
- badges decorativos;
- pills desnecessárias;
- gradientes decorativos;
- glassmorphism;
- sombras pesadas;
- glow;
- ícones sem função;
- emojis decorativos;
- border-radius exagerado;
- fundos "AI style";
- animações gratuitas.

Priorize:

- grid editorial;
- hierarquia;
- espaço em branco;
- alinhamento;
- tipografia;
- proporção;
- gráficos;
- anotações;
- comparação;
- ritmo visual.

Se um elemento puder ser removido sem prejudicar compreensão, remova.

==================================================
9. CORES
==================================================

Garanta consistência semântica.

Uma cor para:

CONTINUIDADE.

Outra para:

RENOVAÇÃO.

Neutros para:

CONTEXTO.

As mesmas categorias precisam manter as mesmas cores em todos os gráficos.

Não use muitas cores diferentes.

Quando houver seleção de UF ou região:

- contexto pode ficar neutro;
- seleção deve receber destaque;
- Brasil deve permanecer uma referência clara.

==================================================
10. INTERAÇÃO
==================================================

Teste TODAS as interações existentes.

A experiência deve seguir o conceito:

BRASIL → REGIÃO → UF.

Quando houver seleção, as visualizações coordenadas devem reagir de maneira coerente.

Quando aplicável, atualize:

- headline contextual;
- números;
- ranking;
- destaque territorial;
- comparação;
- anotação;
- texto interpretativo.

Deve existir uma forma clara de voltar ao Brasil.

Nenhum controle pode ser decorativo.

Para cada interação pergunte:

"Que nova pergunta o usuário consegue responder?"

Se nenhuma, remova.

==================================================
11. VISUALIZAÇÕES
==================================================

Para cada gráfico existente, valide:

PERGUNTA:
o que ele responde?

EVIDÊNCIA:
qual dado mostra?

INSIGHT:
o que deve ser percebido?

Se um gráfico não responder claramente aos três pontos, corrija ou remova.

Não adicione gráficos apenas para preencher espaço.

Evite:

- 3D;
- gauge;
- radar;
- pizza com muitas categorias;
- gráfico exótico sem necessidade;
- efeitos visuais sem função.

==================================================
12. ANOTAÇÕES
==================================================

Sempre que houver descoberta relevante, prefira anotá-la diretamente na visualização.

O gráfico não pode depender do tooltip para ser compreendido.

Tooltip deve fornecer detalhe adicional.

==================================================
13. FORMATOS NUMÉRICOS
==================================================

Use convenções brasileiras.

Exemplos:

43,7%

+6,2 p.p.

5.553 municípios

Evite precisão falsa.

Uma casa decimal normalmente basta para percentuais.

==================================================
14. RESPONSIVIDADE
==================================================

Teste pelo menos conceitualmente/renderizando em larguras próximas a:

1440px
1024px
768px
390px

Corrija:

- overflow;
- textos cortados;
- labels sobrepostos;
- gráficos ilegíveis;
- tooltips fora da tela;
- controles difíceis de usar;
- legendas quebradas.

Mobile não deve ser apenas desktop espremido.

Reorganize quando necessário.

==================================================
15. ACESSIBILIDADE
==================================================

Verifique:

- contraste;
- labels;
- focus;
- controles por teclado;
- uso de ARIA quando apropriado;
- informação não representada exclusivamente por cor.

==================================================
16. dashboard.html
==================================================

O dashboard precisa continuar sendo UM ÚNICO ARQUIVO.

Permitido:

- HTML;
- CSS embutido;
- JavaScript embutido;
- bibliotecas via CDN.

Todos os dados necessários precisam estar agregados e embutidos no próprio HTML/JavaScript.

O dashboard NÃO pode:

- ler eleitos.csv em runtime;
- fazer fetch de arquivo local;
- depender de Python;
- depender de servidor;
- depender de outro arquivo da pasta.

Abra diretamente como:

file://.../dashboard.html

e valide que funciona.

==================================================
17. claude.md
==================================================

Revise completamente.

A primeira seção obrigatória deve permanecer exatamente:

## Qual história meu dashboard conta?

Garanta que ela descreve a HISTÓRIA REAL encontrada nos dados.

Revise:

- contexto;
- público;
- perguntas;
- decisões de design;
- escolhas de visualização;
- limitações;
- metodologia.

Remova placeholders.

Não descreva funcionalidades que não existam mais.

==================================================
18. skill.md
==================================================

Revise a skill final.

Ela precisa ser:

- genérica;
- reutilizável;
- acionável.

Ela NÃO pode depender deste tema específico.

Não deve citar:

- eleições;
- TSE;
- prefeitos;
- reeleição;
- eleitos.csv.

Ela deve expressar os princípios reais utilizados:

- storytelling;
- escolha de gráficos;
- interação;
- cores;
- layout;
- hierarquia;
- acessibilidade;
- responsividade;
- títulos;
- anotações;
- redução de ruído;
- checklist.

==================================================
19. prompts.md
==================================================

Revise prompts.md.

Mantenha os prompts em ordem cronológica.

NÃO invente prompts que não foram usados.

Adicione este prompt final como o último prompt do diário.

Na reflexão "O que funcionou / o que mudei", registre que esta etapa foi usada para:

- auditoria final;
- refinamento de dataviz;
- validação metodológica;
- testes;
- preparação da entrega.

==================================================
20. TESTE AUTOMATIZADO / TÉCNICO
==================================================

Execute tudo que puder para validar a entrega.

Incluindo, quando aplicável:

- análise dos dados;
- scripts temporários;
- validações de agregação;
- parsing do HTML;
- JavaScript;
- links CDN;
- erros óbvios de console;
- caracteres UTF-8;
- elementos inexistentes;
- funções JS não definidas;
- responsividade.

Arquivos temporários NÃO devem ficar dentro de:

entregas/tiago-cardoso/

==================================================
21. TESTE FINAL "ANTI-VIBE-CODING"
==================================================

Antes de encerrar, observe o dashboard renderizado e responda internamente:

Isso parece:

A)
um especial editorial de dados produzido profissionalmente;

ou

B)
uma landing page/dashboard gerado por IA?

Se estiver mais próximo de B:

faça uma última rodada de simplificação.

Não resolva isso adicionando mais efeitos.

Resolva removendo ruído e melhorando:

- hierarquia;
- tipografia;
- alinhamento;
- composição;
- gráficos;
- anotações;
- espaço;
- narrativa.

==================================================
22. NÃO ALTERE
==================================================

Não modifique:

- README.md;
- dados/;
- entregas/_modelo/;
- entregas de outros alunos;
- configurações do professor;

a menos que seja absolutamente necessário apenas para leitura/teste.

A entrega deve modificar somente:

entregas/tiago-cardoso/

==================================================
23. GIT: VERIFICAÇÃO ANTES DA ENTREGA
==================================================

Ao terminar os arquivos:

execute:

git status
git diff

Confirme que as alterações da entrega estão restritas a:

entregas/tiago-cardoso/

Se houver arquivos temporários, remova-os.

Se houver alteração acidental fora da minha pasta, reverta SOMENTE essas alterações acidentais.

NÃO reverta trabalho pré-existente do usuário.

==================================================
24. FAÇA A ENTREGA
==================================================

Depois de todas as validações, finalize a entrega usando Git.

1. verifique em qual branch estou;

2. faça:

git add entregas/tiago-cardoso

3. confira novamente o staged diff;

4. faça o commit:

git commit -m "Entrega Tiago Cardoso - continuidade e renovacao"

5. faça push da branch atual para origin:

git push -u origin HEAD

6. se GitHub CLI (`gh`) estiver disponível e autenticado, abra um Pull Request para o repositório original da disciplina.

Use um título claro, por exemplo:

"Entrega - Tiago Cardoso - Continuidade e renovação"

No corpo do PR:

- identifique o aluno;
- tema Continuidade e renovação;
- informe que os quatro arquivos foram incluídos;
- preencha qualquer checklist existente no template do PR corretamente.

Antes de criar o PR, verifique qual é o repositório upstream/original e qual é a branch base correta.

NÃO adivinhe.

Descubra com:

git remote -v
git branch -vv

e, se necessário, inspecione o repositório.

7. depois de abrir o PR:

- verifique se existe CI/GitHub Actions;
- aguarde ou consulte a verificação automática;
- se houver erro relacionado à minha entrega, leia a mensagem;
- corrija;
- commit novamente;
- push;
- verifique novamente.

Não abra um segundo PR para corrigir o primeiro.

==================================================
25. SE NÃO CONSEGUIR ABRIR O PR
==================================================

Se `gh` não estiver disponível, não estiver autenticado ou alguma permissão impedir a criação do PR:

NÃO pare a entrega anterior.

Garanta que:

- commit foi feito;
- push foi feito.

E ao final me forneça o link exato do meu fork/branch ou a instrução mínima necessária para eu abrir o PR manualmente.

==================================================
26. DEFINIÇÃO DE PRONTO
==================================================

O trabalho só está FINALIZADO quando:

[ ] dashboard.html funciona diretamente no navegador
[ ] narrativa responde à pergunta norteadora
[ ] números foram revalidados
[ ] metodologia está correta
[ ] interação funciona
[ ] visual não parece template/vibe coding
[ ] mobile funciona
[ ] claude.md está completo
[ ] skill.md está completa e genérica
[ ] prompts.md está atualizado
[ ] existem exatamente os 4 arquivos de entrega
[ ] alterações Git estão restritas à minha pasta
[ ] commit foi criado
[ ] push foi realizado
[ ] PR foi aberto, se tecnicamente possível
[ ] verificação automática foi conferida, se disponível

==================================================
27. SAÍDA FINAL
==================================================

Não me mostre logs longos.

Quando terminar, responda apenas com:

ENTREGA FINALIZADA

- história central encontrada:
- arquivos entregues:
- principais interações:
- validações realizadas:
- commit:
- branch:
- push:
- Pull Request:
- CI/verificação automática:
- eventual pendência que dependa exclusivamente de mim:

Agora execute todo o processo até a entrega final.

. Você tem no maximo 5 minutos para finalizar
````

**O que funcionou / o que mudei:** Esta etapa foi usada para:

- **Auditoria final:** releitura dos quatro arquivos contra os requisitos do README e do validador automático.
- **Refinamento de dataviz:** a versão do Prompt 3 já atendia aos critérios editoriais, então foi preservada sem reconstrução.
- **Validação metodológica:** os números foram reconferidos por script contra o CSV (5.553 prefeitos e municípios, regiões, UFs, faixas de votos e de porte, medianas, exclusões por `classificacao_validacao`).
- **Testes:** console, todos os 31 recortes, ausência de rolagem horizontal entre 320 e 1440 px e o arquivo aberto sem dependências locais.
- **Preparação da entrega:** commit, push e Pull Request.

Por causa do limite de 5 minutos, a etapa priorizou validar e entregar em vez de fazer novos ajustes visuais.
