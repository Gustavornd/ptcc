# Segunda Revisão — Fundamentação Teórica

**TCC:** Geração de Layouts de Fases 3D Assistida por Modelos de Linguagem de Grande Porte
**Discente:** Gustavo Rafael Nunes Durães | **Orientador:** Prof. Wagner Ferreira de Barros
**Texto revisado:** [fundamentacao_19_10.tex](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex) (versão de 19/10)
**Base de comparação:** `Guia_Revisao_FundamentacaoTeorica_GustavoRafael.docx` e os 13 comentários de `Fundamentacao_Teorica_Gustavo_Rafael_REVISADA_COMENTADA.pdf`
**Data:** 20/10/2026

> [!NOTE]
> Esta revisão não alterou nenhum arquivo do projeto. Os números de linha citados abaixo se referem a `fundamentacao_19_10.tex`. Mantive o mesmo mapa de cores da revisão anterior: 🟠 escopo/reorganização · 🔵 aprofundar · 🔴 erro ou imprecisão · 🟢 trecho adequado.

---

## 1. Parecer geral

A nova versão representa um **avanço muito grande** em relação à anterior. A reorganização pedida foi seguida praticamente à risca: o capítulo agora segue a estrutura 5.1 → 5.8 proposta no Guia, com todas as subseções previstas. Os conteúdos de implementação foram retirados (não há mais menções a Godot, GDScript, C#, NavigationRegion3D, "arquiteto/engenheiro", "Dual-Agent" ou ao pipeline concreto), e os quatro erros conceituais apontados em vermelho foram corrigidos de forma explícita e correta.

Os problemas que restam são de **outra natureza** e menos graves que os da versão anterior:

1. **Sustentação bibliográfica dos conceitos de base.** Conceitos clássicos (grafo, Transformer, gradiente que desaparece, CSP, A*, NavMesh, AABB, raciocínio espacial, *grounding*) ainda estão apoiados quase só em artigos recentes sobre LLMs e geração 3D, e não nas fontes primárias ou em livros-texto. Ao conferir nos PDFs, encontrei **citações que não sustentam a afirmação** a que estão ligadas (Seção 6.2).
2. **Algumas imprecisões conceituais pontuais**, sobretudo em grafos, transformações espaciais e PCGML (Seção 5).
3. **Extensão e densidade.** O capítulo tem cerca de 8.000 palavras e 192 chamadas `\cite`. Dessas, 87% agrupam duas ou mais referências, e há sentenças com 5 a 7 referências. Isso dificulta a leitura e aumenta o risco de citações mal atribuídas.

| Dimensão | Revisão anterior | Situação atual | Avaliação |
|---|---|---|---|
| Completude | Média | Todos os tópicos da estrutura proposta estão presentes | **Boa** |
| Corretude | Média | Erros anteriores corrigidos; restam imprecisões pontuais | **Boa, com ressalvas** |
| Profundidade | Desigual | Grafos e validação muito mais densos; LLMs gastam muito espaço com arquitetura e pouco com capacidades | **Boa** |
| Aderência ao tema | Boa | Mantida | **Boa** |
| Separação teoria/metodologia | Baixa | Resolvida; só restam dois resquícios leves | **Muito boa** |
| Base bibliográfica | Concentrada em LLMs | Clássicos de PCG/Level Design incluídos; faltam fontes primárias de conceitos gerais | **Média** |

---

## 2. Atendimento aos comentários do PDF

| # | Cor | Comentário (resumo) | Status | Onde / observação |
|---|---|---|---|---|
| 1 | 🟠 | Reorganizar o capítulo na sequência proposta (fases → PCG → PCGML/LLM → espacial → grafos → layouts 3D → híbridos → validade) | ✅ Atendido | Estrutura idêntica à proposta ([L9–L308](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L9-L308)) |
| 2 | 🟠 | Separar PCG e PCGML/LLMs em duas seções | ✅ Atendido | 5.2 ([L35](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L35)) e 5.3 ([L69](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L69)) |
| 3 | 🔴 | Determinismo ≠ garantia de conclusão | ✅ Atendido muito bem | [L53](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L53). ⚠️ Mas a mesma ideia volta de forma contraditória em [L231](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L231) (ver 5.7.1) |
| 4 | 🔵 | Definir raciocínio espacial → *spatial grounding* → limitações; não explicar só por tokens sequenciais; apoiar-se em tarefas e modelos específicos | ⚠️ Parcial | Ordem e definições corretas, e a explicação por tokens foi retirada. **Ainda falta** apoiar as limitações em tarefas, modelos e resultados concretos (ver 5.4.3) |
| 5 | 🔴 | Retirar "inevitavelmente" e generalizações absolutas | ✅ Atendido | [L138](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L138) usa "frequentemente insuficiente" e menciona que os próprios trabalhos introduzem planejadores e restrições. ⚠️ O verbo "explicam" em [L128](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L128) ainda sugere causalidade forte |
| 6 | 🔵 | Base de Teoria dos Grafos; progressão e dependências; grafo ≠ JSON | ✅ Atendido | 5.5.1–5.5.4 e 5.3.3. Restam ajustes de rigor (ver 5.5) |
| 7 | 🟠 | Criar base de layouts 3D antes dos híbridos; remover arquiteto/engenheiro, Godot e pipeline | ✅ Atendido | 5.6 criada ([L185](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L185)); nenhum termo de implementação restante |
| 8 | 🔴 | Não tratar "Arquiteto-Engenheiro"/"Dual-Agent" como paradigma consolidado | ✅ Atendido | Os termos foram removidos; Her et al. (2025) agora aparece só como exemplo de arquitetura híbrida |
| 9 | 🟠 | Reorganizar validação em 5 conceitos separados; sem C#/Godot/ordem de testes | ✅ Atendido | 5.8.1–5.8.5 |
| 10 | 🔴 | AABB/BVH/raycasting não impedem sobreposição | ✅ Atendido muito bem | [L280](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L280) |
| 11 | 🔴 | Separar A*, NavMesh e solvabilidade | ✅ Atendido muito bem | [L301–L308](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L301-L308) |
| 12 | 🟠 | Acrescentar referências fundamentais (Level Design, PCG, grafos, restrições, navegação) | ⚠️ Parcial | Foram incluídos Dormans, Shaker, van der Linden (2013/2014) e Tanagra. **Faltam** fontes de Teoria dos Grafos, Level Design (livro), CSP, navegação/pathfinding e LLMs (Seção 6.3) |
| 13 | 🔴 | Francesco Re é dissertação de 2026 e não deve sustentar as limitações geométricas | ✅ Atendido | A entrada `re2026integration` foi corrigida no `.bib` e deixou de ser citada no texto |

**Resumo:** 10 comentários atendidos integralmente e 3 atendidos parcialmente (4, 12 e, de forma marginal, 5).

---

## 3. Atendimento ao Guia de Revisão

| Item do Guia | Status | Observação |
|---|---|---|
| §3 Estrutura 5.1–5.8 com subseções | ✅ | Hierarquia e títulos coincidem com a proposta |
| §4 Reaproveitar o texto antigo nas novas seções | ✅ | Feito, com reescrita substancial |
| §5 Objeto de estudo (fase, layout 3D, Level Design) | ✅ | 5.1 está boa, mas sem referência específica de Level Design (ver 5.1) |
| §5 Mais espaço para grafos | ✅ | Muito ampliado |
| §5 Representação estruturada intermediária (grafo ≠ JSON) | ✅ | [L100–L102](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L100-L102) |
| §5 Geração baseada em restrições / CSP | ✅ | 5.7.2 |
| §5 Representação espacial modular | ✅ | 5.6 |
| §5 Validade × navegabilidade × solvabilidade | ✅ | Ponto forte do capítulo |
| §6 Retirar implementação para a Metodologia | ✅ | Restam só dois resquícios leves (5.5.4 e 5.8.5) |
| §8 Equilibrar a bibliografia | ⚠️ | Melhorou, mas o capítulo ainda depende muito de Xu & Verbrugge (101 citações somando os dois artigos) e de *preprints* (RoomPlanner, 44 citações) para conceitos gerais |
| §9 Revisar as referências para que cada conceito tenha fonte adequada | ❌ Pendente | Este é o principal trabalho da próxima versão |

---

## 4. Questões estruturais e de arquivo

1. 🟠 **Posição do capítulo no `main.tex`.** Em [main.tex](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/main.tex), `\include{fundamentacao_19_10}` vem **depois** de `consideracoes_finais`. É por isso que a Fundamentação aparece como Seção 5. A ordem esperada é Introdução → Fundamentação Teórica → Materiais e Métodos/Metodologia → … → Considerações Finais. Se isso for intencional nesta fase de rascunho, desconsidere; caso contrário, corrija antes da versão final.
2. 🔴 **Os dois arquivos `.tex` não são idênticos.** Diferem em um caractere: `fundamentacao_19_10.tex` (o arquivo **compilado** pelo `main.tex`) contém o erro de digitação **"contradictórios"** em [L126](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L126), enquanto `fundamentação_19_10.tex` já traz "contraditórios". Recomendo manter um único arquivo, de preferência o nome sem acento, para evitar divergências.
3. **Chave bibliográfica `inproceedings`.** A entrada de van der Linden et al. (2013) usa a chave genérica `inproceedings`, provavelmente herdada de exportação automática. Sugiro renomeá-la (ex.: `linden2013designing`) para evitar confusão e colisão com futuras entradas.
4. **"Este capítulo"** ([L6](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L6)). O modelo usa `\section` (classe `abntex2` em modo artigo). Não é erro, mas avalie se "esta seção" fica mais coerente com o documento compilado.
5. 🔵 **Falta um fechamento.** O capítulo termina abruptamente em 5.8.5. Um parágrafo curto de síntese, relacionando os conceitos entre si **sem antecipar o método**, ajudaria a cumprir o objetivo expresso no item 10 do Guia (preparar o leitor para a Metodologia).

---

## 5. Revisão detalhada por seção

### 5.1 Fases de Jogos, Level Design e Layouts 3D — 🟢 boa, com ajustes

- 🟢 A distinção missão × espaço com base em Dormans (2010) ([L30–L32](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L30-L32)) está correta, e a dicotomia "topologia × topografia" foi eliminada, como pedido.
- 🔵 **Falta uma referência específica de Level Design.** Todas as fontes de 5.1.1 são artigos de PCG (Tanagra, Dormans, van der Linden). Para definir "fase" e "Level Design", e seus objetivos (condução, ritmo/*pacing*, introdução de mecânicas), vale incluir um livro da área, por exemplo: TOTTEN, C. W. *An Architectural Approach to Level Design* (CRC Press); ROGERS, S. *Level Up! The Guide to Great Video Game Design* (Wiley); ou SCHELL, J. *The Art of Game Design* (CRC Press).
- 🔴 [L16](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L16): "sistema ludológico" não é adequado. *Ludologia* é o campo de estudo dos jogos, não o sistema de regras. Use "sistema de jogo" ou "sistema de regras do jogo".
- [L32](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L32): "Essa dissociação teórica **demonstra** que…" é forte demais para uma distinção conceitual. Prefira "evidencia" ou "sugere".

### 5.2 Geração Procedural de Conteúdo — 🟢 boa

- 🟢 A correção sobre determinismo em [L53](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L53) é exatamente o que foi pedido.
- 🟢 Os três componentes de um gerador de masmorras (modelo representacional → construção → geometria) em [L64](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L64) estão corretamente atribuídos a van der Linden et al. (2014) e preparam bem a 5.5.4.
- 🔵 [L51](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L51): "A literatura clássica classifica… em **três** grandes paradigmas" sugere uma taxonomia única. Há outras (ex.: *online/offline*, necessário/opcional, construtivo/gerar-e-testar em TOGELIUS et al., 2011, *Search-Based Procedural Content Generation: A Taxonomy and Survey*, IEEE TCIAIG). Sugiro "Uma classificação recorrente na literatura…" e citar Togelius et al. (2011), que também é a fonte primária para "PCG baseada em busca como caso especial de gerar-e-testar" ([L55](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L55)).
- [L46](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L46): "garantindo resultados consistentes sem sacrificar a diversidade" afirma demais. Controlabilidade e diversidade costumam ser forças em **tensão**. Reformule como objetivo ("buscando…"), não como garantia. Para *expressive range*, a fonte primária é SMITH, G.; WHITEHEAD, J. *Analyzing the Expressive Range of a Level Generator* (PCGames, 2010).
- [L55](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L55): "valor numérico contínuo" é restritivo. A função de aptidão pode ser discreta ou multiobjetivo. Basta "um valor (ou vetor de valores) de aptidão". **Verifiquei** que o PDF de Xu & Verbrugge (*Constraint Is All You Need*) trata de *Simulated Annealing*, mas **não** de PSO nem de MCTS. Para esses dois, Maleki & Zhao (2024) é a fonte suficiente.
- [L57](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L57): enquadrar o WFC como método baseado em restrições está correto. A fonte que sustenta isso é KARTH, I.; SMITH, A. M. *WaveFunctionCollapse is Constraint Solving in the Wild* (FDG, 2017). Para ASP, cite SMITH, A. M.; MATEAS, M. *Answer Set Programming for Procedural Content Generation* (IEEE TCIAIG, 2011). Chen & Jhala (2025) menciona SMT apenas de passagem, nos trabalhos relacionados.
- [L64](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L64): "operam em escala **microscópica**" é um termo impróprio. Use "operam localmente" ou "em escala local". [L42](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L42): "malhas vegetais" → "vegetação".

### 5.3 PCGML e uso de LLMs — 🟢/🔵 boa, mas desbalanceada

**5.3.1 PCGML**
- 🟢 A definição e a distinção em relação à busca (PCGML gera diretamente; a busca usa o modelo como avaliador) estão corretas e fiéis a Summerville et al. (2018).
- 🔴 [L78](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L78): **PCGRL dentro de PCGML conflita com a definição que você mesmo deu em [L76](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L76)** ("modelos treinados sobre conteúdos preexistentes"). O aprendizado por reforço para PCG (KHALIFA et al., *PCGRL*, AIIDE 2020) aprende por recompensa e **não depende de um corpus de níveis**. Summerville et al. (2018) não o inclui (verifiquei: o PDF não menciona *reinforcement*). Ou retire o PCGRL da lista, ou deixe claro que se trata de uma vertente de aprendizado aplicada a PCG que foge da definição estrita de PCGML.
- 🔵 **Falta explicitar a relação entre LLMs e PCGML.** O Guia pedia "corrigir a relação histórica entre esses conceitos". O texto mostra a evolução, mas não diz claramente se usar um LLM pré-treinado via *prompt* (sem treino sobre conteúdo de jogos) é PCGML. Não é, em sentido estrito. Já o ajuste fino de um LLM sobre níveis (como em Todd et al., 2023, com Sokoban) se enquadra. Uma ou duas frases sobre isso evitam ambiguidade conceitual na banca.

**5.3.2 LLMs**
- 🔵 **Desequilíbrio de conteúdo.** Três parágrafos ([L85–L89](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L85-L89)) tratam da história e da arquitetura (Markov → RNN → Transformer → BERT/GPT → RLHF). O que o Guia pedia (capacidades de interpretação de linguagem natural, geração e **planejamento simbólico**) aparece comprimido em [L93](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L93). Sugiro **condensar a parte histórica** e **expandir os papéis dos LLMs em PCG** (gerador direto, planejador semântico, gerador de código/parâmetros para ferramentas procedurais, assistente de design), que é o que sustentará a Metodologia.
- 🔴 **Citações que não sustentam a afirmação** (verificado nos PDFs):
  - "desaparecimento de gradientes" ([L85](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L85)) atribuído a Maleki & Zhao: o termo **não aparece** no artigo. Fonte adequada: BENGIO, Y.; SIMARD, P.; FRASCONI, P. *Learning long-term dependencies with gradient descent is difficult* (IEEE TNN, 1994) e/ou HOCHREITER; SCHMIDHUBER (1997), *LSTM*.
  - "autoatenção" ([L87](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L87)) atribuída a Gallotta et al.: o termo *self-attention* **não aparece** no survey. Maleki & Zhao o menciona citando Vaswani. Cite a fonte primária: VASWANI, A. et al. *Attention Is All You Need* (NeurIPS, 2017).
  - Aprendizado em contexto (ICL) ([L91](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L91)) apoiado em SceneTeller e Her et al.: são trabalhos que **usam** ICL, não que o definem. Fonte primária: BROWN, T. et al. *Language Models are Few-Shot Learners* (NeurIPS, 2020).
  - Faltam também as fontes primárias de BERT (DEVLIN et al., 2019), RLHF (OUYANG et al., 2022), CoT (WEI et al., 2022) e RAG (LEWIS et al., 2020).
- 🔴 [L91](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L91): "escalonamento para **centenas de milhões** ou bilhões de parâmetros faz **emergir** capacidades como o ICL". A capacidade de ICL ficou associada a modelos na casa das dezenas a centenas de **bilhões** de parâmetros (GPT-3), e o caráter "emergente" dessas capacidades é debatido (SCHAEFFER; MIRANDA; KOYEJO, *Are Emergent Abilities of Large Language Models a Mirage?*, NeurIPS 2023). Sugiro suavizar a frase.

**5.3.3 Representações estruturadas**
- 🟢 A distinção modelo conceitual × formato de serialização ([L100–L102](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L100-L102)) atende exatamente ao pedido do Guia.
- 🔴 [L102](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L102): colocar **CSS** ao lado de JSON/XML/YAML como "formato de serialização" é impreciso. CSS é uma linguagem de folhas de estilo. O SceneTeller **adota a sintaxe de CSS** para descrever caixas delimitadoras (seguindo o LayoutGPT); verifiquei isso no PDF. Reformule: "…ou mesmo notações emprestadas de outras linguagens, como a sintaxe de CSS adotada por Öcal et al. (2024)".
- ⚠️ [L100](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L100): a lista de "modelos conceituais" mistura abstrações (grafo, triplas, árvore) com **linguagens** (DSL/GLDL, código). Uma DSL é uma notação que codifica um modelo, mais próxima da camada de serialização/sintaxe. Vale um ajuste para que os exemplos não enfraqueçam a distinção que você acabou de fazer.

### 5.4 Raciocínio e ancoragem espacial — 🟢/🔵

- 🟢 As relações espaciais listadas ([L114](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L114)) cobrem tudo o que o Guia pedia.
- 🔵 **Definições sem fonte de base.** A definição de raciocínio espacial ([L112](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L112)) está apoiada em RoomPlanner e Xu & Verbrugge. Verifiquei: Xu & Verbrugge não usa a expressão *spatial reasoning*, e RoomPlanner a usa uma única vez, de passagem. Sugiro COHN, A. G.; RENZ, J. *Qualitative Spatial Representation and Reasoning* (Handbook of Knowledge Representation, 2008). Para *grounding* ([L119](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L119)), a referência clássica é HARNAD, S. *The Symbol Grounding Problem* (Physica D, 1990).
- 🔴 [L114](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L114), item (iii): **direção** e **orientação** estão fundidas. Direção é uma relação **entre** entidades ("A está ao norte de B"); orientação é a **pose própria** de uma entidade (para onde ela está voltada). Separe os dois conceitos, pois a orientação será retomada em 5.6.2.
- 🔴 [L121](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L121): o exemplo "cadeiras costumam acompanhar mesas" descreve **coocorrência semântica**, não *affordance*. Na acepção de Gibson (1979), *affordance* é a possibilidade de ação que um objeto oferece a um agente (uma cadeira *permite sentar*; uma porta *permite passar*). Ajuste o exemplo ou o termo.
- 🔵 **5.4.3, pendência do comentário 4.** As limitações continuam descritas de forma genérica, com blocos de 4 a 7 citações ([L128–L135](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L128-L135)). Inclua **2 ou 3 evidências concretas**, do tipo "Em [trabalho], ao solicitar a [modelo] que [tarefa], os autores observaram [falha/métrica]". Isso dá peso empírico às afirmações e evita a impressão de generalização.
- 🔴 **Atribuição de "viés de exposição"** ([L128](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L128)). Verifiquei que o termo **não aparece** em RoomPlanner nem em SceneTeller. Em Feng et al. (2026) ele aparece, mas em relação ao **próprio modelo de difusão 3D autorregressivo** dos autores (LaviGen), **não a LLMs**. Além disso, *exposure bias* tem significado técnico preciso (descompasso entre treino com *teacher forcing* e inferência) e não é sinônimo de acúmulo de erros. Sugiro manter apenas "acúmulo/propagação de erros em geração sequencial" com fonte que o sustente, ou explicar corretamente o conceito.
- ⚠️ "Compressão de informação" ([L128](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L128)), atribuída a Feng et al.: **não localizei** essa formulação no PDF. O que o artigo afirma é que métodos que tratam o layout como linguagem (formato tipo JSON) "carecem de modelagem física", o que leva a colisões e interpenetrações. Essa afirmação, sim, sustenta bem os itens da lista em [L132–L133](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L132-L133). Ajuste a paráfrase ao que o texto efetivamente diz.
- [L128](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L128): "fatores técnicos que **explicam**" → "fatores que **podem contribuir para**".

### 5.5 Representação lógica por grafos — 🟢 grande avanço; 🔴 ajustes de rigor

- 🟢 O pedido foi atendido: o capítulo agora cobre vértices, arestas, direção, pesos, rótulos, caminhos, ciclos, conectividade, alcançabilidade, chave/fechadura, rota crítica e ramificações.
- 🔴 **Fonte inadequada para a definição de grafo** ([L148](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L148)). $G=(V,E)$ está apoiado em Summerville, Maleki e Code-as-Room. Verifiquei: Code-as-Room usa $G=(V,E)$ para um *scene graph* próprio, e Maleki traz uma única frase ("a graph is a set of vertices connected by edges"). Use um livro-texto: BONDY, J. A.; MURTY, U. S. R. *Graph Theory* (Springer, 2008); DIESTEL, R. *Graph Theory* (Springer); CORMEN, T. H. et al. *Introduction to Algorithms* (MIT Press); ou, em português, SZWARCFITER, J. L. *Teoria Computacional de Grafos* (Elsevier, 2018). O mesmo vale para "grau" ([L150](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L150)): o PDF de van der Linden (2013) usa *degree* apenas no sentido de "grau de controle".
- 🔴 **Dígrafos merecem tratamento próprio**, já que os grafos de missão e de progressão são direcionados:
  - Grau → defina **grau de entrada** e **grau de saída**.
  - Caminho ([L154](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L154)): em dígrafos, o caminho deve **respeitar o sentido dos arcos**. Além disso, "sequência de vértices conectados sucessivamente" é, em rigor, um *passeio* (*walk*); um caminho não repete vértices.
  - Conectividade ([L156](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L156)): distinga **conectividade forte** e **fraca**. Isso importa para portas unidirecionais.
  - Alcançabilidade ([L157](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L157)): registre que, em dígrafos, ela **não é simétrica** (B pode ser alcançável a partir de A sem que A seja alcançável a partir de B).
- 🔴 **Ordem topológica usada sem definição, e em tensão com ciclos.** Em [L175](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L175) você usa $\tau$ (ordem topológica) e, na mesma frase, fala em "ciclos controlados". Uma ordem topológica só existe em grafos **acíclicos** (DAG). Defina ordenação topológica em 5.5.1 e esclareça que ela se aplica à **relação de dependência/precedência** (que deve ser acíclica para a fase ser solucionável), enquanto o **grafo espacial** pode conter ciclos (atalhos, *backtracking*). Essa distinção é conceitualmente importante e ainda reforça a 5.8.
- 🔵 **Estados** ([L173](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L173)): o Guia pedia "estados necessários à progressão". O texto menciona estados, mas não os define. Uma frase sobre **estado do jogo** (ex.: posição + itens/chaves obtidos) e sobre o **espaço de estados** prepararia melhor o argumento final de [L308](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L308).
- 🟢 [L180–L182](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L180-L182): a relação um-para-muitos entre grafo e layout está correta, assim como a ressalva de planaridade restrita a "grade ortogonal ou pavimento plano". De fato, em 3D qualquer grafo pode ser realizado sem cruzamentos.
- 🟠 [L182](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L182): "durante a etapa de resolução de *layout*" soa como etapa do **seu** sistema. Como isso vem de van der Linden et al. (2013) (verifiquei: *planar graph… reduces edges per node to four by adding new intermediate nodes*), atribua explicitamente: "em abordagens como a de van der Linden et al. (2013), …".

### 5.6 Representação de layouts espaciais 3D — 🟢 nova seção adequada

- 🟢 A tipologia de módulos (tiles/voxels, *chunks*, *room templates*, *prefabs*) e de conectores está correta e no nível de abstração certo.
- 🔴 [L208](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L208): **"pose"** designa posição + orientação, **sem escala**. E **escala** (fator multiplicativo de uma transformação) não é **dimensão** (extensão física $w, l, h$ do objeto). Separe: pose = $(\mathbf{p}_i, \mathbf{R}_i)$; dimensão $\mathbf{s}_i$ é atributo do módulo; escala é uma transformação que pode alterá-la.
- 🔴 [L210](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L210): "AABB… **ajustada conforme a orientação**" é contraditório, porque a AABB é, por definição, alinhada aos eixos do mundo. Quando o objeto gira, a AABB precisa ser **recalculada** (e tende a crescer). Uma caixa que acompanha a rotação é uma **OBB** (*Oriented Bounding Box*). Fontes adequadas: ERICSON, C. *Real-Time Collision Detection* (Morgan Kaufmann, 2004) ou AKENINE-MÖLLER, T. et al. *Real-Time Rendering*.
- ⚠️ [L220](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L220) × [L245](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L245): *clustering* aparece com dois sentidos (congestionamento indesejado em 5.6.3 e métrica de agrupamento a maximizar em 5.7.2, como em Xu & Verbrugge). Padronize o uso.

### 5.7 Arquiteturas híbridas e geração baseada em restrições — 🟢 com uma contradição

- 🟢 A seção ficou genérica, como pedido, sem pipeline nem divisão operacional de papéis. A 5.7.3 (gerar-e-testar, *backtracking*, reparo, *feedback loop*) é conceitual e não antecipa as escolhas do TCC. Verifiquei que o Tanagra descreve *backtracking* com relaxamento de restrições, então a citação procede.
- 🔴 [L231](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L231): "métodos construtivos e baseados em restrições **oferecem garantias estruturais**" **contradiz** o que você corrigiu em [L53](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L53) e em [L66](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L66) (autômatos celulares não asseguram conectividade). Reformule: "…**podem** oferecer garantias quando suas regras ou restrições são projetadas para preservar as propriedades desejadas…".
- 🔵 "Neuro-simbólico" ([L233](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L233)) merece uma definição com fonte geral, ex.: GARCEZ, A. d'A.; LAMB, L. C. *Neurosymbolic AI: the 3rd wave* (Artificial Intelligence Review, 2023).
- [L235](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L235): o *Sentient Sketchbook* está citado via van der Linden (2014), que de fato o descreve (verificado). Ainda assim, prefira a fonte original: LIAPIS, A.; YANNAKAKIS, G. N.; TOGELIUS, J. *Sentient Sketchbook: Computer-Aided Game Level Authoring* (FDG, 2013). Avalie também se o parágrafo sobre iniciativa mista é necessário para o seu método; se não for, ele pode ser encurtado.
- 🔵 [L240](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L240): a definição formal de CSP (variáveis, domínios, restrições) deve vir de uma fonte geral, como RUSSELL, S.; NORVIG, P. *Inteligência Artificial: uma abordagem moderna*, capítulo sobre CSP.
- [L248](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L248): "**frequentemente** modelado como FLP" generaliza a partir de dois artigos dos **mesmos autores**. Prefira "pode ser modelado, como em Xu e Verbrugge (2025), …". Vale observar também que agregar restrições rígidas como penalidades ponderadas as torna, na prática, flexíveis. Uma frase sobre isso mostra domínio do conceito.

### 5.8 Validade, navegabilidade e solvabilidade — 🟢 ponto forte do capítulo

- 🟢 A separação em cinco conceitos, os três contraexemplos de [L303–L305](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L303-L305) e o esclarecimento sobre AABB/raycasting em [L280](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L280) são exatamente o que se espera de uma Fundamentação. Esta seção pode ser preservada praticamente como está.
- 🔵 **Fontes primárias de navegação.** NavMesh: SNOOK, G. *Simplified 3D Movement and Pathfinding Using Navigation Meshes* (Game Programming Gems, 2000) e/ou MILLINGTON, I.; FUNGE, J. *Artificial Intelligence for Games* (2009). A*: HART, P. E.; NILSSON, N. J.; RAPHAEL, B. *A Formal Basis for the Heuristic Determination of Minimum Cost Paths* (IEEE TSSC, 1968). O próprio RoomPlanner cita Hart et al. (verificado).
- ⚠️ [L292](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L292): uma NavMesh não é propriamente uma "representação **discreta**" como uma grade. Ela é formada por polígonos contínuos, e a busca ocorre sobre o **grafo de adjacência** desses polígonos. Explicitar isso **conecta a 5.8.4 à 5.5.1** (A* e BFS são algoritmos sobre grafos), o que dá unidade ao capítulo.
- [L294](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L294): vale mencionar que o A* garante caminho **ótimo** quando a heurística é **admissível**, propriedade central do algoritmo.
- 🔴 [L304](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L304): "chave alocada **após** a própria porta" é ambíguo (após no tempo? no espaço?). Escreva "chave alocada em uma região alcançável apenas atravessando a própria porta".
- 🟠 [L308](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L308): o parágrafo final está no limite do prescritivo ("a verificação plena… **requer**…"). Conceitualmente está correto e pode ficar, mas cuide para que a Metodologia não pareça mera repetição dele.

---

## 6. Questões transversais

### 6.1 Densidade e concentração de citações

| Indicador | Valor |
|---|---|
| Palavras (aprox.) | ~8.000 |
| Chamadas `\cite` | 192 |
| Chamadas com 2 ou mais referências | 167 (87%) |
| Chamadas com 4 a 7 referências | 32 |
| Citações de Xu & Verbrugge (2 artigos) | 101 |
| Citações de RoomPlanner (*preprint* arXiv) | 44 |

A citação múltipla em quase todas as frases passa a impressão de **acúmulo** e não de **argumentação**, e torna difícil para a banca verificar a origem de cada afirmação. Recomendo:
- citar **uma ou duas** fontes por afirmação, escolhendo a mais específica;
- usar trabalhos recentes (Xu & Verbrugge, RoomPlanner, SceneCraft etc.) para **exemplificar** e **contextualizar**, e livros-texto e artigos seminais para **definir**;
- sinalizar no texto quando um trabalho for *preprint* (RoomPlanner, Feng et al., Code-as-Room, Her et al.), sobretudo quando sustentar uma afirmação forte.

### 6.2 Citações verificadas nos PDFs

| Linha | Afirmação | Referência citada | Resultado |
|---|---|---|---|
| [L55](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L55) | SA, PSO, MCTS | `xu2025constraint` | Só SA é tratado; PSO e MCTS não aparecem ⚠️ |
| [L78](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L78) | PCGRL como técnica de PCGML | `summerville2018procedural` | Não menciona RL ⚠️ |
| [L85](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L85) | Gradiente que desaparece | `maleki2024procedural` | Não aparece ❌ |
| [L87](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L87) | Autoatenção | `Gallotta_2024` | Não aparece ❌ (Maleki sim, citando Vaswani) |
| [L102](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L102) | CSS como serialização | `ocal2024sceneteller` | Usa sintaxe CSS para caixas; formulação imprecisa ⚠️ |
| [L112](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L112) | Definição de raciocínio espacial | `sun2024roomplanner`, `xu2025constraint` | Não definem o conceito ⚠️ |
| [L128](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L128) | *Exposure bias* em LLMs | `ocal…`, `sun…`, `feng…`, `yang…` | Ausente em SceneTeller e RoomPlanner; em Feng refere-se a modelo de difusão, não a LLM ❌ |
| [L128](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L128) | "Compressão de informação" | `feng2026…` | Formulação não localizada; o artigo fala em ausência de modelagem física ⚠️ |
| [L148](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L148) | $G=(V,E)$ | `maleki…`, `yang2026…` | Uso incidental; não é fonte de Teoria dos Grafos ⚠️ |
| [L150](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L150) | Grau de vértice | `inproceedings` | *Degree* aparece só como "grau de controle" ❌ |
| [L168](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L168) | Ações co-localizadas | `inproceedings` | ✅ Confirmado |
| [L182](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L182) | Planarização e nós intermediários | `inproceedings` | ✅ Confirmado |
| [L235](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L235) | Sentient Sketchbook | `linden2014dungeons` | ✅ Descrito (fonte secundária) |
| [L256](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L256) | *Backtracking* com relaxamento | `tanagra` | ✅ Confirmado |
| [L62](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L62) | Conteúdo funcional × cosmético | `summerville2018procedural` | ✅ Confirmado |

> [!IMPORTANT]
> A verificação acima é **amostral**: cobre só os pontos que me pareceram suspeitos. Antes da próxima entrega, faça uma conferência completa, garantindo que **cada** referência em cada `\cite` sustente de fato a afirmação a que está ligada. Esse é o tipo de problema que uma banca costuma detectar.

### 6.3 Fontes primárias sugeridas (por conceito)

| Conceito | Referência sugerida |
|---|---|
| Level Design | TOTTEN (2014/2019); ROGERS, *Level Up!*; SCHELL, *The Art of Game Design* |
| Taxonomia de PCG / busca | TOGELIUS et al. (2011), IEEE TCIAIG 3(3) |
| *Expressive range* | SMITH; WHITEHEAD (2010), PCGames |
| ASP em PCG / WFC | SMITH; MATEAS (2011); KARTH; SMITH (2017) |
| PCGRL | KHALIFA et al. (2020), AIIDE |
| Transformer / autoatenção | VASWANI et al. (2017) |
| Gradiente que desaparece / LSTM | BENGIO; SIMARD; FRASCONI (1994); HOCHREITER; SCHMIDHUBER (1997) |
| BERT · ICL · RLHF · CoT · RAG | DEVLIN et al. (2019) · BROWN et al. (2020) · OUYANG et al. (2022) · WEI et al. (2022) · LEWIS et al. (2020) |
| Raciocínio espacial qualitativo | COHN; RENZ (2008) |
| *Symbol grounding* | HARNAD (1990) |
| *Affordance* | GIBSON (1979) |
| Teoria dos Grafos | BONDY; MURTY (2008); DIESTEL; SZWARCFITER (2018); CORMEN et al. |
| Volumes delimitadores / colisão | ERICSON (2004); AKENINE-MÖLLER et al. |
| Neuro-simbólico | GARCEZ; LAMB (2023) |
| CSP / A* / busca | RUSSELL; NORVIG; HART; NILSSON; RAPHAEL (1968) |
| NavMesh | SNOOK (2000); MILLINGTON; FUNGE (2009) |

Não é preciso usar todas; escolha as que cobrem os conceitos que a Metodologia de fato utilizará.

### 6.4 Extensão

Com ~8.000 palavras, só esta seção provavelmente ultrapassa o que o modelo de TCC espera para a Fundamentação. Pontos onde dá para **enxugar sem perda conceitual**:
- histórico de arquiteturas de PLN em 5.3.2;
- lista extensa de técnicas de PCGML em [L78](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L78);
- parágrafo de iniciativa mista em 5.7.1, se não for usado na Metodologia;
- redundâncias entre 5.1.3 (missão × espaço) e 5.5.4 (lógica × espacial). Em 5.5.4, remeta à 5.1.3 em vez de reexplicar.

Confirme o limite de páginas com as normas do curso.

---

## 7. Prioridades para a próxima versão

1. **Conferir todas as citações** e substituir as que não sustentam a afirmação (tabela 6.2), incluindo as fontes primárias da tabela 6.3 para os conceitos de base.
2. **Corrigir os erros conceituais em vermelho:** PCGRL × definição de PCGML; direção × orientação; *affordance*; *exposure bias*; pose/escala/dimensão; AABB × OBB; "garantias estruturais" em [L231](file:///c:/Users/gusta/OneDrive/Documentos/PTCC/modelo_latex_TCC/fundamentacao_19_10.tex#L231); "chave após a porta"; CSS.
3. **Dar rigor aos dígrafos:** graus de entrada/saída, caminho orientado, conectividade forte/fraca, alcançabilidade não simétrica, **ordenação topológica** e sua relação com ciclos.
4. **Concretizar a 5.4.3** com 2 ou 3 evidências empíricas específicas (modelo, tarefa e falha observada).
5. **Reequilibrar a 5.3.2:** menos história da arquitetura, mais papéis e capacidades dos LLMs em PCG, e uma frase sobre a relação LLM × PCGML.
6. **Reduzir a densidade de citações** e a extensão total (seções 6.1 e 6.4).
7. **Ajustes de arquivo:** ordem do `\include` no `main.tex`, erro "contradictórios" no arquivo compilado, chave `inproceedings` e parágrafo de síntese ao final.

---

## 8. Orientação final

O capítulo agora **cumpre a função** que discutimos na revisão anterior: apresenta o objeto (fase e layout 3D), situa PCG, PCGML e LLMs, discute as limitações espaciais, fornece a base de grafos e de representação 3D e separa com clareza validade, navegabilidade e solvabilidade, sem invadir a Metodologia. A estrutura está aprovada e não precisa ser mexida.

O trabalho que resta é de **acabamento acadêmico**: ancorar cada conceito na fonte certa, eliminar as poucas imprecisões técnicas e tornar o texto mais enxuto. Feito isso, a Fundamentação estará em condições de sustentar com segurança o capítulo metodológico, e você poderá avançar para a Metodologia, onde entram as escolhas concretas (representação do grafo, esquema de serialização, algoritmo de posicionamento, motor e rotinas de validação).
