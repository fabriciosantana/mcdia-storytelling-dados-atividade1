## Qual história meu dashboard conta?

Em 2024, as mulheres foram eleitas para comandar 734 dos 5.553 municípios analisados — 13,2% das prefeituras. O mapa não é homogêneo: o Nordeste tem a maior presença feminina entre as regiões, mas nenhuma região se aproxima de uma divisão equilibrada. Para uma comissão do Legislativo, a mensagem é direta: a sub-representação é nacional, com diferenças territoriais que merecem investigação específica.

## Tema escolhido

**Mulheres e homens no comando das prefeituras** — pergunta norteadora: “Como mulheres e homens estão presentes no comando dos municípios brasileiros eleitos em 2024?”

## Público-alvo

Uma comissão do Legislativo em audiência pública, com pouco tempo e opiniões formadas. O painel precisa entregar uma leitura clara em poucos segundos, mostrar o tamanho do desequilíbrio sem dramatização e indicar onde a comissão pode olhar com mais atenção.

## Perguntas que os dados respondem

1. Qual é a proporção nacional de prefeitas e prefeitos eleitos?
2. Essa presença muda entre as cinco regiões brasileiras?
3. Quais UFs estão acima ou abaixo da média nacional?
4. O padrão se altera quando observamos reeleição declarada?

## Principais decisões de design

- Abrir com a conclusão e três números grandes: total de municípios, prefeitas e a distância até uma divisão de 50%.
- Usar barras 100% empilhadas para tornar a assimetria nacional e regional comparável, sem depender de uma legenda distante.
- Ordenar as UFs pela proporção de prefeitas e destacar a linha da média nacional; mostrar também o número de municípios para evitar que percentuais de estados pequenos pareçam conclusivos.
- Incluir reeleição como contexto, não como causalidade: a variável é a declaração eleitoral do TSE e não uma auditoria do exercício do mandato anterior.
- Usar roxo para mulheres, azul-petróleo para homens e amarelo apenas para o marcador de referência. As cores vêm acompanhadas de rótulos e percentuais.

## Cuidados de leitura

Foram filtradas somente as linhas com `cargo = Prefeito`, porque cada município aparece duas vezes na base, uma para prefeito e outra para vice. Municípios foram contados por `codigo_municipio_tse`. “Feminino” e “Masculino” são categorias do campo `genero_tse` cadastrado pelo TSE; não são uma inferência sobre identidade. A base retrata eleitos de 2024 e não confirma quem exerce o cargo atualmente. Ausências não foram convertidas em “Não”.

## Instruções para o Claude

- Gerar um único `dashboard.html`, autocontido, sem ler arquivos locais.
- Embutir apenas agregações necessárias e informar denominadores, período e fonte.
- Escrever títulos que tragam conclusões, não nomes genéricos de gráficos.
- Evitar afirmar causalidade, representatividade social total ou situação atual do mandato.
- Seguir as regras de `skill.md` e revisar o resultado contra o checklist da atividade.
