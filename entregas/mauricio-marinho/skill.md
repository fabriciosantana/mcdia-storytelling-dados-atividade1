---
name: assinatura-visual-marinho
description: Assinatura visual e narrativa de Mauricio Marinho para dashboards em HTML com impacto e sofisticação. Usa azuis e cinzas com laranja só para destaque, interatividade com agrupamentos e filtros cruzados sempre que possível e transições suaves em toda mudança de estado. Use sempre que for criar ou revisar um dashboard, painel, gráfico ou relatório visual, com qualquer base de dados.
---

# Assinatura visual Marinho

> **Impacto na primeira dobra, sofisticação nos detalhes, movimento com propósito.**
> O painel deve parecer editorial (revista de dados), e não um relatório de sistema. O leitor entende a mensagem em 5 segundos e quer explorar por 5 minutos.

## Quando usar

- Ao criar ou revisar qualquer dashboard, painel, gráfico ou relatório visual em HTML.
- Vale para qualquer base de dados e qualquer público. Ajuste o tom da linguagem ao público, mas mantenha a assinatura visual.

## 1. Os cinco princípios da assinatura

1. **Impacto primeiro.** Abra com uma faixa de abertura (hero) escura em azul profundo, com o título-mensagem e 3 ou 4 números-chave que contam de zero até o valor ao carregar.
2. **Sofisticação contida.** Muito espaço em branco, poucas cores, tipografia editorial e nenhum ornamento sem função. Elegância vem de alinhamento, ritmo e consistência, não de efeitos.
3. **Explorar é parte da história.** Todo gráfico que admite recorte ganha **filtro** e, quando houver hierarquia ou dimensão alternativa, **agrupamento**. Os filtros são globais e cruzados.
4. **Movimento suave e significativo.** Nada muda de estado "aos saltos": barras crescem, listas se reordenam deslizando e números contam. A animação mostra o que mudou e nunca atrasa a leitura.
5. **Rigor visível.** Títulos afirmam só o que os dados sustentam, cada recorte mostra o seu n e os limites ficam escritos.

## 2. Estrutura narrativa

- **Hero:** rótulo pequeno em caixa alta (contexto e público), título-mensagem em fonte serifada, um parágrafo de 2 a 3 frases e os números-chave.
- **Barra de filtros fixa no topo** (sticky), logo abaixo do hero, com controles segmentados para as dimensões principais, um botão "Limpar" e um resumo do recorte ativo ("Mostrando 1.200 de 5.000 · Categoria A").
- **Blocos numerados** (01, 02, 03…). Cada um tem um rótulo curto, um **título que é uma conclusão**, uma frase de apoio, o gráfico e uma **leitura do recorte** que se atualiza com os filtros ("No recorte atual: 42%").
- **Títulos descrevem o quadro geral; a leitura do recorte descreve o filtro.** Nunca reescreva o título com base no filtro, porque ele pode deixar de ser verdade.
- **Alerta de leitura errada** logo no primeiro bloco: uma caixa com borda laranja.
- **Hipóteses separadas dos fatos**, cada uma com "os dados mostram / os dados não mostram".
- **Fechamento** com perguntas para o público e, depois, **método, limites e tabela de dados** (a tabela também segue os filtros).

## 3. Interatividade: agrupar e filtrar sempre que possível

**Filtros globais (cross-filter)**
- Todos os gráficos leem o mesmo estado de filtros, guardado em um único objeto (`estado = {dimA: null, dimB: null, …}`) e redesenhado por uma única função `atualizar()`.
- **Um gráfico não filtra a própria dimensão; ele a destaca.** No gráfico por categoria com o filtro "A", todas as categorias continuam visíveis, a categoria A fica em cor plena e as demais em cinza. Assim a comparação não se perde.
- **Clicar em uma barra filtra por ela**, e clicar de novo desfaz. Mostre um cursor de mão e a dica "clique para filtrar".
- Quando o recorte ficar pequeno (n < 30), mostre um aviso discreto: "recorte pequeno: interprete com cautela".
- Mantenha os filtros sempre visíveis e reversíveis, com um "Limpar" de um clique.

**Agrupamentos**
- Use um **controle segmentado** (pílulas lado a lado com um indicador que desliza) acima do gráfico para trocar a unidade ou o agrupamento: "Grupo | Subgrupo", "Categoria | Família", "% | Nº absoluto", "Grupo A | Grupo B".
- Ofereça **ordenação** ("por valor | por tamanho | alfabética") quando a lista tiver mais de 8 itens.
- Trocar o agrupamento anima a transição; o gráfico não é recriado do zero.

**Tooltip**
- Em toda marca de dado, com o rótulo completo, o valor absoluto, o percentual e o n. Funciona com mouse, toque e foco do teclado.
- Fundo azul-noite, texto claro, cantos de 10px, aparecendo em 150ms com leve deslocamento vertical.

## 4. Movimento

| Token | Valor | Uso |
|---|---|---|
| `--ease` | `cubic-bezier(.22, 1, .36, 1)` | Padrão de tudo: começa rápido e pousa suave |
| `--t-rapido` | `180ms` | Hover, foco, tooltip |
| `--t-medio` | `450ms` | Cores, opacidade, controle segmentado |
| `--t-longo` | `750ms` | Largura e altura de barras, reordenação |

- **Barras:** anime `width`/`height` (ou `transform: scaleX`) com `--t-longo`. Na primeira exibição, crescem a partir de zero.
- **Reordenação:** use a técnica FLIP. Meça as posições antes, reordene o DOM, aplique o `translateY` inverso e anime até zero. As barras deslizam para a nova posição.
- **Números:** contam do valor anterior até o novo em 600 a 900ms, com easing.
- **Entrada dos blocos:** surgem com fade e deslocamento de 16px quando entram na tela (`IntersectionObserver`), em cascata de 60ms entre os elementos.
- **Hover:** cartões sobem 2px com sombra suave. Barras fora do hover ficam em 55% de opacidade.
- **Sempre** respeite `prefers-reduced-motion: reduce`, desligando animações e mantendo só as trocas de estado.
- Nunca use bounce, rotação, parallax ou animação em loop.

## 5. Paleta: azuis e cinzas, laranja para destaque

| Papel | Claro | Escuro | Uso |
|---|---|---|---|
| Azul-noite (hero, tooltip) | `#0E2240` | `#0A1626` | Faixa de abertura e superfícies de contraste |
| Série principal | `#2B63B0` | `#2E61B2` | A categoria central da história |
| Série secundária | `#6FA4E6` | `#6497DA` | A categoria em contraste |
| Azul de apoio | `#A9C6EC` | `#294A75` | Faixas, fundos de destaque frio |
| **Destaque laranja** | `#E36A1E` | `#E2671F` | Referência, extremo, foco. **No máximo 1 ou 2 por bloco** |
| Texto laranja | `#B34F10` | `#F29A5E` | Números em destaque (contraste de texto) |
| Fundo laranja | `#FDF0E6` | `#2E2016` | Alertas e cartões em evidência |
| Texto | `#142235` / `#47566B` / `#6B7889` | `#EEF2F7` / `#B9C4D2` / `#8E9BAB` | Principal / secundário / auxiliar |
| Neutro de marca | `#C3CCD8` | `#3D4A5B` | Itens fora de foco |
| Linhas | `#DBE1E9` | `#2B3644` | Bordas e eixos |
| Fundo / cartão | `#F3F5F8` / `#FFFFFF` | `#0F141B` / `#18202A` | Superfícies |

- **Cada categoria tem a mesma cor em todos os gráficos.** O laranja nunca vira uma série a mais.
- **Texto nunca usa a cor da série.** A cor aparece em uma amostra ao lado.
- **Valide** toda paleta nova para daltonismo e contraste nos dois modos, antes de usar.
- O **modo escuro** usa tons escolhidos para ele, com um botão de alternância e respeito a `prefers-color-scheme`.

## 6. Tipografia e composição

- **Títulos:** serifada editorial (`"Source Serif 4"`, fallback `Georgia, serif`), peso 600 e entrelinha de 1,1 a 1,2.
- **Texto e números:** sem serifa (`"Inter"`, fallback `system-ui`), com números tabulares (`font-variant-numeric: tabular-nums`).
- Carregue as fontes via Google Fonts com `display=swap`. O painel precisa ficar bonito também com os fallbacks.
- Escala: hero de 36 a 56px, título de bloco de 24 a 32px, texto de 16 a 17px e notas de 13px. Rótulos de seção em 12px, caixa alta e espaçamento de 0,12em.
- Largura máxima do painel de 1120px e coluna de texto de até 720px. Respiro de 32 a 48px entre blocos.
- Cartões com cantos de 16px, borda de 1px, sombra muito suave e padding de 24 a 36px.
- **Responsivo:** teste em 390px e em 1280px. No celular, filtros viram uma faixa com rolagem horizontal, as grades viram 1 coluna e não pode haver rolagem horizontal da página.
- Posicione linhas de referência em unidades proporcionais (CSS `calc` com %), nunca em pixels calculados uma vez só.

## 7. Escolha de gráficos

| Para mostrar | Use | Evite |
|---|---|---|
| A mensagem principal | Número grande com contagem animada + barra única dividida | Pizza, velocímetro |
| Comparar categorias | Barras horizontais ordenadas, clicáveis para filtrar | Ordem alfabética como padrão, 3D |
| Comparar com uma referência | Linha tracejada laranja rotulada | Duas cores para acima e abaixo sem explicação |
| Duas distribuições | Histograma agrupado normalizado para 100%, com alternância "% / nº" | Contagens absolutas de grupos de tamanhos diferentes |
| Composição | Barras horizontais de 100% com o rótulo do segmento | Rosca com mais de 3 fatias |

- Nunca use eixo duplo. Barras começam em zero. Grade quase invisível. Valor rotulado no fim da barra.

## 8. Linguagem

- Frases curtas, voz ativa, linguagem do público, números arredondados no texto e precisos no gráfico.
- Formato numérico do idioma do público (pt-BR: `12,5%`, `1.234`).
- Use "associado a", "coincide com" ou "pode indicar", nunca "causa", a menos que o desenho do estudo permita.
- Diga com clareza o que os dados não permitem afirmar.

## 9. Requisitos técnicos

- Um único arquivo HTML com CSS e JS embutidos e sem dependências obrigatórias, exceto as fontes por CDN, que têm fallback.
- Os dados entram **agregados**: tabelas de contagem (cubos) com as dimensões de filtro e uma dimensão de análise por cubo. Nada de identificadores pessoais. A agregação fica em um script separado, com `assert` nos totais.
- Inclua `aria-label` nos gráficos, `aria-pressed` nos filtros, foco visível em laranja e uma tabela de dados em `<details>`.

## 10. Checklist da assinatura

- [ ] O hero causa impacto e diz a mensagem em uma frase?
- [ ] Todo gráfico que admite recorte tem filtro, e os filtros se cruzam entre os gráficos?
- [ ] Há agrupamento ou ordenação alternativa onde faz sentido?
- [ ] Toda mudança de estado é animada, suave e respeita `prefers-reduced-motion`?
- [ ] O laranja aparece só onde o olho precisa ir?
- [ ] Os títulos continuam verdadeiros com qualquer filtro, e a leitura do recorte mostra o n?
- [ ] O painel foi conferido no desktop, no celular e no modo escuro, sem erros no console?
