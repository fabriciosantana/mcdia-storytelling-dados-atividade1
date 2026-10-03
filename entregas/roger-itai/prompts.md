# Diário de prompts

**Link compartilhado da conversa (opcional):** não há

---

## Prompt 1

```
Use a skill @.claude/skills/montar-relatorio para montar um dashboard com dados da planilha eleitos.csv que tem um dicionario de dados em dicionario.md . Um portal de transparencia quer um painel de dados que apresente o perfil de quem foi escolhido para comandar as prefeituras. Preciso responder as perguntas : Quem governa os municípios?

Quem são, afinal, as pessoas que governam os municípios brasileiros a partir de 2025?

Para quem: o cidadão comum num portal de transparência, que decide em poucos segundos se continua explorando. Linguagem acessível sem perder precisão. 

Cuidados que evitam erros comuns

* Cada município aparece duas vezes (prefeito e vice). Para falar de prefeitos, filtre `cargo = Prefeito`. Para contar municípios, use `codigo_municipio_tse`.
* Os votos se repetem nas duas linhas da chapa. Some votos apenas com `cargo = Prefeito`, ou você vai contar tudo em dobro.
* Célula vazia não é zero nem "Não". Significa dado indisponível ou não aplicável.
* O CSV usa ponto e vírgula como separador e vírgula como decimal. Importe códigos como texto para não perder zeros à esquerda.
* A base retrata a eleição de 2024, não quem está no cargo hoje. A coluna `classificacao_validacao` explica os critérios de inclusão.

 Use mapas quando for necessário. O relatório deve ser gerado num arquivo único dashboard.html, procure um ângulo que torne o trabalho memorável. O projeto deve ser chamado de transparencia.
```

**O que funcionou / o que mudei:** O prompt bastou para entregar o painel sem nenhuma rodada de perguntas. Funcionou porque trazia o público (cidadão, poucos segundos), as perguntas e os "cuidados": eles viraram o modelo de dados (uma linha por município, com o vice ao lado, e as métricas já filtradas). O pedido de um ângulo memorável levou à comparação com a população do Censo 2022 (o "espelho"). O que o prompt não definiu eu decidi e declarei: a referência da comparação (população com 21 anos ou mais, sem o DF), a visibilidade pública, a página montada à mão em vez de spec e o local do arquivo (`published/transparencia/dashboard.html`). Os ajustes depois foram de execução, não de prompt: ordem das barras horizontais, tabelas que estouravam a largura e a paleta azul/cinza. Para uma próxima vez, valeria dizer no prompt com que referência comparar e onde salvar o HTML.

---

## Prompt 2

````
Salve um arquivo com o prompt chamado prompts.md. Siga o modelo 

<!--
  MODELO — prompts.md
  Registre os prompts em ORDEM CRONOLÓGICA, do primeiro ao último.
  Abaixo de cada um, escreva uma linha "O que funcionou / o que mudei".
  Copie o bloco de um prompt quantas vezes precisar e apague estes comentários.
-->

# Diário de prompts

**Link compartilhado da conversa (opcional):** [cole aqui o link, se houver]

---

## Prompt 1

```
[Cole aqui o texto exato do prompt]
```

**O que funcionou / o que mudei:** [O resultado atendeu? O que você ajustou no prompt seguinte, e por quê?]

---

## Prompt 2

```
[Cole aqui o texto exato do prompt]
```

**O que funcionou / o que mudei:** [...]

---

## Prompt 3

```
[Cole aqui o texto exato do prompt]
```

**O que funcionou / o que mudei:** [...]
````

**O que funcionou / o que mudei:** Gerou este diário. Com o modelo colado no próprio prompt, bastou preencher os blocos na ordem e apagar os comentários. Não houve mudança no painel.
