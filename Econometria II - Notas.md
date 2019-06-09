---
Título: "Notas de Econometria II"
---

# Cap. 13 - Interpolando *cross sections* no tempo

## Intro

Análise de dois tipos diferentes de estruturas de dados: 
* *Cross sections* interpoladas independentemente: amostras randômicas de uma população obtidas em diferentes pontos no tempo; e
* Dados em painel: também conhecido como **dados longitudinais**, são dados que seguem o mesmo indivíduo através do tempo.

Para análise econométrica de dados em painel, não é possível assumir que as observações são independentemente distribuídas através do tempo. Por exemplo, fatores não observados (como habilidade) que afetam o salário de alguém em 1990, também afetaria o salário em 1991. Assim, os métodos estatísticos desenvolvidos para esse tipo de dado buscam remover atributos não observados e constantes no tempo das unidades em estudo.

## 13.1 Agrupamento independente de cortes transversais ao longo do tempo.

Benefícios: aumento do tamanho da amostra, produzindo estimadores mais precisos.

O agrupamento é útil somente se a a relação entre a variável dependente e pelo menos uma variável dependente for constante ao longo do tempo.

Estruturação: Para refletir o fato de que a população pode ter diferentes distribuições através do tempo, usa-se diferentes interceptos através do tempo usando variáveis *dummy*. 

Em caso de heterocedasticidade ao longo do tempo, pode-se usar erros-padrão robustos. O teste Breusch-Pagan é obtido fazendo-se a regressão do quadrado dos resíduos de MQO sobre *todas* as variáveis independentes (inclusive as dummies).

Um procedimento de mínimos quadrados ponderados (ou mínimos quadrados ponderados factível) deve explicar as variâncias que possivelmente mudem ao longo do tempo.

Outra opção: interagir as variáveis explicativas com as variáveis *dummies* para verificar como o efeito da variável mudou ao longo do tempo.

Fazer a interação de todas as variáveis independentes com todas as *dummies* temporais equivale a estimarmos modelos diferentes para cada fatia temporal.

Pode-se utilizar um teste **Chow** para avaliar se há de fato uma diferença entre períodos para verificar a necessidade de realizar todas as interações. (O teste **Chow** pode ser realizado com vários períodos de tempo).

Cabe lembrar que, usando o teste **Chow** com regressões separadas e calculando-se a estatística $F$, tem-se uma estatística **não** robusta em relação à heterocedasticidade. Para executar um teste robusto, deve-se executar um teste **Chow** interagindo cada variável explicativa com cada variável dummy temporal e realizar um teste de significância conjunta robusto.

### Experimentos naturais ou quase-experimento.

Para controlar diferenças sistemáticas entre os grupos de controle e de tratamento, precisamos de dois períodos de dados (anterior e posterior à aplicação do tratamento), resultando em uma amostra com quatro grupos 

* $A$ grupo de controle
* $B$ grupo de tratamento
* $d$ *
* $d2$ *dummy* para o segundo período de tempo
A equação de interesse é:

$$y = \beta_0 +\delta_0 d2 + \beta_1 dB + \delta_1 d2 \cdot dB + e$$


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

A ideia de coletar dados em painel é justamente permitir a correlação entre a variável explanatória e os efeitos fixos para que possamos pegar só o que diferencia. Dessa forma, o método **primeira diferença** permite obter a diferença 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg0MjE1ODA4MSwxMjQ3MDY3MjY2LDQ4Nz
g1MDIwMCwxNDI0MTY5NjgsLTk0MjA1NTc0Miw5MTEwMDk1MTAs
MTYzODU0NzQwNiwxNDYwMjU0MzU4LC02MzQ1ODU4ODQsLTY2Nz
A2MTM3NV19
-->