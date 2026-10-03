---
name: audiencia-legislativa-com-dados
description: Orienta dashboards públicos, acessíveis e baseados em evidências para audiências legislativas com pouco tempo. Use ao transformar estatísticas eleitorais ou sociais em uma narrativa visual clara, comparável e cuidadosa.
---

# Audiência legislativa com dados

## Quando usar

Use esta skill quando o dashboard precisar apoiar uma audiência pública, briefing parlamentar ou reunião de decisão em que a pessoa leitora terá poucos minutos e precisa saber o que o dado mostra, onde há diferença e o que merece atenção.

## Estrutura narrativa

- Comece com uma frase-tese e um número principal; não faça o público descobrir a conclusão sozinho.
- Mostre o denominador logo no início: pessoas, municípios, candidaturas, votos ou outro universo.
- Organize a sequência em quatro movimentos: panorama nacional, comparação territorial, recorte explicativo e implicação para a agenda pública.
- Termine com uma síntese e uma pergunta de acompanhamento; não transforme correlação em causa.
- Prefira linguagem direta, frases curtas e verbos ativos. Explique qualquer termo técnico na primeira ocorrência.

## Escolha de gráficos

- Use barras 100% empilhadas para comparar composição entre grupos com tamanhos diferentes.
- Use barras horizontais ordenadas para ranking de categorias ou territórios.
- Mostre percentual junto do total absoluto quando grupos tiverem denominadores diferentes.
- Use uma linha de referência para a média geral e identifique-a por texto.
- Evite mapas quando a pergunta é ranking e evite pizza, 3D, efeitos decorativos e eixos truncados.
- Se houver uma variável declarada, descreva-a como declaração; não a trate como identidade inferida ou causalidade.

## Paleta de cores

- Fundo: `#f7f4f8`; texto: `#20222a`; texto secundário: `#626573`.
- Categoria feminina: `#8b4c8f`; categoria masculina: `#2f6877`.
- Referência/atenção: `#d99a2b`; grades e contexto: `#d9dce2`.
- Repita a legenda em texto, rótulos ou padrões; nunca dependa só da cor.
- Use a cor de atenção para uma linha ou chamada, não para pintar uma categoria como “certa” ou “errada”.

## Tipografia e layout

- Use fonte sem serifa do sistema, corpo de pelo menos 16px e títulos com alto contraste.
- Mantenha uma coluna de leitura confortável e cartões simples para indicadores.
- Faça o painel funcionar em celular sem rolagem horizontal.
- Inclua título, unidade, período e fonte próximos de cada gráfico.
- SVGs e canvases precisam de `aria-label` ou de uma tabela/texto equivalente.

## Rigor e linguagem

- Diferencie pessoas, chapas, municípios e votos; nunca conte duas vezes uma unidade repetida.
- Preserve ausências como ausências e registre o filtro usado.
- Declare a data/recorte da base e não confunda eleição passada com ocupação atual.
- Use “associação”, “diferença” ou “padrão” quando não houver desenho causal.

## Checklist final

- [ ] A tese está visível antes dos gráficos.
- [ ] Todos os percentuais têm denominador e período identificados.
- [ ] O gráfico pode ser entendido sem depender apenas da cor.
- [ ] O painel informa fonte, filtros e limitações.
- [ ] O HTML abre sozinho e não faz leitura de CSV local.
- [ ] A afirmação final é sustentada pelos números apresentados.
