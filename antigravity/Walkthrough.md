# Roteiro Geral e Walkthrough do Projeto (Histórico de Modificações e Guia Multiagente)

> **Objetivo deste Documento:** Centralizar o contexto completo, o histórico cronológico detalhado de alterações, as decisões estruturais e as diretrizes operacionais do Trabalho de Conclusão de Curso (TCC). Este documento foi concebido para fornecer síncrese imediata a diferentes agentes do ambiente Antigravity operando em dispositivos distintos, viabilizando continuidade sem perda de contexto ou retrabalho.

---

## 1. Visão Geral do Projeto e Escopo do TCC

* **Título do Trabalho:** *Geração de Layouts de Fases 3D Assistida por Modelos de Linguagem de Grande Porte*
* **Autor:** Gustavo Rafael
* **Tema Principal:** Geração Procedural de Conteúdo (PCG), Modelos de Linguagem de Grande Porte (LLMs), Teoria dos Grafos, Geometria Computacional e Validação em Motores de Jogos (*Game Engines*).
* **Proposta Central do TCC:** Desenvolver uma arquitetura híbrida e neuro-simbólica para criação automatizada de fases tridimensionais (masmorras/ambientes modulares). O sistema divide as responsabilidades em dois níveis:
  1. **Nível Semântico/Lógico (LLM):** O modelo atua como planejador de alto nível, gerando o grafo de progressão da fase (salas, conexões, chaves, fechaduras e objetivos) serializado em JSON.
  2. **Nível Geométrico/Físico (Engine - Godot):** Um algoritmo determinístico instancia os módulos 3D no espaço euclidiano contínuo, resolve o layout, realiza detecção de colisões volumétricas, gera a Malha de Navegação (NavMesh) e valida a conectividade física e a solvabilidade lógica da fase.
* **Justificativa Central da Pesquisa:** LLMs apresentam notável capacidade semântica e lógica em texto, mas sofrem de **alucinação espacial** e inconsistência métrica severa quando solicitados a produzir diretamente coordenadas 3D contínuas. A arquitetura híbrida resolve esse problema delegando a geometria a métodos formais e determinísticos.
* **Diretriz de Escopo Inviolável (Orientador):**
  > [!IMPORTANT]
  > O capítulo de **Fundamentação Teórica** deve ser estritamente conceitual e agnóstico de ferramentas de implementação. É expressamente proibido citar nele nomes de tecnologias específicas do projeto (Godot, GDScript, C#, NavigationRegion3D, addon) ou metáforas metodológicas da arquitetura prática (como "LLM-Arquiteto" e "Engine-Engenheiro"). Esses detalhes pertencem exclusivamente ao capítulo de **Metodologia**.

---

## 2. Linha do Tempo e Evolução Cronológica das Modificações

### Fase 0: Diagnóstico Inicial e Parecer do Orientador
* **Arquivo Original:** `fundamentacao_teorica.tex`
* **Diagnóstico:** O orientador apontou que o texto original antecipava prematuramente a metodologia da pesquisa (mencionava nós do Godot, código GDScript e detalhes de implementação), além de apresentar imprecisões conceituais (como o uso indevido da dicotomia "topologia vs. topografia" e justificativas frágeis para as limitações espaciais dos LLMs).
* **Documentos de Referência do Orientador:**
  - `Guia_Revisao_FundamentacaoTeorica_GustavoRafael.docx` (e `docx_extracted.txt`): Guia formal com tópicos de reestruturação.
  - `Fundamentacao_Teorica_Gustavo_Rafael_REVISADA_COMENTADA.pdf`: PDF com comentários pontuais do orientador.

---

### Fase 1 (29/09/2026): Primeira Reestruturação e Limpeza de Metodologia
* **Arquivo Criado:** `fundamentacao_revisada.tex`
* **Ações Executadas:**
  - Identificada a classe LaTeX do projeto: `abntex2` no modo `article` (modelo derivado do SIC). Ajustada a hierarquia para usar `\section` (seção principal) e `\subsection`/`\subsubsection` (subseções), eliminando `\chapter`.
  - Expurgação de termos de implementação (Godot, GDScript, NavigationRegion3D, etc.).
  - Distinção teórica entre *missão* (organização lógica) e *espaço* (organização física), alicerçada em Dormans (2010).
  - Formalização matemática inicial de grafos $G=(V, E)$ (caminhos, ciclos, aciclicidade, conectividade).
  - Decomposição das dimensões de validação: geométrica, navegabilidade, pathfinding, lógica e solvabilidade.
  - Registro de documentação: Criado `Resumo_Alteracoes_29_09_2026.md` e atualizado `Revisao_Literatura_TCC.md`.

---

### Fase 2 (19/10/2026): Reformulação Completa sob Convenção de Versões
* **Arquivos Criados:** `fundamentacao_19_10.tex` e `fundamentação_19_10.tex` (sincronizados byte a byte).
* **Motivação:** O usuário solicitou refazer integralmente a fundamentação para aprofundar 5 eixos teóricos centrais estabelecidos pelo orientador, sem qualquer menção a métodos do projeto:
  1. O que é Geração Procedural de Conteúdo (PCG) e de Fases;
  2. O que é PCG via Aprendizado de Máquina (PCGML);
  3. O que são Modelos de Linguagem de Grande Porte (LLMs);
  4. O que é Level Design;
  5. O que é o problema de alucinação espacial das LLMs.
* **Regra de Nomenclatura Estabelecida:** A partir desta data, as revisões da fundamentação devem ser salvas no formato `fundamentacao_DD_MM.tex` (mantendo cópia idêntica `fundamentação_DD_MM.tex`) para preservar o versionamento histórico.

---

### Fase 3 (19/10/2026 - 20/10/2026): Auditoria de Citações e Alinhamento Bibliográfico
* **Arquivos Auditados:** `fundamentacao_19_10.tex`, `referencias.bib` e pasta `Referências`.
* **Decisões e Ajustes:**
  - Padronização mandatória: Uso exclusivo do comando `\cite{...}` (proibido o uso de `\textcite{...}` que quebrava o padrão impessoal da ABNT).
  - Auditoria profunda cruzando cada citação do texto com os PDFs originais da pasta `Referências`.
  - Elaboração e aprovação do plano `plan_revisao_citacoes.md` adotando a Abordagem 1 (sustentação rigorosa com as referências existentes).

---

### Fase 4 (20/10/2026): Incorporação da Revisão 2 do Claude e Fontes Canônicas
* **Documento Base Recebido:** `Revisao_2_FundamentacaoTeorica_20_10_2026.md` (revisão externa do Claude contendo correções de rigor teórico, sugestões de autores seminais e complementação de lacunas conceituais).
* **Plano de Execução Aprovado:** `plan_revisao_claude.md`.
* **Implementações Concluídas:**
  1. **Atualização da Bibliografia (`referencias.bib`):**
     - Corrigida a chave genérica `@inproceedings{inproceedings,` para `@inproceedings{linden2013designing,` (artigo seminal de van der Linden et al., 2013).
     - Adicionadas 19 novas referências canônicas fundamentais: Totten (2014), Togelius et al. (2011), Smith & Whitehead (2010), Smith & Mateas (2011), Karth & Smith (2017), Khalifa et al. (2020), Vaswani et al. (2017), Brown et al. (2020), Bengio et al. (1994), Cohn & Renz (2008), Harnad (1990), Gibson (1979), Cormen et al. (2009), Ericson (2004), Russell & Norvig (2021), Hart et al. (1968), Snook (2000), Garcez & Lamb (2023) e Liapis et al. (2013).
  2. **Criação da Pasta `Novas Referencias`:**
     - Download automatizado de 7 artigos em acesso aberto (PDFs íntegros): Vaswani et al. (2017), Brown et al. (2020), Khalifa et al. (2020), Karth & Smith (2017), Togelius et al. (2011), Liapis et al. (2013) e Garcez & Lamb (2023).
     - Criação do documento `README_Referencias.md` com fichamento e links para os livros clássicos e artigos sob consulta.
  3. **Geração dos Arquivos Definitivos da Versão 20/10:**
     - Criados `fundamentacao_20_10.tex` e `fundamentação_20_10.tex` (idênticos byte a byte, totalizando ~76,8 KB e cobrindo todas as 8 seções temáticas).
  4. **Atualização de `main.tex`:**
     - O comando `\include{fundamentacao_20_10}` foi inserido no final de `main.tex` (após as considerações finais), preservando exatamente a ordem solicitada pelo usuário para testes no template provisório.
  5. **Verificação e Compilação:**
     - Executados `biber main` e `pdflatex main.tex`. Todas as 47 chaves de citação foram resolvidas perfeitamente, sem warnings de referências indefinidas, gerando `main.pdf` com 36 páginas.

---

### Fase 5 (23/10/2026): Elaboração e Validação do Capítulo de Trabalhos Relacionados
* **Documentos de Referência:** TCCs da pasta `Exemplos/` (`TCC2 Luciano v03_revisado.pdf` e `TCC_Endi_Final.pdf`), ambos orientados pelo Prof. Wagner Ferreira de Barros.
* **Arquivo Criado:** `trabalhos_relacionados.tex` (214 linhas).
* **Estrutura Implementada:**
  1. *Abertura Taxonômica:* 4 famílias de métodos baseadas no paradigma de geração e validação espacial (2D/simbólico, código/render offline, otimizadores/restrições, engines/multiagente).
  2. *Método Dialético:* Aplicação rigorosa da tríade *Mecanismo → Mérito → Ponto de Ruptura* para cada um dos 11 sistemas analisados (Todd et al., Word2World, Narrative-to-Scene, SceneCraft, Code-as-Room, RoomPlanner, Constraint GLDL, Database-Driven Framework, Her et al., UnrealLLM, Regmi/Re).
  3. *Diagnósticos Empíricos e Indústria:* Feng et al. (2026) (*"Layout as Language: Semantic YES, Physical NO"*) e Bandeali (2026) (rejeição de ferramentas autônomas "caixa-preta" e demanda por iniciativa mista com salvaguardas determinísticas na engine).
  4. *Quadro Comparativo do Estado da Arte:* Tabela comparativa matricial cruzando todos os 11 sistemas frente a 7 critérios técnicos essenciais.
  5. *Demonstração da Tríplice Lacuna e Posicionamento da Proposta:* Fechamento formal conectando a literatura diretamente à Metodologia da proposta neuro-simbólica (LLM no planejamento JSON + Godot 4 na geometria, física, NavMesh e solvabilidade).
* **Compilação e Verificação:**
  - `modelo_latex_TCC/main.tex` atualizado com `\include{trabalhos_relacionados}`.
  - Compilação limpa com Biber e pdfLaTeX sem warnings de referências indefinidas, gerando `main.pdf` com 48 páginas.

---

### Fase 6 (27/10/2026): Reescrita de Trabalhos Relacionados no Estilo de `TCC_Endi_Final.pdf` e Auditoria de Citações
* **Motivação:** Adequar o capítulo `trabalhos_relacionados.tex` estritamente à estrutura e ao estilo de escrita em prosa contínua dos TCCs de exemplo orientados pelo Prof. Wagner Ferreira de Barros (`TCC_Endi_Final.pdf` e `TCC2 Luciano v03_revisado.pdf`), mantendo aderência integral aos conceitos de `fundamentacao_20_10.tex` e eliminando imprecisões bibliográficas.
* **Alterações Executadas em `trabalhos_relacionados.tex`:**
  1. *Estrutura espelhada em `TCC_Endi_Final.pdf`:* Abertura direta com classificação dos trabalhos em três grandes categorias em lista (`itemize`), seguida por seções e subseções temáticas em prosa corrida (substituindo os blocos artificiais em tópicos "Mecanismo / Mérito / Ponto de Ruptura" e jargões não canônicos).
  2. *Alinhamento com a Fundamentação Teórica:* Inclusão e conexão direta com os trabalhos seminais de gramáticas de missão e espaço (Dormans, 2010; van der Linden et al., 2013, 2014) e iniciativa mista (Smith et al., 2010; Liapis et al., 2013; Lai et al., 2020; Walton et al., 2022), seguidos pelas abordagens 2D com LLMs (Todd et al., 2023; Nasir et al., 2024; Chen & Jhala, 2025) e pelas três vertentes 3D com LLMs (cenas/cômodos para modelagem e renderização; otimização FLP e bancos de dados; controle de ferramentas procedurais e motores de jogos).
  3. *Auditoria rigorosa dos PDFs das pastas `Referências` e `Novas Referencias`:* Correção de todos os mecanismos descritos conforme os artigos originais — pipeline de 4 passos de *Dwarf Quest* (atribuição de espaço de nós para salas e arestas para corredores, planarização e limitação de grau a 4 portas via inserção de nós intermediários de sala, resolução em grade ortogonal 2D e compressão de corredores) em van der Linden et al. (2013); verificação de alcançabilidade mútua, caminhos mínimos, simulação de exploração via *flood-fill* e evolução via *FI-2pop GA* com busca por novidade em *Sentient Sketchbook* (Liapis et al., 2013); ajuste fino de GPT-2/GPT-3 em *Sokoban* (Todd et al., 2023); reparo determinístico de linhas/células e busca $A^*$ em *Word2World* (Nasir et al., 2024); Autômatos Celulares e regras simbólicas sobre *GameTileNet* em *Narrative-to-Scene* (Chen & Jhala, 2025); restrições de colisão e alcance $A^*$ em *RoomPlanner* (Sun et al., 2025); formulação de penalidades flexíveis via Têmpera Simulada (SA), testes de estabilidade com GPT-4o-mini (82,36% em definições e 25,38% em restrições relacionais) e simulação em Unity3D em Xu & Verbrugge (2025a, GLDL); criação *offline* de três bancos de dados JSON, empilhamento via busca em profundidade gulosa (*greedy DFS*) e reparo em duas fases (*flood-fill* + tentativa de reposicionamento e remoção por agente NavMesh $A^*$) em Xu & Verbrugge (2025b); crítica textual de parâmetros de API em Her et al. (2025); tradução para DSL em JSON, *blueprints* PCG e *splines* via *SketchAgent* em *UnrealLLM* (Tang et al., 2025); revisão de escopo e autoetnografia em Bandeali (2026); e remoção de `re2026integration` (sinalizada em vermelho pelo orientador).
  4. *Síntese Comparativa e Posicionamento:* Tabela comparativa (`\scriptsize` com colunas `p{...}` quebradas automaticamente para legibilidade integral na página A4) fiel aos artigos e fechamento nos moldes de `TCC2 Luciano v03_revisado.pdf`, posicionando a proposta deste TCC.

---

### Fase 7 (09/11/2026): Reescrita da Introdução e Reestruturação de `main.tex`
* **Documentos de Referência:** Versão final revisada do resumo expandido do SIC 2026 (`SIC/Modelo Overleaf_Resumo_Expandido_SIC2026/SIC2026_Ciencias_Exatas_e_da_Terra_identificado.tex`) e TCCs da pasta `Exemplos/` (`TCC2 Luciano v03_revisado.pdf` e `TCC_Endi_Final.pdf`).
* **Alterações Executadas em `modelo_latex_TCC/introducao.tex`:**
  1. *Fusão estrutural dos dois exemplos (`TCC2 Luciano` + `TCC_Endi_Final`):* Organização do capítulo em preâmbulo contextual (4 parágrafos), `\subsection{Motivação}`, `\subsection{Contextualização do Problema}`, `\subsection{Definição do Problema}` (enunciado central da pergunta de pesquisa + lista numerada `enumerate` com 5 questões específicas de pesquisa), `\subsection{Objetivos}` (`\subsubsection{Objetivo Geral}` e `\subsubsection{Objetivos Específicos}` em lista `itemize`) e `\subsection{Organização do Trabalho}`.
  2. *Incorporação integral das revisões do SIC 2026:* Esclarecimento histórico de que a PCGML antecede os LLMs; substituição de afirmações absolutas pela formulação precisa das três classes de restrições verificadas (*progressão lógica possível com chaves e portas via busca de estados*, *ausência de sobreposições geométricas proibidas* e *rota fisicamente navegável entre início e objetivo via NavMesh*); especificação do grafo de progressão serializado em JSON; delimitação do recorte (protótipo de masmorra modular de um pavimento na *engine* Godot, em formato de *addon*, com salas pré-fabricadas de dimensões e conectores conhecidos); e alinhamento dos objetivos ao delineamento experimental (Grupo Controle vs. Grupo Experimental avaliando a arquitetura híbrida como um todo).
* **Alterações Executadas em `modelo_latex_TCC/main.tex`:**
  - Remoção dos artefatos e capítulos obsoletos herdados do modelo base do SIC (`\include{materiais_e_metodos}`, `\include{metodologia_experimental}` e `\include{consideracoes_finais}`, bem como versões antigas comentadas da fundamentação).
  - Atualização do Resumo e Abstract de `main.tex` para refletir o escopo revisado.
  - Estruturação dos capítulos de `main.tex` na ordem canônica do TCC:
    1. **Introdução** (`\include{introducao}`)
    2. **Fundamentação Teórica** (`\include{fundamentacao_20_10}`)
    3. **Trabalhos Relacionados** (`\include{trabalhos_relacionados}`)

---

### Fase 8 (16/11/2026): Implementação da Revisão do Orientador, Diagramas TikZ e Auditoria Completa
* **Documentos de Referência:** Relatório de Auditoria e Revisão do Orientador (`antigravity/Revisao_Orientador_TCC_16_11_2026.md`) e Plano de Implementação (`antigravity/brain/.../implementation_plan.md`).
* **Eixos de Correção Executados:**
  1. *Expurgo do Viés de "Chaves e Portas":*
     - Substituição do dogma restritivo de *lock-and-key* pelo foco real da pesquisa: **geração e validação de um grafo lógico de progressão coerente e sem contradições** (conectividade, presença de início/objetivo, aciclicidade do DAG de dependências $G_{\text{dep}}$ e alcançabilidade sem estrangulamentos).
     - Adoção sistemática do termo **"conectores de passagem"** para as aberturas de encaixe modular entre salas 3D.
  2. *Correção das Citações Narrativas (`biblatex-abnt`):*
     - Eliminação de `Autor (AUTOR, ANO)` e de `em (AUTOR, ANO)`.
     - Adoção de `\textcite{chave}` para citações narrativas no corpo do texto (e.g., `\textcite{dormans2010}` $\to$ Dormans (2010)).
     - Adoção de `Autor \cite*{chave}` para as 16 linhas da Tabela 1 e referências com sufixos desambiguadores (e.g., `van der Linden et al. \cite*{linden2013designing, linden2014dungeons}`, `Xu e Verbrugge \cite*{xu2025constraint}`).
  3. *Correções Factuais e Limpeza de Citation Dumping na Fundamentação Teórica:*
     - Criação da versão versionada `fundamentacao_16_11.tex` e sua réplica idêntica `fundamentação_16_11.tex` (mantendo `fundamentacao_20_10.tex` intacto).
     - Remoção da atribuição falsa de *Matterport3D* ao *RoomPlanner* (Sun et al. não utiliza Matterport3D; otimiza arranjo de cômodos via colisão e $A^*$).
     - Correção da descrição do *SceneCraft* (grafo/blueprint, restrições numéricas em Python e refinamento visual por VLM).
     - Correção da citação de *Code-as-Room* e de Feng et al. (2026).
     - Limpeza rigorosa de citações não sustentadas (remoção de citações indevidas a Xu & Verbrugge em PSO/MCTS e feedback loop, Her et al. em data scarcity, Brown et al. em instruction tuning, Sun et al. em conectores modulares, volumes delimitadores e NavMesh).
  4. *Refinamentos Conceituais e Eliminação do Overfull \hbox:*
     - Rigor em dígrafos: caminho simples vs. passeio, conectividade fraca e assimetria de alcançabilidade.
     - Ajuste da função de aptidão em PCG baseada em busca para valor (ou vetor de valores) numérico.
     - Separação ontológica entre modelo conceitual abstrato e camada sintática/notacional (DSL/código).
     - Eliminação do `Overfull \hbox` de 2.94pt em L23 substituindo travessões por parênteses.
  5. *Inclusão de Diagramas Conceituais em TikZ:*
     - **Figura 1:** Dualidade entre Grafo Lógico de Progressão e Realização Espacial Modular 3D (Seção 2.1.3).
     - **Figura 2:** Acoplamento modular com AABBs, conectores de passagem e vetores normais opostos/colineares (Seção 2.6.3).
     - **Figura 3:** Tríplice dissociação entre validade geométrica, navegabilidade física na NavMesh e solvabilidade lógica (Seção 2.8.5).
  6. *Ajustes Estruturais em `main.tex`:*
     - Inclusão do pacote `\usepackage{csquotes}` antes do `biblatex` (eliminando o warning de compilação).
     - Inclusão de `\usepackage{tikz}` e bibliotecas `arrows.meta`, `positioning`, `shapes.geometric`, `calc`.
     - Ajuste do título (`\textit{LAYOUTS}`) e do Resumo (`frente à geração direta de coordenadas pelo LLM`).
     - Migração de `\include` para `\input` (`\input{introducao}`, `\input{fundamentacao_16_11}`, `\input{trabalhos_relacionados}`), eliminando páginas órfãs em branco.
     - Padronização de referências a "capítulo" para "seção".
     - Ajuste do título de referências para `\printbibliography[title={Referências}]`.
  7. *Correção da Base Bibliográfica (`referencias.bib`):*
     - Remoção de editor em `tang2025unrealllm`, correção de `IEEE` em `walton2020evaluating` e `Gallotta_2024` (com `volume` e `number`), remoção de `number={1}` em `maleki2024procedural` e `khalifa2020pcgrl`, correção de partículas de sobrenome em `araujo2018geracao` e `garcez2023neurosymbolic`, adição de páginas em `xu2025constraint`, remoção de entradas órfãs (`re2026integration`, `vieira2024metodologia`) e preenchimento de `publisher`/`address` para eliminar `[S.l.]`.
  8. *Limpeza Preventiva dos Rascunhos Desvinculados:*
     - Correções gramaticais, tipográficas e conceituais em `materiais_e_metodos.tex`, `metodologia_experimental.tex` e `consideracoes_finais.tex`.

---

## 3. Síntese do Conteúdo da Fundamentação Teórica (`fundamentacao_20_10.tex`)

Abaixo sintetiza-se a cobertura conceitual consolidada em cada subseção (Seção 2 em `main.tex`):

* **2.1 Fases de Jogos, *Level Design* e *Layouts* 3D:**
  - Definição formal de fase como contêiner estruturado e arena interativa governada pelo sistema de regras do jogo.
  - *Level Design* conceituado através de Totten (2014) como arquitetura de experiência, fluxo de navegação e regulação de ritmo (*pacing*).
  - Decomposição do layout em salas, corredores, conectores, instalações (*props*) e entidades dinâmicas.
  - Distinção teórica estrita entre **missão** (organização lógica de objetivos) e **espaço** (realização métrica e física), com base em Dormans (2010) e van der Linden et al. (2013).
* **2.2 Geração Procedural de Conteúdo (PCG):**
  - Definição, escopo (conteúdos cosméticos vs. funcionais) e motivações (redução de custos, rejogabilidade, adaptabilidade).
  - Propriedades técnicas: reprodutibilidade (PRNGs), expressividade (*expressive range* por Smith & Whitehead, 2010) e a tensão entre controle e diversidade.
  - Taxonomia canônica (Togelius et al., 2011): métodos construtivos, baseados em busca (*fitness function*) e baseados em restrições/solucionadores (WFC por Karth & Smith, 2017; ASP por Smith & Mateas, 2011).
  - Técnicas de geração de níveis: particionamento espacial (BSP/octrees), agentes escavadores em escala local, autômatos celulares e gramáticas de grafos/formas.
* **2.3 PCGML e Modelos de Linguagem de Grande Porte (LLMs):**
  - Definição formal de PCGML estrito (Summerville et al., 2018) via treinamento supervisionado sobre *corpora* de jogos prévios.
  - Caracterização de PCGRL (Khalifa et al., 2020) operando via interação dinâmica agente-ambiente e otimização de recompensas cumulativas.
  - Distinção conceitual: *zero-shot/few-shot prompting* opera via aprendizado em contexto (ICL) e transferência transdomínio (Brown et al., 2020); *fine-tuning* sobre fases configura PCGML estrito.
  - Evolução de PLN: gargalos de RNNs/LSTMs e esvanecimento de gradientes (Bengio et al., 1994) superados pela arquitetura Transformer e mecanismo de autoatenção (*self-attention*, Vaswani et al., 2017).
  - Taxonomia dos 4 papéis dos LLMs em PCG: gerador textual direto, planejador lógico de alto nível, sintetizador de código/parâmetros e assistente em iniciativa mista.
  - Separação entre modelo conceitual (grafo, triplas, DSL) e formato de serialização (JSON com esquemas formais; contextualização da sintaxe CSS de SceneTeller).
* **2.4 Raciocínio e Ancoragem Espacial em LLMs:**
  - Raciocínio espacial qualitativo (Cohn & Renz, 2008) vs. raciocínio métrico contínuo.
  - Distinção formal entre **direção** (relação relativa entre entidades) e **orientação** (*pose* intrínseca e vetor frontal).
  - O problema da ancoragem semântica (*symbol grounding problem*, Harnad, 1990).
  - Definição ecológica de *affordance* (Gibson, 1979) como possibilidades reais de ação do ambiente, desvinculada de mera coocorrência estatística.
  - Alucinação espacial formalizada: ausência de modelo físico na autoatenção, severa compressão de dados e deriva autorregressiva cumulativa de erros métricos.
  - Exemplos empíricos da literatura: *SceneCraft* (Hu et al., 2024), *RoomPlanner* (Sun et al., 2024) e *Code-as-Room* (Yang et al., 2026).
  - Quatro tipos de falhas geométricas: colisões/sobreposições (*clipping*), violações de limites/suporte (*out-of-bounds* e flutuação), erros de alinhamento e obstrução de circulação.
* **2.5 Representação Lógica de Fases por Grafos:**
  - Formalismo matemático de dígrafos $G=(V, E)$ (Cormen et al., 2009): graus de entrada/saída, caminhos orientados e conectividade forte.
  - Grafos de espaço (topológicos) vs. grafos de missão/ações; agrupamento de ações colocalizadas (*co-located actions*, Dormans, 2010; van der Linden et al., 2013).
  - Mecanismo de chave e fechadura (*lock-and-key puzzle*).
  - Formalização do subgrafo de dependências $G_{\text{dep}}$ como um Grafo Acíclico Direcionado (DAG) obrigatório com ordenação topológica $\tau(u) < \tau(v)$ para prevenir *deadlocks* lógicos, contrastando com o grafo de circulação física que admite ciclos controlados (*backtracking*, atalhos). Definição do espaço de estados $S$.
  - Mapeamento um-para-muitos e planarização com nós intermediários (van der Linden et al., 2013).
* **2.6 Representação de *Layouts* Espaciais 3D:**
  - Modelagem modular: grades/voxels, chunks, salas pré-construídas e *prefabs* 3D com conectores/portas (posição local, dimensão e vetor normal de orientação).
  - Relações afins no espaço contínuo $\mathbb{R}^3$: decomposição estrita entre *pose* (translação $\mathbf{p}_i$ e rotação $\mathbf{R}_i$ com guinada $\theta_i$), dimensões nominais $(w_i, l_i, h_i)$ e fator de escala $\mathbf{s}_i$.
  - Volumes delimitadores (Ericson, 2004): Caixa Delimitadora Alinhada aos Eixos (AABB) vs. Caixa Delimitadora Orientada (OBB).
  - Restrições geométricas rígidas: não sobreposição volumétrica ($V_{\text{overlap}} = 0$), contenção perimetral, alinhamento de portais e desobstrução (*clearance*) contra adensamento indevido (*overcrowding/clutter*).
* **2.7 Arquiteturas Híbridas e Geração Baseada em Restrições:**
  - Integração neuro-simbólica (Garcez & Lamb, 2023): sinergia entre raciocínio de alto nível (neural/LLM) e garantias determinísticas de restrições (simbólico/algorítmico).
  - Sistemas de iniciativa mista (*Mixed-Initiative PCG*): colaboração humano-IA exemplificada por *Tanagra* (Smith et al., 2010) e *Sentient Sketchbook* (Liapis et al., 2013).
  - Problemas de Satisfação de Restrições (CSP, Russell & Norvig, 2021): variáveis, domínios, restrições e consistência de arcos.
  - Restrições rígidas (*hard*) vs. restrições flexíveis (*soft*) e analogia com o Problema de Layout de Instalações (FLP).
  - Quatro estratégias de qualidade: rejeição integral (*generate-and-test*), *backtracking* construtivo, reparo pós-geração e laço fechado de refinamento (*feedback loop*).
* **2.8 Validade, Navegabilidade e Solvabilidade de Fases:**
  - Decomposição rigorosa das camadas de avaliação funcional:
    1. **Validade Lógica:** Aciclicidade do grafo causal e conectividade abstrata.
    2. **Validade Geométrica:** Não interseção de sólidos e contenção espacial via estruturas de consulta (AABBs, octrees, raycasting).
    3. **Navegabilidade:** Superfícies contínuas transitáveis considerando parâmetros cinemáticos do agente; Malhas de Navegação (NavMesh, Snook, 2000) baseadas em polígonos convexos e busca no grafo dual de adjacência com suavização (*string pulling*).
    4. **Pathfinding:** Algoritmo $A^*$ (Hart et al., 1968) com heurística admissível assegurando caminho de custo ótimo.
    5. **Solvabilidade:** Atingibilidade conjunta no espaço de estados e no espaço geométrico.
  - As 3 dissociações teóricas fundamentais: (i) validade geométrica sem navegabilidade; (ii) navegabilidade física sem solvabilidade dinâmica (chave trancada atrás da porta); (iii) validade lógica abstrata sem solvabilidade espacial (obstáculo físico bloqueando a chave).
  - **2.8.6 Síntese Conceitual:** Consolidação do arcabouço teórico como ponte para as decisões de modelagem e arquitetura a serem formalizadas na Metodologia.

---

## 4. Mapa Estrutural do Repositório e Arquivos Principais

```text
PTCC/
│
├── modelo_latex_TCC/
│   ├── main.tex                       # Documento mestre do TCC (1- Introdução, 2- Fundamentação, 3- Relacionados)
│   ├── referencias.bib                # Base BibTeX unificada e validada (48 entradas)
│   ├── introducao.tex                 # Capítulo 1: Introdução completa do TCC
│   ├── fundamentacao_20_10.tex        # Capítulo 2: Versão ATUAL E DEFINITIVA da Fundamentação Teórica
│   ├── fundamentação_20_10.tex        # Cópia idêntica byte a byte (compatibilidade de acentuação)
│   ├── trabalhos_relacionados.tex     # Capítulo 3: Trabalhos Relacionados
│   ├── fundamentacao_19_10.tex        # Versão intermediária anterior (19/10)
│   ├── fundamentacao_revisada.tex     # Primeira versão revisada pós-parecer do orientador (29/09)
│   ├── fundamentacao_teorica.tex      # Versão legada inicial (rascunho original)
│   ├── materiais_e_metodos.tex        # Arquivo legado do template base do SIC (desvinculado de main.tex)
│   ├── metodologia_experimental.tex   # Arquivo legado do template base do SIC (desvinculado de main.tex)
│   ├── consideracoes_finais.tex       # Arquivo legado do template base do SIC (desvinculado de main.tex)
│   └── main.pdf                       # PDF compilado com sucesso
│
├── antigravity/                       # Documentação técnica, relatórios e guias de contexto
│   ├── Walkthrough.md                 # Este documento mestre (guia multiagente e histórico)
│   ├── Walkthrough_Revisao_20_10_2026.md # Cópia datada deste roteiro geral
│   ├── Revisao_Literatura_TCC.md      # Fichamento analítico dos artigos da bibliografia
│   ├── Revisao_2_FundamentacaoTeorica_20_10_2026.md # Revisão crítica externa do Claude
│   ├── Resumo_Alteracoes_29_09_2026.md # Relatório da primeira refatoração
│   ├── docx_extracted.txt             # Extração em texto puro do Guia do Orientador
│   └── Guia_Revisao_FundamentacaoTeorica_GustavoRafael.docx # Guia formal do orientador
│
├── Referências/                       # Pasta original com 28 PDFs da bibliografia inicial
│
└── Novas Referencias/                 # Pasta criada para referências canônicas adicionadas
    ├── README_Referencias.md          # Fichamento com DOIs, resumos e links de livros/artigos
    ├── Vaswani_et_al_2017_Attention_Is_All_You_Need.pdf
    ├── Brown_et_al_2020_Language_Models_Are_Few_Shot_Learners.pdf
    ├── Khalifa_et_al_2020_PCGRL.pdf
    ├── Karth_Smith_2017_WaveFunctionCollapse.pdf
    ├── Togelius_et_al_2011_Search_Based_PCG.pdf
    ├── Liapis_et_al_2013_Sentient_Sketchbook.pdf
    └── Garcez_Lamb_2023_Neurosymbolic_AI_3rd_Wave.pdf
```

---

## 5. Diretrizes Operacionais para Qualquer Novo Agente Antigravity

Qualquer agente de IA que assumir a continuidade deste projeto em qualquer dispositivo DEVE seguir estritamente as regras abaixo:

1. **Regra de Citações no LaTeX (`biblatex-abnt`):**
   - **Citações Narrativas no Corpo do Texto:** Utilize `\textcite{chave}` (e.g., `\textcite{dormans2010}` imprime `Dormans (2010)`). **NUNCA** escreva manualmente `Dormans \cite{dormans2010}` pois isso gera a anomalia `Dormans (DORMANS, 2010)`.
   - **Citações em Tabelas e Casos Especiais:** Utilize `Autor \cite*{chave}` (e.g., `Dormans \cite*{dormans2010}`, `van der Linden et al. \cite*{linden2013designing, linden2014dungeons}`, `Xu e Verbrugge \cite*{xu2025constraint}`). No `biblatex-abnt`, o comando `\cite*` imprime os parênteses e o ano com letra desambiguadora `(2025b)`, enquanto `\citeyear` gera parênteses duplos `((2025))` e perde a letra.
   - **Citações Parentéticas ao Final de Períodos:** Utilize `\cite{chave}` (e.g., `\cite{tanagra, pcgbook}`).
2. **Sincronização de Chaves BibTeX:**
   - Antes de adicionar qualquer citação nova no texto LaTeX, confirme que a chave correspondente existe em `referencias.bib`.
   - A chave para o artigo de van der Linden et al. (2013) é estritamente `linden2013designing`.
3. **Versionamento e Nomenclatura:**
   - Se novas alterações forem solicitadas na fundamentação teórica, salve em um novo arquivo com a data atual: `fundamentacao_DD_MM.tex` e mantenha uma cópia idêntica byte a byte nomeada `fundamentação_DD_MM.tex`.
   - Nunca sobrescreva ou apague versões de datas anteriores (`fundamentacao_teorica.tex`, `fundamentacao_revisada.tex`, `fundamentacao_19_10.tex`, `fundamentacao_20_10.tex`), preservando o histórico de controle de versões.
4. **Estrutura e Ordem de Inclusão em `main.tex`:**
   - Utilizar `\input` em vez de `\include` para evitar quebras de página indesejadas no modo `article`:
     1. `\input{introducao}` (Seção 1 - Introdução)
     2. `\input{fundamentacao_16_11}` (Seção 2 - Fundamentação Teórica)
     3. `\input{trabalhos_relacionados}` (Seção 3 - Trabalhos Relacionados)
   - **IMPORTANTE:** Sempre manter `\clearpage` imediatamente antes de `\SingleSpacing\printbibliography[title={Referências}]`. Quando seções usam `\input`, ambientes flutuantes (como a Tabela 1 em `trabalhos_relacionados.tex`) podem ser diferidos para páginas subsequentes se não houver um `\clearpage`, o que faria a tabela flutuar para o meio das páginas de Referências bibliográficas.
5. **Agnosticismo Teórico vs. Metodologia:**
   - Em hipótese alguma reintroduza termos da engine (Godot, GDScript, C#, NavigationRegion3D, addon, arquiteto/engenheiro) nos arquivos de Fundamentação Teórica. Esses conceitos pertencem estritamente à Introdução (contextualização do escopo) e aos capítulos de **Metodologia** e **Experimentos**.
6. **Compilação do Documento:**
   - A sequência canônica de 4 passagens de compilação é:
     ```bash
     cd "modelo_latex_TCC"
     pdflatex -interaction=nonstopmode main.tex
     biber main
     pdflatex -interaction=nonstopmode main.tex
     pdflatex -interaction=nonstopmode main.tex
     ```

---

## 6. Próximos Passos do TCC (Roadmap Metodológico)

Com os Capítulos 1 a 3 (Introdução, Fundamentação Teórica e Trabalhos Relacionados) integralmente auditados, corrigidos e alinhados ao escopo do grafo lógico geral de progressão, a frente de trabalho prioritária consiste no desenvolvimento do **Capítulo 4 (Metodologia)**:

1. **Visão Geral da Arquitetura Híbrida (Diagrama do Pipeline):**
   - Fluxo completo: *Prompt em linguagem natural → Engenharia de Prompt / LLM → Grafo Lógico de Progressão em JSON → Validador Topológico e Lógico [com loop de retorno de erro ao LLM em caso de contradição] → Construtor Espacial Modular 3D no Godot → Verificador de Colisão (AABB) e Alinhamento de Conectores → Geração de NavMesh (`NavigationRegion3D`) e Verificação de Rotas ($A^*$) → Cena 3D Editável no Editor do Godot*.
2. **Especificação Formal do Grafo de Progressão e JSON Schema (Objetivo Específico 1):**
   - Estrutura formal de vértices (salas, papéis funcionais, metadados) e arestas (conectores, direcionalidade, pré-requisitos lógicos), com esquema JSON validável.
3. **Algoritmo de Validação Topológica e Lógica do Grafo (Objetivo Específico 2):**
   - Verificação determinística de invariantes: (i) unicidade de início e presença de objetivo; (ii) conectividade (sem salas órfãs); (iii) alcançabilidade do objetivo; (iv) aciclicidade e consistência do DAG de dependências ($G_{\text{dep}}$); (v) formatação do diagnóstico estruturado de erro para retroalimentação do LLM.
4. **Catálogo de Módulos 3D e Algoritmo de Construção Espacial (Objetivo Específico 3):**
   - Especificação de salas modulares pré-fabricadas na Godot (dimensões $w \times l \times h$, conectores de passagem e vetores normais).
   - Cálculo determinístico de pose $(\mathbf{p}_i, \theta_i)$ para alinhamento de conectores, inserção de corredores e verificação de AABBs contra sobreposição (*clipping*).
5. **Verificação Automatizada de Navegabilidade Física (Objetivo Específico 4):**
   - Geração de NavMesh via `NavigationRegion3D` e busca de caminhos via $A^*$ no `NavigationServer3D` entre início, salas intermediárias e objetivo.
6. **Delineamento Experimental e Grupo Controle (Objetivo Específico 6):**
   - Metodologia de comparação quantitativa entre Grupo Controle (LLM gerando estrutura + coordenadas diretamente) e Grupo Experimental (arquitetura híbrida proposta).
