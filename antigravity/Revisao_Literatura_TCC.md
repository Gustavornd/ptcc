# Classificação de Artigos - Revisão de Literatura (TCC)

Este documento contém a classificação dos artigos científicos da pasta de referências, avaliados de acordo com a sua utilidade para o projeto "GERAÇÃO DE LAYOUTS DE FASES 3D ASSISTIDA POR MODELOS DE LINGUAGEM DE GRANDE PORTE".

---

### Procedural Content Generation via Machine Learning (PCGML)
* **Relevância:** Alta
* **Classificação de Uso:** Referência Fundamental
* **Justificativa:** O artigo é o principal "survey" que fundamentou o campo de PCG baseado em aprendizado de máquina, abordando a representação de dungeons via grafos de progressão lógica e a modelagem topológica. Embora anterior ao uso de LLMs, ele estabelece as bases teóricas de como restrições estruturais de jogabilidade devem ser codificadas para geração procedural, conceito que suporta diretamente a decisão do seu TCC de separar a arquitetura lógica da engenharia geométrica.

### Evaluating Mixed-Initiative Procedural Level Design Tools using a Triple-Blind Mixed-Method User Study
* **Relevância:** Média
* **Classificação de Uso:** Contexto Teórico
* **Justificativa:** O estudo foca em co-criação de níveis 2D utilizando Algoritmos Genéticos em vez de LLMs, limitando sua aplicação direta. No entanto, sua discussão profunda sobre a validação matemática de restrições espaciais e de usabilidade (como a proporção de corredores e navegabilidade) serve como forte embasamento teórico para os testes de integridade que seu algoritmo determinístico precisará executar na engine Godot.

### Large Language Models and Games: A Survey and Roadmap
* **Relevância:** Alta
* **Classificação de Uso:** Referência Fundamental
* **Justificativa (3-4 linhas):** Mapeia o estado da arte do PCGML e o uso de LLMs na geração de conteúdo, destacando as falhas inerentes desses modelos com raciocínio espacial e alucinação de dados. Isso embasa teoricamente a arquitetura do TCC, justificando a delegação dos testes geométricos e físicos para o algoritmo determinístico do Godot.

### Word2World: Generating Stories and Worlds through Large Language Models
* **Relevância:** Média
* **Classificação de Uso:** Metodologia
* **Justificativa (3-4 linhas):** Demonstra a geração de ambientes 2D baseada em texto através de um pipeline híbrido que delega validações de navegabilidade para algoritmos clássicos (A*). Essa divisão arquitetural de tarefas orienta diretamente a metodologia do TCC, onde o LLM atua na lógica e a engine (Godot) valida o NavMesh.

### Procedural Content Generation in Games: A Survey with Insights on Emerging LLM Integration
* **Relevância:** Média
* **Classificação de Uso:** Contexto Teórico
* **Justificativa (3-4 linhas):** Aprofunda as definições conceituais do PCG e sua evolução até a integração de LLMs, ressaltando o quão mais complexa e inexplorada é a geração de mundos 3D. Tais observações formam o contexto teórico que valida a pertinência do TCC em aplicar grafos de progressão estruturados em JSON para cenários tridimensionais.

### Towards Friendly Mixed Initiative Procedural Content Generation: Three Pillars of Industry
* **Relevância:** Baixa
* **Classificação de Uso:** Contexto Teórico
* **Justificativa (3-4 linhas):** Trata-se de um artigo focado em PCG tradicional sem processamento de linguagem natural, porém, delineia as bases de sistemas "mixed-initiative" e retenção de controle pelo designer. Esses conceitos suportam a criação da ferramenta como um addon de Godot, onde a automação assistida por IA respeita os fluxos de trabalho da engine.

### A System for Procedural Generation of Virtual Agent Activity Using LLM-Based Scene Interpretation
* **Relevância:** Alta
* **Classificação de Uso:** Metodologia
* **Justificativa (3-4 linhas):** Implementa um sistema que utiliza o LLM apenas como um planejador semântico estruturado, enquanto a engine (Unity) atua como executora de posicionamento e constraints (NavMesh). Esse modelo reflete exatamente a metodologia proposta pelo TCC, que estabelece o LLM como "arquiteto" lógico e o algoritmo em Godot como "engenheiro" validador de geometria e sobreposição.
### DesignerlyLoop: Forming Design Intent through Curated Reasoning for Human-LLM Alignment
* **Relevância:** Baixa
* **Classificação de Uso:** Contexto Teórico
* **Justificativa (3-4 linhas):** O artigo explora como LLMs podem ser estruturados em grafos bidimensionais para o raciocínio de design, mesmo sem foco em level design. Essa representação baseada em nós conceituais se conecta à camada do "arquiteto" no TCC, onde o modelo elabora grafos lógicos de progressão em JSON que posteriormente precisam ser traduzidos e validados geometricamente pelo Godot.

### GENERATIVE AI & THE LEVEL DESIGNER: AN EXPLORATORY REPORT OF TOOLS, WORKFLOWS, AND CHALLENGES
* **Relevância:** Alta
* **Classificação de Uso:** Sustentação/Justificativa de Resultados
* **Justificativa (3-4 linhas):** Apresenta evidências empíricas das falhas de modelos generativos na criação de topologia 3D coerente e no raciocínio espacial, gerando artefatos inutilizáveis (sobreposições e coordenadas alucinadas). Isso fundamenta tecnicamente o TCC: o LLM falha ao operar autonomamente no espaço 3D, sendo imprescindível o algoritmo determinístico no Godot para garantir a integridade da NavMesh e evitar colisões.

### SceneTeller: Language-to-3D Scene Generation
* **Relevância:** Alta
* **Classificação de Uso:** Metodologia
* **Justificativa (3-4 linhas):** Propõe um pipeline híbrido no qual o LLM atua na geração do layout estruturado da cena e um sistema secundário realiza a montagem espacial 3D a partir dos dados. Essa divisão espelha a metodologia "arquiteto-engenheiro" do TCC, demonstrando como os layouts em JSON gerados pela IA são instanciados e validados pelo motor de jogo (Godot) usando restrições geométricas.

### Geração Procedural de Conteúdo Aplicada a Jogos Digitais Educacionais
* **Relevância:** Baixa
* **Classificação de Uso:** Contexto Teórico
* **Justificativa (3-4 linhas):** Descreve técnicas clássicas e algorítmicas de PCG de maneira puramente estocástica e sem o uso de linguagem natural. Os conceitos teóricos sobre geração e estruturação de mapas servem como base para a camada "engenheiro" no TCC, onde o Godot aplica testes geométricos construtivos para corrigir problemas e validar o layout gerado pelo LLM.

### Constructive generation methods for dungeons and levels
* **Relevância:** Baixa
* **Classificação de Uso:** Contexto Teórico
* **Justificativa (3-4 linhas):** Aborda algoritmos tradicionais de geração de masmorras (particionamento espacial e gramáticas construtivas) sem IA generativa em texto. Os conceitos teóricos de conexões entre salas e caminhos viáveis embasam o algoritmo determinístico no Godot, garantindo que os grafos do LLM sejam transformados em fases navegáveis, livres de intersecções incorretas e com uma NavMesh íntegra.
### Narrative-to-Scene Generation: An LLM-Driven Pipeline for 2D Game Environments
* **Relevância:** Média
* **Classificação de Uso:** Metodologia
* **Justificativa (3-4 linhas):** O artigo demonstra a extração de grafos relacionais simbólicos via LLM para guiar um algoritmo de geração, o que espelha a divisão de tarefas do TCC. Essa abordagem legitima metodologicamente a atuação do LLM estritamente como "arquiteto" na formulação da progressão em formato JSON, deixando a responsabilidade das validações de adjacência a cargo da engine.

### A Database-Driven Framework for 3D Level Generation with LLMs
* **Relevância:** Alta
* **Classificação de Uso:** Referência Fundamental
* **Justificativa (3-4 linhas):** O framework atua como um estado da arte (SOTA) recente ao utilizar LLMs apenas para regras semânticas, deixando a montagem e posicionamento 3D para otimização algorítmica baseada em restrições. Isso corrobora diretamente a implementação do addon no Godot, provando que um validador determinístico deve atuar na verificação geométrica e na garantia de funcionalidade da fase.

### Integration of Intelligent agents in Game Development: Prompt Engineering Methodologies for Automatic code generation
* **Relevância:** Baixa
* **Classificação de Uso:** Contexto Teórico
* **Justificativa (3-4 linhas):** A dissertação examina o comportamento e a integração de LLMs em motores gráficos (como a Unity) e detalha limitações crônicas, como alucinações e derivas arquiteturais. No TCC, esse referencial oferece a base teórica de que IA generativa falha em estruturas rigidamente acopladas, validando a abordagem de usar a IA apenas para layouts JSON em vez de controlar o espaço tridimensional de forma livre.

### Repurposing 3D Generative Model for Autoregressive Layout Generation
* **Relevância:** Alta
* **Classificação de Uso:** Sustentação/Justificativa de Resultados
* **Justificativa (3-4 linhas):** Os autores expõem evidências empíricas contundentes de que LLMs sem ancoragem física falham severamente na disposição espacial, causando sobreposições (overlaps) e objetos flutuantes. Esse apontamento justifica a premissa principal do TCC, comprovando a necessidade absoluta de um algoritmo "engenheiro" no Godot para realizar testes de intersecção em bounding boxes e garantir a integridade da NavMesh.

### SceneCraft: An LLM Agent for Synthesizing 3D Scene as Blender Code
* **Relevância:** Alta
* **Classificação de Uso:** Metodologia
* **Justificativa (3-4 linhas):** O estudo constrói um pipeline onde a IA mapeia a cena criando um grafo (blueprint) e, a partir dele, scripts convertem as relações espaciais em regras estritas para a engine (Blender). Essa organização metodológica reflete exatamente a estratégia adotada no TCC: gerar a lógica abstrata no LLM (grafos de progressão em JSON) e delegar a instanciação de blocos 3D e a aprovação geométrica ao algoritmo do motor.

### Constraint Is All You Need: Optimization-Based 3D Level Generation with LLMs
* **Relevância:** Alta
* **Classificação de Uso:** Referência Fundamental
* **Justificativa (3-4 linhas):** A pesquisa propõe uma solução no estado da arte utilizando LLMs para gerar descrições e restrições espaciais que passam por otimização em engine para definir os arranjos 3D. Essa base apoia a visão da tese de separar a intenção semântica gerada pelo modelo da validação geométrica e de colisões, que no TCC ocorrerá de forma determinística via addon no Godot.

### ZERO-SHOT 3D MAP GENERATION WITH LLM AGENTS: A DUAL-AGENT ARCHITECTURE FOR PROCEDURAL CONTENT GENERATION
* **Relevância:** Alta
* **Classificação de Uso:** Metodologia
* **Justificativa (3-4 linhas):** O artigo expõe uma arquitetura onde um agente planeja a semântica da cena e o outro atua como validador rigoroso das instruções em relação às restrições lógicas. Esse *workflow* espelha a metodologia do TCC, onde o papel criativo fica a cargo da IA gerando o percurso, enquanto os algoritmos do Godot atuam como o "engenheiro" avaliando colisões e regras rígidas.

### UnrealLLM: Towards Highly Controllable and Interactable 3D Scene Generation by LLM-powered Procedural Content Generation
* **Relevância:** Alta
* **Classificação de Uso:** Metodologia
* **Justificativa (3-4 linhas):** O texto detalha a integração híbrida entre agentes LLM e uma engine, utilizando representações estruturadas em formato JSON para a criação procedural controlada. Isso embasa diretamente as etapas de desenvolvimento do seu addon, que também extrairá layouts em JSON dos modelos de linguagem para garantir uma instanciação escalonável de *meshes* no Godot.

### METODOLOGIA DE GERAÇÃO PROCEDURAL DE CONTEÚDO PARA ESTRUTURAS NARRATIVAS EM JOGOS ELETRÔNICOS
* **Relevância:** Média
* **Classificação de Uso:** Contexto Teórico
* **Justificativa (3-4 linhas):** A obra compila os conceitos fundamentais da evolução da Geração Procedural de Conteúdo (PCG), suas definições clássicas e a taxonomia da montagem em *tile-based*. Apesar de seu foco ser puramente narrativo, o texto fornece a fundação histórica e teórica necessária para discutir o surgimento da proceduralidade e o controle de progressões modulares em jogos.

### RoomPlanner: Explicit Layout Planner for Easier LLM-Driven 3D Room Generation
* **Relevância:** Alta
* **Classificação de Uso:** Sustentação/Justificativa de Resultados
* **Justificativa (3-4 linhas):** O artigo demonstra como gerações diretas via IA resultam em sobreposições e objetos inacessíveis, necessitando da aplicação de *constraints* de colisão e alcançabilidade em etapas pós-geração. Esses resultados empíricos validam a necessidade vital do addon no Godot para certificar o distanciamento espacial correto e a integridade da malha de navegação (NavMesh).

### Code-as-Room: Generating 3D Rooms from Top-Down View Images via Agentic Code Synthesis
* **Relevância:** Alta
* **Classificação de Uso:** Sustentação/Justificativa de Resultados
* **Justificativa (3-4 linhas):** A pesquisa evidencia que as abordagens baseadas estritamente em dedução textual perdem informações de precisão, resultando em alucinações de coordenadas espaciais e falhas de execução no espaço 3D. Tais constatações justificam perfeitamente a tese de que o LLM só deve gerar grafos de progressão, delegando à engine o cálculo final da geometria.

### Adventures in Level Design: Generating Missions and Spaces for Action Adventure Games
* **Relevância:** Alta
* **Classificação de Uso:** Contexto Teórico
* **Justificativa:** O artigo aborda a diferença crucial entre missões/progressão lógica e o espaço físico, fundamentando a separação de responsabilidades do projeto. Esse conceito valida a arquitetura híbrida do addon, onde o LLM atua como arquiteto/lógica para conceber a progressão, enquanto o Godot opera como engenheiro/geometria para instanciar e validar a estrutura física.

### Tanagra: A Mixed-Initiative Level Design Tool
* **Relevância:** Alta
* **Classificação de Uso:** Metodologia
* **Justificativa:** Ao focar no controle e restrições em Level Design procedural, o estudo justifica a necessidade de balizas matemáticas e espaciais rígidas durante a geração. Isso se conecta diretamente à implementação do addon no Godot, cujas restrições geométricas operadas pelo motor (engenheiro/geometria) limitam e validam as decisões abstratas do modelo de linguagem (LLM = arquiteto/lógica).

### Procedural Generation of Dungeons
* **Relevância:** Alta
* **Classificação de Uso:** Referência Fundamental
* **Justificativa:** O trabalho fornece forte embasamento sobre a geração de níveis e organização estrutural de dungeons, essencial para compreender a viabilidade de espaços de jogo. Tais princípios norteiam a arquitetura híbrida, embasando como o validador no Godot (engenheiro/geometria) interpreta e estrutura de forma coerente a organização idealizada pelo LLM (arquiteto/lógica).

### Procedural Content Generation in Games
* **Relevância:** Alta
* **Classificação de Uso:** Referência Fundamental
* **Justificativa:** Sendo a base geral para PCG, métodos construtivos e geração de níveis, o livro fornece as definições teóricas primárias do projeto. Os conceitos construtivos apresentados sustentam a arquitetura híbrida do addon, legitimando o workflow onde o LLM (arquiteto/lógica) projeta o grafo abstrato e o Godot (engenheiro/geometria) garante sua funcionalidade no espaço 3D.

### Designing Procedurally Generated Levels
* **Relevância:** Alta
* **Classificação de Uso:** Sustentação/Justificativa de Resultados
* **Justificativa:** O artigo explora a geração através de grafos de ações/progressão e restrições de gameplay, métodos ideais para definir a jogabilidade antes da topologia física. Isso corrobora perfeitamente a premissa da arquitetura híbrida: o LLM (arquiteto/lógica) é restrito à criação do grafo de ações, delegando ao Godot (engenheiro/geometria) a verificação de restrições de colisão e volume.
