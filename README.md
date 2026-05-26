NotebookLm -- Engenharia de Prompts
  Estudo prático sobre técnicas de Prompt Engineering utilizando o NotebookLM da Google como base conhecimento e o ChatGPT como principal ambiente de testes. Afim de testar as capacidades da plataforma de extrair conhecimentos das fontes e utilizar desse conhecimento para aplicações práticas.


Contexto e Objetivos
  A engenharia de prompts (Prompt Engineering) é a prática de estruturar instruções para modelos de linguagem de forma a extrair respostas mais precisas, úteis e consistentes. Com a popularização de ferramentas como ChatGPT, Gemini e Claude, saber construir bons prompts se tornou uma habilidade cada vez mais relevante.
Este projeto utiliza o NotebookLM como um segundo cérebro especializado: a ferramenta foi alimentada com fontes selecionadas sobre o tema e configurada para atuar como um assistente de construção de prompts. Os prompts gerados foram então testados no ChatGPT para validação prática.

Objetivos
  -Compreender as principais técnicas de prompt engineering documentadas na literatura
  -Utilizar o NotebookLM como ferramenta de curadoria e geração de conhecimento aplicado
  -Documentar o processo de criação, teste e refinamento de prompts
  -Construir um guia de referência reutilizável para uso futuro

Técnicas principais estudadas
  -Zero-shot
  -Few-shot
  -Chain-of-Thought(COT)
  -Role Prompting


Curadoria de Fontes (Documentos utilizados fornecidos em mais detalhes nos arquivos pdf prompt.pdf e prompt.txt)
  As fontes abaixo foram selecionadas e adicionadas ao NotebookLM. A curadoria priorizou materiais abertos, com cobertura técnica das quatro técnicas estudadas e diferentes formatos (texto, PDF e vídeo).

  Fonte 1 - Prompt Engineering Guide
  Link: https://www.promptingguide.ai/pt
  Justificativa: Referência técnica aberta e abrangente, cobre todas as técnicas com exemplos

  Fonte 2 - Design de Prompt: Introdução à Engenharia de Prompts (Vídeo)
  Link: https://www.youtube.com/watch?v=1VDcke66TRE
  Justificativa: Vídeo completo a respeito do assunto, mais de 1 hora de conteúdo testado e de fontes confiaveis

  Fonte 3 - Engenharia de Prompt: O Guia Definitivo
  Link: https://www.youtube.com/watch?v=ATp4Q4UD-c8
  Justificativa: Vídeo do respeitado professor Gustavo Guanabará e Ramiro Lobo, fornece de maneira didática explicação introdutória do assunto

  Fonte 4 - Google's 6 Hour Prompt Engineering Course
  Link: https://www.youtube.com/watch?v=o3qfL2fcSx4
  Justificativa: Resumo do curso completo em inglês do Google a respeito de engenharia de prompts

  Fonte 5 - Chain-of-Thought Prompting Elicits Reasoning in Large Language Models
  Link: https://arxiv.org/abs/2201.11903
  Justificativa: Material técnico estruturado sobre as técnicas

  Fonte 6 - OpenAI Cookbook
  Link: https://github.com/openai/openai-cookbook
  Justificativa: Complemento às fontes anteriores, vale ressaltar que o OpenAI Cookbook não foi fornecido na integra para o NotebookLM, foi feita uma curadoria dos principais temas dos artigos do repositorio para fornecer como fonte



Engenharia de Prompts e Cicatrizes
  Esta seção documenta as perguntas feitas ao NotebookLM, os prompts gerados e os resultados dos testes práticos. Os ajustes e dificuldades encontrados estão registrados como troubleshooting. Os testes na integra estão disponíveis na pasta testes

  Pergunta 1 -- Zero-shot
    Qual das técnicas de prompt deve ser utilizada para pedir uma análise crítica de um texto sem dar exemplos?
  
  Resposta do NotebookLM:
A técnica indicada foi o Zero-shot Prompting, complementado por três estratégias:

  -Zero-shot Chain-of-Thought: adicionar "Vamos pensar passo a passo" para induzir raciocínio lógico
  -Role Prompting: instruir o modelo a agir como especialista (ex: "Aja como um crítico literário")
  -Instruções de formato: especificar o formato de saída desejado (tópicos, tabela, etc.)

Observação: A resposta demonstrou que, na prática, Zero-shot raramente funciona isolado em tarefas complexas — o notebook combinou automaticamente com outras técnicas. Isso evidencia que as técnicas não são mutuamente exclusivas.

  Pergunta 2 -- Few-shot
    Me ajude a construir um Few-Shot prompt para pedir a análise de textos em inglês, corrigindo-os e dando exemplos de mudanças que poderiam ser feitas.

Prompt gerado pelo NotebookLM:
  # Persona e Contexto
  Aja como um Editor de Textos e Professor de Inglês nativo com 20 anos de experiência
  em escrita acadêmica e profissional. Sua tarefa é analisar textos enviados por estudantes,
  identificar erros gramaticais, sugerir melhorias de estilo e fornecer exemplos práticos
  de como o texto pode ser transformado para soar mais natural.
  
  # Formato de Saída
  Para cada análise, use o seguinte esquema:
  - Análise Crítica: Breve comentário sobre a clareza e o tom.
  - Correções: Lista de erros gramaticais ou ortográficos.
  - Sugestões de Melhoria: Exemplos de mudanças frase a frase para tornar o texto mais fluido.
  
  <exemplo_1>
  Texto de Entrada: "I has a dog and he like play with ball."
  Análise: O texto é compreensível, mas apresenta erros básicos de concordância.
  Correções:
  - "I has" → "I have"
  - "he like" → "he likes"
  - "play with ball" → "playing with a ball"
  Sugestão: "I have a dog, and he loves playing with a ball."
  </exemplo_1>
  
  <exemplo_2>
  Texto de Entrada: "The meeting was boring. We don't decided nothing."
  Análise: Tom informal e double negative gramaticalmente incorreto.
  Correções:
  - "boring" → "unproductive"
  - "don't decided nothing" → "didn't decide anything"
  Sugestão: "The meeting was somewhat unproductive; we didn't reach any decisions."
  </exemplo_2>
  
  # Tarefa Atual
  Analise o texto abaixo seguindo exatamente o padrão dos exemplos anteriores:
  Texto para Analisar: [INSIRA O TEXTO AQUI]
  
Teste no ChatGPT: Aprovado
O prompt foi testado com um parágrafo acadêmico em inglês. O modelo identificou corretamente erros de capitalização, ortografia, preposição e registro formal, entregando correções detalhadas com justificativas e sugestões de reescrita frase a frase.
Por que funciona:

Tags XML (<exemplo>) separam claramente instrução de conteúdo de referência
A persona de especialista ativa vocabulário técnico mais sofisticado
O formato de saída especificado evita respostas genéricas

  Pergunta 3 -- Role Prompting
    Monte um Role Prompting para transformar o ChatGPT em um professor de anatomia artística.

  Prompt gerado pelo NotebookLM:
    Você é um professor especialista em anatomia artística com foco em desenho figurativo.
  Sua função é ensinar de forma clara e progressiva, usando analogias visuais simples
  (formas geométricas, volumes) para descrever músculos, ossos e proporções.
  
  Ao explicar qualquer estrutura anatômica:
  1. Descreva a forma base (ex: cilindro, esfera, placa)
  2. Explique como ela se conecta às estruturas vizinhas
  3. Indique como ela muda com o movimento
  4. Aponte os erros mais comuns ao desenhá-la
  
  Responda sempre com foco na aplicação prática para o desenho, não na biologia médica.
  
Teste no ChatGPT: Aprovado
  O modelo adotou a persona corretamente, descrevendo peitoral, deltoide e bíceps usando formas geométricas simples e uma hierarquia visual clara (esqueleto → músculos → pele). A resposta foi estruturada em tabelas e fluxogramas textuais, alinhada com o formato solicitado.
  Observação de troubleshooting: Este teste foi intencionalmente feito com um tema fora do escopo técnico do projeto (anatomia artística) para verificar se o notebook conseguia gerar prompts para áreas não relacionadas às suas fontes. O resultado foi positivo — o notebook aplicou os princípios de role prompting corretamente independente do domínio, embora as justificativas baseadas nas fontes tenham sido mais genéricas do que nos testes anteriores.

  Pergunta 4 -- Chain-of-Thought
    Monte um Chain-of-Thought prompting para construção de prompts de criação de imagem com IAs generativas.

    Prompt gerado pelo NotebookLM:
# Persona
Você é um especialista em engenharia de prompt para IAs generativas de imagem
(DALL-E 3, Midjourney, Stable Diffusion). Sua função é transformar ideias simples
em descrições altamente detalhadas e tecnicamente otimizadas.

# Instruções de Processamento (Chain-of-Thought)
Para cada pedido, pense passo a passo seguindo este roteiro:
1. Identificar o Sujeito Central: O que é o foco principal?
2. Definir Estilo e Atmosfera: Natural ou Vivid? Qual movimento artístico?
3. Estabelecer Composição e Iluminação: Ângulo, enquadramento, fonte de luz?
4. Parâmetros Técnicos: Qualidade (standard/HD) e proporção (aspect ratio)?

# Exemplos de Referência (Few-Shot)
[exemplos de entrada → raciocínio → prompt final]

# Nova Tarefa
Processe a seguinte ideia seguindo o mesmo método:
Ideia: [INSIRA SUA IDEIA AQUI]

Teste no ChatGPT: Aprovado
  Testado com a ideia: "Um mago medieval idoso olhando para o céu estrelado." O modelo seguiu o raciocínio passo a passo — sujeito, estilo, composição, parâmetros — antes de gerar o prompt final em inglês com vocabulário técnico adequado para IAs de imagem.
  Observação importante — troubleshooting: O notebook gerou espontaneamente um prompt Few-Shot CoT combinado, não CoT puro. Isso ocorreu porque a tarefa envolvia variáveis complexas (estilo, iluminação, parâmetros técnicos) e o modelo identificou que apenas o raciocínio passo a passo seria insuficiente sem exemplos de referência. Isso confirma o que as fontes indicam: para tarefas complexas, as técnicas se complementam naturalmente.

Resumos Estruturados
  Zero-shot Prompting
    Instrução direta ao modelo sem fornecer exemplos. Funciona bem para tarefas simples e diretas. Para tarefas complexas, deve ser combinado com chain-of-thought ou role prompting para obter resultados de qualidade.
  Few-shot Prompting
    Fornece pares de exemplo (entrada → saída) antes da tarefa real. Reduz ambiguidade e força o modelo a seguir um padrão específico de resposta. Quanto mais específico o formato dos exemplos, mais precisa a resposta.
  Chain-of-Thought (CoT)
    Induz o modelo a raciocinar passo a passo antes de responder. Melhora significativamente a qualidade em tarefas que envolvem lógica, análise ou múltiplas variáveis. A instrução mais simples para ativar CoT é: "Vamos pensar passo a passo."
  Role Prompting
    Atribui uma persona ou especialização ao modelo. Ativa vocabulário, tom e critérios de julgamento condizentes com o papel definido. Mais eficaz quando combinado com instruções de formato de saída.

Glossário

Prompt = Instrução ou entrada de texto fornecida a um modelo de linguagem
, Zero-shot = Abordagem sem exemplos, apenas com a instrução da tarefa
, Few-shot = Abordagem com exemplos de entrada e saída antes da tarefa
, Chain-of-Thought = Técnica que induz raciocínio intermediário passo a passo
, Role Prompting = Atribuição de uma persona ou papel ao modelo
, LLM = Large Language Model — modelo de linguagem de grande escala
, Token = Unidade básica de texto processada pelo modelo (palavra ou parte dela)
, Temperatura = Parâmetro que controla a criatividade/aleatoriedade das respostas
, RAG = Retrieval-Augmented Generation — geração aumentada por recuperação de documentos
, NotebookLM = Ferramenta do Google que usa RAG para responder com base em fontes enviadas pelo usuário
, Tags XML = Marcadores estruturais usados em prompts para separar instruções de conteúdo

Prompts Reutilizáveis

Prompts para o NotebookLM

1. Comparação crítica das técnicas de prompt
  Compare as técnicas Zero-shot, Few-shot e Chain-of-Thought: quando cada uma
falha e quando cada uma se destaca? Use exemplos das fontes.

2. Analise das fontes para extração de técnicas para construção de prompts melhores
  Baseado nas fontes, quais são os erros mais comuns ao construir prompts
e como corrigi-los

3. Montagem de prompts para tarefas específicas
  Monte um prompt reutilizável para [TAREFA ESPECÍFICA] e justifique
qual técnica foi usada e por quê.

Prompts para uso prático em outras IAs

1. Análise crítica de texto (Zero-shot + CoT + Role)
  Aja como um crítico especialista em [ÁREA]. Analise o texto abaixo passo a passo,
avaliando: [CRITÉRIO 1], [CRITÉRIO 2] e [CRITÉRIO 3].
Formato de saída: tópicos com pontos positivos e pontos a melhorar.

Texto: [INSIRA O TEXTO AQUI]

2. Correção e melhoria de texto em inglês (Few-shot)
  Aja como um editor de inglês nativo. Para cada análise, siga o esquema:
- Análise Crítica, Correções, Sugestões de Melhoria frase a frase.

<exemplo>
Entrada: "He go to school every days."
Correção: "He goes to school every day."
Justificativa: Concordância verbal (3ª pessoa) e substantivo invariável.
</exemplo>

Texto para analisar: [INSIRA O TEXTO AQUI]

3. Geração de prompt para IA de imagem (Few-shot CoT)
     Você é especialista em prompts para IAs de imagem. Para cada ideia, pense passo a passo:
    1. Sujeito central
    2. Estilo e atmosfera
    3. Composição e iluminação
    4. Parâmetros técnicos (qualidade e proporção)

Depois, gere o prompt final em inglês.

Ideia: [INSIRA SUA IDEIA AQUI]



Projeto desenvolvido como atividade prática do módulo de IA — DIO
