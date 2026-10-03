---
name: editorial-data-storytelling
description: Orienta a criação de dashboards narrativos e editoriais em HTML a partir de dados, priorizando clareza da mensagem, hierarquia visual, escolha adequada de gráficos, acessibilidade e uso semântico da cor. Use sempre que for construir um dashboard, reportagem de dados, relatório explicativo ou painel que precise contar uma história guiada por uma pergunta.
---

# Editorial data storytelling

## Quando usar

Use esta skill quando:
- o produto final for um **dashboard narrativo**, uma **reportagem de dados**, um **relatório explicativo** ou uma **apresentação orientada por uma pergunta**;
- o público for leigo ou geral e precisar entender uma mensagem, não explorar livremente uma base;
- houver uma pergunta norteadora e uma sequência de achados que a respondem;
- o resultado for publicado como página HTML lida de cima para baixo, em desktop e celular.

Não use como guia principal para painéis operacionais de monitoramento contínuo (métricas em tempo real, filtros livres, BI exploratório). Nesses casos, aproveite apenas as regras de cor, tipografia e acessibilidade.

## Estrutura narrativa

### Antes de escrever
- **Comece pela pergunta.** Escreva a pergunta norteadora e a resposta em uma frase antes de escolher qualquer gráfico. Se não conseguir escrever a resposta, volte para a análise.
- **Defina o público e o que ele já sabe.** Liste os termos técnicos que ele não conhece e explique cada um na primeira vez que aparecer.

### Ordem dos blocos
- **Abra com a mensagem principal como título jornalístico:** uma afirmação verificável, com número, e não um rótulo ("O tempo médio de espera caiu de 40 para 25 minutos", e não "Visão geral").
- **Use um subtítulo para dar contexto mínimo:** o que é a base, período, unidade de contagem e o que ela não representa.
- **Apresente primeiro a visão mais familiar e compreensível** (a contagem que o leitor já espera ver).
- **Introduza uma virada só quando os dados justificarem:** uma segunda leitura, um contraste ou uma exceção que muda a interpretação inicial. Explique a nova métrica *antes* de mostrá-la, de preferência com um exemplo concreto.
- **Organize em começo → virada → aprofundamento → fechamento.**
  - Cada bloco responde a **uma** pergunta explícita.
  - Cada bloco termina com uma frase de transição para o próximo.

### Aprofundamento sem repetição
- **Aprofunde sem repetir gráficos.** Se dois blocos mostram o mesmo dado, una-os (por exemplo, revele o mesmo gráfico em etapas) ou troque a medida (contagem → proporção).
- **Mantenha entre 4 e 7 visualizações principais.** Use KPIs e texto apenas quando fizerem a narrativa avançar.

### Fechamento
- **Termine com síntese, fonte, método e limitações** em um bloco próprio, com o título "O que os dados mostram e o que não mostram".
- **Repita as limitações perto da interpretação a que se referem**, não apenas no rodapé.

### Linguagem
- Escreva de forma factual e neutra, sem adjetivos valorativos sobre os grupos comparados.
- Não sugira causalidade quando os dados só mostram associação ou distribuição.
- Não dê nomes de impacto ("domínio", "força", "influência") a métricas que não medem isso. Diga exatamente o que é contado.
- Não dramatize diferenças pequenas. Se dois valores estão próximos, diga que estão próximos.

## Escolha de gráficos

### Qual forma para qual comparação
| Pergunta | Use | Evite |
|---|---|---|
| Comparar quantidades entre categorias | Barras horizontais ordenadas, com rótulo de valor | Pizza/rosca com mais de 3 fatias, barras verticais com rótulos longos |
| Evolução no tempo | Linha (ou barras para poucos períodos discretos) | Área empilhada com muitas séries |
| Duas medidas comparáveis por categoria | Halteres (dumbbell) ou slope chart na mesma escala | Dois gráficos separados com escalas diferentes |
| Parte de um todo, poucas partes | Barra 100% única ou gráfico de unidades (100 quadrados) | Pizza 3D, rosca com legenda separada |
| Composição em vários grupos | Barras 100% com poucas categorias; matriz se houver muitas | Barras empilhadas com 6 ou mais cores categóricas |
| Cruzamento de duas dimensões com muitas categorias | Matriz/tabela de calor com o valor escrito na célula | Barras agrupadas com dezenas de séries |
| Unidades territoriais quando a área não importa | Tile map (quadrados iguais) ou matriz | Mapa coroplético por área |
| Proporção com bases de tamanhos diferentes | Barras 100% com o n escrito ao lado | Percentuais sem denominador |

### Regras gerais
- **Comece as escalas de barras em zero.** Nunca corte o eixo de uma barra.
- **Use mapas somente quando a geografia for parte da pergunta.** Quando a área territorial não representa a quantidade medida, não use área como substituto visual de quantidade: prefira tile map ou matriz.
- **Nunca empilhe nem some uma métrica não aditiva** (por exemplo, quando um item pode pertencer a vários grupos). Declare na nota quando a soma ultrapassar 100%.
- **Mostre o n** sempre que um percentual vier de uma base pequena.
- **Não escolha um gráfico porque é bonito.** Escolha pela comparação que o leitor precisa fazer.
- **Evite 3D, efeitos de profundidade, pictogramas decorativos e gráficos de radar.**

### Anotações
- Use no máximo **2 anotações por gráfico**: texto curto, número-chave em negrito, fio-guia fino de 1px até o ponto anotado.
- Anote **o que observar**, não o que concluir.
- Não use caixas, setas decorativas nem balões.

### Tooltips
- Use tooltips só como complemento: **nunca** como única fonte de um dado essencial.
- Mantenha um formato fixo: **categoria · valor absoluto · denominador · percentual**.
- Garanta abertura por mouse, foco de teclado e toque, e fechamento com Esc ou toque fora.

### Evitar chartjunk
- Remova bordas de gráfico, fundos coloridos, sombras, gradientes e cantos arredondados acima de 2px.
- Mostre grade apenas no eixo de valor, em cor de fio clara. Remova o eixo quando houver rótulo direto de valor.
- Prefira **rótulo direto** a legenda. Use legenda apenas quando o rótulo direto for impossível.
- Use **um único destaque** por gráfico.

## Paleta de cores

### Regras
- **Dê a cada cor uma função semântica** (métrica, destaque, contexto, estrutura) e registre essa função. Cor sem função é decoração: remova.
- **Mantenha o contexto em neutros.** Use cinzas para tudo o que não é o ponto do bloco.
- **Use poucas cores de destaque:** no máximo um matiz de destaque mais sua variação clara, além da família neutra/tinta.
- **Mesma função = mesma cor em todo o documento.** Nunca reutilize uma cor com outro significado.
- **Não crie uma cor por categoria quando houver categorias demais** (mais de 5) ou quando as categorias tiverem associação simbólica (marcas, organizações, grupos). Identifique-as por **rótulo direto e ordem estável**.
- **Evite arco-íris** e paletas categóricas longas.
- **Não use verde/vermelho como bom/ruim** nem pares de cores com associação simbólica, a não ser que o dado tenha de fato essa polaridade e ela esteja explicada.
- **Não dependa apenas de cor:** combine cor com luminância, forma (● × ○, ● × ■), padrão, posição ou rótulo.
- **Verifique o contraste WCAG:**
  - texto: 4,5:1 ou mais;
  - texto grande e elementos gráficos essenciais: 3:1 ou mais.
- Um tom claro de destaque que fique abaixo de 3:1 contra o fundo deve ter borda no tom escuro.
- Para escalas sequenciais, use **um único matiz** (ou cinzas) variando em luminância. Troque a cor do texto (escuro/branco) conforme a faixa para manter o contraste.

### Tokens

| Token | HEX | Função | Onde usar | Onde não usar |
|---|---|---|---|---|
| `--paper` | #FFFFFF | Fundo da página e dos gráficos | Fundo geral | — |
| `--paper-alt` | #F5F6F7 | Fundo secundário neutro | Nota metodológica destacada, cabeçalho de tabela | Cards decorativos, fundo de gráfico |
| `--ink` | #1A1F24 | Texto principal; métrica ou série primária | Títulos, corpo, dado principal em destaque | Elementos de contexto |
| `--ink-2` | #48515A | Texto secundário | Subtítulos, rótulos de dado, anotações | Títulos |
| `--ink-3` | #646D77 | Texto terciário | Fonte, notas, rótulos de eixo | Dados essenciais |
| `--rule` | #DDE1E5 | Fios e grade | Separadores de seção, linhas de grade | Qualquer marca que carregue dado |
| `--rule-strong` | #8A939C | Conectores, contexto de dado | Linhas de conexão, barras de contexto | Texto |
| `--accent` | #0E7470 | Destaque semântico (petróleo) | A métrica ou conceito que o bloco quer evidenciar; números-chave ligados a ele | Decoração, categorias, polaridade bom/ruim |
| `--accent-light` | #9FCFCB | Variação clara do destaque | Segmentos complementares ao destaque, sempre com borda `--accent` | Sozinho, sem borda ou rótulo |

**Escala sequencial neutra (opcional), com a cor de texto indicada para cada faixa:**

| Faixa | HEX | Texto |
|---|---|---|
| 1 (menor) | #EEF0F2 | `--ink` |
| 2 | #CDD3D9 | `--ink` |
| 3 | #9AA4AE | `--ink` |
| 4 | #5E6872 | branco |
| 5 (maior) | #262D34 | branco |

Contrastes medidos contra #FFFFFF:

| Token | Contraste |
|---|---|
| `--ink` | 16,6:1 |
| `--ink-2` | 8,1:1 |
| `--ink-3` | 5,3:1 |
| `--accent` | 5,6:1 |
| `--rule-strong` | 3,1:1 |
| `--accent-light` | 1,7:1 (exige borda) |

## Tipografia e layout

### Fontes e hierarquia
- **Use uma serif editorial para narrativa e títulos:** *Source Serif 4*, com fallback `Georgia, serif`.
- **Use uma sans legível para dados e interface:** *Libre Franklin*, com fallback `system-ui, -apple-system, "Segoe UI", sans-serif`. Ative `font-variant-numeric: tabular-nums` em números, tabelas e rótulos de gráfico.
- **Escala tipográfica (desktop / celular, em px):**

  | Elemento | Fonte | Desktop | Celular | Peso / cor |
  |---|---|---|---|---|
  | Rótulo de seção (kicker) | sans, caixa alta, espaçamento +0,08em | 13 | 12 | 600, `--ink-2` |
  | Título principal | serif | 46 / altura de linha 1,1 | 30 | 700 |
  | Subtítulo principal | serif | 21 / 1,45 | 18 | 400, `--ink-2` |
  | Título de bloco | serif | 30 / 1,2 | 24 | 700 |
  | Corpo | serif | 18 / 1,6 | 17 | 400 |
  | Título de gráfico | sans | 17 | 16 | 600 |
  | Subtítulo de gráfico (unidade e denominador) | sans | 15 | 14 | 400, `--ink-2` |
  | Rótulos de dado e eixos | sans | 13 | 13 (mínimo) | — |
  | Número em destaque (KPI) | sans, tabular | 64 | 48 | 700 |
  | Notas, fonte e metodologia | sans | 13 / 1,5 | 13 / 1,5 | `--ink-3` |

- Use no máximo duas famílias tipográficas e três pesos (400, 600, 700).

### Largura e espaçamento
- **Controle a largura de leitura:** coluna de texto com no máximo **680px** (65–75 caracteres por linha); gráficos podem se estender até **960px**.
- **Use um sistema de espaçamento de base 8:** 4, 8, 12, 16, 24, 32, 48, 72, 96px.
  - Entre blocos narrativos: 96px no desktop e 64px no celular.
  - Entre título do gráfico e gráfico: 16px.
  - Entre gráfico e fonte: 12px.
- **Use espaço em branco e fios de 1px para separar seções.** Não use cards, caixas, sombras ou gradientes decorativos.
- Coloque a linha de fonte e base abaixo de cada gráfico: "Base: … · Fonte: …, período/data de referência".

### Layout responsivo
- Funcione a partir de **360px de largura**, com margem lateral de 16px (24px a partir de 768px).
- **Não permita rolagem horizontal no celular.**
  - Barras horizontais continuam horizontais, com o rótulo acima da barra se necessário.
  - Matrizes são transpostas.
  - Mapas em grade usam células de no mínimo 44px e escondem informação secundária no tooltip ou na tabela.
- Teste em 360, 768 e 1280px.

### Acessibilidade e interação
- Dê a cada SVG `role="img"` e um `aria-label` com uma frase-resumo do que o gráfico mostra (não "gráfico de barras").
- Ofereça uma **tabela equivalente** para cada gráfico (por exemplo, em `<details>`), com os mesmos números.
- Garanta **foco de teclado visível** em todo elemento interativo e suporte a teclado e toque para tooltips e controles.
- Respeite `prefers-reduced-motion`: sem animações de entrada quando ativado; nunca use elementos piscantes.
- Declare o idioma da página (`lang`) e formate números e datas no padrão do público (por exemplo, vírgula decimal e ponto de milhar em pt-BR).
- Mantenha a mesma precisão decimal em todo o documento: 1 casa em textos e gráficos, mais casas só em notas ou tabelas.
- Gere texto, gráficos, tabelas e tooltips a partir de **um único objeto de dados agregados** embutido na página.

## Checklist final

Antes de entregar o HTML, verifique cada item e corrija o que falhar:

**História**
- [ ] A história responde à pergunta norteadora? A resposta aparece no título ou no primeiro bloco?
- [ ] Cada gráfico tem uma função narrativa declarada (a pergunta que responde)?
- [ ] Existe algum gráfico redundante (mesmo dado, mesma medida)? Se sim, una ou remova.
- [ ] Os títulos dos gráficos comunicam uma mensagem verificável, e não apenas o tema?
- [ ] Cada bloco termina com uma transição para o seguinte?

**Números e escalas**
- [ ] As escalas de barras começam em zero? Diferenças pequenas não estão exageradas no texto nem no destaque?
- [ ] Unidade e denominador estão explícitos junto a cada gráfico ("% de N …")?
- [ ] Métricas não aditivas estão sinalizadas e não aparecem empilhadas nem em pizza?
- [ ] Os números do texto, dos gráficos, das tabelas e dos tooltips vêm da mesma fonte agregada e batem entre si?
- [ ] A precisão decimal é consistente e há nota de arredondamento quando os percentuais não somam 100?

**Contexto e limites**
- [ ] Fonte, período e data de referência estão visíveis?
- [ ] As limitações aparecem próximas da interpretação a que se referem, além do bloco final?
- [ ] O texto evita causalidade, juízo de valor e termos que a métrica não sustenta?

**Cor, legibilidade e acessibilidade**
- [ ] Cada cor tem um significado único e consistente em todo o documento?
- [ ] O dashboard funciona sem depender da cor (teste em escala de cinza)?
- [ ] Texto com contraste de 4,5:1 ou mais e elementos gráficos essenciais com 3:1 ou mais?
- [ ] Existem tabelas ou alternativas acessíveis, `aria-label` nos SVGs e foco de teclado visível?
- [ ] Os tooltips são só complementares e funcionam por teclado e toque?

**Layout e técnica**
- [ ] Funciona em 360, 768 e 1280px, sem rolagem horizontal?
- [ ] Não há chartjunk (sombras, gradientes, 3D, cards, ícones decorativos, legendas desnecessárias)?
- [ ] O HTML abre direto no navegador, sem erros no console e sem ler arquivos locais?
