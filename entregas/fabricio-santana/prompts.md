# Diário de prompts

**Link compartilhado da conversa (opcional):** não se aplica.

---

## Prompt 1

```
Leia o README, o dicionário e o briefing dos cinco temas. Escolha o tema que pode render uma narrativa mais clara para um público específico, explique a pergunta norteadora e liste os cuidados de contagem da base.
```

**O que funcionou / o que mudei:** escolhi mulheres e homens no comando das prefeituras porque a pergunta tem uma métrica central fácil de entender e permite mostrar diferenças territoriais sem extrapolar para causalidade.

## Prompt 2

```
Analise eleitos.csv usando apenas cargo = Prefeito. Calcule total nacional, distribuição por genero_tse, distribuição por região e UF, além de reeleicao declarada. Conte municípios por codigo_municipio_tse, preserve ausências e produza percentuais com seus denominadores.
```

**O que funcionou / o que mudei:** o filtro mostrou 5.553 prefeitos, 734 na categoria FEMININO e 4.819 na categoria MASCULINO. Mantive “gênero cadastrado no TSE” na redação para não transformar a variável em inferência sobre identidade.

## Prompt 3

```
Proponha um storyboard para uma comissão do Legislativo em audiência pública, com leitura em poucos minutos. Use a sequência panorama nacional, regiões, UFs e reeleição. Para cada visualização indique o tipo de gráfico, a mensagem e o cuidado metodológico.
```

**O que funcionou / o que mudei:** barras 100% empilhadas funcionam melhor que um ranking isolado para mostrar composição. Acrescentei contagens absolutas nas UFs, porque percentuais em estados pequenos podem induzir a uma leitura exagerada.

## Prompt 4

```
Gere os quatro arquivos finais: claude.md, skill.md, prompts.md e dashboard.html. O HTML deve ser autocontido, responsivo, acessível, sem ler arquivos locais e com dados agregados embutidos. Revise o texto para não afirmar quem ocupa o cargo hoje, não duplicar municípios e não inferir identidade a partir do campo de gênero.
```

**O que funcionou / o que mudei:** a revisão final transformou as limitações em notas visíveis no painel e separou regras genéricas na skill de decisões específicas no claude.md.
