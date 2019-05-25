---
Título: "Notas de Econometria II"
---

# Cap. 13 - Interpolando *cross sections* no tempo

## Intro

Análise de dois tipos diferentes de estruturas de dados: 
* *Cross sections* interpoladas independentemente: amostras randômicas de uma população obtidas em diferentes pontos no tempo; e
* Dados em painel: também conhecido como **dados longitudinais**, são dados que seguem o mesmo indivíduo através do tempo.

Para análise econométrica de dados em painel, não é possível assumir que as observações são independentemente distribuídas através do tempo. Por exemplo, fatores não observados (como habilidade) que afetam o salário de alguém em 1990, também afetaria o salário em 1991. Assim, os métodos estatísticos desenvolvidos para esse tipo de dado buscam remover atributos não observados e constantes no tempo das unidades em estudo.

## 13.1 *Cross sections* interpoladas independentemente

Tipicamente, para refletir o fato de que as populações podem ter diferentes distribuições através do tempo, usa-se diferentes interceptos através do tempo usando variáveis *dummy*
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYzNDU4NTg4NCwtNjY3MDYxMzc1XX0=
-->