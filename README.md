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

  _`Prompt Ruim:`_

  ```
  O agente a seguir recomenda filmes para um cliente. NÃO PEÇA INTERESSES. NÃO PEÇA INFORMAÇÕES PESSOAIS.

  Cliente: Por favor, recomende um filme baseado nos meus interesses.
  Agente:
  ```

  _`Prompt bom:`_

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

_Prompt:_

```
Classifique o texto em neutro, negativo ou positivo.
Texto: Acho que as férias estão boas.
Sentimento:
```

_Saída:_

```
Neutro // Errado pois está com N maiúsculo
```

Quando o zero-shot não funciona, é recomendável fornecer demonstrações ou exemplos no prompt que leva ao `Few-shot prompting`.

#### Few-shot Prompting

Consiste em adicionar demonstrações no prompt para direcionar o modelo para um melhor desempenho.

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

Ao adicionar no prompt um passo a passo de como o problema deve ser analisado pode gerar melhores respostas.

#### Self-Consistency

Utiliza o CoT múltiplas vezes afim de obter respostas mais consistentes em problemas que envolvem raciocínio aritmético e bom senso.

Mais informações em [Self-Consistency](https://www.promptingguide.ai/pt/techniques/consistency)

#### Generate Knowledge Prompting

É a capacidade de incorporar conhecimento ou informações que ajude o modelo a obter previsões mais precisas. O conhecimento pode ser usado como parte do prompt

Mais informações em [Generate Knowledge Prompting](https://www.promptingguide.ai/pt/techniques/knowledge)

#### Prompt Chaining

Consiste em dividir o prompt em sub-tarefas e cada resposta de uma tarefa é utilizada como entrada no prompt da proxima, com o objetivo de criar uma cadeia de operações de prompts.

É útil para realizar tarefas complexas que um LLM pode ter dificuldade em realizar se for solicitado com um prompt muito detalhado, permitindo analisar problemas mais facilmente e aprimorar o desempenho de diferentes etapas.

Mais informações em [Prompt Chaining](https://www.promptingguide.ai/techniques/prompt_chaining)

#### Tree of Thoughts (ToT)

#### Retrieval Augmented Generation (RAG)

Consiste na capacidade de adicionar uma ampla base de conhecimento externo que pode evoluir com o tempo ao LLM. O RAG recebe uma entrada e recupera um conjunto de documentos relevantes/de apoio, considerando uma fonte (por exemplo, Wikipédia). Os documentos são concatenados como contexto com o prompt de entrada original e enviados ao gerador de texto, que produz a saída final. Essas bases podem ser bancos vetoriais.

Tornando o RAG muito adaptável para situações onde os fatos evoluem conforme o tempo.

#### Automatic Reasoning and Tool-use (ART)

#### Automatic Prompt Engineer (APE)

#### Active-Prompt

#### ReAct Prompting

Consiste na junção de Reasoning + Act (Raciocinar + Ação), onde utilizamos o CoT adicionando ações como chamada de tools em cada passo, trazendo dados que tragam contexto para criação de CoT pelo LLM

Mais informações em [ReAct Prompting](https://www.promptingguide.ai/techniques/react)

### Versionamento de Prompt

Aprender mais sobre LangChain

## Agentes de IA

Agentes são sistemas alimentados por LLM's projetado para executar ações e resolver tarefas complexas de forma autônoma. São equipados com recursos adicionais como:

- Planejamento e execução: agentes podem analisar problemas, dividi-los em etapas e ajustar sua abordagem com base em novas informações.
- Acesso a ferramentas: podem interagir com ferramentas e recursos externos, como bancos de dados, API e aplicativos, para coletar informações e executar ação.
- Memória: agentes podem armazenar e recuperar informações permitindo que eles aprendam com experiências passadas e tomem decisões mais informadas

### Componentes do agente

Agentes de IA exigem 3 capacidades fundamentais para lidar com tarefas complexas: capacidade de planejamento, utilização de ferramentas e gerenciamento de memória.

#### Planejamento

A capacidade de planejamento em agentes de IA vem do uso de modelos de linguagem LLMs, que possibilitam diversas funções como:

- Decomposição de tarefas por meio de raciocínio em cadeia de pensamentos
- Autorreflexão sobre ações e informações passadas
- Aprendizagem adaptativa para melhores decisões futuras
- Análise crítica do progresso atual

#### Utilização de ferramentas

Um agente de IA bem projetado não só precisa ter acesso a diversas ferramentas, mas também entender quando e como usá-las adequadamente. Ferramentas comuns incluem:

- Intérpretes de código em ambientes de execução
- Utilitários de pesquisa na web
- Calculadoras matemáticas
- Sistema de gerenciamento de imagem

Essas ferramentas permitem que o agente execute as ações planejadas, sendo crucial para lidar com tarefas complexas de formas eficaz.

#### Sistema de memória

Para um agente de IA, gerenciamento de memória é essencial e vem de duas formas principais:

1. Memória de curto prazo

- Funciona como um buffer de contexto imediato
- Permite aprendizagem em contexto
- Ajuda a manter a continuidade durante a iteração da tarefa

2. Memória de longo prazo

- Implementado por meio de armazenamentos de vetores externos
- Permite a recuperação rápida de informações históricas

Esses sistemas de memória permitem que os agentes recuperem informações coletadas de ferramentas externas.


## MCP
