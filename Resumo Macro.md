# Resumo Macroeconomia

[link aulas](https://www.youtube.com/watch?v=eoo1d0ef_M8&index=1&list=PLSbo9kXA_LcxSeXYQqDwFjXsksE9m1p1P)

[link latex](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)

[link greek letters](https://www.latex-tutorial.com/symbols/greek-alphabet/)

[artigo log como diferença %](https://stats.stackexchange.com/questions/244199/why-is-it-that-natural-log-changes-are-percentage-changes-what-is-about-logs-th)

[Caracteres latex](https://www.commentcamarche.net/contents/620-latex-table-de-caracteres)

# Importância

# História

Enfoque neoclássico - Modelos de Crescimento Exógeno

1. Modelo Solow (1956) e Swan (1956)  
2. Modelo Ramsey (1928), Cass (1965) e Koopmans (1965) -

Chave: função de produção com rendimentos decrescente de capital
Predições: 

1. Não há crescimento econômico a longo prazo. Só a crescimento quando se impõe de forma exógena ao modelo
2. Há convergência econômica entre os países

Modelos de crescimento endógeno

1. Modelo de Romer (1986) - Externalidades do Capital
2. Modelo de Rebelo (1990) - Modelo AK (linear)
3. Modelo de Lucas (1988) - Capital Humano
4. Modelo de Barro (1990) - Gasto público produtivo

Chave: Função de produção com rendimentos constantes de capital (ou existência de competição imperfeita nos mercados)

Predições:
1. Há crescimento econômico de longo prazo, explicado endogenamente
2. Não há convergência ecômica entre os países.

# 1. Modelagem neoclássica
Há dois tipos de modelagem:

1. Taxa de poupança constante: 

$$s_t = sy_t \rightarrow c_t = (1 - s)y_t$$

2. Modelos de crescimento ótimos (poupança e consumo ótimos)

$$U(0) = \int_0^\infty e^{-\rho t} u(c_t)L_tdt \rightarrow c_t^*$$

A capacidade preditiva dos modelos depende mais das escolhas de funções de produção do que da complexidade matemática dos modelos.

# Modelos c/ Taxas de Poupança Constantes

## Três passos para obtenção da eq fundamental

Obtenção da equação fundamental de crescimento: três passos:
1. Definição dos pressupostos (taxa de poupança, depreciação, população e etc);
2. Obtenção da lei de acumulação do capital agregado;

$$\dot K_t = sY_t - \delta K_t$$

3. Obtenção da equação fundamental do crescimento

$$\dot k_t = sy_t - (\delta +n)k_t$$

Chave: Características da função de produção.

$$Y_t=F(K_t,L_t,A_t,...)$$

### Passo 1: Definição dos pressupostos

Pressupostos:
1) $$S_t = sY_t$$ (poupança) constante;
2) $$\delta$$ (depreciação) constante. $$I_t = \dot K_t + \delta K_t, 0 \le \delta \le 1$$. 
3) População = Trabalho = $$L_t$$. 
4) $$\frac{\dot L_t}{L_t} = n$$ (taxa de crescimento constante)

### Passo 2: Obtendo a lei de acumulação de capital:

Repartição do produto da economia:

$$Y_t = C_t + I_t$$ (1.1)  

$$Y_t = C_t + S_t$$ (1.2)

$$C_t + I_t = C_t + S_t \rightarrow I_t = S_t$$ (1.3)

Usando pressupostos 1 e 2 em (1.3), 

$$sY_t = \dot K_t + \delta K_t$$ (1.4)

ou, a lei de acumulação de capital na economia:

$$\dot K_t = sY_t - \delta K_t$$ (1.5)

### Passo 3: Obtenção da equação do crescimento

Essa equação vem da lei de acumulação de capital (1.5), na sua forma intensiva (per capta).

$$\frac {\dot K_t}{L_t} = s \frac {Y_t}{L_t} - \delta \frac{K_t}{L_t}$$ (1.6)

Como $$\frac {Y_t}{L_t} = y_t$$ e $$\frac {K_t}{L_t} = k_t$$, encontramos $$\frac{\dot K_t}{L_t}$$ através da linearização de $$k_t$$ e de sua derivação com respeito a $$_t$$.

$$k_t = \frac {K_t}{L_t} \rightarrow \ln k_t = \ln K_t - \ln L_t$$ (1.7)

Derivando (1.7) com respeito ao tempo $$\biggl(\frac {\partial {\ln k_t}} {\partial t} = \frac 1{k_t} \frac{k_t}{\partial {_t}} = \frac {\dot k_t}{k_t} \biggr)$$ temos: 

$$\frac {\dot k_t}{k_t} = \frac {\dot K_t}{K_t} - \frac {\dot L_t}{L_t}$$ (1.8)

Assim, 

$$\dot k_t = k_t \frac {\dot K_t}{K_t} - k_t \frac{\dot L_t}{L_t}$$

Usando pressuposto 4 $$\biggl(\frac{\dot L_t}{L_t} = n \biggr)$$, temos que 

$$\dot k_t = k_t \frac {\dot K_t}{K_t} - k_t n$$ 

Sabendo que temos que $$k_t = \frac {K_t}{L_t}$$, então, $$\dot k_t = \frac {K_t}{L_t} \frac {\dot K_t}{K_t} - k_t n$$. 

Eliminando termos, 

$$\dot k_t = \frac {\dot K_t}{L_t} - nk_t \rightarrow \frac {\dot K_t}{L_t} = \dot k_t + nk_t$$

Substituindo em (1.5), temos que:

$$\dot k_t + nk_t = sy_t - \delta k_t$$

ou

$$\dot k_t = sy_t - k_t(n + \delta)$$ (1.9)

Essa é a __equação básica de crescimento__ de qualquer modelo de crescimento com taxa de poupança constante. A chave para modelar está na *função de produção* utilizada.

## Modelo Solow e Swan - Equação Fundamental de Crescimento

Método

1. Obtenção matemática
    1. Hipóteses
    1. Caracterização da função de produção neoclássica
        1. Rendimentos constantes de escala
        1. Produtividade marginal dos fatores positiva e decrescente
        1. Cumprimento das condições de Inada
    1. Obtenção da lei de acumulação de capital agregado $$\dot K_t = sA_t K_t^\alpha L_t^{1-\alpha} - \delta K_t$$
1. Interpretação
1. Representação gráfica

### Obtenção Matemática

#### Hipóteses

1. $$s$$ constante
2. $$\delta$$ constante
3. População = Trabalho = $$L_t$$
4. $$\frac{\dot L_t}{L_t}$$ constante

#### Caracterização da função de produção 

Exemplo de função de produção neoclássica (que possui características que devem ser respeitadas para uso no modelo): Cobb-Douglas 

$$Y_t = AK_t^\alpha L_t^{1-\alpha}$$ (1.10)

Características necessárias para funções de produção neoclássicas:

1. Retornos constantes de escala 
$$\lambda Y_t = \lambda AK_t^\alpha L_t^{1-\alpha}$$
1. Rendimentos dos fatores decrescentes (produtividade marginal positiva mas decrescente)
1. Condições de Inada

Romer trabalha a modelagem sem entrar na função de produção. Trabalha somente com uma definição $$Y_t = F(K_t, A_tL_t)$$, onde:

1. $$A_tL_t$$ = trabalho efetivo,
1. A renda dos fatores de produção permanece constante para uma dada combinação $$K/Y$$
1. O progresso tecnológico $$A$$ é aumentador do trabalho (*Harrod-neutra*)
1. Outras formas são possíveis, como:
    1. Aumentadora de capital (*Solow-neutra*) $$Y_t = F(A_tK_t, L_t)$$ - renda dos fatores de produção são constantes para uma combinação $$L/Y$$; e
    1. $$Y_t = AF(K_t,L_t)$$ - onde a relação entre as produtividades marginais permance constante para uma dada combinação $$K/L$$.

Atenção: a opção pela função aumentadora do trabalho implica relação $$K/Y$$ constante, facilitando o tratamento do modelo.



#### Obtenção matemática

$$Y_t = C_t + I_t$$

$$Y_t = C_t + S_t$$

$$S_t = I_t$$

Substituindo a função de exemplo (Cobb-Douglas) na lei de acumulação de capital $$sY_t = \dot K_t + \delta K_t$$, temos que:

$$\dot K_t = sAK_t^\alpha L_t^{1-\alpha} - \delta K_t$$ (1.11)

Transformando na forma intensiva, temos:

$$ \frac {\dot K_t}{L_t} = s\frac {AK_t^\alpha L_t^{1-\alpha}}{L_t} - \frac{\delta K_t}{L_t}$$ (1.12)

Sabendo que:
1. $$\frac{K_t}{L_t} = k_t$$
1. $$\frac {AK_t^\alpha L_t^{1-\alpha}}{L_t} = \frac {AK_t^\alpha L_t^{1-\alpha}}{L_t^\alpha L_t^{1-\alpha}} = \frac {AK_t^\alpha}{L_t^\alpha} = Ak_t^\alpha$$; e
1. Como demonstrado na obtenção da lei de acumulação de capital per capta, $$\frac{\dot K_t}{L_t} = \dot k_t + nk_t$$,

Temos que:

$$\dot k_t + nk_t = sAk_t^\alpha - \delta k_t$$

$$\dot k_t = sAk_t^\alpha - \delta k_t + nk_t$$

E por fim, a __equação fundamental de crescimento de Solow e Swan__ para a função de produção Cobb-Douglas:

$$ \dot k_t = sAk_t^\alpha + k_t(n - \delta)$$ (1)

#### Representação gráfica
[Análise GeoAlgebra](https://www.geogebra.org/graphing/tsytu8jw)

## Predições do modelo Solow e Swan

Método:

1. Obtenção da equação fundamental e da taxa de crescimento 

$$\gamma_k = \frac{\dot k_t}{k_t} = sA_tk_t^{\alpha-1} -(\delta - n)$$

2. Representação gráfica
3. Estudo da dinâmica de transição até o estado estacionário
4. Caracterização do estado estacionário

$$k^* = \biggl(\frac{sA}{n+\delta}\biggr)^\frac1{1-\alpha}$$

Predições:
1. Ausência de crescimento econômico a longo prazo (a não ser por imposição exógena)
2. Existência de convergência

### Obtenção da taxa de crescimento

Usando a equação básica do modelo de crescimento com taxa de poupança constante $$\dot k_t = sy_t - k_t(n + \delta)$$, 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM4MjIzNDc3MywxNjAxMzIyODAzXX0=
-->