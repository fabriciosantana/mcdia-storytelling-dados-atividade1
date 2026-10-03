---
name: dashboard-narrativo-acessivel
description: Criar dashboards autocontidos que apresentem uma história verificável, com gráficos adequados, filtros claros e metodologia acessível.
---

# Dashboard narrativo acessível

## Antes de desenhar

1. Identifique a pergunta central, o público e a unidade de análise.
2. Leia o dicionário da fonte. Confirme cobertura, período, chaves, duplicações e ausências.
3. Calcule as principais métricas antes de escrever títulos. Separe achados verificáveis de hipóteses.
4. Defina o denominador de cada proporção. Preserve a distinção entre zero e ausência.

## Estrutura narrativa

Abra com uma resposta curta à pergunta principal, acompanhada de período, recorte, contagem e denominador. Desenvolva a história em até quatro blocos: retrato geral, comparação relevante, variação contextual e implicações. Escreva títulos que expressem achados comprovados. Termine com o que os dados permitem afirmar e quais perguntas dependem de outras fontes.

## Gráficos

- Use barras para comparar categorias, linhas para séries temporais e dispersão para relações entre variáveis quantitativas.
- Inicie barras em zero. Para proporções comparáveis, mantenha escala comum de 0 a 100%.
- Use barras empilhadas de 100% apenas para composição; ofereça uma tabela para leitura exata.
- Não use efeitos 3D, eixos duplos sem necessidade, áreas decorativas ou escalas que exagerem diferenças.
- Mostre unidade, período, denominador e rótulos junto aos gráficos. Preserve categorias pequenas na tabela e nos textos.
- Calcule com precisão completa e arredonde somente na apresentação.

## Estilo visual

Use fundo claro (`#f4f3ed`), texto escuro (`#193b38`) e texto secundário (`#526660`). Reserve um tom de destaque (`#b4482b`) para hierarquia editorial. Para séries categóricas, use uma paleta estável como `#356b73`, `#c06a44`, `#755a96`, `#ac8a24`, `#347c59` e `#94a39a`. Não atribua significado moral às cores. Acrescente rótulos escritos para que a interpretação não dependa da cor.

Use fontes de sistema para o corpo, com tamanho inicial de 16 px e entrelinha de cerca de 1,5. Títulos podem usar uma fonte serifada local. Prefira espaços em branco, linhas discretas e poucos contornos. Não reduza fontes para acomodar conteúdo.

## Interação e acessibilidade

- Rotule filtros e controles com elementos semânticos, permita navegação por teclado e mostre foco visível.
- Exiba o recorte ativo e atualize totais, títulos e explicações quando filtros mudarem.
- Identifique referências fixas que não mudam com filtros.
- Mantenha definições e limites próximos das métricas que eles qualificam.
- Em recortes vazios, informe ausência de registros e não produza percentuais artificiais.
- Ofereça contagens tabulares e exportação quando ajudarem a verificar os números.
- Em telas pequenas, empilhe os painéis e mantenha controles utilizáveis.

## Rigor e portabilidade

Documente origem, extração, cobertura, transformações, critérios de inclusão e limitações. Não infira características ausentes. Não use linguagem causal quando a análise for descritiva. Para um arquivo autocontido, incorpore CSS, JavaScript e dados agregados no HTML, sem solicitar arquivos locais. Evite dependências externas quando o uso offline for desejado.

## Verificação

Reconcilie totais com a fonte e confira uma comparação manualmente. Teste os filtros, a limpeza, o download e a impressão. Revise a renderização em desktop e celular, procurando cortes, sobreposições e falta de contraste. Registre verificações feitas e limitações que permanecerem, sem declarar testes não executados.
