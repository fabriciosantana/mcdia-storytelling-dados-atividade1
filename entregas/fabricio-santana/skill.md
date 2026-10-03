---
name: narrativa-visual-de-dados
description: Orienta a criação de dashboards HTML claros, acessíveis e baseados em evidências para transformar qualquer base tabular em uma narrativa visual verificável. Use ao criar ou revisar um painel de dados.
---

# Narrativa visual de dados

## Quando usar

Use esta skill para dashboards, relatórios exploratórios e páginas de storytelling que precisem levar uma pessoa da pergunta à conclusão sem exigir conhecimento prévio da base.

## Estrutura narrativa

- Comece com uma frase-tese e um número principal; não faça o público descobrir a conclusão sozinho.
- Mostre o denominador logo no início: registros, pessoas, unidades, eventos ou outro universo relevante.
- Organize a sequência em quatro movimentos: contexto, evidência principal, contraste ou exceção e implicação.
- Termine com uma síntese e uma pergunta de acompanhamento; não transforme correlação em causa.
- Prefira linguagem direta, frases curtas e verbos ativos. Explique qualquer termo técnico na primeira ocorrência.

## Escolha de gráficos

- Use barras 100% empilhadas para comparar composição entre grupos com tamanhos diferentes.
- Use linhas para evolução temporal e barras horizontais ordenadas para rankings de categorias.
- Use barras agrupadas quando a comparação entre poucas categorias for o foco.
- Mostre percentual junto do total absoluto quando grupos tiverem denominadores diferentes.
- Use uma linha de referência para a média geral e identifique-a por texto.
- Evite mapas quando a pergunta é apenas ranking e evite pizza, 3D, efeitos decorativos e eixos truncados.
- Nunca faça uma soma parecer comparação de volume sem explicar unidade, período e cobertura.

## Paleta de cores

- Defina uma cor principal para a série ou categoria de referência, uma cor de destaque para exceções e tons neutros para contexto.
- Use contraste suficiente entre fundo, texto, linhas e marcas; teste a leitura em telas pequenas.
- Repita a legenda em texto, rótulos ou padrões; nunca dependa só da cor.
- Use a cor de atenção para uma linha ou chamada, não para pintar uma categoria como “certa” ou “errada”.

## Tipografia e layout

- Use fonte sem serifa do sistema, corpo de pelo menos 16px e títulos com alto contraste.
- Mantenha uma coluna de leitura confortável e cartões simples para indicadores.
- Faça o painel funcionar em celular sem rolagem horizontal.
- Inclua título, unidade, período e fonte próximos de cada gráfico.
- SVGs e canvases precisam de `aria-label` ou de uma tabela/texto equivalente.

## Rigor e linguagem

- Identifique a unidade de análise e evite contar duas vezes uma unidade repetida.
- Preserve ausências como ausências; nunca as converta automaticamente em zero, “Não” ou outra categoria.
- Registre filtros, transformações, período e limitações da base.
- Diferencie descrição, associação e causalidade; não faça afirmações causais sem desenho adequado.
- Se uma variável for declarada, publicada ou estimada, explique sua natureza e não atribua a ela um significado que a fonte não sustenta.

## Checklist final

- [ ] A tese está visível antes dos gráficos.
- [ ] Todos os percentuais têm denominador e período identificados.
- [ ] O gráfico pode ser entendido sem depender apenas da cor.
- [ ] O painel informa fonte, filtros e limitações.
- [ ] O HTML abre sozinho e não faz leitura de CSV local.
- [ ] A afirmação final é sustentada pelos números apresentados.
