## Qual história meu dashboard conta?

De cada 100 prefeituras brasileiras eleitas em 2024, só 13 são comandadas por uma mulher. Elas aparecem mais como vice do que como titular, estão mais presentes no Nordeste e no Norte do que no Sul e no Sudeste e quase somem nas maiores cidades. O perfil não explica a diferença: prefeitas e prefeitos têm a mesma idade, e elas têm mais escolaridade. Quem vê o dashboard deve sair entendendo o tamanho da desigualdade e onde ela é maior.

## Contexto do projeto

- **Tema recebido:** Mulheres e homens no comando das prefeituras.
- **Pergunta norteadora:** Como mulheres e homens estão presentes no comando dos municípios brasileiros eleitos em 2024?
- **Base de dados:** `dados/eleitos.csv`, com prefeitos e vice-prefeitos eleitos nas eleições municipais ordinárias de 2024 (11.106 pessoas, 5.553 municípios, 26 UFs).
- **Cuidados de leitura do dicionário que foram seguidos:**
  - O CSV usa `;` como separador, vírgula decimal e UTF-8 com BOM; os códigos foram lidos como texto.
  - Cada município tem duas linhas (prefeito e vice). Para falar de prefeituras, filtrei `cargo = Prefeito`; para falar de chapas, juntei as duas linhas pelo `id_chapa`.
  - O gênero é o declarado ao TSE (`genero_tse`), que só traz FEMININO e MASCULINO. Nada foi inferido por nome.
  - A base retrata o resultado de 2024, não quem está no cargo em 2026. Ficaram de fora 16 municípios sem confirmação suficiente, e o Distrito Federal não tem eleição municipal.
  - A base não traz população. Para o porte do município usei os votos válidos do turno decisivo (`votos_validos_municipio_turno_atual_tse`); 9 municípios estão sem esse dado e ficaram fora desse gráfico.
  - A reeleição é a declaração eleitoral do TSE, sem auditoria do mandato anterior.

## Público-alvo

Gestores públicos, colegas do mestrado em Administração Pública e pessoas interessadas em participação política, sem formação em estatística. Conhecem o que é uma eleição municipal, mas não os números. Têm de 2 a 3 minutos e precisam compreender três coisas: o tamanho da diferença entre mulheres e homens, onde ela é maior e que ela não se explica pelo perfil de quem foi eleito.

## Perguntas que os dados respondem

1. Quantas prefeituras são comandadas por mulheres e quantas por homens?
2. Como as chapas (prefeito + vice) são compostas: quantas não têm nenhuma mulher?
3. As mulheres aparecem mais como prefeitas ou como vice-prefeitas?
4. Em quais regiões e estados há mais prefeitas, e em quais há menos?
5. O tamanho do município muda a presença de mulheres?
6. Prefeitas e prefeitos têm perfis diferentes de idade, escolaridade e reeleição?

## Decisões de design

- **Título com a mensagem, não com o assunto.** O dashboard abre com "De cada 100 prefeituras, 13 são comandadas por uma mulher" e um quadro de 100 quadradinhos, porque uma proporção de 100 é mais fácil de sentir do que "13,2%".
- **Três atos.** (1) O tamanho da diferença; (2) onde elas estão; (3) quem são. Cada seção tem como título a conclusão do gráfico.
- **Duas cores com papel fixo em todo o dashboard:** laranja para mulheres e azul para homens. O par foi testado para leitura por pessoas com daltonismo, e evitei o estereótipo rosa/azul.
- **Barras horizontais ordenadas** para regiões, estados e composição das chapas, porque os nomes são longos e a comparação é de tamanho. As barras de porte seguem a ordem natural (do menor para o maior município), não a de valor.
- **Mesma escala (0 a 30%) nos gráficos de região, estado e porte,** sempre começando no zero, para que as barras possam ser comparadas entre si sem distorção. Uma linha marca a média nacional (13,2%).
- **Valores escritos ao lado das barras** e tabela com os números por estado, para ninguém depender só da cor.
- **Ressalvas à vista:** estados com poucos municípios (RR, AP, AC) têm percentuais instáveis, e isso está escrito junto ao gráfico.
- **O que ficou de fora:** partidos, raça/cor, bens declarados e ocupação. São temas relevantes, mas abririam outras histórias e tirariam o foco da pergunta norteadora.
- **Skill seguida:** `skill.md` desta pasta (`data-story-dashboard`).

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos.
- Seguir a skill descrita em `skill.md`.
- Não ler o `eleitos.csv` a partir do HTML; calcular os agregados antes e embutir só os números finais.
- Contar prefeituras sempre com `cargo = Prefeito` e chapas por `id_chapa`, para não duplicar municípios.
- Escrever todos os textos em português do Brasil, com números no formato brasileiro (vírgula decimal, ponto de milhar).
- Informar a fonte e as ressalvas no rodapé do dashboard.
- Não afirmar causas: os dados mostram onde a diferença está, não por que ela existe.
