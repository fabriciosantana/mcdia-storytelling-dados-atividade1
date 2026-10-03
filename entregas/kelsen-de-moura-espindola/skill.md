---
name: painel-narrativo
description: Regras de narrativa, gráficos, cores e layout para dashboards em HTML que contam uma história com dados. Use sempre que for criar um painel, relatório visual ou gráfico em HTML para um público específico.
---

# Painel narrativo

## Quando usar

Sempre que a tarefa for transformar uma base de dados em um painel HTML para um público definido, especialmente quando houver uma pergunta norteadora a responder. Não use para painéis operacionais de monitoramento contínuo.

## Antes de desenhar

- Escreva em uma frase a resposta à pergunta norteadora. Se não conseguir, ainda não é hora de fazer gráficos.
- Liste o que o público já sabe, quanto tempo terá e o que precisa decidir ou entender. Cada seção deve servir a isso.
- Confira as regras de leitura da base (duplicidades, ausentes, unidades) e calcule os agregados fora do HTML. Embuta só os números necessários, em JSON.

## Estrutura narrativa

- **Abertura:** o título é uma afirmação com a resposta, não o nome do tema. Ex.: "Seis em cada dez clientes voltaram", e não "Retenção de clientes".
- Logo abaixo, 3 ou 4 números-chave com rótulo em linguagem comum.
- **Meio:** seções numeradas, cada uma com uma pergunta implícita, um título-afirmação, uma frase de apoio e um único gráfico principal. Ordem: retrato geral → variação (onde/quem) → explicação (por quê/como) → nuances.
- Dê ao leitor um jeito de se localizar (um seletor de "seu grupo" ou "sua região") quando o público tiver uma realidade própria a comparar.
- **Fechamento:** hipóteses e perguntas para discussão, nunca causas que os dados não sustentam. Termine com uma seção "O que estes dados não permitem afirmar".
- Rodapé com a fonte, a data de referência e o recorte usado.

## Escolha de gráficos

- Comparar categorias: barras horizontais ordenadas pelo valor, com uma linha de referência para a média geral.
- Partes de um todo com até 4 grupos: uma barra única de 100% dividida em faixas. Evite pizza e rosca.
- Comparar duas distribuições: histograma espelhado (um grupo para cima, outro para baixo) no mesmo eixo.
- Comparar o perfil de dois grupos: pares de números lado a lado, com as mesmas cores dos grupos.
- Nunca use 3D, eixos que não começam no zero em barras, nem mais de um gráfico por mensagem.
- Mostre percentuais no texto e valores absolutos no tooltip.
- Com mais de 15 categorias, ordene e destaque só a selecionada. Não use 15 cores.

## Paleta de cores

- `#1f5f8b` (azul): grupo A da história principal. No escuro: `#5fa3d3`.
- `#d0742c` (laranja): grupo B, o contraste da história. No escuro: `#ec9a5a`.
- `#a9c6dc` / `#efc6a1`: versões claras para estados intermediários de A e B.
- `#1d232b` (tinta): texto e linhas de referência. `#5d6673`: texto secundário.
- `#f7f5f0` (fundo) e `#ffffff` (cartões); no escuro, `#14181d` e `#1c2229`.
- `#fbe9d7`: fundo de destaque para a frase dinâmica do seletor.
- As duas cores de grupo mantêm o mesmo significado no painel inteiro. Defina tudo como variáveis CSS e redefina em `prefers-color-scheme: dark`.

## Tipografia e layout

- Títulos em serifada (Source Serif 4) e texto em sem serifa (Source Sans 3), via Google Fonts, com fallback do sistema.
- Corpo de 17px, títulos de seção entre 23 e 31px, título principal até 48px, com largura máxima de cerca de 30 caracteres por linha.
- Coluna central de até 1040px, margem lateral de 16px e cartões com borda fina e cantos de 10 a 12px.
- Gráficos em SVG desenhados com o tamanho real do contêiner (redesenhe ao redimensionar), para que o texto não encolha no celular.
- Abaixo de 760px, todas as grades viram uma coluna.
- Um arquivo HTML único: CSS e JS embutidos, sem leitura de arquivos locais.

## Linguagem

- Frases curtas e voz ativa, sem jargão técnico do banco de dados (nada de nomes de colunas na tela).
- Números arredondados no texto ("44%", "4 em cada 10"); decimais só no tooltip.
- Use os nomes que o público usa. Explique um termo técnico na primeira vez em que aparecer.

## Checklist final

- [ ] O título responde à pergunta norteadora.
- [ ] Todo número do texto vem dos dados embutidos e confere com a fonte.
- [ ] Nenhuma contagem duplicada (confira as regras de unidade da base).
- [ ] As duas cores de grupo significam a mesma coisa em todos os gráficos.
- [ ] Há uma seção de limites da leitura e o rodapé com a fonte.
- [ ] Abre com dois cliques, sem erros no console, legível em 375px e em 1280px, em modo claro e escuro.
- [ ] Sem rolagem horizontal.
