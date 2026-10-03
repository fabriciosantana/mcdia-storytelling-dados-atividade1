---
name: storytelling-data-dashboard
description: Constrói dashboards HTML de storytelling de dados, com narrativa guiada pelo público, gráficos honestos, validação dos números e documentação. Use sempre que for criar um painel, relatório visual ou conjunto de gráficos a partir de uma base de dados para uma audiência específica.
---

# Dashboard de storytelling de dados

Um dashboard conta uma história para uma pessoa específica. Cada elemento precisa ajudar essa pessoa a entender a pergunta. O que não ajuda, sai.

## 1. Compreensão do público
- Antes de qualquer análise, escreva: quem vai ler, quanto tempo tem, o que já sabe, o que precisa entender ou decidir e em que contexto verá a peça (reunião, tela, impressão).
- Pouco tempo = resposta principal na primeira tela, sem depender de clique ou tooltip.
- Defina se a peça informa ou persuade. Se for informar, não conduza a conclusão.

## 2. Definição da pergunta
- Reduza o briefing a uma pergunta norteadora e a 3 ou 4 perguntas derivadas, em ordem de progressão (geral → específico).
- Cada gráfico responde a exatamente uma pergunta. Se não souber qual, não o crie.

## 3. Descoberta da narrativa
- Não comece com uma tese. Calcule, observe os padrões, escolha os relevantes e só então escreva a história.
- Hipótese não sustentada pelos dados não vira narrativa. Resultado "sem diferença" é válido: descarte ou cite em uma frase.
- Não use números fornecidos de antemão como resultado: recalcule da fonte.

## 4. Análise exploratória
- Leia primeiro a documentação da base: unidade de observação, filtros, codificação, valores ausentes, limitações.
- Confira nomes de colunas e categorias reais; não presuma.
- Defina o universo (filtro) e a unidade de análise antes de contar. Verifique duplicidades e chaves.
- Explore muitas variáveis; publique só as que acrescentam à pergunta.
- Faça a análise em script reprodutível. Guarde os agregados que irão para o dashboard.

## 5. Hierarquia narrativa
- Estrutura padrão: (1) panorama com a resposta principal; (2) comparação ou corte principal; (3) detalhe onde a atenção deve ir; (4) dimensão complementar, só se acrescentar; (5) síntese com 2 ou 3 mensagens factuais; (6) fonte e método.
- Uma leitura vertical contínua é preferível a várias abas. A história deve funcionar sem interação.
- Evite repetir em texto o que o gráfico já mostra.

## 6. Escolha de gráficos
- Comparar categorias: barras (horizontais para rótulos longos ou muitas categorias), ordenadas por valor.
- Composição: barra 100% ou número destacado; pizza só com 2 ou 3 fatias.
- Evolução no tempo: linhas; distribuição: histograma ou boxplot; relação entre variáveis: dispersão.
- Mapa só se a localização exata for a resposta. Caso contrário, barras ordenadas comparam melhor.
- Proibidos: 3D, velocímetro, eixos duplos enganosos, efeitos decorativos.

## 7. Títulos orientados por mensagem
- O título diz o achado ("A taxa varia de X a Y entre as regiões"), não o nome da variável.
- Escreva títulos só depois de ver os resultados; números do título vêm do cálculo, nunca digitados à mão.
- Tom factual: "os dados mostram", "observa-se". Evite "prova que", "o problema é", "porque".

## 8. Honestidade visual
- Não sugira causa onde só há descrição. Hipóteses entram como pergunta para investigação, rotuladas.
- Não ranqueie de modo normativo (melhor/pior) quando a medida é descritiva.
- Mostre o tamanho da amostra quando grupos são pequenos e sinalize os instáveis.

## 9. Escalas
- Barras sempre partem do zero. Mesmo eixo máximo em gráficos que serão comparados entre si.
- Sem truncar eixo, sem escala logarítmica sem aviso. Linhas de referência (média, meta) ajudam a leitura.

## 10. Comparação
- Compare grupos com a mesma medida e o mesmo denominador. Use uma linha de referência comum.
- Cuidado com a ordem: ordene por valor, não alfabeticamente, quando o objetivo é comparar.

## 11. Denominadores
- Taxas e percentuais: deixe o denominador explícito ("x de y"). Número absoluto e percentual não são a mesma medida; não confunda tamanho do grupo com presença relativa.
- Calcule com precisão total e arredonde só na exibição. Garanta que partes somem o total.
- Deixe claro a unidade (pessoas, registros, eventos, locais).

## 12. Dados ausentes
- Vazio não é zero, "Não" nem ausência de característica. Siga a documentação.
- Não impute sem justificativa. Se excluir ausentes, declare quantos e por quê.
- Se os ausentes forem relevantes, mostre-os ou cite-os.

## 13. Acessibilidade
- Contraste mínimo 4,5:1 para texto e 3:1 para elementos gráficos. Verifique.
- Não dependa só da cor: use rótulos, valores, posição, hachura ou ícone.
- Tooltip é complemento, nunca o único lugar de uma informação essencial. Elementos interativos acessíveis por teclado e com foco visível.
- Use `lang`, `aria-label` e texto alternativo nos gráficos.

## 14. Tipografia
- Sans-serif legível, corpo de 16 a 18 px, títulos grandes, números de destaque em tamanho e peso maiores.
- Poucos pesos e tamanhos. Evite caixa alta em excesso, parágrafos longos e texto pequeno.

## 15. Cor
- Use a paleta dada de forma coerente: uma cor principal de dado, uma secundária, neutros para apoio, uma escura para texto.
- Não use convenções estereotipadas (por exemplo rosa/azul por categoria demográfica). Distinga por posição, rótulo e intensidade.
- Cor tem função (destaque, referência, apoio), não decoração. Mantenha o mesmo significado em todo o painel.

## 16. Interação
- Só o que melhora a compreensão: tooltip, destaque, filtro simples. Nenhum filtro para demonstrar tecnologia.
- A narrativa principal funciona sem clicar. Interações devem ser reversíveis (opção "Todas").

## 17. Responsividade
- Leitura vertical em uma coluna, sem rolagem horizontal, sem texto cortado ou sobreposto. Teste em 360 a 400, ~800 e 1280 px ou mais.
- Prefira HTML/CSS e SVG fluido a gráficos de tamanho fixo. Em telas pequenas, simplifique rótulos secundários em vez de reduzir a fonte.

## 18. Validação dos dados
- Faça uma auditoria independente do script de análise (outro código ou biblioteca) e compare com o que está embutido no HTML.
- Confira: totais, soma das partes, percentuais, ausência de duplicidades, filtro correto, nenhum número digitado à mão, todos rastreáveis a uma agregação.
- Faça um teste de sensibilidade quando o universo tiver casos duvidosos.

## 19. Validação do HTML
- Arquivo único e autocontido; dados agregados embutidos; sem ler arquivos locais. Evite dependências externas quando possível.
- Teste em navegador headless: sem erros de console, todos os gráficos renderizados, tooltips e interações funcionando, sem rolagem horizontal, sem requisições a arquivos locais.
- Confira capturas de tela em larguras diferentes.

## 20. Documentação
- Registre a narrativa, o público, as perguntas, o recorte, as decisões de design e de visualização, e o que foi descartado e por quê.
- Registre os prompts usados em ordem, com o que funcionou e o que mudou. Não invente etapas.
- O documento deve descrever o que foi realmente feito.

## 21. Limitações
- Inclua no próprio painel uma seção discreta de fonte e método: base, período, universo, unidade, filtros, temporalidade, limitações.
- Declare o que a base não permite afirmar (causas, situação atual, grupos não cobertos).

## 22. Revisão final
- [ ] A primeira tela responde à pergunta para quem tem poucos minutos?
- [ ] A narrativa avança do geral para o específico?
- [ ] Cada gráfico responde uma pergunta? Algum pode sair sem perda?
- [ ] Algum texto só repete o gráfico? Reduza.
- [ ] Os títulos dizem o achado e foram escritos depois dos resultados?
- [ ] Denominadores explícitos; unidades claras; formato numérico local.
- [ ] Sem causalidade não demonstrada, recomendação ou julgamento, se a peça for informativa.
- [ ] Contraste, teclado, responsividade e console verificados.
- [ ] Números auditados de forma independente.
- [ ] Fonte, método, temporalidade e limitações visíveis.
