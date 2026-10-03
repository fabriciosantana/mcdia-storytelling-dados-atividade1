# Diário de prompts

**Link compartilhado da conversa (opcional):** https://claude.ai/code/session_01CRY8zSwEXdX1CP7wrZfrzJ

Trabalhei com o Claude Code (claude.ai/code). Os prompts abaixo estão em ordem cronológica. O primeiro foi o enunciado inteiro da atividade, colado como veio.

---

## Prompt 1

```
preciso fazer isso Storytelling de Dados
Quem governa as cidades: um dashboard sobre as eleições municipais de 2024
[enunciado completo da atividade: a base eleitos.csv, os cuidados com os dados, os 5 temas e o que entregar: dashboard.html, claude.md, skill.md e prompts.md]
```

**O que funcionou / o que mudei:** O Claude olhou o repositório antes de começar e viu que não tinha a base, o tema nem o repositório da disciplina, então pediu essas três informações em vez de inventar números. Isso evitou um dashboard sobre dados que eu não tinha.

---

## Prompt 2

```
primeiro preciso criar isso O que entregar
Cada estudante cria uma pasta dentro de `entregas/` com o próprio nome, no formato `nome-sobrenome`... A pasta precisa ter exatamente estes 4 arquivos...
vamos fazer passo a passo
```

**O que funcionou / o que mudei:** Pedi para ir por etapas, e a estrutura da pasta saiu primeiro. Mas ela foi criada no repositório errado (`meu-primeiro-repo`), porque eu ainda não tinha dito qual era o da disciplina. Depois refiz no fork certo.

---

## Prompt 3

```
[captura de tela do meu painel do GitHub]
esse é meu github
```

**O que funcionou / o que mudei:** Mostrar a tela ajudou o Claude a achar o repositório `storytelling` na minha conta. Só que ele não era o da disciplina: era de outro projeto meu. Aprendi que "esse é meu github" não bastava e que era melhor mandar o link direto.

---

## Prompt 4

```
disiplina e esse https://github.com/prof-danny-idp/storytelling-dados-atividade1 e vamos usar o vscode
```

**O que funcionou / o que mudei:** Com o link, o Claude leu o README, o modelo, o dicionário e as regras da verificação automática. Isso já definiu pontos importantes, como a skill precisar ser genérica e só mudar arquivos na minha pasta. Também expliquei que eu não precisaria do VS Code para a entrega, só para revisar.

---

## Prompt 5

```
[captura de tela da página do repositório do professor, com o botão Fork]
me ajude passo a passo
```

**O que funcionou / o que mudei:** O Claude me guiou no clique do Fork e, quando mandei a captura do fork criado, conectou-o à sessão. Funcionou bem para quem não está acostumado com o GitHub.

---

## Prompt 6

```
Quem governa os municípios. 2 Meu nome completo é Ricardo Carvalho da Costa
```

**O que funcionou / o que mudei:** Informei o tema (5) e o nome para a pasta. Meu "2" era só o número da minha segunda resposta, e o Claude interpretou isso corretamente como o tema 5 e avisou da suposição. Daqui em diante ele analisou a base e gerou os quatro arquivos: calculou os números só com `cargo = Prefeito`, conferiu contagem de municípios, tratou dado ausente fora do denominador e testou o HTML em tela larga, em celular e em modo escuro.

---

## O que eu mudaria da próxima vez

- Dizer logo no primeiro prompt qual é o tema e o link do repositório da disciplina.
- Pedir ao Claude para mostrar os números que ele conferiu antes de aceitar o gráfico, porque o rigor com a base é critério de avaliação.
