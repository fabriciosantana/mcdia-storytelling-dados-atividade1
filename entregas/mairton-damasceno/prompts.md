# Diário de prompts

**Link compartilhado da conversa (opcional):** —

---

## Prompt 1

```
clone o respositório: https://github.com/prof-danny-idp/storytelling-dados-atividade1
```

**O que funcionou / o que mudei:** O clone funcionou de primeira. O Claude listou a estrutura e se ofereceu para resumir o README; eu pulei o resumo e fui direto para o pedido do dashboard, pois já conhecia a atividade.

---

## Prompt 2

```
/dataviz
```

**O que funcionou / o que mudei:** Carreguei a skill `dataviz` do Claude Code antes de qualquer gráfico. Ela traz um procedimento (forma → cor → validação → marcas → interação → acessibilidade → olhar o resultado) e um verificador de paleta executável. Isso mudou o fluxo: em vez de escolher cores primeiro, o Claude leu o README e o dicionário de dados primeiro.

---

## Prompt 3

```
utilize uma skill futurista para criar um html que reresente "A cor do poder municipal"
```

**O que funcionou / o que mudei:** O Claude leu "A cor do poder" nos dois sentidos (partidos e raça/cor), explorou a base em pandas e descobriu que a história racial era muito mais forte: 65,8% de prefeitos brancos, 2,3% de pretos, 1 prefeitura preta entre as 100 maiores cidades. Ele propôs uma paleta "neon" e **rodou o verificador**: as cores brilhantes falharam na banda de luminosidade e precisaram ser escurecidas; um par verde↔rosa falhou no teste para daltonismo e foi trocado. O que eu mudei: ainda faltavam a pergunta norteadora e o briefing, que mandei nos prompts seguintes.

---

## Prompt 4

```
Use como pergunta norteadora: Que retrato emerge das pessoas eleitas para governar os municípios brasileiros em 2024?
```

**O que funcionou / o que mudei:** A pergunta é mais ampla que "cor". O Claude manteve a cor como fio condutor mas abriu o dashboard com um "retrato-robô" (gênero, idade, escolaridade, estado civil, bens, continuidade) para responder à pergunta na sua amplitude antes de aprofundar. Achei a solução boa: responde a pergunta e preserva a história.

---

## Prompt 5

```
Briefing: Um observatório da sociedade civil que acompanha a representação política vai lançar um relatório anual e encomendou um dashboard que abra a publicação. O público é amplo: Pesquisadores, jornalistas, gestores públicos e cidadão interessados. O dashboard será compartilhado online e precisa ser compreendido sem que alguém esteja ao lado para explica-lo. Sua história deve apresentar o retrato racial de quem governa os municípios e tratar o tema com rigor, respeitando o que a base permite e o que não permite afirmar.
```

**O que funcionou / o que mudei:** O briefing confirmou o foco racial e acrescentou a exigência de rigor. O Claude inseriu um bloco "O que esta base permite dizer / o que ela não permite" logo após o herói, ajustou textos para não confundir "candidato à reeleição" com "reeleito", e reescreveu uma frase do Ato 3 que afirmava algo impreciso sobre "os estados do Norte" (RO e RR ficam abaixo da linha) — a versão final lista os oito estados corretos. Depois renderizou a página no Chrome em 1280px e em 390px, encontrou rótulos colidindo nos dumbbells (valores pequenos sobre o nome da categoria) e eixos sobrepostos no celular, e corrigiu os dois antes de entregar.

---

## Prompt 6

```
Use essa paleta de cores: https://www.color-hex.com/color-palette/1294. Traga um layout futurista. Insira a possibildiade de filtros e seleção nos gráficos. Verifique se com as informaçoes da base não tem como inserir mapa.
```

**O que funcionou / o que mudei:** O Claude não conseguiu ler o site pelo fetch (bloqueio do Cloudflare) e abriu a página no meu Chrome para ler a paleta: “Beautiful Blues”, cinco azuis. Como é monocromática, ele reorganizou as funções de cor (medida, contexto, rampa, identidade por luminosidade) e revalidou com o verificador — a rampa passa; o teste categórico acusa falta de matiz, o que foi documentado como limitação assumida. Para os filtros, em vez de embutir o CSV, ele gerou um cubo de contagens (3.398 células) e um cubo de chapas, e reescreveu os gráficos para recalcular a partir dele, com seleção cruzada ao clicar em barras, tiles e no mapa. Sobre o mapa: confirmou que a base tem código IBGE e UF mas nenhuma geometria, baixou a malha oficial das UFs do IBGE, simplificou para 60 KB e embutiu no HTML, documentando a origem no rodapé. Testou os filtros (Nordeste + 5 a 20 mil + vices) e corrigiu um tile que mostrava “0” quando o recorte ficava acima da paridade.

---

## Prompt 7

```
inclua um botão para deixar claro ou escuro
```

**O que funcionou / o que mudei:** O Claude converteu todas as cores fixas do HTML em tokens CSS, criou um tema claro com os mesmos cinco azuis (papéis invertidos) e um botão ☾/☀ no cabeçalho que salva a escolha e respeita a preferência do sistema. Revalidou a rampa clara: a primeira tentativa (`#b3cde0` como passo mais claro sobre branco) falhou no piso de contraste 2:1 e foi substituída por `#8cb2c9`; a identidade do waffle no claro também teve de mudar porque `#8cb2c9` e `#6497b1` ficaram perto demais (ΔE 9,5) — ficou `#b3cde0 / #3279a4 / #011f4b` (ΔE 27). Conferiu os dois temas tela a tela no Chrome.
