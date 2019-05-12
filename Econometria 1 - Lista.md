---
title: "Lista Exercícios 1"
author: "Fabiano Andrade Lima"
date: "28/04 ~ 12/05 de 2019"
output: word_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## Pré requisitos

```{r setup_2, echo=FALSE, include=TRUE}
knitr::opts_chunk$set(include = FALSE)

#install.packages("wooldridge")
#install.packages("dplyr")

library("wooldridge")
library(dplyr)

lmp <- function (modelobject) {
	if (class(modelobject) != "lm") stop("Not an object of class 'lm' ")
	f <- summary(modelobject)$fstatistic
	p <- pf(f[1],f[2],f[3],lower.tail=F)
	attributes(p) <- NULL
	return(p)
}
```

## Questão 1

Em um esforço de determinar se comparecer às classes melhora o desempenho do estudante de graduação, o professor Romer desenvolveu a seguinte equação:

$$G_{i} = \beta_{0} + \beta_1ATT_i +\beta_2PS_i + u_i $$

Onde:

* $G_i$ é a nota do estudante $i$ na classe do professor Romer;
* $ATT_i$ é a porcentagem das aulas nas quais o aluno $i$ compareceu;
* $PS_i$ é a porcentagem das listas de exercícios completadas pelo estudante $i$.

a) Antes de rodar sua regressão, quais sinais você espera para os coeficientes $\beta_1$ e $\beta_2$? Explique.

Resposta: A princípio, seria de se esperar que tanto $\beta_1$ como $\beta_2$ tivessem coeficientes positivos, visto que ambas atividades contribuem para o aprendizado dos alunos.

b) Claramente interprete os coeficientes $\hat{\beta_1}$ e $\hat{\beta_2}$.

Resposta: Os coeficientes $\hat{\beta_1}$ e $\hat{\beta_2}$ são estimadores dos respectivos parâmetros populacionais $\beta_1$ e $\beta_2$.

O Prof Romer estimou a equação acima. Sua base de dados inclui 195 estudantes e obteve as seguintes estimativas:

$$\hat{\beta_0} = 1,07; \hat{\beta_1} = 1,74; \hat{\beta_2}=0,60;R^2 =0,33$$

c) Estes sinais satisfazem suas expectativas?

Sim, conforme exposto na resposta (a)

(d) Suponha que um aluno médio gaste no trimestre 25 horas com aulas e 50 horas para completar todas as listas de exercícios no trimestre. Se este estudante tivesse somente uma hora a mais para se dedicar ao curso e melhorar sua nota, deveria o estudante ir para a aula ou trabalhar na lista de exercícios por mais uma hora? (nota: Você não pode somente olhar para os coeficientes para responder a esta questão; os coeficientes precisam ser convertidos para refletir as horas gastas durante o trimestre com aulas e com listas de exercícios).


```{r, include=TRUE}
b0 = 1.07

b1 = 1.74
attm_h = 25
beneficio_b1 = b1 * (1 / attm_h)

b2 = 0.60
ps_h = 50
beneficio_b2 = b2 * (1/ ps_h)

```
O benefício de um aumento de 1 hora em $\beta_1$ resultaria em uma aumento de `r beneficio_b1`, que é maior que um aumento de uma hora em $\beta_2$ que resultaria em um acréscimo de `r beneficio_b2`.

(e) Agora, supondo que ao invés de 25 horas com aulas e 50 com exercícios, o estudante gastasse 50 horas com aulas e somente 10 com litas. como o estudante deveria gastar sua hora, aula ou lista?

```{r, include=TRUE, echo=FALSE}
attm_h = 50
ps_h = 10

beneficio_b1 = b1 * (1 / attm_h)
beneficio_b2 = b2 * (1/ ps_h)

```

Nesse caso, o benefício de um aumento de uma hora na lista representaria um aumento de `r beneficio_b2`, um valor maior que `r beneficio_b1` no caso do gasto desse mesmo valor com aula.

(f) Considerando suas respostas para as partes (d) e (e), você pode concluir que, sozinha, a magnitude dos coeficientes tem importância relativa.

Dados que os coeficientes se aplicam a uma variável de controle, sua importância está intimamente ligada à construção/magnitude da variável de controle. O coeficiente sozinho não tem poder interpretativo suficiente a respeito de seu impacto no resultado que se deseja estudar.

(g) O que um $R^2$ de 0.33 implica?

Implica que o modelo é capaz de explicar 33% da variação das notas em função das variáveis usadas.

(h) Você acha que os coeficientes $\hat{\beta_1}$ e $\hat{\beta_2}$ são não-viesados? Explique.

Quatro são as hipóteses para se obter estimadores não enviesados:

1. Linearidade nos parâmetros;
1. Amostragem aleatória;
1. Média condicional do erro igual a zero
1. Variação amostral na variável independente.

Com respeito à linearidade dos parâmetros, creio que seja possível aventar a posssibilidade de que ela não seja demosntrada nos dados. A distribuição dos percentuais de horas de aula e de esforço com lista de exercícios muito provavelmente segue um padrão não linear. 

Com respeito à amostragem aleatória, uma vez que não há informações de como foi realizado o processo para colher as amostras, não é possível afirmar que esse critério tenha sido corretamente atendido.

Também não é possível afirmar nada sobre a variação amostral das variáveis independentes, uma vez que não há nenhuma informação disponível sobre a distribuição desses dados.

Assim, não é possível afirmar nada a respeito do viés desses coeficientes.

## Questão 2

A equação seguinte descreve o preço mediano das residências de uma comunidade em termos da quantidade de poluição (*ox*, de óxido nitroso) e do número médio de cômodos nas residências da comunidade (*cmods*):

$$log(price) = \beta_0 + \beta_1 log(oxn) + \beta_2 comods +u$$

(i) Quais são os prováveis sinais de $\beta_1$ e $\beta_2$? Qual é a interpretação de $\beta_1$? Explique.

A princípio, $\beta_1$ deveria ter sinal negativo, uma vez que a presença de poluição na área onde se situa o imóvei seria um fator de desvalorização do preço do mesmo. Com respeito a $\beta_2$, seria razoável esperar um sinal positivo, uma vez que a quantidade de cômodos indica o tamanho da casa, e esse é um fator fundamental na avaliação de preços de imóveis.

Como $\beta_1$ interage com $\log oxn$, e a variável dependente também é $\log price$, a interpretação seria a elasticidade do preço do imóvel com relação à quantidade de poluição, ou seja, uma variação de 1% na poluição corresponderia à uma variação de $\beta_1$% no preço do imóvel.

(ii) Porque *oxn* (ou, mais precisamente, $\log oxn$) e $comods$ deveriam ser negativamente correlacionados? Se esse é o caso, a regressão simples de $\log price$ sobre $\log oxn$ produz um estimador viesado para cima ou para baixo de $\beta_1$?


Se se partir do princípio de que casas com mais quartos geralmente são casas da parte mais rica da população, a qual tem condições de se distanciar mais de áreas poluídas, então, sim, as duas variáveis deveriam ter uma correlação negativa. Sendo esse o caso, uma regressão simples de $\log price$ sobre $\log oxn$ produziria um estimador viesado negativamente (acentuando o efeito de $oxn$).

(iii) Utilizando hprice2, foram estimadas as seguinte equações:

$$\hat{\log price} = 11,71 - 1.043 \log oxn, n= 506, R^2 = 0,264$$


$$\hat{\log price} = 9,23 - 0,718 \log oxn + 0,306 comods, n=506, R^2 = 0,514$$

A relação entre as estimativas da elasticidade do preço das regressões simples e múltipla é a que você previu tomando como base sua resposta na parte (ii)? Pode-se dizer que -0,718 está clarametne mais próximo da elasticidade verdadeira que -1,043?


Sim. Exatamente como previsto, a inclusão de $comods$ na regressão atenuou o efeito de $\log oxn$. os sinais também foram os previstos. Dadas as hipóteses sobre a relação de comodos com poder aquisitivos aqui colocadas, realmente seria possível dizer que o valor de -0,
718 está mais próximo da verdadeira elasticidade que -1,043.

## Questão 3

Em um estudo que relaciona a nota média em curso superior ($supGPA$) ao tempo gasto em várais atividades, você distribui uma pesquisa para vários estudantes. Os estudantes devem responder quantas horas eles despendem, em cada semana, em quatro atividades: estudo, sono, trabalho e lazer. Toda atividade é colocada em uma das quatro categorias de modo que, para cada estudante, a soma das horas nas quatro atividades deve ser igual a 168.

(i) No modelo

$$supPGA = \beta_0 + \beta_1 estudar +\beta_2 dormir + \beta_3 trabalhar +\beta_4 lazer +u$$

faz sentido manter dormir, trabalhar e lazer fixos enquanto $estudar$ varia?

Resposta: Não. Dado que a soma dos quatros tem é um valor fixo, o valor de três variáveis determina o valor da quarta como o resíduo da soma das três menos o valor da quarta.

(ii) Explique a razão de esse modelo violar a hipótese RLM.3


Relembrando as hipóteses da RLM:

* RLM.1: Linearidade dos parâmetros;
* RLM.2: Amostra aleatória;
* RLM.3: Ausência de colinearidade perfeita
* RLM.4: Média condicional zero do erro

Para qualquer observação, é possível reescrever qualquer uma das quatro variávies como uma combinação linear das das outras três, uma vez que todas  somam um valor fixo.

(iii) Como você poderia reformular o modelo de modo que seus parãmetros tivessem uma interpretação útil e ele satisfizese a hipóteses RLM.4?

Pode-se retirar uma das variávies, como lazer, por exemplo. Nesse caso, a RLM.4 estaria sendo atendida e seria possível realizar um estudo do efeito de estudar, dormir e trabalhar sobre a nota no vestibular.

## Questão 4

Assuma que a você é presentada a seguinte equação:

$$Q = \beta_0 + \beta_1 P_1 + \beta_2 P_2 + \beta_3 P_3 +\beta_4 I + \beta_5Pop$$

(a) A equação acima é consdierada um modelo matemático. Por que ela é de interesse limitado para um econometrista?

Normalmente, um econometrista estará interessado nas relações entre as variávies, e não, em quantidades absolutas. Além disso, a equação parece misturar variávies com diferentes granularidades. Se $I$ representa a renda de uma observação e a observação representa um indivíduo, teríamos as variáveis $P$'s e $Pop$ se repetindo para todos os indivíduos.

(b) Como esta equação deve ser modificada para ser considerado um modelo econométrico? O que fica implicado por esta modificação?

Caso se deseje analisar o relacionamento entre quantidades de um determinado produto como função do preço de outros produtos, da renda de seu público alvo e do tamanho de seu mercado, poder-se ia alterar a equação para algo como 

$$\log Q = \beta_0 + \beta_1 \log P_1 + \beta_2 \log P_2 + \beta_3 \log P_3 +\beta_4 \log I_m + \log Pop_m$$

Onde:

* $I_m$ seria a renda média da população do mercado representado na amostra e;
* $Pop_m$ seria a população do mercado representado na amostra. 

Os dados seriam preços de produtos em diferentes mercados, como por exemplo, bairros, universidades ou qualquer outro agrupamento.

Ao invés de mercados, poder-se-ia também alterar o nível de agrupamento para períodos. Assim, preços, renda e população seriam determinados para um período composto de um intervalo pré-determinado, de forma que se pudesse verificar se relacionam essas variáveis em um determinado mercado em função dos preços e da característica da população que a compõe naquele período de tempo.

Assuma que $Q$ acima seja a quantidade de pão de queijo vendidos nas cafeterias da UnB. Dados diários sobre essa demanda foram coletados nos últimos 10 anos para um projeto. $P_1$ é o preço médio dos diferentes tipos de salgados, $P_2$ o preço médio dos diferentes tipos de bolos, $P_3$ é o preço do café expresso, $I$ é a renda média dos estudantes e $Pop$ é a população de estudantes.

(c) Por que estas variávies em particular foram incluídas no modelo como determinantes da demanda por pão de queijo?

O consomo de outros salgoados que não o pão de queijo, bem como o consumo de café parecem influenciar o consumo de pão de queijo. Além disso, a renda do público também pode influenciar nessas quantidades bem como o próprio tamanho da população.

(d) Para cada um dos parãmetros a ser estimados, diga o que você espera dos sinais e explique brevemente.

* $\beta_1$: espera-se um sinal positivo, no sentido que, quanto menor o preço dos salgados que concorrem com o pão de queijo, menor será a quantidade demandada de pão de queijo;
* $\beta_2$: espera-se também um sinal positivo, no sentido que, quanto maior o preço dos bolos, que também podem concorrer com pão de queijo, maior será o consumo de pão de queijo.
* $\beta_3$: espera-se um sinal negativo. O café é um produto complementar ao café, de forma que, um aumento no preço do café ira atuar no sentido inverso na demanda por pão de queijo.
* $\beta_4$: espera-se um sinal positivo. Quanto maior a renda, maior a quantidade de pão de queijo vendida.
* $\beta_5$: espera-se um sinal positivo. Quanto maior o público alvo, maior será a quantidade demandada.

(e) O que você faria se tivesse que obter os dados para este modelo? Por onde começaria?

Começaria por um levantamento junto às lanchonetes sobre os dados das vendas desses grupos de produto bem como seu histórico de preço. Posteriormente, faria um leventamento junto à administração da UnB a respeito dos dados socioeconômicos dos estudantes nos vários períodos analisados bem com as listas de presença nas aulas dos períodos analisados. Com esses dados, talvez fosse possível realizar uma regressão com dados populacionais ao invés de amostrais, o que traria um resultado muito mais exato.

## Questão 5

Um problema de interesse das autoridades da saúde é determinar os efeitos que fumar durante a gravidez exerce sobre a saúde do recém-nascido. uma medida da saúde do recém-nascido é o peso de nascimento (pesonas); um peso de nascimento muito baixo pode atribuir á criaçã o risco de contrair várias doenças. Como outros fatores que afetam o peso de nascimento, além de fumar cigarros (cigs), estão provavelmente correlacionados com o fumo, devemos levar em consideração tais fatores. Por exemplo, uma renda (rendfam) maior geralmente permite acesso a pré-natais melhores, bem como a uma nutrição melhor da mulher. Uma equação que reconhece isso é:

$$pesonas = \beta_0 + \beta_1 cigs + \beta_2 rendfam + u$$

(i) Qual é o sinal mais provavel de $\beta_2$?

Levando em consideração que  a unidade que se está medindo são grandezas absolutas, e levando em consideração que há um peso ideal, e que, se o peso for muito acima do ideal, isso pode representar um problema, penso que seria difícil determinar o sinal de $\beta_2$.

(ii) Você acha que $cigs$ e $rendafam$ estão, provavelmente, correlacionados? Explique por que a correlação pode ser positiva ou negativa.

Se pensarmos em cigarros como um bem normal, uma análise superficial poderia levar à idéia de que renda estaria positivamente correlacionada com cigarros. Caso a amostra de dados seja somente de pessoas que fumam, talvez essa correlação possa até existir. Agora, se pensarmos que o nível de educação e conhecimento podem influenciar na decisão do indivíduo quanto a fumar ou não, essa correlação pode deixar de existir ou pode até exitir com sinal negativo. Dessa forma, é difícil afirmar, antes de olhar os dados, se existe, e qual seria a correlação entre número de cigarros e renda familiar.

## Questão 6

No exemplo 4.7, usamos dados de empresas manufatureiras não sindicalizadas para estimar a relação entre a taxa de rejeição e outras características da firma. Agora, vamos olhar esse exemplo mais de perto e usar todas as empresas disponíveis.

(i) O modelo populacional estimado no exemplo 4.7 pode ser escrito como:

$$\log(rejei) = \beta_0 +\beta_1 hrsemp + \beta_2 \log(vendas) + \beta_3 \log(empreg) + u$$

Usando as 43 observações disponíveis para 1987, a equação estimada é:

$$
\begin{align}
\hat{\log(rejei)} = &11,74 - &0,042 hrsemp - &0,951 \log(vendas) + &0,992 \log(empreg) \\
                    &(0,57)  &(0,019)        &(0,370)              &(0,360)\\
n = 43, R^2=0,310
\end{align}
$$

Rodando o cálculo do exemplo (empresas sindicalizadas).
```{r, include=TRUE, echo=TRUE}
fit = lm(lscrap ~ hrsemp + lsales + lemploy, data = jtrain[jtrain$year == 1987 & jtrain$union==0, ])
summary(fit)
```

Rodando o cálculo incluindo todas as empresas.
```{r, include=TRUE, echo=TRUE}
fit = lm(lscrap ~ hrsemp + lsales + lemploy, data = jtrain[jtrain$year == 1987, ])
summary(fit)
```

Compare essa equação com aquela estimada com somente 29 firmas não sindicalizadas na amostra.

a variável lemploy aumentou seu coeficiente, bem como passou a ter significância esatística a 1%. A variável hrsemp passou a ser significativa 1%. O modelo como um todo passou a ser significativo a menos que 5%.


(ii) Mostre que o modelo populacional também pode ser escrito como

$$\log(rejei) = \beta_0 + \beta_1 hrsemp + \beta_2 \log(vendas/empreg) + \theta_3 \log(empreg) + u$$

Onde:
*$\theta_3 = \beta_2 + \beta_3$.

Interprete a hipóteses $H_0: \theta_3 = 0$.

```{r, include=TRUE, echo=TRUE}
fit = lm(lscrap ~ hrsemp + log(sales/employ) + lemploy, data = jtrain[jtrain$year == 1987, ])
summary(fit)
```

Assumindo empresas maiores como empresas que tem maior número de empregados (employ), pode-se constatar que o nível de rejeição não parece ser influenciado pelo tamanho da empresa, contorlando-se os parãmetros hrsemp e a relação (sales/employ).

(iv) Teste a hipótese de que um aumento de 1% em vendas/empreg está associado a uma queda de 1% na taxa de rejeição ($H_0: \beta_2 = -1$).

Cabe notar que, segundo a regressão, uma aumento de 1 em log(sales/employ) está associado com uma **diminuição** 0.95 em em lscrap com significância a 1%. O que se pede para testar é se aumento de 1 em log(sales/employ) estaria relacionado a uma **diminuição** de 1 em lscrap, ou seja, se $\beta_1 = -1$.

Para tanto, subtraímos 1 de $\beta_1$ e dividimos pelo seu erro padrão.

```{r}
beta1 = fit$coefficients["log(sales/employ)"]
beta1stderr = summary(fit)$coef["log(sales/employ)", "Std. Error"]
tstat = (beta1 - (-1))/beta1stderr
```

A estatística t para a hipótese $H_0$ é de `r tstat`, ou seja, não se pode rejeitar a hipótese de que o coeficiente $\beta_1$ seja -1.

### Questão 6: Detalhando o cálculo para fins de revisão...

Recordando o teste de hipótese para MLC.

Sob as hipóteses do MLC RLM.1 a RLM.6, temos que:

$$\hat{\beta_j} \sim Normal[\beta_j, var(\hat{\beta_j})]$$
Ou seja:
$$\frac{(\hat{\beta_j}-\beta_j)}{dp(\hat{\beta_j})} \sim Normal(0,1)$$

Para realização de testes de hipótese, usamos o seguinte resultado:

$$\frac{(\hat{\beta_j}-\beta_j)}{ep(\hat{\beta_j})} \sim t_{n-k-1}$$

A diferença está na substituição de $dp$, desvio padrão, por $ep$, erro padrão, que é $\sigma^2/\sqrt(n)$.

Sabendo que $\hat{\beta_j} \sim Normal[\beta_j, var(\hat{\beta_j})]$, o cálculo do intervalo de confiança a $\alpha = 0.05$ seria dado por $\hat{\beta_j}\pm 1.96 * ep(\hat{\beta_j})$, o que no caso em tela resultaria no intervalo de `r beta1 - 1.96 * beta1stderr` a `r beta1 + 1.96 * beta1stderr`, ou, usando o R:

```{r}
confint(fit)
```
Dessa forma, vemos que o coeficiente de log(sales/employ) pode sim ser -1, ou seja, não é possível rejeitar a hipótese de que um aumento de 1% em vendas/empreg esteja associado a uma queda de 1% na taxa de rejeição.

No caso em tela, $\frac{(\hat{\beta_j}-\beta_j)}{ep(\hat{\beta_j})}$ resulta em `r tstat`, ou seja, um valor que não nos permite rejeitar a hipótese de $\beta_1 = -1$.

## Questão 7

A análise de regressão pode ser usada para testar se o mercado usa eficientemente as informações ao avaliar ações. Seja $retorno$ o retorno total de possuir ações de uma firma ao longo de um período de quatro anos, do final de 1990 até o final de 1994. A **hipótese de mercados eficientes** diz que esses retornos não devem estar sistematicamente relacionados à informação conhecida em 1990. Se as características conhecidas da empresa no início do perído ajudassem a prever os retornos das ações, poderíamos usar essas informações para escolher ações.

Para 1990, seja $dkr$ a relação dívida-capital de uma empresa, seja $eps$ os ganhos por ação, seja $rendliq$ a renda líquida e seja $salário$ a remuneração total dos CEOs da empresa.

(i) Usando os dados do arquivo RETURN.RAW, estimou-se a seguinte equação:

$$
\begin{align}
\hat{retorno} = &-14,37 + &0,321rdc + &0,043gpa - &0,0051rendliq + &0,0035salário \\
&(0,89) &(0,201) &(0,078) &(0,0047) &(0,0022) \\
n= 142, R^2 =0,0395
\end{align}
$$
```{r}
fit <- lm(return ~ dkr + eps + netinc + salary, data=return)
summary(fit)
```
Como podemos ver, o modelo como um todo só apresentaria significância a um nível de `r lmp(fit)`, ou seja, o modelo parece não apresentar significância estatística como um todo.

(ii) Agora, usando nova estimação do modelo usando a forma log para $netinc$ e $salary$, estimou-se o seguinte modelo:

```{r}
fit <- lm(return ~ dkr + eps + lnetinc + lsalary, data=return)
summary(fit)
```

Novamente, o modelo parece não apresentar significância estatístca geral. Os coeficientes se alteraram significativamente, mas o modelo, como um todo, apresenta um p-value de `r lmp(fit)`, o que não nos permite descartar a hipótese de que as variáveis escolhidas não tem influência no retorno.

(iii) Nesta amostra, algumas firmas têm zero de dívidas e outras tem ganhos negativos. Deveríamos tentar usar $\log(dkr)$ ou $\log(eps)$ para vermos se isso melhorará o ajustamento? Esplique

A presença de zeros e númeors negativos impossibilita o uso dessas variáveis em sua forma logarítmica. Para que esse uso fosse possível, poder-se-ia eliminar da amostra as observações com valores <= 0 para essas variáveis e refazer a regressão. O ajustamento, medido pelo $R^2$ que já é bastante baixo (em torno de 3%) provavelmente melhoraria, visto haverem menos observações para um mesmo número de variáveis.

(iv) Em geral, a evidência da previsibilidade dos retornos é forte ou fraca?

Em geral, pode-se dizer que a evidência é fraca.

## Questão 8

Considere o modelo de regressão múltipla com três variávies independentes, sob has hipóteses do modelo linear clássico RLM.1 a RLM.6:

$$y=\beta_0 + \beta_1 x_1 \beta_2 x_2 + \beta_3 x_3 + u$$

Você deseja testar a hipótese núla $H_0: \beta_1 - 3\beta_2 = 1$

(i) Sejam $\hat{\beta_1}$ e $\hat{\beta_2}$ os estimadores MQO de $\beta_1$ e $\beta_1$. Encontre $Var(\hat{\beta_1} - 3\hat{\beta_2})$ em termos  das variãncias de $\hat{\beta_1}$ e $\hat{\beta_2}$ e a covariância entre eles. Qual é o erro-pádrão de $(\hat{\beta_1} - 3\hat{\beta_2})$?

Encontrando $Var(\hat{\beta_1} - 3\hat{\beta_2})$ em termos de $Var(\hat{\beta_1})$ e $Var(\hat{\beta_2})$

$$Var(\hat{\beta_1} - 3\hat{\beta_2}) = Var(\hat{\beta_1}) + 3Var(\hat{\beta_2}) - 6Cov(\hat{\beta_1}, \hat{\beta_2})$$

O erro padrão é dado por

$$ep(\hat{\beta_1} - 3\hat{\beta_2}) = \{[ep(\hat{\beta_1})]^2 + [3ep(\hat{\beta_1})]^2 - 6S_{12}\}^{ 1/2}$$

Onde $$S_{12}$$ é uma estimativa para $$Cov(\hat{\beta_1}, \hat{\beta_2})$$

(ii) Escreva a estatística $t$ para testar $H_0: \beta_1 - 3\beta_2 = 1$

$$t=\frac{\hat{\beta_1} - 3\hat{\beta_2}}{ep(\hat{\beta_1} - 3\hat{\beta_2})}$$

$$t=\frac{\hat{\beta_1} - 3\hat{\beta_2}}{\{[ep(\hat{\beta_1})]^2 + [3ep(\hat{\beta_1})]^2 - 6S_{12}\}^{ 1/2}}$$


(iii) Defina $\theta = \beta_1 - 3\beta_2$ e $\hat{\theta} = \hat{\beta_1} - 3\hat{\beta_2}$. Escreva uma equação de regressão que envolva $\beta_0$, $\theta$, $\beta_2$ e $\beta_3$ que permita que você obtenha diretamente $\hat{\theta}$ e seu erro-padrão.

$$\theta = \beta_1 -3\beta_2$$

A $$H_0$$ se torna

$$H_0: \theta = 1$$

e

$$H_1: \theta \neq 1$$

Como

$$\theta = \beta_1 - 3\beta_2 \Rightarrow \beta_1 = \theta + 3\beta_2$$

Reescrevendo a equação principal, temos:

$$y=\beta_0 + (\theta + 3\beta_2) x_1 + \beta_2 x_2 + \beta_3 x_3 + u$$

$$y=\beta_0 + \theta x_1 + 3\beta_2 x_1 + \beta_2 x_2 + \beta_3 x_3 + u$$

$$y=\beta_0 + \theta x_1 + \beta_2 (3x_1 + x_2) + \beta_3 x_3 + u$$

Com essa equação, podemos calcular facilmente $ep(\hat{\theta})$ para testar $H_0$.

## Questão 9

Suponha que o modelo

$$ pctação = \beta_0 + \beta_1 funds + \beta_2 risctol + u$$
satisfaça as quatro hipóteses de Gauss-Markov, em que $pctação$ é a percentagem da pensão de um trabalhador investida no mercado de ações, $fudns$ é o número de fundos mútuos que o trabalhador pode escolher e $risctol$ é alguma medida de tolerância de risco ($risctol$ maior significa que a pessoa tem uma tolerância maior ao risco). Se $funds$ e $risctol$ são positivamente correlacionados, qual é a inconsistência em $\hat{\beta_1}$, o coeficiente de inclinação da regressão de $pctação$ sobre $funds$?

O coeficiente $\beta_1$ nesse caso não representará o efeito que $funds$ tem sobre $pctação$ *ceteris paribus*. À medida que $risctol$ aumenta, o número de fundos disponíveis aumenta mecanicamente, ou seja, não há como medir o aumento na quantidade de fundos mantendo $risctol$ constante.

## Questão 10

no modelo de regressão simples sob os RLM.1 a RLM.4, afirmamos que o estimador de inclinação, $\hat{\beta_1}$, é consistente com $\beta_1$. Usando $\hat{\beta_0} = \bar{y} - \hat{\beta_1}\bar{x_1}$, demonstre que $\hat{\beta_0} = \beta_0$. (Você precisará usar a consistência de $\hat{\beta_1}$ e a lei dos grandes números, juntamente com o fato de que $\beta_0 = E[y] - \beta_1 E[x_1]$).

Se

$$y = \beta_0 + \beta_1 x_1 + u$$

Então

$$\bar{y} = \beta_0 + \beta_1 \bar{x}_1 + \bar{u}$$

Sabendo que $$\bar{u} = 0$$, temos que 

$$\bar{y} = \beta_0 + \beta_1 \bar{x}_1$$

$$\beta_0 = \bar{y} - \beta_1 \bar{x}_1$$

Aplicando o operador plim, temos que:

$$plim(\beta_0) = plim(\bar{y} - \beta_1 \bar{x}_1)$$

$$plim(\hat{\beta}_0) = plim(\bar{y}) - plim(\hat{\beta}_1) plim(\bar{x}_1)$$

$$plim(\hat{\beta_0}) = plim(\bar{y}) - plim(\hat{\beta}_1) plim(\bar{x}_1)$$

$$plim(\hat{\beta_0}) = \bar{y} - \beta_1 \bar{x}_1$$

Onde

$$plim(\bar{y}) = \bar{y}$$

$$plim(\bar{x}_1) = \bar{x}_1$$

e, pela lei dos grandes números,

$$plim(\hat{\beta}_0) = \beta_0$$

$$plim(\hat{\beta}_1) = \beta_1$$

## Questão 11

Considere o modelo de regressão múltipla contendo três variáveis independentes, sob as hipóteses RLM.1 a RLM.4:

$$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3 + u$$

Você está interessado em estimar a soma dos parâmetros de $x_1$ e $x_2$. Chame-a de $\theta_1 = \beta_1 + \beta_2$.

(i) Mostre que $\hat{\theta_1} = \hat{\beta}_1 + \hat{\beta}_2$ é um estimador não viesado de $\theta_1$.

$$\theta_1 = \beta_1 + \beta_2 \Rightarrow \beta_1 = \theta_1 - \beta_2$$

$$y = \beta_0 + (\theta_1 - \beta_2) x_1 + \beta_2 x_2 + \beta_3 x_3 + u$$

$$y = \beta_0 + \theta_1 x_1 - \beta_2 x_1 + \beta_2 x_2 + \beta_3 x_3 + u$$

$$y = \beta_0 + \theta_1 x_1 + \beta_2 (x_2 - x_1)  + \beta_3 x_3 + u$$

A consistência de $\hat{\theta}_1$ como estimador de $\theta_1$ é dada por:

$$\hat{\theta}_1 - \theta_1 = \frac{Cov(x_1,u)}{Var(x_1)}$$

Como, sob a hipótese de $E(u) = 0$ e $E(u|x_1,...,x_n)=0$ temos que $Cov(x_1,u) = E(x_1u) = 0$

Isso nos traz o resultado

$$\hat{\theta}_1 - \theta_1 = \frac{0}{Var(x_1)} \Rightarrow \hat{\theta}_1 = \theta_1$$

(ii) Encontre a variância de $\hat{\theta}_1$ em termos de $Var(\hat{\beta}_1)$, $Var(\hat{\beta}_2)$ e $Corr(\hat{\beta}_1, \hat{\beta}_2)$

$$Var(\hat{\theta}_1) = Var(\hat{\beta}_1 + \hat{\beta}_2)$$

$$Var(\hat{\beta}_1 + \hat{\beta}_2) = Var(\hat{\beta}_1) + Var(\hat{\beta}_2) - 2Corr(\hat{\beta}_1, \hat{\beta}_2)$$

## Questão 12

Suponha que o modelo populacional que determina $y$ seja:

$$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3 + u$$

e esse modelo satisfaz as hipóteses Gauss-Markov. Entretanto, estimamos o modelo que omite $x_3$. Sejam $\tilde{\beta}_0$, $\tilde{\beta}_1$ e $\tilde{\beta}_2$ os estimadores MQO da regressão $y$ sobre $x_1$ e $x_2$. Mostre que o valor esperado de $\beta_1$ (dados os valores das variáveis independentes da amostra é:

$$E(\tilde{\beta}_1) = \beta_1 + \beta_3 \frac{\sum_{i=1}^n \hat{r}_{i1} x_{i3}}{\sum_{i=1}^{n} \hat{r}_{i1}^2}$$

em que os $\hat{r}_{i1}$ são os resídulos de MQO da regressão $x_1$ sobre $x_2$.

Sugestão: a fórmula de $\tilde{\beta}_1$ é proveniente da equação

$$\hat{\beta}_1 = \frac{\sum_{i=1}^n \hat{r}_{i1} y_{i}}{\sum_{i=1}^{n} \hat{r}_{i1}^2}$$

Coloque $y_i = \beta_0 + \beta_1 x_{i1} + \beta_2 x_{i2} + \beta_3 x_{i3} + u_i$ nessa equação. Após alguma algebra, aplique o operador expectativa, tratando $x_{i3}$ e $\hat{r}_{i1}$ como não aleatórios.

$$\hat{\beta}_1 = \frac{\sum_{i=1}^n \hat{r}_{i1} (\beta_0 + \beta_1 x_{i1} + \beta_2 x_{i2} + \beta_3 x_{i3} + u_i)}{\sum_{i=1}^{n} \hat{r}_{i1}^2}$$

Sabendo-se que:

* $\sum_{i=1}^n r_{i1} = 0$
* $\sum_{i=1}^n r_{i1}x_{i1} = \sum_{i=1}^n r_{i1}^2$
* $\sum_{i=1}^n r_{i1}x_{i2} = 0$ e;

A expressão simplifica para:
$$\hat{\beta}_1 = \frac{\beta_1 \sum_{i=1}^n \hat{r}_{i1}^2 + \beta_3 \sum_{i=1}^n \hat{r}_{i1}x_{i3} + \sum_{i=1}^n \hat{r}_{i1}u_i}{\sum_{i=1}^{n} \hat{r}_{i1}^2}$$

$$\hat{\beta}_1 = \frac{\beta_1 \sum_{i=1}^n \hat{r}_{i1}^2}{\sum_{i=1}^n \hat{r}_{i1}^2} + \frac {\beta_3 \sum_{i=1}^n \hat{r}_{i1}x_{i3} + \sum_{i=1}^n \hat{r}_{i1}u_i}{\sum_{i=1}^{n} \hat{r}_{i1}^2}$$

Como $E(u_i)=0$, $E(\sum_{i=1}^n r_{i1}u_i) = \sum_{i=1}^n E(r_{i1}u_i) = \sum_{i=1}^n E(r_{i1})E(u_i) = 0$, visto que $E(u_i)=0$, a equação acima simplifca para:

$$E(\hat{\beta}_1) = \beta_1 + \beta_3 \frac {\sum_{i=1}^n \hat{r}_{i1}x_{i3}}{\sum_{i=1}^{n} \hat{r}_{i1}^2}$$

## Questão 13

Na seção 4.5 usamos como exemplo o teste da racionalidade da avaliação dos preços das casas. Lá, usamos um modelo log-log em $preço$ e $aval$. Aqui, vamos usar uma formulação nível-nível.

(i) No modelo de regressão simples

$$preço =  \beta_0 + \beta_1 + u $$

A avaliação é racional se $\beta_1=1$ e $\beta_0 = 0$. A equação estimada é:

$$\widehat{preço} = -14,47 + 0,976aval $$
* $std. err intercept = 16,27$
* $std. err aval = 0,049$
* $n = 88$
* $SQR = 165.644,51$
* $R^2 = 0,820$
Primeiro, teste a hipótese $H_0: \beta_0 = 0$ contra a hipótese alternativa bilateral. Em seguida, teste $H_0: \beta_1 = 1$ contra a hipótese alternativa bilateral. O que você conclui?

```{r}
beta_0 = -14.47
beta_0_stderr = 16.27
beta_1 = 0.976
beta_1_stderr = 0.049

beta_0/beta_0_stderr

beta_0 + (1.96 * beta_0_stderr)
beta_0 - (1.96 * beta_0_stderr)
```
Conforme podemos ver, o teste aponta uma estatística t de `r beta_0/beta_0_stderr`, a qual não nos permite rejeitar $H_0$.O teste $H_0: \beta_1 = 1$ resulta numa estatística t de `r (beta_1 - 1)/beta_1_stderr`, que não nos permite rejeitar $H_0$ a 5%.

(ii) Para testar a hipótese conjunta $\beta_0 = 0$ e $\beta_1 = 1$, precisamos do SQR do modelo restrito. Isso é igual a calcular $\sum(preço - aval)^2$, em que $n=88$, visto que os resíduos do modelo restrito são exatamente $preço - aval$ (nenhuma estimação é necessária para o modelo restrito porque ambos os parâmetros estão especificados sob $H_0$). Isso tem como resultado SQR = 209.448,99. Faça o teste *F* para a hipótese conjunta.

Relembrando, para testar significância estatística de diferenças em SQRs, usamos a distribuição *F*, e para obter a statística *F* usamos a seguinte fórmula:

$$F=\frac{\frac{(SQR_r - SQR_{ir})}{q}}{\frac{SQR_{ir}}{n - k - 1}} \sim F_{(q, n - k - 1)}$$

Onde $q$ é o número de graus de liberdade do numerador e é dado por $q=(n - k - 1)_{r} - (n - k - 1)_{ir}$.

Nesse caso, queremos a hipótese conjunta para $\beta_0$ e $\beta_1$. Assim, teríamos a seguinte situação:

* $q=(n - k - 1)_{r} - (n - k - 1)_{ir} = (88 - 0 - 1) - (88 - 2 - 1) = 2 $
* $n-k-1 = 88 - 2 - 1 = 85*



Plugando esses valores na fórmula, temos:

$$\frac{\frac{(209.448,99 - 165.644,51)}{2}}{\frac{165.644,51}{88 - 1 - 1}} = F$$


Usando a tabela *F* a um nível de 1%, obtemos o valor de 4.85. Como o valor da nossa estatística F é de `r ((209448.99 - 165644.51)/2)/(165644.51/(88 - 1 - 1))`, podemos rejeitar $H_0$ a 1%.

(iii) Agora, teste $H_0= \beta_2 = 0, \beta_3 = 0, \beta_4 = 0$ no modelo $preço = \beta_0 + \beta_1 aval + \beta_2 dimterr + \beta_3 arconstr + \beta_4 qtdorm + u$. O $R^2=0,829$ com as mesmas 88 residências.

Para esse caso, podemos usar a forma *R-quadrado* da estatística F:

$$F=\frac{\frac{(R_{ir}^2 - R_r^2)}{q}}{\frac{(1 - R_{ir}^2)}{n - k - 1}}  \sim F_{(q, n - k - 1)}$$

Nesse caso, temos que $q = 88 - 1 - 1 - (88 - 4 -1) = 3$ e $(n - k -1) = 83$

A estatística F usando a forma *F-quadrado* nos dá um valor de `r ((0.829 - 0.820)/3)/((1 - 0.829) / (88 - 4 - 1))`, o que faz com que não seja possível rejeitar $H_0$ nem a 10%.

(iv) A regra RLM.5 $Var(u|x1,...,x_k) = \sigma^2(u)$ é essencial para o uso das estatísticas $t$ e $F$. Se não for esse o caso, ou seja, os dados apresentam heterocedasticidade, os testes $t$ e $F$ podem não ser aplicáveis.

## Questão 14

$$y=\beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3  u$$

$$\tilde{\beta}_1 | y=\tilde{\beta}_0 + \tilde{\beta}_1 x_1 + e$$

$$\hat{\beta}_1 | y=\tilde{\beta}_0 + \tilde{\beta}_1 x_1 + \tilde{\beta}_2 x_2 + \tilde{\beta}_3 x_3  + e$$

(i) Caso $x_1$ seja muito correlacionado com $x_2$ e $x_3$, grande parte do efeito que $x_1$ tem em $y$ que poderia ser distribuído entre $x_2$ e $x_3$ ficará concentrado em $x_1$. Dessa forma, o esperado é que $\tilde{\beta}_1$ seja consideravelmente diferente de $\hat{\beta}_1$

(ii) Nesse caso, como a regressão que calcula $\tilde{\beta}_1$ não faz referência a $x_2$ e $x_3$, e, dada a **não correlação** de $x_1$ com $x_2$ e $x_3$, isso implicará que $E[y|x_1] = E[y|x_1, x_2, x_3]$, ou seja, $\tilde{\beta}_1 \approx \hat{\beta}_1$.

(iii) A RLM.5 prevê que $Var(y|\boldsymbol{x}) = \sigma^2$ Já a variância dos betas, pode ser obtida com a seguinte equação:

$$Var(\hat{\beta}_j)=\frac{\sigma^2}{SQT_j(1-R^2_j)}$$

Onde $SQT_j=\sum_{i =1}^n(x_{ij} - \bar{x}_{j})^2$ é a variação amostral total em $x_j$, e $R^2_j$ é o R-quadrado da regressão $x_j$ sobre todas as outras variáveis independentes.

Como, nesse caso, estamos analisando uma situação em que há correlação entre $x_1$ e $x_2$ e $x_3$, é de se esperar que o $R^2_1$ será maior, o que tornará o denominador da equação que determina a variância do $\beta$ menor, o que *aumentará* $Var(\hat{\beta}_1)$. Assim, esperaria-se que $ep(\hat{\beta}_1) >ep(\tilde{\beta}_1)$.

(iv) Aqui, a situação é a inversa do item (iii). Não sendo $x_1$ correlacionada com $x_2$ e $x_3$, o $R_1^2$ tenderá a ser menor, o que deixará o denominador da equação de $Var(\beta)$ maior, produzindo assim $ep(\tilde{\beta}_1) >ep(\hat{\beta}_1)$.

## Questão 15

(i) Partindo da hipótese de que os pais tem uma certa capacidade de manter os filhos estudando sem necessidade de trabalhar, um aumento no número de filhos acaba por distribuir essa capacidade  entre eles, o que pode configurar um fator de diminuição no número de anos de educação de filhos que tem mais irmãos. Para que a quantidade de irmãos signifique um ano a menos de educação, a seguinte formulação matemática deve ser feita: $irms=\frac{educ - (educ - 1)}{-0,094} = 10,63$

(ii) Pelos coeficientes da equação, entendemos que a quantidade de anos de educação formal da mãe tem menos influência na quantidade de anos de educação formal dos filhos do que a quantidade de anos de educação formal do pai. Como o arquivo utilizado trata somente de homens, poder-se-ia aventar a possibilidade de que o nível de educação formal do pai tem mais influência sobre filhos homens do que o da mãe.

(iii) 

$$educA = 10,36 - 0,94 * 0  + 0,131 * 12 + 0,210 * 12 = 14,45$$

$$educB = 10,36 - 0,94 * 0  + 0,131 * 16 + 0,210 * 16 = 15,81$$

$$educB - educA = 1,36$$

## Questão 16

```{r}
supgpa = c(2.8, 3.4, 3.0, 3.5, 3.6, 3.0, 2.7, 3.7)
act = c(21, 24, 26, 27, 29, 25, 25, 30)

length(supgpa)
length(act)
fit <- lm(supgpa ~ act)
summary(fit)
```

A partir da regressão acima, identifica-se que $act$ está positivamente correlacionado com $supGPA$ (coeficiente `r coef(fit)["act"]`). Isso indica que quanto melhor a nota de ingresso do aluno, melhor é sua nota média durante o curso. O intercepto aqui praticamente não tem significado. Ele fica perto de zero e as escalas das notas são diferentes. Como um aluno com nota zero não entraria no curso superior, o intercepto (valor de $E[supGPA|act = 0]$) parece não ter relevância. Caso $act$ aumentasse cinco pontos, o valor de $supGPA$ aumentaria de acordo com a equação:

$$gpa = \beta_0 + \beta_1(act + 5)$$ 

$$ gpa = \beta_0 + 5\beta_1 + \beta_1 act $$ 

$$ gpa = 0,56 + 0,10 * 5 + 0,10 act =  1,06 + 0,10 act$$

(ii)

* Valores estimados: `r fit$fitted.values`

* Resíduos: `r fit$residuals`

* Soma dos resíduos: `r sum(fit$residuals)`

(iii)

O valor quando $act=20$ é `r coef(fit)["(Intercept)"] + coef(fit)["act"] * 20`

(iv) `r summary(fit)$r.squared`. O valor de $R^2$ mostra o quão ajsutado o modelo está aos dados. Nesse caso, aproximadamente 57% da variação foi capturada pelos coeficientes produzidos pelo modelo.

## Questão 17

Inclinação da reta:

$$\hat{\beta}_1 = \frac{\sum_{i=1}^n(x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^n(x_i - \bar{x})^2}$$

* $\bar{x} = (1+2+3)/3 = 2$
* $\bar{y} = (3 + 5 + 6)/3 = 4,66$
* $\sum_{i=1}^n(x_i - \bar{x})(y_i - \bar{y}) = 3$
* $\sum_{i=1}^n(x_i - \bar{x})^2 = 2$
* $\hat{\beta}_1 = 3/2 = 1,5$

Intercepto

$$\hat{\beta}_0 = \bar{y} - \hat{\beta}_1\bar{x}$$

* $\hat{\beta}_0 = 4,66 - 1,5 * 2 = 1,66$

Calculando $R^2$ pelo método $SQE/SQT$:

* $\hat{\boldsymbol{y}} = \{1,66 + 1,5 * 1;  1,66 + 1,5 * 2; 1,66 + 1,5 * 3\} = \{3,16; 4,66; 6,16\}$

* $SQE = \sum(\hat{y_i} - \bar{y})^2 = 4,5$
* $SQT = \sum(y_i - \bar{y})^2 = 4,66$

Calculando $R^2=\frac{SQE}{SQT} = \frac{4.5}{4.66} = 0.96$

O resultado de $R^2$ mostra que a reta calculada pelo método MQO tem um nível de ajuste de 96%, ou seja, é uma reta muito bem ajustada aos números.

Calculando $R^2$ pelo método $\widehat{cov}(y,\hat{y})^2/[\widehat{var}(y)\widehat{var}(\hat{y})]$

* $Cov(y,\hat{y}) = \sum_{i=1}^n (y_i - \bar{y})(\hat{y}_i - \bar{y}) = 4,5$
* $Var(y) = \sum_{i=1}^n(y_i - \bar{y})^2 = 4,66$
* $Var(\hat{y}) = \sum_{i=1}^n(\hat{y}_i - \bar{y})^2 = 4,5$
*  $\widehat{cov}(y,\hat{y})^2/[\widehat{var}(y)\widehat{var}(\hat{y})] = \frac{4,5 * 4,5}{4,66 * 4,55} = \frac{4,5}{4,66} = 0,96$

## Questão 18

$$renda = 0,417 + 0,08educ + 0,029exper$$

* $ep(intercepto) = 0,099$
* $ep(educ) = 0,007$
* $ep(exper) = 0,005$
* $R^2 = 0,411$
* $n = 526$

a) Estatística t de cada coeficiente:
* $0,417/0,099 = 4,63$ ***
* $0,08/0,007 = 11,42$ ***
* $0,029/0,005 = 5,8$ ***
b) A um nível de significância de 5% bicaudal, a estatística $t$ limite para um $n > 120$ seria de 1,96.  Dessa forma, os três coeficientes são estatisticamente significantes. Os intervalos de confiança são os seguintes:

* $0,417 \pm 1,96 * 0,099 = 0,417 \pm 0,19 = [0,607; 0,227]$
* $0,08 \pm 1,96 * 0,007 = 0,08 \pm 0,01372 = [0,066; 0,0937]$
* $0,029 \pm 1,96 * 0,005 = 0,029 \pm 0,0098 = [0,0192; 0,0388]$

c) O impacto de um ano adicional de educação na renda é de 0,08

d) $renda = 0,417 + 0,08 * 10 + 0,029 * 5 = 1,362$

## Questão 19

a) Os coeficientes para as variáveis *masculino*, *formal*, *experiancia2* possuem estatísticas $t$ que não permitem descartar a hipótese de que sejam zero a um nível de 5%. Isso fica evidente no intervalo de confiança a 95% para essas variáveis, os quais passam todos pela possibilidade dos respectivos betas serem zero.

b) A variável que possui maior impacto é a $anos_est$, com impacto médio de 154,53. Esta é seguida pela variável $experiencia$, com impacto médio de 46,02. Há ainda o impacto  da variável $\_const$ que, apesar de ser a que possui o maior impacto em termos absolutos, parece se tratar de uma variável sem variabilidade (dado que é uma constante). Ela parece ter sido algum tipo de variável instrumental.

c) A estatística F do modelo possui um valor de 8,65. para um n > 120, e com um numerador de $q=(n - k - 1)_{r} - (n - k - 1)_{ir} = 167 - 1 -1 - 167 + 6 + 1 = 5$, teríamos significância estatística para esse valor a partir de 3,02, ou seja, o modelo, como um todo, apresenta sim significância estatística a 1%.

d) 

## Questão 20

Para verificar se a inclusão de $roe^2$ é necessário, precisamos verificar sua significância estatística, que nesse caso é de $0,00008/0,00026 =  0,3$, ou seja, não se pode descartar a hipótese de que o termo seja zero. Além do mais, su impacto na regressão ($0,00008$) também é muito pequeno. Nesse caso, a inclusão do termo não se mostra particularmente útil.

## Questão 21

$\widehat{pditens} = 2,613 + 0,00030 vendas + 0,000000007 vendas^2$

$$max_{vendas} = 2,613 + 0,00030 + (0,000000007)vendas^2$$

$$\frac{\partial .}{\partial vendas} = 0,00030 + 2(-0,000000007)vendas = 0$$

$$2(-0,000000007)vendas = -0,00030$$

$$vendas = \frac{-0,00030}{2(-0,000000007)} = 21.428,57$$

A partir de $21.428,57$, o efeito marginal de $vendas$ começa a impactar negativamente $pditens$ .

(ii) O termo quadrático apresenta uma estatística $t = 2,33$, ou seja, estatisticamente significante. Por esse motivo, e pelo conhecimento que a questão dos retornos marginais de $vendas$ trazem à interpretação dos resultados, parece razoável manter o termo.

(iii) 

$$\widehat{pditens} = 2,613 + 0,30\frac{vendasbil}{1000} vendas + 0,000007\frac{vendasbil^2}{1000^2}$$

(iv) A segunda opção possui coeficientes com menos zeros, o que facilita a interpretação.


## Questão 22

A segunda equação nos parece a que produz melhores resultados. Tem melhor ajustamento, bem como coeficientes com interpretação mais fácil.

## Questão 23

(ii)

$$log(salário) = \beta_0 + \beta_1 educ + \beta_2 educ * edupais + \beta_2 exper + zbeta_4 perm +u$$

$$\frac{\partial log(salario)}{\partial educ} = \beta_1 + \beta_2 edupais$$

Da teoria por trás desses dados, poder-se-ia aventar que os salários de filhos de pais com maior nível de instrução tendem a ser maiores do que salários de filhos de pais com baixo nível de instrução. Isso pode se dever a fatores tais como influência dos pais para colocação profissional dos filhos, por exemplo. Dessa forma, esperar-se-ia um sinal positivo para $\beta_2$.

(ii)

O coeficiente do termo de interação confirma  a ideia de que o nível de instrução dos pais potencializa o salário dado o nível de instrução do filho.

(iii)

A estatística $t$ para o coeficiente de $edupais$ é de $0,033/0,17 = 1,94$,  o que é significante a 95%. Ao mesmo tempo, a estatística $t$ para o termo de interação ficou em $0,0016/0,0012=1,33$, ou seja, ela não permite o descarte da hipótese nula nem a 10%. Assim, ao mesmo tempo que se poderia descartar a hipótese nula de que $edupais$ não influencia em $log(salario)$, poder-se-ia descartar o termo de interação entre essas duas variáveis. A equação que não controla o termo de forma independente parece ter enviesado o coeficiente do termo de interação.

## Questão 24

(i) A estatística $t$ para $masculino$ é de $87,75/34,33 = 2,55$, ou seja, ela guarda significância estatística a 99%. Assim, a evidência é forte no sentido de que o fato de ser homem implica em maior quantidade de minutos de sono.

(ii) O coeficiente de $trabtot$ é de $-0,163$ com estatística $t=0,163/0,018 = 9,05$, ou seja,com significância estatística a mais de 99%. Assim, existe forte evidência de uma relação de substituição entre $trabtot$ e $dormir$.

(iii) Pode-se realizar um teste $F$ com $\beta_3 = \beta_4 = 0$

## Questão 25

(i) Para cada cigarro a mais consumido, a criança parece ter um peso 0,44% menor. Dessa forma, para 10 cigarros, a redução de peso seria de 4,4%.

(ii) Espera-se um peso 5,5% maior com significância estatística a 99%.

(iii) O efeito estimado é de 0,3%, porém, sem significância estatística nem a 90%. Assim, não é possível descartar a hipótese nula.

(iv) O cálculo dessa estatística só faz sentido para dois modelos ajustados para uma mesma amostra, o que não parece ser o caso em tela, dada a diferença no tamanho das amostras. Para executar esse calculo, a primeira equação teria que ser reestimada usando a mesma amostra da segunda equação.

## Questão 26

(i) O coeficiente de $tamclas^2$ tem uma estatística $t = 2,19/0,53 = 4,13$, o que a torna estatisticamente significante a mais de 99,5%. Dessa forma, existe sim evidência de que sua inclusão no modelo é necessária.

O tamanho ótimo da classe é dado por:

$\max_{tamclass} 1028,10 + 19,30 tamclas - 2,19 tamclas^2 - 45,09 feminino - 169,81 negro + 62,31 feminino \cdot negro$

$\frac{\partial \cdot}{\partial tamclas} = 19,30 - 2 \cdot 2,19 tamclas = 0$

$2 \cdot 2,19 tamclas = 19,30$

$tamclas = \frac{19,30}{2 \cdot 2,19}$

$tamclas^* = 4,40$

(ii) A diferença estimada é o coeficientes de $feminino$ que é de -45,09. Esse coeficiente possui estatística $t = 45,09/4,29 = 10,51$, ou seja, possui significância estatística a mais de 99%.

(iii) A diferença é o coeficiente da variável $negro$ que é de -169,81 com estatística $t = -169,81/12,71 = -13,36$, ou seja, possui significância estatística a mais de 99%.

(iv) A diferença é dada pela soma dos coeficientes de $feminino$, $negro$  e $feminino \dot negro$ menos o coeficiente de $feminino$. 

$-45,09 - 169,81 + 62,31 - (-45,09) = -107,5$

Como esse coeficiente envolve várias variáveis, não é possível realizar um teste de significância estatística. Para tal, ter-se-ia que modelar a interação entre essas variáveis no desenho do modelo.

## Questão 27

(i) A diferença percentual é o coeficiente da variável $servpub$ , que é de -0,283 (28,3%). Esse coeficiente tem estatística $t = 0,283/0,099 = 2,85$ o qual demonstra significância estatística a 99%.

(ii) A diferença exata é dada por $100 * [exp(-0,283) - 1] = -24.64802$. O valor é um pouco menor que o valor aproximado obtido em (i).

(iii) A diferença seria dada pela diferença entre os coeficientes. $0,181 - 0,158 = 0,23 = 23\%$. Para verificar se essa diferença é estatisticamente significante, poder-se-ia trabalhar o seguinte modelo:

$$\widehat{log(salário)} = \beta_0 + \beta_1 log(vendas) + \beta_2 roe +  \beta_3 prodcons + \beta_4 transporte + \beta_5 servpub$$

Nesse caso, a base seria o setor financeiro.

## Questão 28

(i) Conforme mostrado abaixo, npGPA e aumfGPA são significantes a 95%, e tothrs não, independente do erro padrão utilizado.

* $t_{npGPA} = 0,9/0,175 = 5,14$ **
* $t_{npGPA_{r}} = 0,9/0,166 = 5,42$ **
* $t_{aumfGPA} = 0,193/0,064 = 3,01$ **
* $t_{aumfGPA_{r}} = 0,193/0,074 = 2,60$ **
* $t_{tothrs} = 0,0014/0,0012 = 1,16$ 
* $t_{tothrs_{r}} = 0,0014/0,0012 = 1,16$

(ii) Essa hipótese indicaria uma relação 1:1 entre npGPA e nsGPA. Usando erro padrão normal, $t=(0,900 - 1)/0,175 = -0,57$. Usando o erro padrão robusto, $t_r = (0,9 - 1)/0,166 = -0,6$. Ou seja, não se pode rejeitar a hipótese de uma relação 1:1 entre npGPA e nsGPA.

(iii) $t = -0,157 / 0,098 = -1,6$ e $t_r = -0,157/0,08 = -1,9625$. Nesse caso, poder-se-ia rejeitar a hipótese nula a 10% bicaudal usando-se o erro padrão robusto. Assim, dependendo do erro padrão utilizado e do nível de significância, pode-se tomar diferentes decisões com respeito à rejeição ou não da hipótese nula.

## Questão 29

(i) Não.

(ii) A probabilidade diminui em $2,9\%*4 = 11,6\%$

(iii)

$$max_{idade} 0,656 - 0,069 log(precig) + 0,012 log(renda) - 0,029 educ + 0,02 idade - 0,00026 idade^2 - 0,101 restaurn - 0,026 branco$$

$$\frac{\partial \cdot}{\partial idade} = 0,02 - 2(0,00026)idade = 0$$

$$- 2(0,00026)idade = -0,02$$

$$idade = \frac{-0,02}{- 2(0,00026)} = 38,4$$

(iv) $t=-0,101/0,038 = 2,65$. Com significância estatística a 99% (bicaudal), o modelo parece indicar que a restrição de fumo em restaurantes está relacionada a uma diminuição de 10% na probabilidade de a pessoa ser fumante.

(v) 

$0,656 - 0,069 log(67,44) + 0,012 log(6500) - 0,029 (16) + 0,02 (77) - 0,00026 (77)^2 = 0.005239246$

Visto que a essa observação tem como resultado "não fumante", o modelo produziu um resultado bastante apurado.

## Questão 30

Fazendo um teste F usando a fórmula R-quadrática, temos que:

$q=(n - k - 1)_{r} - (n - k - 1)_{ir} = 177 - 5 - 1 - (177 - 7 - 1) = 2$

$F=\frac{\frac{(R_{ir}^2 - R_r^2)}{q}}{\frac{(1 - R_{ir}^2)}{n - k - 1}}  \sim F_{(q, n - k - 1)}$

$F=\frac{\frac{(R_{ir}^2 - R_r^2)}{q}}{\frac{(1 - R_{ir}^2)}{n - k - 1}}  = \frac{(0,375 - 0,353)/2}{(1 - 0,375)/(177-7-1)} = \frac{0,011}{0,003698} = 2,974$

O valor crítico da estatística F a 10% para $q = 2$ e $n - k - 1 > 120$ é de 2,3 a 10% e 3 a 5%.

Dessa forma, a 10% poder-se-ia rejeitar a $H_0: \beta_6 = \beta_7 = 0$ de que o modelo não esteja subespecificado. A 5%, esse já não seria o caso. Assim, pode-se aventar que, mesmo que haja uma subespecificação, ela seria pouco relevante.

## Questão 31

(i) A variável indicaria que a cada ponto percentual a mais do candidato nas eleições de 88, isso implicaria em 0,067 pontos percentuais a mais na eleição de 90. Com estatística $t = 0,067/0,053 = 1,26$, não se pode descartar a hipótese de que essa variável tenha coeficiente 0 mesmo a 10%. 

(ii) A inclusão de $votoA88$ produziu alterações pequenas nos demais coeficientes e erros padrão.

## Questão 32

(i) Provavelmente, a aceitação para o programa de merenda escolar depende de algum tipo de comprovação de necessidade, o que seria um proxy razoável para o identificação da condição de pobreza.

(ii) O efeito de $gasto$ na coluna dois exibe estatística $t = 7,75/3,04 = 2,54$, ou seja, têm significância estatística a 5%. No modelo da coluna 1 (sem a variável pobreza), o valor de $gasto$ está enviesado, visto ser o fator renda de suma importância para o desempenho escolar.

(iii) Com estatística $t=-1,26/0,58 = 2,17$, o que já daria significância estatística  a 5% bicaudal, o modelo indica que um aumento de 1% no número de matriculados na escola está relacionado a uma diminuição de 1,26 pontos percentuais na quantidade de alunos aprovados. Esse valor parece bastante alto, o que 

(iv) Para cada ponto percentual a mais de alunos pobres, existe uma diminuição de 0,32 pontos percentuais de alunos aprovados no teste.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcwNjM2MTI1LC0xMDYwNDY1MTc4LC0xNT
I1ODQxMDY0LC0xOTcwNTk0MTE5LC0xMTkzNDU0MzM0LDgzNzIx
Nzc0LC0xNzE2MzgyOTEyLC0xNjQ5NjQyMjAsLTM3MTc5MzE0Mi
wtMTIzNTY2MTEwNSwtMTc3OTU5MTMwMCwtODMwNTU2NjMwLC0x
ODMyNzc3Mjc1LDUxMDk1MjY2MSwtNzc5MjE0OTQwLC0xODM1Mz
M5NDE1LC01OTIxNjE2NTUsLTE2NjM1ODkyNTAsLTIwOTcxMjcz
NzgsMjI0MzI1NTgyXX0=
-->