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

## 3. Síntese do Conteúdo da Fundamentação Teórica (`fundamentacao_20_10.tex`)

Abaixo sintetiza-se a cobertura conceitual consolidada em cada subseção:

* **5.1 Fases de Jogos, *Level Design* e *Layouts* 3D:**
  - Definição formal de fase como contêiner estruturado e arena interativa governada pelo sistema de regras do jogo.
  - *Level Design* conceituado através de Totten (2014) como arquitetura de experiência, fluxo de navegação e regulação de ritmo (*pacing*).
  - Decomposição do layout em salas, corredores, conectores, instalações (*props*) e entidades dinâmicas.
  - Distinção teórica estrita entre **missão** (organização lógica de objetivos) e **espaço** (realização métrica e física), com base em Dormans (2010) e van der Linden et al. (2013).
* **5.2 Geração Procedural de Conteúdo (PCG):**
  - Definição, escopo (conteúdos cosméticos vs. funcionais) e motivações (redução de custos, rejogabilidade, adaptabilidade).
  - Propriedades técnicas: reprodutibilidade (PRNGs), expressividade (*expressive range* por Smith & Whitehead, 2010) e a tensão entre controle e diversidade.
  - Taxonomia canônica (Togelius et al., 2011): métodos construtivos, baseados em busca (*fitness function*) e baseados em restrições/solucionadores (WFC por Karth & Smith, 2017; ASP por Smith & Mateas, 2011).
  - Técnicas de geração de níveis: particionamento espacial (BSP/octrees), agentes escavadores em escala local, autômatos celulares e gramáticas de grafos/formas.
* **5.3 PCGML e Modelos de Linguagem de Grande Porte (LLMs):**
  - Definição formal de PCGML estrito (Summerville et al., 2018) via treinamento supervisionado sobre *corpora* de jogos prévios.
  - Caracterização de PCGRL (Khalifa et al., 2020) operando via interação dinâmica agente-ambiente e otimização de recompensas cumulativas.
  - Distinção conceitual: *zero-shot/few-shot prompting* opera via aprendizado em contexto (ICL) e transferência transdomínio (Brown et al., 2020); *fine-tuning* sobre fases configura PCGML estrito.
  - Evolução de PLN: gargalos de RNNs/LSTMs e esvanecimento de gradientes (Bengio et al., 1994) superados pela arquitetura Transformer e mecanismo de autoatenção (*self-attention*, Vaswani et al., 2017).
  - Taxonomia dos 4 papéis dos LLMs em PCG: gerador textual direto, planejador lógico de alto nível, sintetizador de código/parâmetros e assistente em iniciativa mista.
  - Separação entre modelo conceitual (grafo, triplas, DSL) e formato de serialização (JSON com esquemas formais; contextualização da sintaxe CSS de SceneTeller).
* **5.4 Raciocínio e Ancoragem Espacial em LLMs:**
  - Raciocínio espacial qualitativo (Cohn & Renz, 2008) vs. raciocínio métrico contínuo.
  - Distinção formal entre **direção** (relação relativa entre entidades) e **orientação** (*pose* intrínseca e vetor frontal).
  - O problema da ancoragem semântica (*symbol grounding problem*, Harnad, 1990).
  - Definição ecológica de *affordance* (Gibson, 1979) como possibilidades reais de ação do ambiente, desvinculada de mera coocorrência estatística.
  - Alucinação espacial formalizada: ausência de modelo físico na autoatenção, severa compressão de dados e deriva autorregressiva cumulativa de erros métricos.
  - Exemplos empíricos da literatura: *SceneCraft* (Hu et al., 2024), *RoomPlanner* (Sun et al., 2024) e *Code-as-Room* (Yang et al., 2026).
  - Quatro tipos de falhas geométricas: colisões/sobreposições (*clipping*), violações de limites/suporte (*out-of-bounds* e flutuação), erros de alinhamento e obstrução de circulação.
* **5.5 Representação Lógica de Fases por Grafos:**
  - Formalismo matemático de dígrafos $G=(V, E)$ (Cormen et al., 2009): graus de entrada/saída, caminhos orientados e conectividade forte.
  - Grafos de espaço (topológicos) vs. grafos de missão/ações; agrupamento de ações colocalizadas (*co-located actions*, Dormans, 2010; van der Linden et al., 2013).
  - Mecanismo de chave e fechadura (*lock-and-key puzzle*).
  - Formalização do subgrafo de dependências $G_{\text{dep}}$ como um Grafo Acíclico Direcionado (DAG) obrigatório com ordenação topológica $\tau(u) < \tau(v)$ para prevenir *deadlocks* lógicos, contrastando com o grafo de circulação física que admite ciclos controlados (*backtracking*, atalhos). Definição do espaço de estados $S$.
  - Mapeamento um-para-muitos e planarização com nós intermediários (van der Linden et al., 2013).
* **5.6 Representação de *Layouts* Espaciais 3D:**
  - Modelagem modular: grades/voxels, chunks, salas pré-construídas e *prefabs* 3D com conectores/portas (posição local, dimensão e vetor normal de orientação).
  - Relações afins no espaço contínuo $\mathbb{R}^3$: decomposição estrita entre *pose* (translação $\mathbf{p}_i$ e rotação $\mathbf{R}_i$ com guinada $\theta_i$), dimensões nominais $(w_i, l_i, h_i)$ e fator de escala $\mathbf{s}_i$.
  - Volumes delimitadores (Ericson, 2004): Caixa Delimitadora Alinhada aos Eixos (AABB) vs. Caixa Delimitadora Orientada (OBB).
  - Restrições geométricas rígidas: não sobreposição volumétrica ($V_{\text{overlap}} = 0$), contenção perimetral, alinhamento de portais e desobstrução (*clearance*) contra adensamento indevido (*overcrowding/clutter*).
* **5.7 Arquiteturas Híbridas e Geração Baseada em Restrições:**
  - Integração neuro-simbólica (Garcez & Lamb, 2023): sinergia entre raciocínio de alto nível (neural/LLM) e garantias determinísticas de restrições (simbólico/algorítmico).
  - Sistemas de iniciativa mista (*Mixed-Initiative PCG*): colaboração humano-IA exemplificada por *Tanagra* (Smith et al., 2010) e *Sentient Sketchbook* (Liapis et al., 2013).
  - Problemas de Satisfação de Restrições (CSP, Russell & Norvig, 2021): variáveis, domínios, restrições e consistência de arcos.
  - Restrições rígidas (*hard*) vs. restrições flexíveis (*soft*) e analogia com o Problema de Layout de Instalações (FLP).
  - Quatro estratégias de qualidade: rejeição integral (*generate-and-test*), *backtracking* construtivo, reparo pós-geração e laço fechado de refinamento (*feedback loop*).
* **5.8 Validade, Navegabilidade e Solvabilidade de Fases:**
  - Decomposição rigorosa das camadas de avaliação funcional:
    1. **Validade Lógica:** Aciclicidade do grafo causal e conectividade abstrata.
    2. **Validade Geométrica:** Não interseção de sólidos e contenção espacial via estruturas de consulta (AABBs, octrees, raycasting).
    3. **Navegabilidade:** Superfícies contínuas transitáveis considerando parâmetros cinemáticos do agente; Malhas de Navegação (NavMesh, Snook, 2000) baseadas em polígonos convexos e busca no grafo dual de adjacência com suavização (*string pulling*).
    4. **Pathfinding:** Algoritmo $A^*$ (Hart et al., 1968) com heurística admissível assegurando caminho de custo ótimo.
    5. **Solvabilidade:** Atingibilidade conjunta no espaço de estados e no espaço geométrico.
  - As 3 dissociações teóricas fundamentais: (i) validade geométrica sem navegabilidade; (ii) navegabilidade física sem solvabilidade dinâmica (chave trancada atrás da porta); (iii) validade lógica abstrata sem solvabilidade espacial (obstáculo físico bloqueando a chave).
  - **5.8.6 Síntese Conceitual:** Consolidação do arcabouço teórico como ponte para as decisões de modelagem e arquitetura a serem formalizadas na Metodologia.

---

## 4. Mapa Estrutural do Repositório e Arquivos Principais

```text
PTCC/
│
├── modelo_latex_TCC/
│   ├── main.tex                       # Documento mestre do artigo/TCC (classe abntex2/article)
│   ├── referencias.bib                # Base BibTeX unificada e validada (48 entradas)
│   ├── fundamentacao_20_10.tex        # Versão ATUAL E DEFINITIVA da Fundamentação Teórica
│   ├── fundamentação_20_10.tex        # Cópia idêntica byte a byte (compatibilidade de acentuação)
│   ├── fundamentacao_19_10.tex        # Versão intermediária anterior (19/10)
│   ├── fundamentacao_revisada.tex     # Primeira versão revisada pós-parecer do orientador (29/09)
│   ├── fundamentacao_teorica.tex      # Versão legada inicial (rascunho original)
│   ├── introducao.tex                 # Introdução do trabalho
│   ├── materiais_e_metodos.tex        # Capítulo de Materiais e Métodos
│   ├── metodologia_experimental.tex   # Detalhamento de experimentos
│   ├── consideracoes_finais.tex       # Conclusões e trabalhos futuros
│   ├── trabalhos_relacionados.tex     # Capítulo de Trabalhos Relacionados (criado em 23/10)
│   └── main.pdf                       # PDF compilado com sucesso (48 páginas)
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

1. **Regra de Citações no LaTeX:**
   - Utilize **exclusivamente** `\cite{chave}`.
   - **NUNCA** utilize `\textcite{chave}`. O estilo bibliográfico configurado (`abntex2` com `biblatex`) gera quebras sintáticas no texto caso `\textcite` seja empregado. As referências devem sempre ser introduzidas de forma impessoal no corpo do texto (ex.: *"Conforme demonstrado por Dormans \cite{dormans2010}..."*).
2. **Sincronização de Chaves BibTeX:**
   - Antes de adicionar qualquer citação nova no texto LaTeX, confirme que a chave correspondente existe em `referencias.bib`.
   - A chave para o artigo de van der Linden et al. (2013) é estritamente `linden2013designing` (a antiga chave genérica `inproceedings` foi renomeada e abolida).
3. **Versionamento e Nomenclatura:**
   - Se novas alterações forem solicitadas na fundamentação teórica, salve em um novo arquivo com a data atual: `fundamentacao_DD_MM.tex` e mantenha uma cópia idêntica byte a byte nomeada `fundamentação_DD_MM.tex`.
   - Nunca sobrescreva ou apague versões de dias anteriores (`fundamentacao_teorica.tex`, `fundamentacao_revisada.tex`, `fundamentacao_19_10.tex`), pois o usuário mantém histórico de controle entre versões.
4. **Posicionamento de Inclusão em `main.tex`:**
   - O comando `\include{fundamentacao_20_10}` deve permanecer exatamente onde está (ao final de `main.tex`, logo após `\include{consideracoes_finais}`). Não reposicione este include para o meio do documento, pois o usuário está usando o template apenas para carregar e inspecionar o capítulo compilado isoladamente e fará a formatação final posteriormente.
5. **Agnosticismo Teórico vs. Metodologia:**
   - Em hipótese alguma reintroduza termos da engine (Godot, GDScript, C#, NavigationRegion3D, addon, arquiteto/engenheiro) nos arquivos de Fundamentação Teórica. Esses conceitos devem ser reservados exclusivamente aos capítulos de **Materiais e Métodos** e **Metodologia Experimental**.
6. **Compilação do Documento:**
   - O ambiente utiliza MiKTeX no Windows PowerShell.
   - A sequência correta de compilação quando bibliografias ou referências forem alteradas é:
     ```powershell
     cd "modelo_latex_TCC"
     biber main
     pdflatex -interaction=nonstopmode main.tex
     ```

---

## 6. Próximos Passos do TCC (Roadmap Metodológico)

Com a Fundamentação Teórica plenamente validada, alinhada ao orientador e compilada sem pendências, a frente de trabalho prioritária para os próximos agentes consiste no desenvolvimento do **Capítulo de Metodologia**:

1. **Especificação da Arquitetura Híbrida do Sistema:**
   - Detalhar formalmente o fluxo de dados entre o LLM e o motor de jogos (Godot 4.x).
   - Especificar o esquema JSON formal (*JSON Schema*) utilizado para representar o grafo de progressão (nós, salas, corredores, conexões, requisitos de chaves/portas e tipos funcionais).
2. **Estratégia de Engenharia de Prompt e Chamada ao Modelo:**
   - Estrutura de prompts em poucas passagens (*few-shot*) e decomposição em Cadeia de Pensamento (CoT) para síntese do grafo lógico sem alucinações sintáticas.
3. **Mecanismo de Instanciação Geométrica 3D e Resolução de Restrições:**
   - Algoritmo determinístico de alocação modular de salas e corredores com base em portas/conectores.
   - Algoritmo de posicionamento de mobiliário e *props* com base em restrições de contenção e áreas livres (*clearance*).
4. **Pipeline Automatizado de Teste e Validação Funcional:**
   - Rotinas de *bake* e reconstrução programática da NavMesh (`NavigationRegion3D`).
   - Algoritmo de teste de conectividade física com $A^*$ entre todos os nós e pontos de interesse.
   - Verificador de solvabilidade no espaço de estados dinâmicos (simulador de inventário e progressão chave-fechadura).
5. **Planejamento de Experimentos e Métricas:**
   - Métricas quantitativas de avaliação: taxa de validade geométrica (ausência de colisão), taxa de navegabilidade contínua da NavMesh, taxa de solvabilidade lógica, tempo de geração e expressividade do espaço de fases (*expressive range*).
