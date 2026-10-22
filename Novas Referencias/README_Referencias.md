# Novas Referências Bibliográficas (Fundamentação Teórica - TCC)

Este diretório reúne os documentos complementares e referências fundamentais incorporadas na revisão aprofundada da Fundamentação Teórica (`fundamentacao_20_10.tex`), conforme apontado nas diretrizes de revisão acadêmica.

---

## 1. Artigos em Acesso Aberto com Download Concluído (Nesta Pasta)

Os seguintes artigos científicos estão disponíveis em PDF diretamente nesta pasta:

1. **`Vaswani_et_al_2017_Attention_Is_All_You_Need.pdf`**
   - **Autores:** Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Łukasz Kaiser, Illia Polosukhin.
   - **Título:** *Attention Is All You Need* (NeurIPS 2017).
   - **ArXiv:** [arXiv:1706.03762](https://arxiv.org/abs/1706.03762)
   - **Uso no TCC:** Sustentação teórica da arquitetura Transformer, mecanismo de auto-atenção (*self-attention*) e base dos Modelos de Linguagem de Grande Porte (Seção 5.3).

2. **`Brown_et_al_2020_Language_Models_Are_Few_Shot_Learners.pdf`**
   - **Autores:** Tom B. Brown et al.
   - **Título:** *Language Models are Few-Shot Learners* (NeurIPS 2020).
   - **ArXiv:** [arXiv:2005.14165](https://arxiv.org/abs/2005.14165)
   - **Uso no TCC:** Conceituação do aprendizado em contexto (*in-context learning* / ICL), prompting zero-shot/few-shot e distinção formal em relação ao treinamento de modelos generativos (Seção 5.3).

3. **`Khalifa_et_al_2020_PCGRL.pdf`**
   - **Autores:** Ahmed Khalifa, Philip Bontrager, Sam Earle, Julian Togelius.
   - **Título:** *PCGRL: Procedural Content Generation via Reinforcement Learning* (AIIDE 2020).
   - **ArXiv:** [arXiv:2001.09200](https://arxiv.org/abs/2001.09200)
   - **Uso no TCC:** Caracterização do paradigma de aprendizado por reforço em PCG, operando via recompensa cumulativa e exploração dinâmica de estados (Seção 5.3).

4. **`Karth_Smith_2017_WaveFunctionCollapse.pdf`**
   - **Autores:** Isaac Karth, Adam M. Smith.
   - **Título:** *WaveFunctionCollapse is Constraint Solving in the Wild* (FDG 2017).
   - **DOI:** [10.1145/3102071.3110566](https://doi.org/10.1145/3102071.3110566)
   - **Uso no TCC:** Fundamentação de métodos construtivos baseados em restrições locais de adjacência (WFC) e propagação de restrições em PCG (Seções 5.2 e 5.7).

5. **`Togelius_et_al_2011_Search_Based_PCG.pdf`**
   - **Autores:** Julian Togelius, Georgios N. Yannakakis, Kenneth O. Stanley, Cameron Browne.
   - **Título:** *Search-Based Procedural Content Generation: A Taxonomy and Survey* (IEEE TCIAIG 2011).
   - **DOI:** [10.1109/TCIAIG.2011.2148116](https://doi.org/10.1109/TCIAIG.2011.2148116)
   - **Uso no TCC:** Taxonomia canônica de PCG (online vs. offline, determinístico vs. estocástico, construtivo vs. baseado em busca) e espaço de busca guiado por funções de avaliação (Seção 5.2).

6. **`Liapis_et_al_2013_Sentient_Sketchbook.pdf`**
   - **Autores:** Antonios Liapis, Georgios N. Yannakakis, Julian Togelius.
   - **Título:** *Sentient Sketchbook: Computer-Aided Game Level Authoring* (FDG 2013).
   - **Repositório Institucional:** [OAR@UM Handle 123456789/29607](https://www.um.edu.mt/library/oar/handle/123456789/29607)
   - **Uso no TCC:** Ferramentas de autoria mista (*mixed-initiative*), geração assistida por computador e computação de métricas espaciais em tempo de autoria (Seção 5.7).

7. **`Garcez_Lamb_2023_Neurosymbolic_AI_3rd_Wave.pdf`**
   - **Autores:** Artur d'Avila Garcez, Luís C. Lamb.
   - **Título:** *Neurosymbolic AI: The 3rd Wave* (Artificial Intelligence Review 2023).
   - **ArXiv:** [arXiv:2012.05876](https://arxiv.org/abs/2012.05876) / **DOI:** [10.1007/s10462-023-10448-w](https://doi.org/10.1007/s10462-023-10448-w)
   - **Uso no TCC:** Fundamentação epistemológica da integração neuro-simbólica (conexão entre raciocínio simbólico/restrições lógicas e modelos conexionistas generativos) (Seção 5.7).

---

## 2. Referências Adicionais (Livros Fundamentais e Artigos Clássicos)

Para as referências que consistem em livros-texto consagrados ou artigos sob paywall de editoras acadêmicas, segue o detalhamento com DOI e informações de consulta:

### Livros Clássicos de Referência
1. **Totten (2014)**
   - **Título:** *An Architectural Approach to Level Design*
   - **Autor:** Christopher W. Totten
   - **Editora:** CRC Press / Taylor & Francis, 2014.
   - **ISBN:** 978-1466585416
   - **Uso no TCC:** Definição formal de *Level Design*, fluxo de navegação, ritmo (*pacing*) e a relação entre arranjo espacial e experiência do jogador (Seção 5.1).

2. **Cormen et al. (2009)**
   - **Título:** *Introduction to Algorithms* (3ª edição)
   - **Autores:** Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, Clifford Stein.
   - **Editora:** MIT Press, 2009.
   - **ISBN:** 978-0262033848
   - **Uso no TCC:** Definição formal de dígrafos $G=(V, E)$, graus de entrada/saída, caminhos orientados, conectividade forte e ordenação topológica em DAGs (Seção 5.5).

3. **Russell & Norvig (2021)**
   - **Título:** *Artificial Intelligence: A Modern Approach* (4ª edição)
   - **Autores:** Stuart Russell, Peter Norvig.
   - **Editora:** Pearson, 2021.
   - **ISBN:** 978-0134610993
   - **Uso no TCC:** Formulação formal de Problemas de Satisfação de Restrições (CSP), consistência de arcos e algoritmos de busca com retrocesso (Seção 5.7).

4. **Ericson (2004)**
   - **Título:** *Real-Time Collision Detection*
   - **Autor:** Christer Ericson
   - **Editora:** Morgan Kaufmann / Elsevier, 2004.
   - **ISBN:** 978-1558607323
   - **Uso no TCC:** Volumes delimitadores hierárquicos: formulação matemática e distinção geométrica entre AABB (*Axis-Aligned Bounding Box*) e OBB (*Oriented Bounding Box*) (Seção 5.6).

5. **Gibson (1979)**
   - **Título:** *The Ecological Approach to Visual Perception*
   - **Autor:** James J. Gibson
   - **Editora:** Houghton Mifflin, Boston, 1979.
   - **ISBN:** 978-0898599596
   - **Uso no TCC:** Conceito ecológico estrito de *affordance* (propriedades funcionais e possibilidades de ação que o ambiente oferece ao agente) (Seção 5.4).

### Artigos Clássicos Complementares
6. **Harnad (1990)**
   - **Título:** *The Symbol Grounding Problem*
   - **Autor:** Stevan Harnad
   - **Periódico:** *Physica D: Nonlinear Phenomena*, 42(1-3), pp. 335-346, 1990.
   - **DOI:** [10.1016/0167-2789(90)90087-6](https://doi.org/10.1016/0167-2789(90)90087-6)
   - **Uso no TCC:** Fundamentação filosófico-computacional do problema de ancoragem semântica (*symbol grounding*) e descolamento perceptual em modelos puramente textuais (Seção 5.4).

7. **Cohn & Renz (2008)**
   - **Título:** *Qualitative Spatial Representation and Reasoning*
   - **Autores:** Anthony G. Cohn, Jochen Renz.
   - **Obra:** *Handbook of Knowledge Representation*, Elsevier, pp. 559-598, 2008.
   - **DOI:** [10.1016/S1574-6526(07)03013-1](https://doi.org/10.1016/S1574-6526(07)03013-1)
   - **Uso no TCC:** Raciocínio espacial qualitativo (direção vs. orientação intrínseca, topologia e mereologia) (Seção 5.4).

8. **Smith & Mateas (2011)**
   - **Título:** *Answer Set Programming for Procedural Content Generation: A Design Space Approach*
   - **Autores:** Adam M. Smith, Michael Mateas.
   - **Periódico:** *IEEE Transactions on Computational Intelligence and AI in Games*, 3(3), pp. 187-200, 2011.
   - **DOI:** [10.1109/TCIAIG.2011.2158545](https://doi.org/10.1109/TCIAIG.2011.2158545)
   - **Uso no TCC:** Paradigma de Programação em Conjuntos de Respostas (ASP) para formalização declarativa do espaço de design e geração por restrições (Seções 5.2 e 5.7).

9. **Snook (2000)**
   - **Título:** *Simplified 3D Movement with Navigation Meshes*
   - **Autor:** Greg Snook.
   - **Obra:** *Game Programming Gems*, Charles River Media, pp. 288-295, 2000.
   - **Uso no TCC:** Origem seminal da técnica de Malhas de Navegação (*Navigation Meshes* / NavMesh) e particionamento de superfícies contínuas transitáveis em polígonos convexos (Seção 5.8).

10. **Hart, Nilsson & Raphael (1968)**
    - **Título:** *A Formal Basis for the Heuristic Determination of Minimum Cost Paths*
    - **Autores:** Peter E. Hart, Nils J. Nilsson, Bertram Raphael.
    - **Periódico:** *IEEE Transactions on Systems Science and Cybernetics*, 4(2), pp. 100-107, 1968.
    - **DOI:** [10.1109/TSSC.1968.300136](https://doi.org/10.1109/TSSC.1968.300136)
    - **Uso no TCC:** Formulação matemática canônica do algoritmo A*, critério de admissibilidade da heurística $h(n)$ e garantia de caminhos de custo mínimo no grafo dual da NavMesh (Seção 5.8).

11. **Bengio, Simard & Frasconi (1994)**
    - **Título:** *Learning Long-Term Dependencies with Gradient Descent is Difficult*
    - **Autores:** Yoshua Bengio, Patrice Simard, Paolo Frasconi.
    - **Periódico:** *IEEE Transactions on Neural Networks*, 5(2), pp. 157-166, 1994.
    - **DOI:** [10.1109/72.279181](https://doi.org/10.1109/72.279181)
    - **Uso no TCC:** Problema do esvanecimento e explosão do gradiente (*vanishing/exploding gradients*) em redes neurais recorrentes clássicas (Seção 5.3).
