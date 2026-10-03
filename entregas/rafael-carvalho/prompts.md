# Registro real dos prompts

Ferramenta utilizada: Codex. Os textos abaixo reproduzem os pedidos substantivos do estudante; caminhos de anexos e marcação de interface foram omitidos. Não houve uma sequência fictícia de prompts para simular o uso de outra ferramenta.

## 1. Compreensão da atividade

> Olá. Preciso que façamos um trabalho da matéria Storytelling de Dados. Segue o link do Github do repositório do professor: https://github.com/prof-danny-idp/storytelling-dados-atividade1. Você consegue acessá-lo? Segue também as instruções. Peço para que avalie com cuidado para que não deixemos nada passar "em branco". Você entendeu o que devemos fazer?

O que funcionou / o que mudei: o Codex leu as imagens, consultou o README e o dicionário e identificou as quatro entregas, cuidados de contagem, exigência de skill genérica e divergência de prazo. O tema ainda precisava ser informado.

## 2. Definição do tema, local e ferramenta

> Segue a foto com o tema. Consegue ler? Fiquei com o tema 1. Quero que fique tudo na pasta: C:\Users\rafae\OneDrive\Documentos\Mestrado IDP\Matérias\Storytelling com Dados\Dashboard - Atividade. Lembrar de alterar tudo que for "Claude" para "Codex".

O que funcionou / o que mudei: o briefing definiu a comissão legislativa como público. A narrativa passou a separar os cargos, comparar territórios e examinar chapas. O documento de contexto recebeu o nome codex.md conforme pedido, criando uma incompatibilidade com o nome esperado na entrega original que está explicitada nas orientações locais.

## 3. Autorização para produzir

> Ótimo! Podemos prosseguir.

O que funcionou / o que mudei: a base foi baixada, contagens verificadas por PowerShell e Python e o HTML foi construído com agregados embutidos. Incluiu-se um filtro para separar o recorte histórico das chapas marcadas como eleitas na extração do TSE. Os documentos foram redigidos durante a execução; a skill registra regras reutilizáveis, sem afirmar que já havia sido instalada ou aplicada por um mecanismo de skills.

## 4. Revisão das regras de design

> Ótimo! Mas eu gostaria de acrescentar algumas partes de design gráfico na Skill para que você siga na criação do Dashboard. Podemos fazer as alterações? Essa skill é específica para esse dashboard, né?

O que funcionou / o que mudei: esclareceu-se que a skill é reutilizável; as escolhas específicas deste trabalho ficam no codex.md.

## 5. Paleta e cartografia

> Ok. A skill precisa dizer que, no caso de comparação entre homens e mulheres, as cores utilizadas devem ser em tons de azul marinho para homens e roxo para as mulheres...como no anexo. A tipografia e o espaçamento estão bons. Quando for feita alguma análise territorial, mostrando diferentes cidades, fazer uma análise com mapa. Utilizando as cores indicadas para homens e mulheres no mapa, com intuito de ressaltar as cidades ou as regiões onde tem mais mulheres ou mais homens. Comecemos com essas. Você tem alguma sugestão para alterarmos o design?

O que funcionou / o que mudei: a paleta passou a usar azul-marinho e roxo. Adicionou-se à skill a exigência de mapas territoriais com escala, legenda, fonte e tratamento de ausência. Para o dashboard, definiu-se um mapa estadual com alternância de gênero e consulta de contagens. Mantiveram-se barras, tipografia e espaçamento. Um estado com participação feminina relativamente maior não foi rotulado como maioria feminina.

## 6. Contorno dos estados

> Quando passo o mouse por cima dos estados o contorno é preto. Pode colocar esse roxo para as mulheres e azul escuro para homens.

O que funcionou / o que mudei: hover, seleção e foco passaram a usar a cor do gênero selecionado no mapa: roxo #7f00b2 para mulheres e azul-escuro #000020 para homens.


## 7. Preenchimento do estado selecionado

> Ótimo! Mas quando selecionar, pode pintar todo o estado e deixar os que não foram selecionados com a transparência em cerca de 30%...tanto de homens quanto de mulheres.

O que funcionou / o que mudei: seleção sólida na cor do gênero, demais estados com 30% de opacidade. Botão Limpar seleção restaura o mapa proporcional. Uma nota distingue destaque de seleção de valores da escala.


## 8. Opacidade e botões de gênero

> Aumenta para 50 a opacidade de quando for selecionado o das mulheres... o dos homens ficou bom. Quando clicar novamente no estado, deve voltar para o mapa completo, e não apenas quando clicar em limpar seleção. A seleção de mostrar no mapa entre homens e mulheres será melhor se for algo apenas clicável, ao invés de uma lista suspensa.

O que funcionou / o que mudei: estados não selecionados com 50% de opacidade no modo mulheres e 30% no modo homens; segundo clique ou ativação por teclado limpa a seleção. Dois botões com indicação de ativo substituem a lista de gênero.


## 9. Distrito Federal e pictogramas

> Apenas o DF, quando é selecionado, não está sendo pintado. Nessas porcentagens de mulheres na prefeitura, daria para colocar um quadrinho com 100 bonecos e marcar apenas o que representaria cada porcentagem? Talvez uma representação mais visual ajude o entendimento.

O que funcionou / o que mudei: DF pode receber destaque de seleção, mantendo seu aviso de ausência de eleição municipal. Cada cartão ganhou 100 pictogramas, com preenchimento parcial para a casa decimal. A unidade de análise é explicitada, sobretudo no cartão de chapas, que representa municípios.


## 10. Título e contraste dos pictogramas

> Quero o título: O Brasil precisa de mais mulheres! No subtítulo: Mulheres ocupam apenas 13,2% das prefeituras no recorte nacional. Precisamos de mais contraste entre as cores dos bonecos. O comentário sobre a representação pode ser apenas um para todos, abaixo.

O que funcionou / o que mudei: título solicitado, subtítulo factual com percentual nacional que acompanha o critério de inclusão; bonecos com roxo vivo #a600d9 e azul-marinho #000020; uma nota abaixo dos três cartões distingue pessoas de municípios.


## 11. Ajuste do azul dos bonecos

> Deixe apenas esse azul, dos bonecos masculinos, mais claro (mas não muito).

O que funcionou / o que mudei: apenas o azul dos pictogramas passou de #000020 para #303b68, preservando o roxo e as cores do mapa.


## 12. Revisão final do exercício

> Ótimo! Agora podemos seguir com o exercício.

O que funcionou / o que mudei: revisaram-se narrativa, documentação e requisitos de entrega. O codex.md foi alinhado às decisões finais, incluindo cores, seleção e pictogramas; as regras de design foram organizadas na skill. Preparou-se um pacote com somente os quatro arquivos principais, deixando identificação e compatibilidade do nome do contexto pendentes de resposta do estudante.


## 13. Identificação e nome aceito pelo professor

> Rafael Carvalho. O usuário do GitHub é https://github.com/rafael7carvalho. O professor disse que o arquivo agents.md deve ser entregue com o nome de claude.md.

O que funcionou / o que mudei: pasta de entrega definida como entregas/rafael-carvalho. O contexto consolidado do Codex foi entregue com o nome claude.md, conforme orientação do professor transmitida diretamente pelo estudante, mantendo o registro verdadeiro da ferramenta utilizada.

