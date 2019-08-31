Mapa Análise Microeconômica
===========================

# 1. Tecnologia

## 1.1 Medição de entradas e resultados

Trata do requisito de estabelecer um sistema para sumarizar as possibilidades de produção como combinações de entradas e saídas. Preferencialmente, deve ser feito usando fluxos c/ dimensão temporal.

## 1.2 Especificação da tecnologia

Definição de bens, insumos, produtos, produto líquido e plano de produção. Define alguns exemplos tias como:

1. conjunto de requerimento de insumos $V(y) = \{\boldsymbol{x}\ in\ R_+^n : (y, \boldsymbol{-x}) \text{ está em } Y\}$;
1. isoquanta $Q(y) = \{\boldsymbol{x} \in R_+^n: \boldsymbol{x}\ está\ em\ V(y)\ e\ \boldsymbol{x}\ não\ está\ em\ V(y\prime)\ para\ y\prime \ge\ y\}$;
1. função de produção: $f(x) = \{y \in R: y\ \text{ é o máximo de produto associado com } \boldsymbol{-x}\ em\ Y\}$
1. função de transformação: analoga à função de produção, porém, é uma função $T: R^n \rightarrow R$ onde $T(\boldsymbol{y}) = 0$ somente se $\boldsymbol{y}$ é eficiente. 

Posteriormente, são dados exemplos da especificação da tecnologia usando *Cobb-Douglas*, e *Leontief*.

## 1.3 Análise de atividade

Descreve a forma mais simples de descrever os conjuntos de produção (ou conjuntos de requerimento de insumos) através da sua simples listagem. Entretanto, a simples listagem não cobre todas as possibilidades, assim, é descrita uma forma de listagem onde um fator é função do outro.


## 1.4 Tecnologias Monotônicas

Se $\boldsymbol{y\prime} \le \boldsymbol{y}$ então cada componente do vetor $\boldsymbol{y\prime}$ é menor ou igual ao correspondente vetor $\boldsymbol{y}$, ou seja, o plano de produção $\boldsymbol{y\prime}$ produz uma quantidade menor ou igual de todos os __produtos__ usando pelo menos a mesma quantidade de insumos que $\boldsymbol{y}$.

Resumindo: __livre descarte__.

## 1.5 Tecnologias Convexas

Se $\boldsymbol{x}$ e $\boldsymbol{x\prime}$ estão em $V(y)$, então $t\boldsymbol{x} + (1-t)\boldsymbol{x\prime}$ está em $V(y)$ para todo $0 \le t \le 1$.

__Conjunto de produção convexo implica em conjunto de requerimento de insumos convexo__

__Conjuntos de requerimento de insumos convexos é equivalente à uma função de produção quasiconcava__
$V(y) = \{\boldsymbol{x}: f(\boldsymbol{x}) \ge y\}$ é basicamente o contorno superior da função de produção.

## 1.6 Tecnologias regulares

Só para evitar frases como "assumindo que $y$ pode ser produzido".

## 1.7 Representações paramétricas da tecnologia

Diz respeito à suavização do conjunto de requerimento de insumos.

## 1.8 Taxa de Substituição Técnica

É a inclinação da tangente da curva do requerimento de insumos suavizada.

Dados dois insumos, 

$$\frac{dx_2}{dx_1} = - \frac{\frac{\partial{f}}{\partial{x_1}}}{\frac{\partial{f}}{\partial{x_2}}}$$

## 1.9 Elasticidade da substituição

Mede a curvatura da isoquanta, % de mudança na razão dos fatores pelo % de mudança na TST.

$$\sigma =  \frac{d\ln(x_2/x_1)}{d\ln{|TST|}}$$

## 1.10 Retornos de escala

Podem ser constantes, crescentes ou decrescentes.

Firmas podem exibir os três tipos dependendo do nível de produção. Assim, usa-se em medida local do retorno.

A elasticidade da escala é o % de aumento na produção em função de um aumento de 1% em todos os insumos.

$$e(x) = \frac{dy(t)}{dt} \frac{t}{y}\biggr\rvert_{t=1} = \frac{df(t\boldsymbol{x})}{dt} \frac{t}{f(t{\boldsymbol{x})}}\biggr\rvert_{t=1}$$

## 1.11 Tecnologias homogêneas e homotéticas

* Homogêneas: aumento do produto igual ao aumento nos insumos
* Homotéticas: aumento do produto diferente do aumento dos insumos

# 2. Maximização do Lucro

Diferença entre retorno e custos. 

Retorno pode ser descrito como uma função do nível de operação de *n* ações $R(a_1,\dots,a_n)$ e os ustos podem ser descrito como uma função dessas mesmas ações $C(a_1,\dots,a_n)$

A função de maximização da firma é adotar o conjunto de ações $(a_1,\dots,a_n)$ que maximizam $R(a_1,\dots,a_n) - C(a_1,\dots,a_n)$.

$$\max_{a_1,\dots,a_n} R(a_1,\dots,a_n) - C(a_1,\dots,a_n)$$

A condição é caracterizada por:

$$\frac{\partial {R(\boldsymbol{a^*})}}{\partial {a_i}} = \frac{\partial {C(\boldsymbol{a^*})}}{\partial {a_i}} \ \ i = 1,\dots,n$$ 

Intuição: se a receita marginal for maior que o custo marginal, vale a pena aumentar o nível de atividade. Caso contrário, vale a pena diminuir o nível de atividade.

Retorno é composto de quantidade * preços de venda. Custos são quantidade de insumos * preços.

O problema de maximização é determinar que preços cobrar por seus produtos ou que preços pagar por seus insumos e quais níveis de insumos e produtos ela quer usar de forma a maximizar o lucro. 

Restrições: tecnologia e mercado.

Hipótese do livro: *price-taking behavior* (ou firma competitiva): a firma só pode influenciar nas quantidades, uma vez que os preços são variáveis exógenas.

## 2.1 Maximização do lucro

$$\pi(\boldsymbol{p}) = \max \boldsymbol{py}$$

tal que $\boldsymbol{y} \in Y$.

Na maximização, como os insumos são dados em valores negativos, a maximização dos planos de produção já contempla $R - C$.

A otimização pode ser efetuada nas funções de custo para firmas monopolistas (firmas que ditam o preço).

A condição de maximização é descrita por $\boldsymbol{p}Df(\boldsymbol{x^*}) = \boldsymbol{w}$ (o gradiente de $f$ tem que ser igual ao preço dos insumos).

Lembrar da idéia de que $w/p$ é a inclinação da curva. A solução que se procura é __igualar__ a $PMg_\boldsymbol{x}$ à essa inclinação.

Para uma firma de somente um produto, o comportamento de maximização pode ser descrito por:

$$p\frac{\partial{f(\boldsymbol{x^*})}}{\partial x_i} = w_i \  \  \ para\ i = 1, \dots, n$$

__CPO__: o valor marginal de cada fator de produção deve ser igual a seu preço.

A maximização quer achar um ponto no *conjunto de produção* com o máximo nível de lucro, ou seja um ponto onde 

$$\frac{df(x^*)}{dx} = \frac{w}{p}$$

Nesse ponto, a segunda derivada tem q ser negativa, mostrando que a função é concava no ponto encontrado, ou seja,

$$ \frac{d^2f(x^*)}{dx^2} \le 0$$

Para uma função com múltiplos insumos a matriz hessiana

$$ D^2f(\boldsymbol{x^*}) = \biggl(\frac{\partial^2{f(\boldsymbol{x^*})}}{\partial x_i \partial x_j}\biggr)$$

precisa satisfazer a condição $hD^2f(\boldsymbol{x^*})h^t \le 0$ para todos vetores $h$ (onde $^t$ significa transposição da matriz), ou seja, a matriz deve ser negativa semidefinida.

## 2.2 Dificuldades

A função de demanda $\boldsymbol{x}(p,\boldsymbol{w})$ retorna a escolha ótima de insumos em função dos preços. Similarmente, a função da oferta $y(p,\boldsymbol{w}) = f(\boldsymbol{x}(p,\boldsymbol{w}))$ retorna o plano de produção dada a escolha ótima de insumos dados os preços.

Restrições:

1. Se a tecnologia não pode ser descrita por uma função diferenciável, os diferenciais não serão adequados.
2. As condições só fazem sentido em uma vizinhança aberta com variáveis positivas, ou seja, o valor das variáveis pode ser escolhido em uma vizinhança aberta. Caso uma das variáveis seja zero, a solução pode não mais ser __interior__. 

Para tratar soluções de canto, pode-se usar as seguintes modificações nas condições de primeira ordem:

$$ p\frac{\partial f(\boldsymbol{x})}{\partial x_i} - w_i \le 0 \ \ \  se \ \  x_i = 0$$

ou

$$ p\frac{\partial f(\boldsymbol{x})}{\partial x_i} - w_i = 0 \ \ \  se \ \  x_i \gt 0$$

3. Por fim, as funções de retornos constantes de escala $f(x) = x$ sempre apresentam soluções de máximo infinitas para $p > w$. Ver demonstração na página.
4. Em 3, vemos que uma solução maximizadora pode envolver diferentes planos e produção (se a solução envolve lucro zero, qualquer plano de produção é solução da maximização).

## 2.3 Propriedades das funções de oferta e demanda

Ex: $x_i(tp, t\boldsymbol{w}) = x_i(p,\boldsymbol{w})$, ou seja, a função deve ser homogênea de grau zero.

Para checar se algum comportamento de uma firma vem de um modelo de maximização de lucros, pode-se verificar se as funções de demanda e oferta são homogêneas de grau zero. Caso não o sejam, a firma não tem como estar maximizando lucro.

Objetivo: Encontrar o conjunto completo de restrições nas funções de demanda. Essa lista poderia ser usada de duas formas: 1) examinando afirmações teoricas de como uma firma reagiria a mudanças no ambiente econômico. 2) usando as restrições empiricamente para decidir se o comportamento da firma é consistente com um modelo de maximização.

Método: abordagem em três formas:

1. Examinando as condições de primeira ordem que caracterizam as escolhas ótimas;
1. Examinando as propriedades da maximização diretamente; e
1. Examinando as propriedades das funções de lucro e custo e relacionado essas propriedades com as funções de demanda (*dual approach*)

## 2.4 Estática comparativa usando condições de primeira ordem

Considerando o problema

$$\max_x pf(x) - wx$$

Se $f(x)$ é diferenciável, então, $x(w, p)$ tem que satisfazer as condições de primeira e segunda ordem:

$$f\prime(x(w, p)) = \frac wp \rightarrow p f\prime(x(w, p)) - w = 0$$

e

$$f\prime \prime(x(p,w)) \le 0$$

Como a CPO é uma igualdade, podemos diferenciar com respeito a $w$ para entender o comportamento de $x(w, p)$ quando da mudança de $w$.

$$ p \frac{\partial f\prime(x(w, p))}{\partial{w}} - 1 = 0 $$

aplicando a regra da cadeia:

$$p \frac{\partial f\prime(x(w, p))}{\partial {x(w, p)}} * \frac{\partial x(w, p)}{\partial{w}} = 1 $$

ou seja:

$$\frac{\partial x(w, p)}{\partial{w}} =\frac{1}{pf\prime\prime(x(w,p))}$$

Dado que $f\prime \prime(x(p,w)) \le 0$, A derivada $x_w$ é negativa, ou seja, a curva de $x(w,p)$ em relação a $w$ é decrescente.

Quanto maior a magnitude de $f\prime \prime$ no ponto de máximo (quanto mais curva for a função de produção no ponto de máximo), menor será o efeito da mudança nos preços no nível de produção.

O mesmo raciocínio pode ser feito para várias variávies. Assumindo $p = 1$ para simplificar, temos que:

$$Df(x(w)) - w = 0$$

$$D^2f(x(w))Dx(w) - I = 0$$

Resolvendo para a matriz de substituição temos que:

$$Dx(w) = [D^2f(x(w))]^{-1}$$

Dado que $D^2(f(x(w)))$ é uma matriz simétrica negativa definida, a matriz $Dx(w)$ também é uma matriz negativa definida.

## 2.5 Estática comparativa usando algebra

Axioma Fraco da Maximização do Lucro (__WAPM__)

Baseia-se na verificação se uma firma é maximizador a partir de observações empíricas. Dada uma lista de preços $p^t$ e a lista de produtos líquidos correspondentes $y^t$, então, o produto líquido a um nível de preço $p^t$ deve ser pelo menos igual ou superior ao lucro de qualquer outro produto líquido que a firma escolhesse., ou seja, $p^ty^t \ge p^ty^s$ para todo $t$ e $s=1,\dots,T$.

$$p^t(y^t - y^s) \ge 0$$

$$-p^t(y^t - y^s) \ge 0$$

Adicionando essas equações:

$$(p^t - p^s)(y^t - y^s) \ge 0$$

ou seja,

$$\Delta p \Delta y \ge 0$$

Isso é basicamente uma versão $\Delta$ da seção 2.4, mas é bastante forte visto que se aplica não somente a aumentos infinitesimais.

## 2.6 Recuperabilidade

Trata da idéia de recuperar a tecnologia que gera um determinado comportamento $(p^t, y^t)$ como um comportamento de maximização. Se é possível recuperar a tecnologia para um conjunto de dados que  satisfaz a __WAPM__, então, __WAPM__ exauri as implicações do comportamento maximizador de lucro.

# 3 Função Lucro

Dado um conjunto de produção Y, trata-se de calcular a função lucro $\pi(p)$ que fornece o lucro máximo obtido aos preços $p$

Definição de lucro: $\pi(\boldsymbol{p})= \max_y \boldsymbol{py}$ para $\boldsymbol{y}\ \ in\ \  \boldsymbol{Y}$. A função objetivo é uma função linear dos preços.

## 3.1 Propriedades da função

Propriedades seguem somente a hipótese da maximização. Hipóteses sobre convexidade, monotonicidade ou outras regularidades não são necessárias.

1. Não decrescente em preços dos produtos e não crescente em preços de insumos. se $p\prime_i \ge pi$ para todos os preços de produtos e $p\prime_j \le p_j$ para todos preços de insumos, então $\pi(p\prime) \ge \pi(p)$. *Se todos os preços aumentarem na mesma proporção, o lucro aumenta na mesmas proporção)*.
1. Homogênea de grau 1 em $\boldsymbol{p}$. $\pi(t\boldsymbol{p}) = t\pi(\boldsymbol{p})$ para todo $t \ge 0$.
1. Convexa em $\boldsymbol{p}$.
1. Contínua em $\boldsymbol{p}$

## 3.2 Funções de demanda e oferta a partir da função de produção

$$\pi(\boldsymbol{p}) = \boldsymbol{py}(\boldsymbol{p})$$

__Lema de Hotelling (a propriedade derivativa)__

# 4 Minimização do Custo

# 6. Dualidade

Dada uma função de custo, é possível encontrar uma tecnologia que poderia ter gerado a função. Essencialmente, a função de custo contém as mesmas informações da função de produção.


# 7. Maximização da Utilidade

Objetivo: derivar funções de demanda considerando um modelo de maximização da utilizade.

## 7.1 Preferências do consumidor

A preferência "ordena" o o conjunto de cestas de produtos. A ordenção segue a sintaxe $\boldsymbol{x} \succeq \boldsymbol{y}$.

Propriedades do conjunto de cestas de produtos:

1. Completa: para todo $\boldsymbol{x}$ e $\boldsymbol{y}$ em $X$, ou $\boldsymbol{x} \succeq \boldsymbol{y}$ ou $\boldsymbol{x} \preceq \boldsymbol{y}$ ou os dois.
1. Reflexiva: para todo $\boldsymbol{x}$ em $X$, $\boldsymbol{x} \succeq \boldsymbol{x}$
1. Transitiva: se $\boldsymbol{x} \succ \boldsymbol{y}$ e $\boldsymbol{y} \succ \boldsymbol{z}$, então, $\boldsymbol{x} \succ \boldsymbol{z}$
1. Contínua
1. Monotonicidade fraca: se $\boldsymbol{x} \ge \boldsymbol{y}$, então $\boldsymbol{x} \succeq \boldsymbol{y}$
1. Monotonicidade forte: se $\boldsymbol{x} \ge \boldsymbol{y}$ e $\boldsymbol{x} \neq \boldsymbol{y}$ então $\boldsymbol{x} \succ \boldsymbol{y}$
1. Insaciedade local (*Local nonstation*): dado um $\boldsymbol{x} \in X$ e um $\epsilon > 0$, então, existe uma cesta $\boldsymbol{y} \in X$ com $|\boldsymbol{x} - \boldsymbol{y}| < \epsilon$ tal que $\boldsymbol{y} \succ \boldsymbol{x}$
1. Convexidade: dados $\boldsymbol{x}, \boldsymbol{y}\ e\  \boldsymbol{z} \in X$, tal que $\boldsymbol{x} \succeq \boldsymbol{z}\ e\ \boldsymbol{y} \succeq \boldsymbol{x}$, então $t\boldsymbol{x} + (1-t)\boldsymbol{y} \succeq \boldsymbol{z}\ \ \forall \ \ 0 < t < 1$
1. Convexidade estrita: dados $\boldsymbol{x} \neq \boldsymbol{y}\ e\  \boldsymbol{z} \in X$, tal que $\boldsymbol{x} \succeq \boldsymbol{z}\ e\ \boldsymbol{y} \succeq \boldsymbol{x}$, então $t\boldsymbol{x} + (1-t)\boldsymbol{y} \succ \boldsymbol{z}\ \ \forall \ \ 0 < t < 1$

As propriedades de completude, reflexividade, transitividade, e continuidade são suficientes para resumir as preferências através de uma função utilidade $u : X \rightarrow R$ tal que se $\boldsymbol{x} \succ \boldsymbol{y}$, então $u(\boldsymbol{x}) > u(\boldsymbol{y})$.

A convexidade implica que o agente prefere médias do que extremos. Fora disso, a convexidade não tem muitos efeitos.

Se as preferências são __completas__, __reflexivas__, __transitivas__, __contínuas__ e __fortemente monotônicas__, então existe uma função de utilidade contínua $u:R_+^k \rightarrow R$ que representa essas preferências.

## 7.2 Comportamento do consumidor

O conjunto de cestas que estão dentro do orçamento do consumidor é dado por:

$$ B = \{\boldsymbol{x}\  in\  X: \boldsymbol{px}\le m\}$$

Quando se trata de consumidor, não se faz mais diferenciação de $p$ e $w$. Preços são preços de mercadorias.

O problema de maximização é;

$\max u(\boldsymbol{x})$ tal que $\boldsymbol{px} \le m$ e $\boldsymbol{x} \in X$

Dada a hipótese da não saciedade, é necessário encontrar uma função que possa ser otimizada: A função indireta de utilidade:

$$ \nu(\boldsymbol{p},m) = \max u(\boldsymbol{x})$$

com $\boldsymbol{px} = m$.

A função que relaciona $\boldsymbol{p}$ com a cesta demandada é chamada a função de demanda do consumidor $\boldsymbol{x}(\boldsymbol{p},m)$. A convexidade estrita garante que para cada restrição, existe uma única cesta que maximiza a utilidade.

Caracterizando o comportamento otimizador via cálculo.

$$\mathcal{L} =\boldsymbol{u}(\boldsymbol{x}) - \lambda(\boldsymbol{px}-m)$$

# 8 Escolha

O livro aborda o problmea da escolha de três formas: diferenciando as condições de primeira ordem, usando as propriedades das funções $\nu(\boldsymbol{p}, m)$  e $e(p,u^*)$ e usando desigualdades implicadas pelo processo de otimização.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYzMjkzNjcyOF19
-->