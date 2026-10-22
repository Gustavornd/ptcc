# Resumo de Alterações e Refatoração - 29/09/2026

Este documento centraliza todas as ações, correções e revisões bibliográficas aplicadas ao projeto no esforço de reescrever a Fundamentação Teórica, alinhando-a rigorosamente aos comentários do orientador.

## 1. Compreensão da Estrutura do Projeto LaTeX
* **Adaptação à Classe:** Identificado que o template `modelo_latex_TCC/main.tex` opera sobre a classe `abntex2` no modo `article` (derivado do modelo SIC).
* **Correção de Hierarquia:** O uso indevido de `\chapter` foi substituído por `\section`, e todas as ramificações de `\section` foram rebaixadas para `\subsection`, prevenindo erros de compilação.
* **Mecanismo de Citação:** O projeto utiliza `biblatex` (padrão ABNT). Todas as menções a `\textcite` foram expurgadas do texto novo, padronizando-se apenas o uso de `\cite` e reescrevendo as sentenças de forma impessoal.

## 2. Ingestão de Novas Referências (Literatura)
* Foram adicionados 5 novos artigos cruciais ao repositório, indicados no Guia de Revisão do orientador (Tópico 8):
  1. *Adventures in Level Design* (Dormans, 2010).
  2. *Procedural Content Generation in Games* (Shaker, 2016).
  3. *Designing Procedurally Generated Levels* (van der Linden, 2013).
  4. *Procedural Generation of Dungeons* (van der Linden, 2014).
  5. *Tanagra: a mixed-initiative level design tool* (Smith, 2010).
* As análises detalhadas destes artigos e sua conexão com a Arquitetura Híbrida do TCC (LLM = Arquiteto, Godot = Engenheiro) foram anexadas ao arquivo `Revisao_Literatura_TCC.md`.

## 3. Criação do arquivo `fundamentacao_revisada.tex`
A fundamentação teórica antiga foi descartada por conter menções prematuras à metodologia (GDScript, Godot, NavMeshRegion3D). Um novo documento (`fundamentacao_revisada.tex`) foi gerado do zero e refinado após uma severa **auditoria (Deep Investigator)** cruzando as anotações do PDF e o DOCX. As principais intervenções foram:

* **Seção 5.1 (Fases e Level Design):** Posicionada a distinção fundamental entre *missão* (lógica) e *espaço* (físico), baseada em Dormans (2010). A dicotomia equivocada de "topologia x topografia" foi removida a pedido do orientador.
* **Seção 5.3 (PCGML e LLMs):** Adicionada a explicação sobre representações estruturadas intermediárias, estabelecendo que o **JSON atua como o mecanismo de serialização** para traduzir o raciocínio semântico para a camada sistêmica.
* **Seção 5.4 (Ancoragem Espacial - Spatial Grounding):** A justificativa errônea de que LLMs falham no espaço 3D "por lerem sequências unidimensionais de tokens" foi cortada (conforme PDF comentado). Em substituição, definiu-se corretamente que eles carecem de habilidade inata para processar variáveis absolutas do espaço euclidiano (posição, distância, direção, adjacência).
* **Seção 5.5 (Grafos):** A pedido do guia, o texto foi expandido para fornecer o formalismo matemático de um grafo de ações $G=(V,E)$, incluindo definições rigorosas para *caminhos, ciclos, pesos, rótulos, conectividade e alcançabilidade* da missão antes da instanciação de geometria física.
* **Seção 5.8 (Taxonomia de Validação):** A conclusão do capítulo foi desmembrada em 5 conceitos rigidamente separados (para evitar sobreposição conceitual reprovada na versão anterior):
  1. **Validade Geométrica:** Ausência de *clipping* e colisões indevidas.
  2. **Navegabilidade:** Integridade das malhas (*NavMesh*).
  3. **Pathfinding:** Algoritmos diretores de rota (A*).
  4. **Validade Lógica:** Coerência estrutural (ex: portas que não bloqueiam a si mesmas).
  5. **Solvabilidade:** Possibilidade concreta de concluir a fase cumprindo todas as regras mecânicas impostas.

## 4. Alinhamento de Keys Bibliográficas
As chaves de citação no `.tex` foram rigorosamente sincronizadas com o `referencias.bib` do projeto (ex: `\cite{dormans2010}`, `\cite{pcgbook}`, `\cite{sun2024roomplanner}`, `\cite{inproceedings}`). Identificou-se ainda a presença de alguns PDFs na pasta `Referências` que atualmente não constam ou não possuem rastreabilidade direta no arquivo `referencias.bib`.

---
*Próximos Passos Sugeridos:* Iniciar a formulação do Capítulo de **Metodologia**, aproveitando todos os detalhes operacionais (Godot, C#, heurísticas do JSON, algoritmo determinístico do addon) que foram limpos desta base teórica.
