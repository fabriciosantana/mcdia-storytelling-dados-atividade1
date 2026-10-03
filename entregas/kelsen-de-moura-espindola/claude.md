## Qual história meu dashboard conta?

Em 2024, quatro em cada dez prefeitos brasileiros foram reconduzidos e seis em cada dez prefeituras passaram a ser comandadas por quem não disputava a reeleição. O equilíbrio, porém, muda muito de um estado para outro (de 31% de recondução em Santa Catarina a 67% em Roraima). Quem fica costuma vencer com folga, inclusive em disputas sem adversário. E a renovação de nomes não trouxe renovação de perfil: novos e reconduzidos têm a mesma proporção de mulheres e de pessoas com curso superior.

## Contexto do projeto

- **Tema 4: Continuidade e renovação.** Pergunta norteadora: _o que as eleições de 2024 revelam sobre continuidade e renovação no comando das prefeituras?_
- **Base:** `dados/eleitos.csv` (11.106 pessoas, 5.553 municípios), lida com `;` como separador, vírgula decimal e códigos como texto.
- **Cuidados do dicionário aplicados:**
  - Todas as contagens usam só `cargo = Prefeito`, uma linha por município. O vice entra apenas para classificar a chapa.
  - "Reconduzido" = prefeito com `candidato_a_reeleicao_tse = Sim`. Como a base só tem eleitos, isso equivale a quem tentou e conseguiu a reeleição.
  - Votos e percentuais vêm de `percentual_validos_chapa_atual_tse`, também só na linha do prefeito.
  - Mantive os 5.553 municípios. As 23 chapas cassadas ou com confirmação apenas histórica estão sinalizadas nos limites do painel.
  - O porte do município foi aproximado por `votos_validos_municipio_turno_atual_tse`, porque a base não tem população.
- Os agregados foram calculados em Python (`pandas`) e embutidos como JSON no HTML. O dashboard não lê o CSV.

## Público-alvo

A turma da aula inaugural de uma escola de governo: gestores, servidores e assessores de várias regiões. Conhecem bem a própria realidade e pouco a dos outros municípios. Assistem numa projeção ou abrem no notebook durante a aula, têm alguns minutos e precisam sair com uma leitura do contexto político em que vão atuar e com perguntas para discutir no curso.

## Perguntas que os dados respondem

1. Quantas prefeituras ficaram com quem já governava e quantas mudaram de mãos? E a chapa inteira, foi mantida?
2. Esse equilíbrio é igual no país inteiro? Como o meu estado se compara?
3. Com que força quem ficou e quem chegou venceram as eleições?
4. O porte do município e o partido mudam o padrão?
5. Quem são as pessoas que chegam ao poder? A renovação muda o perfil de quem governa?
6. O que pode estar por trás desse equilíbrio, e o que a base não permite afirmar?

## Decisões de design

- **Título como afirmação.** O título já é a resposta ("Quatro em cada dez... Seis em cada dez..."), porque o público tem pouco tempo.
- **Duas cores fixas para toda a história:** azul para continuidade e laranja para renovação. As versões claras dessas cores indicam continuidade parcial (só o prefeito ou só o vice). Assim a pessoa aprende a legenda uma vez só.
- **Barra de 100% em quatro faixas** em vez de pizza, para mostrar que a continuidade tem graus.
- **Seletor "Seu estado"**, porque o público conhece a própria realidade e precisa se localizar em relação aos outros. A frase muda com o estado e diz quantos pontos ele está acima ou abaixo do Brasil. Os estados ficam ordenados do mais ao menos contínuo, com uma linha de referência nacional.
- **Histograma espelhado** (reconduzidos para cima, novos para baixo) para comparar a força eleitoral dos dois grupos no mesmo eixo, com marcação dos 50% e uma coluna separada para candidato único.
- **Ocupações dos novos prefeitos** com as ocupações políticas destacadas em azul, para mostrar que parte da "renovação" já tinha trajetória política.
- **Seção de hipóteses para debate**, em vez de conclusões causais: a base mostra resultados, não causas.
- **Limites explícitos ao final:** não existe taxa de sucesso de quem tentou a reeleição, "reeleição" é uma declaração, e assim por diante.
- **Ficou de fora:** um mapa municipal (pesado para um arquivo único e pouco legível em 5.553 polígonos), bens declarados (não dialoga com a pergunta) e raça/cor (é outro tema).
- Segue a skill `skill.md` (painel-narrativo).

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos.
- Seguir a skill descrita em `skill.md`.
- Toda contagem de pessoas ou municípios usa só `cargo = Prefeito`. Nunca somar votos das duas linhas da chapa.
- Não afirmar causas nem "taxa de reeleição" (a base não tem os derrotados). Usar "reconduzidos" e "novos".
- Escrever em português do Brasil, com frases curtas e números arredondados no texto (decimais só no tooltip).
- Todo número citado no texto deve vir do JSON embutido, não digitado à mão.
