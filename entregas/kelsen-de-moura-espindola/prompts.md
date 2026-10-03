# Diário de prompts

**Ferramenta:** Claude Code (app desktop), com a extensão Claude in Chrome e o Remote Control para enviar a foto do tema pelo celular.

**Link compartilhado da conversa (opcional):** não se aplica (sessão local do Claude Code).

---

## Prompt 1

```
preciso fazer uma tarefa, a pagina esta aberta na aba IDP do chrome.

depois que vc se localizar vou enviar o meu tema
```

**O que funcionou / o que mudei:** O Claude não conseguia ver a aba, porque a extensão só enxerga as abas do grupo que ela cria. Ele explicou isso e me deu duas opções: mandar a URL ou mover a aba para o grupo.

---

## Prompt 2

```
eu arrasto para o grupo
```

**O que funcionou / o que mudei:** O Claude criou o grupo de abas no Chrome e eu arrastei a aba da tarefa para dentro dele.

---

## Prompt 3

```
pronto
```

**O que funcionou / o que mudei:** O Claude leu a página da tarefa e resumiu prazo, base, cuidados de leitura, entregáveis, links e os 5 temas. Isso me poupou tempo de releitura. Depois ele clonou o repositório, leu o README, o dicionário e a verificação automática do PR, para saber as regras exatas antes de começar.

---

## Prompt 4

```
claude rc
```

**O que funcionou / o que mudei:** O prompt era ambíguo, e o Claude perguntou o que eu queria em vez de adivinhar. No seguinte expliquei o objetivo.

---

## Prompt 5

```
quero o remote pra poder adicionar a imagem do tema
```

**O que funcionou / o que mudei:** O Claude ativou o Remote Control na sessão e eu enviei a foto do briefing pelo celular.

---

## Prompt 6

```
[foto do briefing impresso do Tema 4 - Continuidade e renovação]
```

**O que funcionou / o que mudei:** A foto bastou: o Claude leu a pergunta norteadora e o público direto da imagem. Antes de desenhar, ele explorou os dados e encontrou os achados que viraram a espinha da história:

- 44% de prefeitos reconduzidos;
- variação de 31% (SC) a 67% (RR) entre os estados;
- mediana de 65% dos votos válidos para os reconduzidos, contra 54% para os novos;
- 195 das 288 disputas com candidato único foram reconduções;
- mesmo perfil de gênero e escolaridade entre os dois grupos.

O que mudou no caminho:

- **Linguagem:** o Claude evitou falar em "taxa de reeleição", porque a base não traz quem tentou e perdeu, e passou a usar "reconduzidos" e "novos".
- **Celular:** a primeira versão tinha gráficos ilegíveis no celular, com o texto encolhendo junto com o SVG. O Claude refez os gráficos para usar a largura real da tela e redesenhar ao redimensionar.
- **Números de destaque:** um estilo genérico apagava a cor dos percentuais, e o Claude corrigiu.
