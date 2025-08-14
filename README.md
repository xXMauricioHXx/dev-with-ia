# Desenvolvimento com IA

## Prompt Engineering

A engenharia de prompt visa desenvolver e otimizar os prompts e utilizar os modelos de linguagem de forma eficiente.

Além de projetar e desenvolver prompts a engenharia de prompts abrange a melhora na segurança, eficiência e maneiras de aumentar o conhecimento do domínio dos LLM's de forma a obter melhores resultados.

### Elementos de um prompt

Um prompt pode conter qualquer um dos seguintes componentes:

`Instrução` - uma tarefa ou instrução especifica que você deseja que o modelo execute.

`Contexto` - poder envolver informação externas ou contexto adicional que pode direcionar o modelo para melhores respostas.

`Dados de entrada` - é a entrada ou pergunta para a qual estamos interessados em encontrar uma resposta.

`Indicador de saída` - indica o tipo ou formato de saída.

Nem todos os components são necessários para o prompt e o formato depende da tarefa em questão.


### Dicas para criação de prompts

- Comece simples
- Divida tarefas grandes em subtarefas
- Experimente instruções diferentes com palavras-chave ("Escrever", "Classificar", "Resumir", "Traduzir", "Ordenar", etc)
- Seja específico sobre a instrução e a tarefa que deseja que o modelo execute.
- Forneça exemplos no prompt, tanto de possíveis entradas e formato de saída
- Inclua somente detalhes que são relevantes e contribuam para a tarefa em mão.
- Seja especifico e direto
- Evite dizer oque não fazer, mas dizer oque fazer.
  
  *`Prompt Ruim:`*
  ```
  O agente a seguir recomenda filmes para um cliente. NÃO PEÇA INTERESSES. NÃO PEÇA INFORMAÇÕES PESSOAIS.

  Cliente: Por favor, recomende um filme baseado nos meus interesses.
  Agente:
  ```

  *`Prompt bom:`*
  ```
  O agente a seguir recomenda filmes para um cliente. O agente é responsável por recomendar um filme dos principais filmes de tendências globais. Deve abster-se de perguntar aos usuários sobre suas preferências e evitar pedir informações pessoais. Se o agente não tiver um filme para recomendar, ele deve responder "Desculpe, não foi possível encontrar um filme para recomendar hoje.".
  Cliente: Por favor, recomende um filme baseado nos meus interesses.
  Agente:
  ```

É possível ver os exemplos acima citados sendo aplicados em https://www.promptingguide.ai/pt/introduction/examples 

### Técnicas de Prompting

#### Zero-shot Prompting

Prompts onde não é fornecido exemplos de funcionamento

Ex.:

*Prompt:*
```
Classifique o texto em neutro, negativo ou positivo.
Texto: Acho que as férias estão boas.
Sentimento:
```

*Saída:*
```
Neutro // Errado pois está com N maiúsculo
```

Quando o zero-shot não funciona, é recomendável fornecer demonstrações ou exemplos no prompt que leva ao `Few-shot prompting`.

#### Few-shot Prompting

Consiste em adicionar demonstrações no prompt  para direcionar o modelo para um melhor desempenho.

`Prompt:`
```
Um "whatpu" é um pequeno animal peludo nativo da Tanzânia. Exemplo de frase que usa
a palavra whatpu é:
Estávamos viajando pela África e vimos esses whatpus muito fofos.
"Farduddlear" significa pular para cima e para baixo muito rápido. Exemplo de frase que usa
a palavra farduddlear é:
```

`Saída:`

```
Quando ganhamos o jogo, todos farduddleamos em festejo.
```

Em tarefas mais complexas podemos aumentar a quantidade de exemplos fornecidos. Porém com problemas que exigem raciocínio usar `Few-shot` pode não fornecer o resultado esperado.

#### Chain-of-Thought (CoT)

Permite raciocínio complexo por meio de etapas intermediárias de raciocínio. 

Pode se obter melhores respostas adicionando um "Pense passo a passo" nos prompts.

#### Self-Consistency


