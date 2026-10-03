# Diário de prompts

**Link compartilhado da conversa (opcional):** não há — o trabalho foi feito no Claude Code, no terminal, dentro do repositório clonado.

---

## Prompt 1

```
Vamos desenvolver um trabalho que é: Usar o Claude para analisar uma base de dados real e construir um dashboard em  HTML que conte uma história com esses dados. O tema e a pergunta norteadora são definidas professor. Além do dashboard, você vai entregar o "bastidor" do trabalho: o contexto que deu ao Claude (claude.md), uma skill de visualização criada por você (skill.md) e o registro dos prompts usados (prompts.md). Avalie o README do projeto e faça o que é pedido utilizando /mattpocock-skills:wayfinder quando precisar, lembre-se dos arquivos que você deve armazenar para a entrega.
O tema e pergunta que vamos desenvolver é:
2. A cor do poder municipal
Que retrato racial emerge das pessoas eleitas para governar os municípios brasileiros em 2024?
Para quem: leitores do relatório anual de um observatório da sociedade civil. Público amplo, on-line, sem ninguém para explicar. Exige rigor sobre o que a base permite e não permite afirmar.
Utilize agents se for necessário para paraleliza o desenvolvimento.
Utilize como base para a escrita da skill os livros:
A psicologia das cores: Como as cores afetam a emoção e a razão por Eva Heller  e
Storytelling with Data: A Data Visualization Guide for Business Professionals por Cole Nussbaumer Knaflic
Me questione o que  for necessário.
```

**O que funcionou / o que mudei:** Funcionou entregar de uma vez o tema, a pergunta, o público e a exigência de rigor: o Claude leu o README e o dicionário antes de tocar nos dados e transformou a exigência em uma seção própria do dashboard (“o que a base permite e não permite afirmar”). Indicar os dois livros também deu direção concreta à skill: de Knaflic vieram os títulos que afirmam o achado e o cinza como padrão; de Heller, a decisão de não usar cores que imitem tons de pele. O que não saiu como pedi: a skill `wayfinder` não estava instalada na sessão, então o Claude seguiu sem ela; e ele preferiu não usar agentes, porque o trabalho era sequencial (analisar, depois desenhar, depois documentar). Pedi “me questione o que for necessário”, mas ele assumiu as decisões e as registrou no `claude.md` em vez de perguntar — ganhei tempo, e a revisão das escolhas ficou comigo. Num próximo trabalho, eu separaria em dois prompts: primeiro a análise e a proposta de história, para eu aprovar; só depois o HTML.

---

## Prompt 2

```
segue a url do fork https://github.com/AlanTulio/storytelling-dados-atividade1.git
```

**O que funcionou / o que mudei:** Depois de abrir o dashboard e revisar os arquivos, só faltava a entrega. O Claude tinha parado antes de enviar qualquer coisa, porque o repositório clonado apontava para o do professor e não para o meu fork. Com a URL, ele criou uma branch a partir da versão mais recente do repositório original, fez o commit apenas da minha pasta e enviou para o fork. O Pull Request eu abri pelo navegador.
