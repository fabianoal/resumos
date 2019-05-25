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

Tipicamente, para refletir o fato de que as populações podem ter diferentes distribuições através do tempo, usa-se diferentes interceptos através do tempo usando variáveis *dummy*. O método é conhecido como diferenças em diferenças. 

## 13.2 Diferenças em diferenças

Pode-se se usar simples subtração de coeficientes em diferentes regressões, ou usar diferentes interceptos e interações. Essa metodologia é especialmente interessante quando dados emergem de experimentos naturais (*quasi-experimento*).

## 13.3 Dados em Painel: 2 períodos

Modelo de efeitos não observados:

$$y_{it} = \beta_0 + \delta_0 d2_t + \beta_1 x_{it} +  a_i + u_{it}, t= 1,2$$

Onde:
* $i$ denota a unidade de *cross section*
* $d2$ é 0 quando $t=1$ e 2 quando $t=2$. Obviamente, ela varia em $t$
* $a_i$ denota os efeitos não observados (ou efeitos fixos), ou seja, aqueles que variam de acordo com o indivíduo mas não variam de acordo com o tempo. Outros nomes: heterogeneidade não observada/heterogeneidade individual (da unidade de *cross section* utilizada.
* $u_{it}$ denota o termo de erro tanto no tempo como no indivíduo. Outros nomes: erro idiossincrático/erro variável no tempo.

Exemplo para dados de criminalidade:

$$crmrte_{it} = \beta_0 + \delta_0 d87_t + \beta_1 unem_{it} + a_i + u_{it}$$

Onde:
* $a_i$ denota o *efeito não observado da cidade*, ou o *efeito fixo da cidade*.

Os problemas em usar OLS para estimar o modelo como se fosse *cross section* interpolada independente:

1. Seria necessário afirmar que $a_i$ não é correlacionado com $x_{it}$, ou seja, $y_{it} = \beta_0 + \delta_0 d2_t + \beta_1 x_{it} +  \nu_{it}, t= 1,2$ onde $\nu_{it} = a_i + u_{it}$ é chamado de **erro composto**. Mesmo assumindo que o erro idiossincrático não é correlacionado com $x_{ij}$, a regressão via OLS estaria enviesada se $a_i$ form, de alguma forma, correlacionado com $x_{it}$. Esse viés em OLS interpolada é chamado de viés de heterogeneidade e representa  um viés causado pela omissão de uma variável constante no tempo.
2. TODO


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMTYyMjczOTIsOTExMDA5NTEwLDE2Mz
g1NDc0MDYsMTQ2MDI1NDM1OCwtNjM0NTg1ODg0LC02NjcwNjEz
NzVdfQ==
-->