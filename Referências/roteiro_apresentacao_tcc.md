# Roteiro de Apresentação — TCC

**Tema:** Geração de Layouts de Fases 3D Assistida por Modelos de Linguagem de Grande Porte  
**Tempo estimado:** ~7 minutos

---

## Slide 1 — Título | ~20 segundos

> Boa noite. Meu nome é Gustavo Rafael Nunes Durães e hoje vou apresentar meu trabalho sobre geração de layouts de fases 3D assistida por modelos de linguagem de grande porte.
>
> A proposta do trabalho é utilizar modelos de linguagem para auxiliar na criação da estrutura lógica de uma fase 3D, utilizando o Godot para fazer a validação e a construção efetiva desse ambiente.

---

## Slide 2 — Motivação e área de estudo | ~50 segundos

> O trabalho está inserido principalmente na área de geração procedural de conteúdo, ou PCG, combinada com inteligência artificial.
>
> A motivação vem de dois problemas principais.
>
> O primeiro é que a criação manual de fases pode ser um processo bastante demorado, principalmente quando precisamos definir salas, caminhos, ramificações e regras de progressão.
>
> O segundo problema é que, embora os LLMs sejam muito bons em interpretar linguagem natural e gerar estruturas lógicas, eles não são confiáveis quando precisamos trabalhar diretamente com geometria 3D e coordenadas espaciais.
>
> Então a ideia do trabalho é separar essas duas responsabilidades: deixar a parte criativa e estrutural para o LLM e deixar os cálculos espaciais e as garantias de funcionamento para algoritmos determinísticos.

**Frase importante para decorar:**

> **O LLM pensa na fase; o Godot constrói e verifica a fase.**

---

## Slide 3 — Divisão de responsabilidades | ~50 segundos

> Essa divisão pode ser entendida como se tivéssemos dois profissionais trabalhando juntos.
>
> O LLM funciona como um arquiteto. Ele recebe uma descrição em linguagem natural, entende o que o usuário quer e transforma isso em uma planta lógica da fase.
>
> Já o módulo desenvolvido no Godot funciona como um engenheiro. Ele recebe essa planta, verifica se ela respeita as regras, calcula as posições dos elementos e constrói a fase.
>
> Dessa forma, o LLM não precisa calcular coordenadas X, Y e Z, nem precisa saber exatamente como instanciar uma parede ou construir um corredor.
>
> Ele trabalha principalmente com a lógica da fase, representada por um grafo estruturado em JSON.

---

## Slide 4 — Processamento da linguagem | ~1 minuto

> Para exemplificar o funcionamento, podemos imaginar que o usuário forneça um prompt como este.
>
> Ele pede uma pequena masmorra contendo uma sala inicial, duas salas de combate, uma sala opcional com tesouro e uma sala final com um chefe. Além disso, o jogador precisa encontrar uma chave antes de conseguir entrar na sala do chefe.
>
> O LLM interpreta essa solicitação e identifica os elementos necessários: a sala inicial, as salas de combate, o tesouro, o chefe, a chave e a porta trancada.
>
> Mas aqui existe um detalhe importante: ele não cria diretamente o mapa 3D.
>
> Em vez disso, ele gera uma representação lógica. Por exemplo: início leva ao combate 1; o combate 1 pode levar ao tesouro ou ao combate 2; no combate 2 encontramos a chave; e então podemos chegar ao chefe.
>
> Essa representação é armazenada em um grafo JSON.

### Estrutura para visualizar

**Início → Combate 1 → Combate 2 + Chave → Chefe**

Ramificação:

**Combate 1 → Tesouro**

---

## Slide 5 — Validação determinística | ~1 minuto

> Depois que o LLM gera esse grafo, entra a segunda parte do sistema: a validação determinística.
>
> Aqui não temos mais um modelo tentando interpretar o que é correto. Temos regras programadas que precisam ser satisfeitas.
>
> Por exemplo: deve existir apenas uma sala inicial; deve existir uma sala final alcançável; todas as salas obrigatórias precisam ser acessíveis; uma chave precisa estar disponível antes da porta que ela abre; e salas opcionais não podem bloquear o caminho principal.
>
> Então o sistema analisa o grafo e determina se ele é válido ou não.
>
> Isso é importante porque um LLM pode gerar uma estrutura que parece fazer sentido textualmente, mas que não funciona como uma fase jogável.

### Exemplo de erro

> Por exemplo, imagine que o LLM coloque a chave depois da porta trancada. Para o modelo, a estrutura pode parecer válida, mas para o jogador isso cria um bloqueio impossível.
>
> O validador consegue identificar esse problema porque ele verifica a ordem de acesso entre os elementos.

---

## Slide 6 — Construção do mapa e testes | ~1 minuto e 20 segundos

> Depois que o grafo é aprovado, podemos finalmente construir a fase.
>
> O construtor recebe o JSON e utiliza módulos previamente definidos no Godot, como salas de combate, sala inicial, sala de recompensa, sala do chefe e corredores.
>
> A partir dessas informações, o algoritmo calcula onde cada elemento deve ser colocado.
>
> E aqui temos outra diferença importante em relação ao LLM: as coordenadas não são escolhidas livremente pelo modelo.
>
> Elas são calculadas utilizando as dimensões das salas, o tamanho dos corredores e as distâncias necessárias entre os elementos.
>
> Depois da construção, o sistema realiza novos testes. Ele verifica, por exemplo, se existem sobreposições, se os corredores estão conectados, se as portas estão corretamente ligadas e se o jogador consegue realmente chegar aos pontos importantes da fase.
>
> Também são utilizadas ferramentas do próprio Godot para verificar navegação, caminhos, colisões e aspectos físicos da construção.

### Fluxo

**Prompt → LLM → JSON → Validação → Construção → Testes**

> Portanto, o processo não termina quando o LLM gera o JSON. O resultado ainda precisa passar pela validação e pelos testes da própria engine.

---

## Slide 7 — Arquitetura do sistema | ~1 minuto

> A arquitetura proposta pode ser resumida nesses passos.
>
> Primeiro, o usuário fornece um prompt textual.
>
> Depois, o LLM interpreta esse prompt e cria a lógica básica da fase.
>
> Essa lógica é transformada em um grafo JSON.
>
> O grafo passa pela validação determinística.
>
> Se estiver correto, a fase é construída e testada no Godot.
>
> Caso sejam encontrados problemas, essas informações podem ser utilizadas para gerar um feedback e alimentar novamente o processo.
>
> Então temos um ciclo de geração, validação, construção, teste e, quando necessário, correção.

---

## Slide 8 — Objetivos e resultados esperados | ~50 segundos

> A partir dessa arquitetura, o trabalho pretende avaliar principalmente o impacto da validação na geração das fases.
>
> Um dos objetivos é comparar a geração de fases com e sem essa etapa de validação.
>
> Também existe como resultado esperado a possibilidade de desenvolver um addon para o Godot integrado a APIs de modelos de linguagem.
>
> Na prática, os principais desafios são garantir que a linguagem natural seja corretamente transformada em uma estrutura lógica, que essa estrutura respeite as regras do jogo e, principalmente, que a fase gerada seja solucionável.

---

## Slide 9 — Encerramento | ~30 segundos

> Então, resumindo, a proposta não é fazer com que o LLM construa sozinho uma fase 3D.
>
> A proposta é utilizar o que ele faz melhor, que é interpretar linguagem natural e tomar decisões estruturais, enquanto os cálculos geométricos, a validação e a construção ficam sob responsabilidade de algoritmos determinísticos.
>
> Dessa forma, o LLM funciona como um arquiteto que define a planta conceitual, enquanto o sistema no Godot funciona como o engenheiro que verifica e executa essa construção.
>
> Essa é a ideia central do trabalho. Muito obrigado pela atenção.

---

# ⏱️ Distribuição do tempo

| Slide | Tempo |
|---|---:|
| 1 — Título | 0:20 |
| 2 — Motivação | 0:50 |
| 3 — Responsabilidades | 0:50 |
| 4 — Processamento da linguagem | 1:00 |
| 5 — Validação | 1:00 |
| 6 — Construção e testes | 1:20 |
| 7 — Arquitetura | 1:00 |
| 8 — Objetivos | 0:50 |
| 9 — Encerramento | 0:30 |
| **Total** | **~7:40** |

> **Observação:** durante o ensaio, faça alguns cortes para chegar a aproximadamente 7 minutos. Na apresentação real, pausas e comentários naturalmente aumentam o tempo.

---

# 🧠 O que realmente decorar

Não é necessário decorar o texto palavra por palavra. Decore esta sequência:

1. **Problema** — Fazer fases manualmente é demorado + LLM não é confiável para geometria 3D.
2. **Ideia** — Separar responsabilidades.
3. **LLM** — Linguagem natural → lógica → grafo JSON.
4. **Validador** — Verifica regras.
5. **Godot** — JSON → posições → salas → corredores.
6. **Testes** — Navegação + colisões + conectividade + solvabilidade.
7. **Feedback** — Se der problema → corrige → testa novamente.
8. **Objetivo** — Comparar geração com e sem validação.
9. **Conclusão** — **LLM pensa; algoritmo verifica e constrói.**

## Frase-chave

> **LLM pensa; algoritmo verifica e constrói.**
