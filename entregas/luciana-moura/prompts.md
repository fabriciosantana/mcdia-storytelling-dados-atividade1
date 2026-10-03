# Diário de prompts

**Link compartilhado da conversa (opcional):** não há; o trabalho foi feito no Claude Code, no terminal.

---

## Prompt 1

```
Estou aprendendo a fazer esta atividade e tenho que fazer esta atividade. Prepare todo o ambiente para eu fazer a atividade. https://github.com/prof-danny-idp/storytelling-dados-atividade1
```

**O que funcionou / o que mudei:** O Claude leu o README, os modelos e a regra de validação do repositório antes de mexer em qualquer coisa, e conferiu que o git, o GitHub CLI e o Python já estavam instalados. Ele avisou que o prazo era no mesmo dia e pediu minha confirmação antes de cada passo: criar o fork, clonar e copiar o modelo para a pasta `entregas/luciana-moura`. O prompt não dizia o meu tema, e o Claude me pediu o tema e a pergunta norteadora, que informei no prompt seguinte.

---

## Prompt 2

```
Mulheres e homens no comando das prefeituras. Pergunta norteadora Como mulheres e homens estão presentes no comando dos municípios brasileiros eleitos em 2024?
```

**O que funcionou / o que mudei:** Com o tema e a pergunta, o Claude analisou a base e me mostrou uma tabela de achados (13,2% de prefeitas, 19,3% de vice-prefeitas, 69,6% das chapas sem mulher, diferenças por região, estado e porte, e o perfil de idade, reeleição e escolaridade). Ele apontou duas ressalvas: a base não tem população, então o porte foi medido por votos válidos, e estados com poucos municípios têm percentuais instáveis. Depois propôs uma história em três atos e mais duas alternativas (só geografia ou só chapas).

---

## Prompt 3

```
Sim, usar essa (Recomendado)
Aprovar os 4 agora
```

**O que funcionou / o que mudei:** Não foi um texto livre: escolhi entre as opções que o Claude apresentou. Fiquei com a história em três atos (o tamanho da diferença, onde elas estão, quem são) e autorizei a criação dos quatro arquivos de uma vez, por causa do prazo. O Claude então escreveu o `claude.md`, a `skill.md` genérica, o `dashboard.html` com os dados agregados embutidos e este diário.
