# Diário de prompts

**Link compartilhado da conversa (opcional):**

---

## Prompt 1

```
estou aprendendo e tenho de fazer essa atividade prepare para mim todo o ambiente para eu fazer essa atividade https://github.com/prof-danny-idp/storytelling-dados-atividade1
```

**O que funcionou / o que mudei:** O Claude clonou o repositório, criou o fork, montou um ambiente Python com pandas e copiou o modelo para a minha pasta. Percebi que ele precisava do meu tema para seguir, então no prompt seguinte passei a pergunta norteadora e o briefing completos.

---

## Prompt 2

```
pergunta norteadora: como o poder municipal ficou distribuido entre partidos e alianças após as eleições de 2024? Briefing: a editora de política de um veículo de impressa está preparando um especial sobre o resultado das eleições municipais e quer um dashboard que funcione como peça central da matéria. O leitor é o público geral do jornal: interessado em política, mas sem familiaridade com os dados eleitorais. A editora quer uma história que se sustente sozinha e que vá além da simples contagem de vitórias. Sua história deve mostrar como o poder local se organizou entre partidos e alianças e o que esse arranjo diz sobre a política brasileira.
```

**O que funcionou / o que mudei:** Com o briefing, o Claude analisou além da contagem de prefeituras: o tamanho das alianças, os vices de outro partido, o peso por eleitorado e as diferenças por região. Isso virou o rascunho do `claude.md`, com a história central ("seis partidos, três em cada quatro prefeituras") e a ordem dos capítulos. Concordei com a narrativa proposta e, no prompt seguinte, pedi a skill e o dashboard.

---

## Prompt 3

```
concordo sem precisar revisar. agora Crie a skill.md genérica e depois o dashboard.html seguindo o claude.md
```

**O que funcionou / o que mudei:** O Claude criou uma skill genérica, sem citar a base, com regras de narrativa (título-manchete, capítulos, conclusão), escolha de gráficos, paleta com papéis (destaque, contraponto, neutro) e um checklist. Em seguida, calculou os agregados em Python, embutiu os dados como JSON e montou o dashboard em HTML/CSS puro, sem bibliotecas externas. Na revisão, ele mesmo corrigiu um título que exagerava ("quase sempre os dois são do bloco") porque o dado mostrava 51%; o título passou a dizer "em metade das cidades". Também conferiu o layout em telas de computador e de celular.
