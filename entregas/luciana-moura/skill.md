---
name: data-story-dashboard
description: Regras narrativas e visuais para dashboards em HTML que contam uma história com dados. Use sempre que for criar ou revisar um dashboard, painel, gráfico ou relatório visual em um único arquivo HTML, com qualquer base de dados.
---

# Dashboard que conta uma história

## Quando usar

Use esta skill sempre que o pedido envolver um dashboard, painel ou conjunto de gráficos em HTML para um público que não é especialista em dados. Ela vale para qualquer base e qualquer tema. O que for específico do projeto (tema, pergunta, público, cuidados com a base) vem do arquivo de contexto do projeto, não daqui.

## Antes de desenhar

- Escreva a mensagem central em uma frase. Se não couber em uma frase, a história ainda não está pronta.
- Liste de 3 a 6 perguntas que o público faria, na ordem em que faria. Cada pergunta vira uma seção.
- Calcule os números antes de escolher os gráficos. Confira a unidade de contagem (pessoa, domicílio, município, pedido) para não contar a mesma coisa duas vezes.
- Leia a documentação da base e anote o que falta, o que foi excluído e o que não pode ser afirmado.

## Estrutura narrativa

- Abra com a mensagem central como título da página, escrita como afirmação com o número principal. Evite títulos que só nomeiam o assunto.
- Organize em três atos: o que acontece, onde ou com quem acontece, e o que isso significa.
- Dê a cada seção um título que seja a conclusão do gráfico, não a descrição dele.
- Coloque uma frase curta de leitura abaixo de cada gráfico, dizendo o que observar.
- Feche com uma síntese de duas ou três frases que retome a mensagem central.
- Mostre uma ideia por gráfico. Se um gráfico precisa de duas explicações, divida em dois.
- Não afirme causa quando os dados só mostram diferença ou associação.

## Escolha de gráficos

- Um número sozinho: use um destaque numérico grande com uma frase de contexto, não um gráfico.
- Proporção simples (parte de um todo com 2 ou 3 partes): use um quadro de 100 unidades ou uma barra única empilhada. Evite pizza com mais de 3 fatias.
- Comparação entre categorias: use barras horizontais, ordenadas do maior para o menor.
- Categorias com ordem natural (faixas de idade, de tamanho, de renda): mantenha a ordem natural, não a de valor.
- Evolução no tempo: use linha, com o tempo no eixo horizontal.
- Relação entre duas medidas: use dispersão.
- Sempre comece o eixo das barras no zero.
- Use a mesma escala em gráficos que o leitor vai comparar entre si.
- Nunca use dois eixos verticais no mesmo gráfico, efeitos 3D ou gráficos decorativos.
- Mostre uma linha de referência (média, meta) quando ela ajudar a julgar se um valor é alto ou baixo.
- Quando um grupo tiver poucos casos, avise que o percentual dele é instável.

## Paleta de cores

- Dê a cada cor um papel e mantenha esse papel no dashboard inteiro. A mesma categoria tem a mesma cor em todos os gráficos.
- Use no máximo duas cores de dados quando a história compara dois grupos:
  - Destaque (o grupo em foco): `#eb6834` no tema claro, `#d95926` no escuro.
  - Comparação (o outro grupo): `#2a78d6` no tema claro, `#3987e5` no escuro.
- Para mais categorias, siga esta ordem fixa e não invente cores novas: `#2a78d6`, `#eb6834`, `#1baf7a`, `#eda100`. Acima de quatro, agrupe o restante em "Outros".
- Neutros:
  - Fundo da página: `#f9f9f7` (escuro `#0d0d0d`).
  - Fundo dos cartões: `#fcfcfb` (escuro `#1a1a19`).
  - Texto principal: `#0b0b0b` (escuro `#ffffff`).
  - Texto secundário: `#52514e` (escuro `#c3c2b7`).
  - Eixos e rótulos discretos: `#898781`.
  - Linhas de grade: `#e1e0d9` (escuro `#2c2c2a`).
- Reserve vermelho e verde para alerta e sucesso; não os use como cor de categoria.
- Escreva números e rótulos na cor do texto, nunca na cor da série.
- Nunca dependa só da cor: toda série tem legenda ou rótulo, e todo valor importante aparece escrito.
- Evite cores que reforcem estereótipos sobre os grupos comparados.
- Teste o par de cores para daltonismo antes de entregar.

## Tipografia e layout

- Use a fonte do sistema: `system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`.
- Tamanhos: título da página de 28 a 40 px, título de seção de 20 a 24 px, texto de 16 px, notas de 13 px. Não use texto menor que 12 px.
- Limite a largura do conteúdo a cerca de 960 px e as linhas de texto a cerca de 70 caracteres.
- Coloque cada gráfico em um cartão com título, gráfico, frase de leitura e nota, nessa ordem.
- Faça o layout em uma coluna no celular e em até duas colunas em telas largas. Nada pode exigir rolagem horizontal.
- Escreva números no formato do idioma do público (em português: vírgula decimal e ponto de milhar) e arredonde percentuais para uma casa decimal.
- Deixe grades e eixos discretos; o que deve chamar atenção são os dados.
- Mostre o valor ao lado da barra quando houver poucas barras; com muitas, mostre também o detalhe ao passar o mouse.
- Ofereça uma tabela com os números para quem prefere ler ou usa leitor de tela.

## Requisitos técnicos

- Entregue um único arquivo HTML, com CSS e JavaScript embutidos.
- Embuta os dados já agregados no próprio arquivo. O HTML não lê arquivos locais.
- Se usar biblioteca externa, carregue por CDN e confira que a página não quebra sem ela.
- Declare `lang` e `meta viewport`, e dê texto alternativo ou `aria-label` a cada gráfico.
- Suporte tema claro e escuro com variáveis CSS.

## Rodapé obrigatório

- Fonte dos dados, com o nome da base e a data de referência.
- O recorte usado (o que entrou e o que ficou de fora).
- As ressalvas de leitura que mudam a interpretação.

## Checklist final

- [ ] O título da página é a mensagem central, com o número principal.
- [ ] Cada seção tem um título que é uma conclusão.
- [ ] Todas as barras começam no zero e gráficos comparáveis usam a mesma escala.
- [ ] Cada cor tem o mesmo significado em todo o dashboard, e há legenda.
- [ ] Os números do texto batem com os dos gráficos e com a base.
- [ ] Os totais e a unidade de contagem estão explícitos.
- [ ] Fonte, recorte e ressalvas estão no rodapé.
- [ ] O arquivo abre com dois cliques, sem erros no console e sem depender de arquivos locais.
- [ ] A página funciona em tela de celular e em tela larga, sem rolagem horizontal.
- [ ] Nenhuma frase afirma causa que os dados não sustentam.
