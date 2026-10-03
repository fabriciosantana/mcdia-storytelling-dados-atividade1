# Diário de prompts

**Link compartilhado da conversa (opcional):** —

> Os prompts abaixo estão em ordem cronológica e transcritos como enviados. Entre o prompt 2 e o 4 há uma rodada de "grilling" (o Claude entrevista o estudante, em rodadas numeradas de perguntas com recomendação) que serviu de especificação do dashboard. As perguntas do Claude estão resumidas; as respostas são as minhas.

---

## Prompt 1

```
Vamos fazer um exercicio da aula Storytelling de Dados, do professor Danny, do mestrado que estou fazendo. O primeiro passo era fazer um fork do repositorio do professor, o que eu ja fiz. Faça o clone do repositorio https://github.com/pedroigp/storytelling-dados-atividade1.git e leia as instruções para criarmos o dashboard.
```

**O que funcionou / o que mudei:** O Claude clonou, leu README, dicionário e modelos, e resumiu a entrega (4 arquivos, regras do PR, cuidados da base). Ele notou que o tema e a pergunta norteadora não estavam no repositório e pediu que eu os informasse. Faltou eu já ter colado o briefing neste prompt.

---

## Prompt 2

```
/grill-me vamos entao conversar sobre tudo o que falta para voce iniciar a tarefa. O tema é O mapa partidário de 2025. A pergunta norteadora é Como o poder municipal ficou distribuído entre partidos e aliançãs após as eleições de 2024. O Briefing é: A editoria de política de um veículo de imprensa está preparando um especial sobre o resultado das eleições municipais e quer um dashboard que funcione como peça central da matéria. O leitor é o público geral do jornal: interessado em política, mas sem familiaridade com dados eleitorais. A editora quer uma história que se sustente sozinha e que vá além da simples contagem de vitórias. Sua história deve mostrar como o poder local se organizou entre partidos e alianças e o que esse arranjo diz sobre a política brasileira.
```

**O que funcionou / o que mudei:** Pedir o grilling antes de construir funcionou bem: em vez de começar a gerar gráficos, o Claude olhou a base e voltou com 7 perguntas, cada uma com recomendação. Os achados dele já mudaram a história: só 5% dos prefeitos venceram sem coligação e em cerca de 77% das chapas o vice é de outro partido. Isso me deu a tese ("ninguém governa sozinho") que vai além de contar vitórias. As perguntas cobriram: tese central, como medir "poder" (prefeituras ou eleitorado), o que conta como aliança, recorte da base, tratamento do "mapa", formato (narrativa ou painel) e rótulos ideológicos.

---

## Prompt 3

```
Q1–Q6: ok. Q7) Voce tem a informacao se o partido é de centro, direita ou esquerda? Esse rótulo e agrupamento é muito interessante para saber como está distribuido o poder. Uma observacao, fiz o setup das skills do mat-pocock-skills nesse repositorio. se for o caso de precisarmos de ir para to-spec to-tickets implement etc.
```

**O que funcionou / o que mudei:** Aceitei as seis primeiras recomendações sem mudar, porque estavam bem argumentadas. Discordei da sétima (o Claude sugeria não classificar ideologicamente) e perguntei se havia a informação. O Claude disse que a base não a traz, apontou uma classificação acadêmica (Bolognesi, Ribeiro e Codato, 2023) e propôs três cuidados: citar a fonte, usar poucos grupos e tratar partidos novos como "sem classificação". Ele também propôs um fluxo enxuto em vez de to-spec e to-tickets, por causa do prazo. Na segunda rodada ele abriu 7 perguntas novas: capítulos, nome da pasta, fluxo, cores, publicação do PR e registro dos prompts.

---

## Prompt 4

```
Q7b) Concordo. Q8) pedro-povoa. Q9-Q10) OK. Q11) Ok. Você consegue pesquisar as cores dos partidos para usarmos nos gráficos? Q12) Ok. você pergunta e faz o pr, commit, branch, etc. AQ13) registre tudo em prompts.md inclusive nosso grilling.
```

**O que funcionou / o que mudei:** Aqui eu mudei de rumo em um ponto: o Claude tinha recomendado evitar as cores oficiais dos partidos, mas eu pedi que as pesquisasse. Ele pesquisou (Wikipédia pt) e aplicou só nas 10 maiores siglas, avisando que vários azuis são parecidos e por isso toda barra leva a sigla escrita. Também confirmou a classificação ideológica na fonte (survey de 2018) e achou um problema que eu não previa: MDB, PSD e PSDB ficam a centésimos da fronteira entre centro e direita, então o dashboard ganhou uma chave de sensibilidade. A pesquisa mostrou também que o PRD, partido novo, não foi avaliado e entra como "sem classificação". Daí o Claude agregou os dados, gerou o dashboard, o `claude.md` e a `skill.md`, e conferiu o HTML no navegador antes de eu abrir o PR.

---

## Prompt 5

```
a paleta de cores está a do claude padrão. Pode usar as cores do Brasil?
```

**O que funcionou / o que mudei:** Olhei o primeiro resultado e achei a interface genérica (fundo creme e vermelho-tijolo). O pedido curto bastou: o Claude trocou só a interface pelas cores da bandeira (faixa de abertura azul com filete verde e amarelo, números verdes, fecho azul) e manteve as cores dos partidos nos gráficos, para uma coisa não confundir a outra. Atualizou também a `skill.md` (de forma genérica) e o `claude.md`. Se eu fosse especificar melhor, diria já no começo qual identidade visual eu queria.
