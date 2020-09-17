# Introducción al Aprendizaje Estadístico {#intro-AE}

<!-- 
knitr::purl("01-introduccion.Rmd", documentation = 2)
knitr::spin("01-introduccion.Rmd",knit = FALSE)
-->





<!-- 
## Introducción {#intro} 
-->

La denominada *Ciencia de Datos* (Data Science; también denominada *Science of Learning*) se ha vuelto muy popular hoy en día. 
Se trata de un campo multidisciplicar, con importantes aportaciones estadísticas e informáticas, dentro del que se incluirían disciplinas como *Minería de Datos* (Data Mining), *Aprendizaje Automático* (Machine Learning), *Aprendizaje Profundo* (Deep Learning), *Modelado Predictivo* (Predictive Modeling), *Extracción de Conocimiento* (Knowlegde Discovery) y también el *Aprendizaje Estadístico* (Statistical Learning).

Podríamos definir la Ciencia de Datos como el conjunto de conocimientos y herramientas utilizados en las distintas etapas del análisis de datos (ver Figura \@ref(fig:esquema)). Otras definiciones podrían ser:

-   El arte y la ciencia del análisis inteligente de los datos.

-   El conjunto de herramientas para entender y modelizar conjuntos
    (complejos) de datos.

-   El proceso de descubrir patrones y obtener conocimiento a partir de
    grandes conjuntos de datos (*Big Data*).


\begin{figure}[!htb]

{\centering \includegraphics[width=0.8\linewidth]{images/esquema2} 

}

\caption{Etapas del proceso}(\#fig:esquema)
\end{figure}

Una de estas etapas (que están interrelacionadas) es la construcción de modelos a partir de los datos para aprender y predecir. Podríamos decir que el Aprendizaje Estadístico (AE) se encarga de este problema desde el punto de vista estadístico.

En Estadística se consideran modelos estocásticos (con componente aleatoria), para tratar de tener en cuenta la incertidumbre debida a que no se disponga de toda la información (sobre las variables que influyen en el fenómeno de interés).

> "Nothing in Nature is random... a thing appears random only through the incompleteness of our knowledge."
>
> --- Spinoza, Baruch (Ethics, 1677)

> "To my mind, although Spinoza lived and thought long before Darwin, Freud, Einstein, and the startling implications of quantum theory, he had a vision of truth beyond what is normally granted to human beings."
>
> --- Shirley, Samuel (Complete Works, 2002). Traductor de la obra completa de Spinoza al inglés.

La Inferencia Estadística proporciona herramientas para ajustar este tipo de modelos a los datos observados (seleccionar un modelo adecuado, estimar sus parámetros y contrastar su validez). 
Sin embargo, en la aproximación estadística clásica como primer objetivo se trata de explicar por completo lo que ocurre en la población y suponiendo que esto se puede hacer con modelos tratables analíticamente, emplear resultados teóricos (típicamente resultados asintóticos) para realizar inferencias (entre ellas la predicción). 
Los avances en computación han permitido el uso de modelos estadísticos más avanzados, principalmente métodos no paramétricos, muchos de los cuales no pueden ser tratados analíticamente (por lo menos no por completo o no inicialmente), este es el campo de la Estadística Computacional^[Lauro (1996) definió la Estadística Computacional como la disciplina que tiene como objetivo "diseñar algoritmos para implementar métodos estadísticos en computadoras, incluidos los impensables antes de la era de las computadoras (por ejemplo, bootstrap, simulación), así como hacer frente a problemas analíticamente intratables".]. Desde este punto de vista, el AE se enmarcaría dentro del campo de la Estadística Computacional.

Cuando pensamos en AE pensamos en:

- Flexibilidad (hay menos suposiciones sobre los datos).

- Procesamiento automático de datos.

- Big Data (en el sentido amplio, donde "big" puede hacer referencia a datos complejos).

- Predicción.

Por el contrario, muchos de los métodos del AE no se preocupan (o se preocupan poco) por:

- Reproducibilidad.

- Cuantificación de la incertidumbre (en términos de probabilidad).

- Inferencia.

La idea es “dejar hablar a los datos” y no "encorsetarlos" a priori, dándoles mayor peso que a los modelos.
Sin embargo, esta aproximación puede presentar diversos inconvenientes:

-   Algunos métodos son poco interpretables (se sacrifica la interpretabilidad por la precisión de las predicciones).

-   Pueden aparecer problemas de sobreajuste (*overfitting*; en los métodos estadísticos clásicos es más habitual que aparezcan problemas de infraajuste, *underfitting*).

-   Pueden presentar más problemas al extrapolar o interpolar (en comparación con los métodos clásicos).


## Aprendizaje Estadístico vs. Aprendizaje Automático

El término *Machine Learning* (ML; Aprendizaje Automático) se utiliza en el campo de la *Intelingencia Artificial* desde 1959 para hacer referencia, fundamentalmente, a algoritmos de predicción (inicialmente para reconocimiento de patrones). 
Muchas de las herramientas que utilizan provienen del campo de la Estadística y, en cualquier caso, la Estadística (y por tanto las Matemáticas) es la base de todos estos enfoques para analizar datos (y no conviene perder la base formal).
Por este motivo desde la Estadística Computacional se introdujo el término *Statistical Learning* (Aprendizaje Estadístico) para hacer referencia a este tipo de herramientas, pero desde el punto de vista estadístico (teniendo en cuenta la incertidumbre debida a no disponer de toda la información).

Tradicionalmente ML no se preocupa del origen de los datos e incluso es habitual que se considere que un conjunto enorme de datos es equivalente a disponer de toda la información (i.e. a la población).

> "The sheer volume of data would obviate the need of theory and even
> scientific method"
>
> --- Chris Anderson, físico y periodista, 2008

Por el contrario en el caso del AE se trata de comprender, si es posible, el proceso subyacente del que provienen los datos y si estos son representativos de la población de interés (i.e. si tienen algún tipo de sesgo).
No obstante, en este libro se considerará en general ambos términos como sinónimos.

ML/AE hacen un importante uso de la programación matemática, ya que muchos de sus problemas se plantean en términos de la optimización de funciones bajo restricciones. 
Recíprocamente, en optimización también se utilizan algoritmos de ML/AE.


### Machine Learning vs. Data Mining

Mucha gente utiliza indistintamente los nombres ML y *Data Mining* (DM). 
Sin embargo, aunque tienen mucho solapamiento, lo cierto es que hacen referencia a conceptos ligeramente distintos.

ML es un conjunto de algoritmos principalmente dedicados a hacer predicciones y que son esencialmente automáticos minimizando la intervención humana.

DM intenta *entender* conjuntos de datos (en el sentido de encontrar sus patrones), requiere de una intervención humana activa (al igual que la Inferencia Estadística tradicional), pero utiliza entre otras las técnicas automáticas de ML. Por tanto podríamos pensar que es más parecido al AE.


### Las dos culturas (Breiman, 2001)

Breiman diferencia dos objetivos en el análisis de datos, que él llama *información* (en el sentido de *inferencia*) y *predicción*. 
Cada uno de estos objetivos da lugar a una cultura:

- *Modelización de datos*: desarrollo de modelos (estocásticos) que permitan ajustar los datos y hacer inferencia. Es el trabajo habitual de los estadísticos académicos.

- *Modelización algorítmica* (en el sentido de predictiva): esta cultura no está interesada en los mecanismos que generan los datos, sólo en los algoritmos de predicción. Es el trabajo habitual de muchos estadísticos industriales y de muchos ingenieros informáticos. El ML es el núcleo de esta cultura que pone todo el énfasis en la precisión predictiva (así, un importante elemento dinamizador 
son las competiciones entre algoritmos predictivos, al estilo del [Netflix Challenge](https://en.wikipedia.org/wiki/Netflix_Prize)).


### Machine Learning vs. Estadística (Dunson, 2018)

- "Machine learning: The main publication outlets tend to be peer-reviewed conference proceedings and the style of research is very fast paced, trendy, and driven by performance metrics in prediction and related tasks".

- "Statistical community: The main publication outlets are peer-reviewed journals, most of which have a long drawn out review process, and the style of research tends to be careful, slower paced, intellectual as opposed to primarily performance driven, emphasizing theoretical support  (e.g., through asymptotic properties), under-stated, and conservative".

- "*Big data* in ML typically means that the number of examples (i.e. sample size) is very large".

- "In statistics (...) it has become common to collect high dimensional, complex and intricately structured data. Often the dimensionality of the data vastly exceeds the available sample size, and the fundamental challenge of the statistical analysis is obtaining new insights from these huge data, while maintaining reproducibility/replicability and reliability of the results".


## Métodos de Aprendizaje Estadístico

Dentro de los problemas que aborda el Aprendizaje Estadístico se suelen diferenciar dos grandes bloques: el aprendizaje no supervisado y el supervisado. El *aprendizaje no supervisado* comprende los métodos exploratorios, es decir, aquellos en los que no hay una variable respuesta (al menos no de forma explícita). El principal objetivo de estos métodos es entender las relaciones entre los datos y su estructura, y pueden clasificarse en las siguientes categorías:

  -   Análisis descriptivo.
    
  -   Métodos de reducción de la dimensión (análisis de componentes principales, análisis factorial...).
    
  -   Clúster.
    
  -   Detección de datos atípicos.

El *aprendizaje supervisado* engloba los métodos predictivos, en los que una de las variables está definida como variable respuesta. Su principal objetivo es la construcción de modelos que posteriormente se utilizarán, sobre todo, para hacer predicciones. Dependiendo del tipo de variable respuesta se diferencia entre:

  -   Clasificación: respuesta categórica (también se emplea la denominación de variable cualitativa, discreta o factor).

  -   Regresión: respuesta numérica (cuantitativa).

En este libro nos centraremos únicamente en el campo del aprendizaje supervisado y combinaremos la terminología propia de la Estadística con la empleada en AE (por ejemplo, en Estadística es habitual considerar un problema de clasificación como un caso particular de regresión).


### Notación y terminología

<!-- Emplearemos principalmente la terminología estadística, pero trataremos de incluir también la de ML -->

Denotaremos por $\mathbf{X}=(X_1, X_2, \ldots, X_p)$ al vector formado por las variables predictoras 
(variables explicativas o variables independientes; también *inputs* o *features* en la terminología de ML), cada una de las cuales podría ser tanto numérica como categórica^[Aunque hay que tener en cuenta que algunos métodos están diseñados para predictores numéricos, otros para categóricos y algunos para ambos tipos.].
En general (ver comentarios más adelante), emplearemos $Y\left(\mathbf{X} \right)$ para referirnos a la variable objetivo (variable respuesta o variable dependiente; también *output* en la terminología de ML), que como ya se comentó puede ser una variable numérica (regresión) o categórica (clasificación).

Supondremos que el objetivo principal es, a partir de una muestra:
$$\left\{ \left( x_{1i}, \ldots, x_{pi}, y_{i} \right)  : i = 1, \ldots, n \right\},$$
<!-- 
$$\left\{ \left( \mathbf{x}_{i}, y_{i} \right)  : i = 1, \ldots, n \right\},$$
siendo $\mathbf{x}_{i}=\left(  x_{1i},\ldots,x_{pi}\right)^{\prime}$ el vector de valores de las variables explicativas e $y_i$ el valor de la respuesta en la observación *i*-ésima,
-->
obtener (futuras) predicciones $\hat Y\left(\mathbf{x} \right)$ de la respuesta para $\mathbf{X}=\mathbf{x}=\left(x_{1}, \ldots, x_{p}\right)$.
<!-- 
ajustando un modelo, diseñando un algoritmo, entrenando una *machine* o *learner* 

$\mathbf{Y}=\left(  y_{1},\ldots,y_{n}\right)^{\prime}$
vector de observaciones de la variable $Y$
-->

En regresión consideraremos como base el siguiente modelo general (podría ser después de una transformación de la respuesta): 
\begin{equation} 
  Y(\mathbf{X})=m(\mathbf{X})+\varepsilon,
  (\#eq:modelogeneral)
\end{equation}
donde $m(\mathbf{x}) = E\left( \left. Y\right\vert_{\mathbf{X}=\mathbf{x}} \right)$ es la media condicional, denominada función de regresión (o tendencia), y $\varepsilon$ es un error aleatorio de media cero y varianza $\sigma^2$, independiente de $\mathbf{X}$.
Este modelo puede generalizarse de diversas formas, por ejemplo, asumiendo que la distribución del error depende de $X$ (considerando $\varepsilon(\mathbf{X})$ en lugar de $\varepsilon$) podríamos incluir dependencia y heterocedasticidad. 
En estos casos normalmente se supone que lo hace únicamente a través de la varianza (error heterocedástico independiente), denotando por $\sigma^2(\mathbf{x}) = Var\left( \left. Y\right\vert_{\mathbf{X}=\mathbf{x}} \right)$ la varianza condicional^[Por ejemplo considerando en el modelo base $\sigma(\mathbf{X})\varepsilon$ como termino de error y suponiendo adicionalmente que $\varepsilon$ tiene varianza uno.].


Como ya se comentó se podría considerar clasificación como un caso particular, por ejemplo definiendo $Y\left(\mathbf{X} \right)$ de forma que tome los valores $1, 2, \ldots, K$, etiquetas que identifican las $K$ posibles categorías (también se habla de modalidades, niveles, clases o grupos). 
Sin embargo, muchos métodos de clasificación emplean variables auxiliares (variables *dummy*), indicadoras de las distintas categorías, y emplearemos la notación anterior para referirnos a estas variables (también denominadas variables *target*). En cuyo caso, denotaremos por $G \left(\mathbf{X} \right)$ la respuesta categórica (la clase verdadera; $g_i$, $i =1, \ldots, n$, serían los valores observados) y por $\hat G \left(\mathbf{X} \right)$ el predictor.

Por ejemplo, en el caso de dos categorías, se suele definir $Y$ de forma que toma el valor 1 en la categoría de interés (también denominada *éxito* o *resultado positivo*) y 0 en caso contrario (*fracaso* o *resultado negativo*)^[Otra alternativa sería emplear 1 y -1, algo que simplifica las expresiones de algunos métodos.].
Además, en este caso, los modelos típicamente devuelven estimaciones de la probabilidad de la clase de interés en lugar de predecir directamente la clase, por lo que se empleará $\hat p$ en lugar de $\hat Y$. 
A partir de esa estimación se obtiene una predicción de la categoría. 
Normalmente se predice la clase más probable, i.e. "éxito" si $\hat p(\mathbf{x}) > c = 0.5$ y "fracaso" en caso contrario (con probabilidad estimada $1 - \hat p(\mathbf{x})$).

Resulta claro que el modelo base general \@ref(eq:modelogeneral) puede no ser adecuado para modelar variables indicadoras (o probabilidades).
Muchos de los métodos de AE emplean \@ref(eq:modelogeneral) para una variable auxiliar numérica (denominada puntuación o *score*) que se transforma a escala de probabilidades mediante la función logística (denominada función sigmoidal, *sigmoid function*, en ML)^[De especial interés en regresión logística y en redes neuronales artificiales.]:
$$p(s) = \frac{1}{1 + e^{-s}},$$
cuya inversa es la *función logit*:
$$\operatorname{logit}(p)=\log\left( \frac{p}{1-p} \right).$$

Lo anterior se puede generalizar para el caso de múltiples categorías, considerando variables indicadoras de cada categoría $Y_1, \ldots, Y_K$ (es lo que se conoce como la estrategia de "uno contra todos"). En este caso típicamente:
$$\hat G \left(\mathbf{x} \right) = \underset{k}{\operatorname{argmax}} \left\{ \hat p_k(\mathbf{x}) : k = 1, 2, \ldots, K \right\}.$$

<!-- 
Otra notación:

$\mathcal{G}$ conjunto de posibles categorías

Matrices en mayúsculas y negrita/caligráfico? 
Mayúsculas y negrita/caligráfico con subíndice para referirse al vector columna? 
Traspuesta al estilo de JSS 
-->
    

### Métodos (de aprendizaje supervisado) y paquetes de R

Hay una gran cantidad de métodos de aprendizaje supervisado implementados en centenares de paquetes de `R` (ver por ejemplo [CRAN Task View: Machine Learning & Statistical Learning](https://cran.r-project.org/web/views/MachineLearning.html)).
A continuación se muestran los principales métodos y algunos de los paquetes de R que los implementan (muchos son válidos para regresión y clasificación, como por ejemplo los basados en árboles, aunque aquí aparecen en su aplicación habitual).

Métodos de Clasificación:

-   Análisis discriminante (lineal, cuadrático), Regresión logística, multinomial...: 
    `stats`, `MASS`...

-   Árboles de decisión, *bagging*, *random forest*, *boosting*: 
    `rpart`, `party`, `C50`, `Cubist`, `randomForest`, `adabag`, `xgboost`...

-   *Support vector machines* (SVM): 
    `kernlab`, `e1071`...

Métodos de regresión:

-   Modelos lineales:

    -   Regresión lineal: `lm()`, `lme()`, `biglm`...

    -   Regresión lineal robusta: `MASS::rlm()`...

    -   Métodos de regularización (Ridge regression, Lasso):
        `glmnet`, `elasticnet`...

-   Modelos lineales generalizados: `glm()`, `bigglm`, ..

-   Modelos paramétricos no lineales: `nls()`, `nlme`...

-   Regresión local (vecinos más próximos y métodos de suavizado):
    `kknn`, `loess()`, `KernSmooth`, `sm`, `np`...

-   Modelos aditivos generalizados (GAM): `mgcv`, `gam`...

-   Redes neuronales: `nnet`... 

También existen paquetes de `R` que permiten utilizar plataformas de ML externas, como por ejemplo [`h2o`](https://github.com/h2oai/h2o-3/tree/master/h2o-r ) o [`RWeka`](https://CRAN.R-project.org/package=RWeka).

Como todos estos paquetes emplean opciones, estructuras y convenciones sintácticas diferentes, se han desarrollado paquetes que proporcionan interfaces unificadas a muchas de estas implementaciones. 
Entre ellos podríamos citar [`caret`](https://topepo.github.io/caret),[`mlr3`](https://mlr3.mlr-org.com) y [`tidymodels`](https://www.tidymodels.org).
En la Sección \@ref(caret) se incluye una breve introducción al paquete [`caret`](https://topepo.github.io/caret) que será empleado en diversas ocasiones a lo largo del presente libro.

Adicionalmente hay paquetes de R que disponen de entornos gráficos que permiten emplear estos métodos evitando el uso de comandos. 
Entre ellos estarían R-Commander con el plugin FactoMineR (`Rcmdr`, `RcmdrPlugin.FactoMineR`) y [`rattle`](https://rattle.togaware.com).


## Construcción y evaluación de los modelos {#const-eval}

En Inferencia Estadística clásica el procedimiento habitual es emplear toda la información disponible para construir un modelo válido (que refleje de la forma más fiel posible lo que ocurre en la población) y asumiendo que el modelo es el verdadero (lo que en general sería falso) utilizar métodos de inferencia para evaluar su precisión. 
Por ejemplo, en el caso de regresión lineal múltiple, el coeficiente de determinación ajustado sería una medida del la precisión del modelo para predecir nuevas observaciones (no se debería emplear el coeficiente de determinación sin ajustar; aunque, en cualquier caso, su validez dependería de la de las suposiciones estructurales del modelo).

Alternativamente, en Estadística Computacional es habitual emplear técnicas de remuestreo para evaluar la precisión (entrenando también el modelo con todos los datos disponibles), principalmente validación cruzada (leave-one-out, k-fold), jackniffe o bootstrap. 

Por otra parte, como ya se comentó, algunos de los modelos empleados en AE son muy flexibles (están hiperparametrizados) y pueden aparecer problemas si se permite que se ajusten demasiado bien a las observaciones (podrían llegar a interpolar los datos). 
En estos casos habrá que controlar el procedimiento de aprendizaje, típicamente a traves de  parámetros relacionados con la complejidad del modelo (ver sección siguiente).

En AE se distingue entre parámetros estructurales, los que van a ser estimados al ajustar el modelo a los datos (en el entrenamiento), e hiperparámetros (*tuning parameters* o parámetros de ajuste), que imponen restricciones al aprendizaje del modelo (por ejemplo determinando el número de parámetros estructurales).
Si los hiperparámetros seleccionados producen un modelo demasiado complejo aparecerán problemas de sobreajuste (*overfitting*) y en caso contrario de infraajuste (*undefitting*).

Hay que tener en cuenta también que al aumentar la complejidad disminuye la interpretabilidad de los modelos. 
Se trataría entonces de conseguir buenas predicciones (habrá que evaluar la capacidad predictiva) con el modelo más sencillo posible.

<!-- Sección \@ref(bias-variance) -->

### Equilibrio entre sesgo y varianza: infraajuste y sobreajuste {#bias-variance}

La idea es que queremos aprender más allá de los datos empleados en el entrenamiento (en Estadística diríamos que queremos hacer inferencia sobre nuevas observaciones).
Como ya se comentó, en AE hay que tener especial cuidado con el sobreajuste. 
Este problema ocurre cuando el modelo se ajusta demasiado bien a los datos de entrenamiento pero falla cuando se utiliza en un nuevo conjunto de datos (nunca antes visto).

Como ejemplo ilustrativo emplearemos regresión polinómica, considerando el grado del polinomio como un hiperparámetro que determina la complejidad del modelo. 
En primer lugar simulamos una muestra y ajustamos modelos polinómicos con distintos grados de complejidad. 


```r
# Simulación datos
n <- 30
x <- seq(0, 1, length = n)
mu <- 2 + 4*(5*x - 1)*(4*x - 2)*(x - 0.8)^2 # grado 4
sd <- 0.5
set.seed(1)
y <- mu + rnorm(n, 0, sd)
plot(x, y) 
lines(x, mu, lwd = 2)
# Ajuste de los modelos
fit1 <- lm(y ~ x)
lines(x, fitted(fit1))
fit2 <- lm(y ~ poly(x, 4))
lines(x, fitted(fit2), lty = 2)
fit3 <- lm(y ~ poly(x, 20)) 
# NOTA: poly(x, degree, raw = FALSE) tiene un problema de desbordamiento si degree > 25
lines(x, fitted(fit3), lty = 3)
legend("topright", legend = c("Verdadero", "Ajuste con grado 1", 
                              "Ajuste con grado 4", "Ajuste con grado 20"), 
       lty = c(1, 1, 2, 3), lwd = c(2, 1, 1, 1))
```

\begin{figure}[!htb]

{\centering \includegraphics[width=0.8\linewidth]{01-introduccion_files/figure-latex/polyfit-1} 

}

\caption{Muestra (simulada) y ajustes polinómicos con distinta complejidad.}(\#fig:polyfit)
\end{figure}

Como se observa en la Figura \@ref(fig:polyfit) al aumentar la complejidad del modelo se consigue un mejor ajuste a los datos observados (empleados en el entrenamiento), a costa de un incremento en la variabilidad de las predicciones, lo que puede producir un mal comportamiento del modelo a ser empleado en un conjunto de datos distinto del observado. 

Si calculamos medidas de bondad de ajuste, como el error cuadrático medio (MSE) o el coeficiente de determinación, se obtienen mejores resultados al aumentar la complejidad. 
Como se trata de modelos lineales, podríamos obtener también el coeficiente de determinación ajustado, que sería preferible (en principio, ya que dependería de la validez de las hipótesis estructurales del modelo) para medir la precisión al emplear los modelos en un nuevo conjunto de datos.


```r
knitr::kable(t(sapply(list(fit1 = fit1, fit2 = fit2, fit3 = fit3), 
       function(x) with(summary(x), 
                        c(MSE = mean(residuals^2), R2 = r.squared, R2adj = adj.r.squared)))), digits = 2)
```


\begin{tabular}{l|r|r|r}
\hline
  & MSE & R2 & R2adj\\
\hline
fit1 & 1.22 & 0.20 & 0.17\\
\hline
fit2 & 0.19 & 0.87 & 0.85\\
\hline
fit3 & 0.07 & 0.95 & 0.84\\
\hline
\end{tabular}

Por ejemplo, si generamos nuevas respuestas de este proceso, la precisión del modelo más complejo empeorará considerablemente:


```r
y.new <- mu + rnorm(n, 0, sd)
plot(x, y) 
points(x, y.new, pch = 2)
lines(x, mu, lwd = 2)
lines(x, fitted(fit1))
lines(x, fitted(fit2), lty = 2)
lines(x, fitted(fit3), lty = 3)
legend("topright", legend = c("Verdadero", "Muestra", "Ajuste con grado 1", "Ajuste con grado 4", 
                              "Ajuste con grado 20", "Nuevas observaciones"), 
       lty = c(1, NA, 1, 2, 3, NA), lwd = c(2, NA, 1, 1, 1, NA), pch = c(NA, 1, NA, NA, NA, 2))
```

\begin{figure}[!htb]

{\centering \includegraphics[width=0.8\linewidth]{01-introduccion_files/figure-latex/polyfit2-1} 

}

\caption{Muestra con ajustes polinómicos con distinta complejidad y nuevas observaciones.}(\#fig:polyfit2)
\end{figure}

```r
MSEP <- sapply(list(fit1 = fit1, fit2 = fit2, fit3 = fit3), 
               function(x) mean((y.new - fitted(x))^2))
MSEP
```

```
##      fit1      fit2      fit3 
## 1.4983208 0.1711238 0.2621064
```

<!-- lines(x, y.new, type = "b", pch = 2, lty = 4, col = "blue") -->

Como ejemplo adicional, para evitar el efecto de la aleatoriedad de la muestra, en el siguiente código se simulan 100 muestras del proceso anterior a las que se les ajustan modelos polinómicos variando el grado de 1 a 20. Posteriormente se evalua la precisión en la muestra empleada en el ajuste y en un nuevo conjunto de datos procedente de la misma población.



```r
nsim <- 100
set.seed(1)
grado.max <- 20
grados <- seq_len(grado.max) 
mse <- mse.new <- matrix(nrow = grado.max, ncol = nsim) # Error cuadrático medio
for(i in seq_len(nsim)) {
  y <- mu + rnorm(n, 0, sd)
  y.new <- mu + rnorm(n, 0, sd)
  for (grado in grados) { # grado <- 1
    fit <- lm(y ~ poly(x, grado))
    mse[grado, i] <- mean(residuals(fit)^2)
    mse.new[grado, i] <- mean((y.new - fitted(fit))^2)
  }
}
# Simulaciones
matplot(grados, mse, type = "l", col = "lightgray", lty = 1, ylim = c(0, 2),
        xlab = "Grado del polinomio (complejidad)",
        ylab = "Error cuadrático medio")
matlines(grados, mse.new, type = "l", lty = 2, col = "lightgray") 
# Global
precision <- rowMeans(mse)
precision.new <- rowMeans(mse.new)
lines(grados, precision, lwd = 2)
lines(grados, precision.new, lty = 2, lwd = 2)
abline(h = sd^2, lty = 3)
abline(v = 4, lty = 3)
legend("topright", legend = c("Muestras", "Nuevas observaciones"), lty = c(1, 2))
```

\begin{figure}[!htb]

{\centering \includegraphics[width=0.8\linewidth]{01-introduccion_files/figure-latex/polyfitsim-1} 

}

\caption{Precisiones (errores cuadráticos medios) de ajustes polinómicos variando la complejidad, en las muestras empleadas en el ajuste y en nuevas observaciones (simulados).}(\#fig:polyfitsim)
\end{figure}


Como se puede observar en la Figura \@ref(fig:polyfitsim) los errores de entrenamiento disminuyen a medida que aumenta la complejidad del modelo.
Sin embargo los errores de predicción en nuevas observaciones primero disminuyen hasta alcanzar un mínimo, marcado por la línea de puntos vertical que se corresponde con el modelo de grado 4, y después aumentan (la línea de puntos horizontal es la varianza del proceso; el error cuadrático medio de predicción asintótico).
La línea vertical representa el equilibrio entre el sesgo y la varianza.
Considerando un valor de complejidad a la izquierda de esa línea tendríamos infraajuste (mayor sesgo y menor varianza) y a la derecha sobreajuste (menor sesgo y mayor varianza).


En general, al aumentar la complejidad disminuye el sesgo y aumenta la varianza (y viceversa).
Será necesario seleccionar los hiperparámetros de forma que haya un equilibrio entre el sesgo y la varianza (es lo que se conoce como *bias-variance tradeoff*).

<!-- 
PENDIENTE: 
Gráfico equilibrio entre sesgo y varianza
Ecuaciones a partir del modelo general
-->

### Datos de entrenamiento y datos de test {#entrenamiento-test}

Como se mostró en la sección anterior hay que tener mucho cuidado si se pretende evaluar la precisión de las predicciones empleando la muestra de entrenamiento.

Si el número de observaciones no es muy grande, se puede entrenar el modelo con todos los datos y emplear técnicas de remuestreo para evaluar la precisión (típicamente validación cruzada o bootstrap). 
Habría que asegurase de que el procedimiento de remuestreo empleado es adecuado (por ejemplo, la presencia de dependencia requeriría de métodos más sofisticados).

Sin embargo, si el número de obervaciones es grande, se suele emplear el procedimiento tradicional en ML, que consiste en particionar la base de datos en 2 (o incluso en 3) conjuntos (disjuntos):

-   Conjunto de datos de entrenamiento (o aprendizaje) para construir los modelos.

-   Conjunto de datos de test para evaluar el rendimiento de los modelos.

Los datos de test deberían utilizarse únicamente para evaluar los modelos finales, no se deberían emplear para seleccionar hiperparámetros. 
Para seleccionalos se podría volver a particionar los datos de entrenamiento, es decir, dividir la muestra en tres subconjuntos: datos de entrenamiento, de validación y de test (por ejemplo considerando un 70\%, 15\% y 15\% de las observaciones, respectivamente). 
Para cada combinación de hiperparámetros se ajustaría el correspondiente modelo con los datos de entrenamiento, se emplearían los de validación para evaluarlos y posteriormente seleccionar los valores "óptimos". Por último, se emplean los datos de test para evaluar el rendimiento del modelo seleccionado. 
No obstante, lo más habitual es seleccionar los hiperparámetros empleando validación cruzada (o otro tipo de remuestreo) en la muestra de entrenamiento, en lugar de considerar una muestra adicional de validación. 
En la siguiente sección se describirá esta última aproximación. 

En R se puede realizar el particionamiento de los datos empleando la función `sample()` del paquete base (otra alternativa sería emplear la función `createDataPartition` del paquete `caret` como se describe en la Sección \@ref(caret)). 
Típicamente se selecciona el 80\% de los datos como muestra de entrenamiento y el 20\% restante como muestra de test, aunque esto dependería del número de datos.

Como ejemplo consideraremos el conjunto de datos `Boston` del paquete `MASS` que contiene, entre otros datos, la valoración de las viviendas (`medv`, mediana de los valores de las viviendas ocupadas, en miles de dólares) y el porcentaje de población con "menor estatus" (`lstat`) en los suburbios de Boston.
Podemos contruir las muestras de entrenamiento (80\%) y de test (20\%) con el siguiente código:


```r
data(Boston, package = "MASS")
# ?Boston
set.seed(1)
nobs <- nrow(Boston)
itrain <- sample(nobs, 0.8 * nobs)
train <- Boston[itrain, ]
test <- Boston[-itrain, ]
```

<!-- Sección \@ref(cv) -->

### Validación cruzada {#cv} 

Como ya se comentó, una herramienta para evaluar la calidad predictiva de un modelo es la *validación cruzada*, que permite cuantificar el error de predicción utilizando una única muestra de datos. 

En su versión más simple, validación cruzada dejando uno fuera (*Leave-one-out cross-validation*, LOOCV), para cada observación de la muestra se realiza un ajuste empleando el resto de observaciones, y se mide el error de predicción en esa observación (único dato no utilizado en el ajuste del modelo). 
Finalmente, combinando todos los errores individuales se puede obtener medidas globales del error de predicción (o aproximar características de su distribución).

El método de LOOCV requeriría, en principio (ver comentarios más adelante), el ajuste de un modelo para cada observación por lo que pueden aparecer problemas computacionales si el conjunto de datos es grande.
En este caso se suele emplear grupos de observaciones en lugar de observaciones individuales. 
Si se particiona el conjunto de datos en *k* grupos, típicamente 10 o 5 grupos, se denomina *k-fold cross-validation* (LOOCV sería un caso particular considerando un número de grupos igual al número de observaciones).
Hay muchas variaciones de este método, entre ellas particionar repetidamente de forma aleatoria los datos en un conjunto de entrenamiento y otro de validación (de esta forma algunas observaciones podrían aparecer repetidas veces y otras ninguna en las muestras de validación). 

Continuando con el ejemplo anterior, supongamos que queremos emplear regresión polinómica para explicar la valoración de las viviendas (`medv`) a partir del "estatus" de los residentes (`lstat`). 
Al igual que se hizo en la Sección \@ref(bias-variance), consideraremos el grado del polinomio como un hiperparámetro.


```r
plot(medv ~ lstat, data = train)
```



\begin{center}\includegraphics[width=0.8\linewidth]{01-introduccion_files/figure-latex/unnamed-chunk-4-1} \end{center}

Podríamos emplear la siguiente función que devuelve para cada observación (fila) de una muestra de entrenamiento, el error de predicción en esa observación ajustando un modelo lineal con todas las demás observaciones:


```r
cv.lm0 <- function(formula, datos) {
    n <- nrow(datos)
    cv.res <- numeric(n)
    for (i in 1:n) {
        modelo <- lm(formula, datos[-i, ])
        cv.pred <- predict(modelo, newdata = datos[i, ])
        cv.res[i] <- cv.pred - datos[i, ]
    }
    return(cv.res)
}
```

La función anterior no es muy eficiente, pero podría modificarse fácilmente para emplear otros métodos de regresión. 
En el caso de regresión lineal múltiple (y de otros modelos lineales), se pueden obtener fácilmente las predicciones eliminando una de las observaciones a partir del ajuste con todos los datos.
Por ejemplo, en lugar de la anterior sería preferible emplear la siguiente función (ver `?rstandard`):


```r
cv.lm <- function(formula, datos) {
    modelo <- lm(formula, datos)
    return(rstandard(modelo, type = "predictive"))
}
```

Empleando esta función, podemos calcular una medida del error de predicción de validación cruzada (en este caso el *error cuadrático medio*) para cada valor del hiperparámetro (grado del ajuste polinómico) y seleccionar el que lo minimiza.


```r
grado.max <- 10
grados <- seq_len(grado.max) 
cv.mse <- cv.mse.sd <- numeric(grado.max)
for(grado in grados){
  cv.res <- cv.lm(medv ~ poly(lstat, grado), train)
  se <- cv.res^2
  cv.mse[grado] <- mean(se)
  cv.mse.sd[grado] <- sd(se)/sqrt(length(se))
}
plot(grados, cv.mse, ylim = c(25, 45),
  xlab = "Grado del polinomio (complejidad)")
# Valor óptimo
imin.mse <- which.min(cv.mse)
grado.op <- grados[imin.mse]
points(grado.op, cv.mse[imin.mse], pch = 16)
```



\begin{center}\includegraphics[width=0.8\linewidth]{01-introduccion_files/figure-latex/unnamed-chunk-7-1} \end{center}

```r
grado.op
```

```
## [1] 5
```
En lugar de emplear los valores óptimos de los hiperparámetros, Breiman *et al.* (1984) propusieron la regla de "un error estándar" para seleccionar la complejidad del modelo.
La idea es que estamos trabajando con estimaciones de la precisión y pueden presentar variabilidad, 
por lo que la sugerencia es seleccionar el modelo más simple^[Suponiendo que los modelos se pueden ordenar del más simple al más complejo.] dentro de un error estándar de la precisión del modelo correspondiente al valor óptimo 
(se consideraría que no hay diferencias significativas en la precisión; 
además, se mitigaría el efecto de la variabilidad debida a aleatoriedad/semilla).


```r
plot(grados, cv.mse, ylim = c(25, 45))
segments(grados, cv.mse - cv.mse.sd, grados, cv.mse + cv.mse.sd)
# Límite superior "oneSE rule" y complejidad mínima por debajo de ese valor
upper.cv.mse <- cv.mse[imin.mse] + cv.mse.sd[imin.mse]
abline(h = upper.cv.mse, lty = 2)
imin.1se <- min(which(cv.mse <= upper.cv.mse))
grado.1se <- grados[imin.1se]
points(grado.1se, cv.mse[imin.1se], pch = 16)
```



\begin{center}\includegraphics[width=0.8\linewidth]{01-introduccion_files/figure-latex/unnamed-chunk-8-1} \end{center}

```r
grado.1se
```

```
## [1] 2
```



```r
plot(medv ~ lstat, data = train)
fit.op <- lm(medv ~ poly(lstat, grado.op), train)
fit.1se <- lm(medv ~ poly(lstat, grado.1se), train)
newdata <- data.frame(lstat = seq(0, 40, len = 100))
lines(newdata$lstat, predict(fit.op, newdata = newdata))
lines(newdata$lstat, predict(fit.1se, newdata = newdata), lty = 2)
legend("topright", legend = c(paste("Grado óptimo:", grado.op), paste("oneSE rule:", grado.1se)), 
       lty = c(1, 2))
```



\begin{center}\includegraphics[width=0.8\linewidth]{01-introduccion_files/figure-latex/unnamed-chunk-9-1} \end{center}


### Evaluación de un método de regresión {#eval-reg}

Para estudiar la precisión de las predicciones de un método de regresión se evalúa el
modelo en el conjunto de datos de test y se comparan las predicciones frente a los valores reales.

Si generamos un gráfico de dispersión de observaciones frente a predicciones, los puntos deberían estar en torno a la recta $y=x$ (línea continua).


```r
obs <- test$medv
pred <- predict(fit.op, newdata = test)

plot(pred, obs, main = "Observado frente a predicciones",
     xlab = "Predicción", ylab = "Observado")
abline(a = 0, b = 1)
res <- lm(obs ~ pred)
# summary(res)
abline(res, lty = 2)
```



\begin{center}\includegraphics[width=0.8\linewidth]{01-introduccion_files/figure-latex/obs-pred-plot-1} \end{center}

También es habitual calcular distintas medidas de error. 
Por ejemplo, podríamos emplear la función `postResample()` del paquete `caret`: 

```r
caret::postResample(pred, obs)
```

```
##      RMSE  Rsquared       MAE 
## 4.8526718 0.6259583 3.6671847
```

La función anterior, además de las medidas de error habituales (que dependen en su mayoría de la escala de la variable respuesta) calcula un *pseudo R-cuadrado*. 
En este paquete (también en `rattle`) se emplea uno de los más utilizados, el cuadrado del coeficiente de correlación entre las predicciones y los valores observados (que se corresponde con la línea discontinua en la figura anterior). 
Estos valores se interpretarían como el coeficiente de determinación en regresión lineal, debería ser próximo a 1. 
Hay otras alternativas (ver Kvålseth, 1985), pero la idea es que deberían medir la proporción de variabilidad de la respuesta explicada por el modelo, algo que en general no es cierto con el anterior^[Por ejemplo obtendríamos el mismo valor si desplazamos las predicciones sumando una constante (i.e. no tiene en cuenta el sesgo).].
La recomendación sería emplear:
$$\tilde R^2 = 1 - \frac{\sum_{i=1}^n(y_i - \hat y_i)^2}{\sum_{i=1}^n(y_i - \bar y_i)^2}$$
implementado junto con otras medidas en la siguiente función:


```r
accuracy <- function(pred, obs, na.rm = FALSE, 
                     tol = sqrt(.Machine$double.eps)) {
  err <- obs - pred     # Errores
  if(na.rm) {
    is.a <- !is.na(err)
    err <- err[is.a]
    obs <- obs[is.a]
  }  
  perr <- 100*err/pmax(obs, tol)  # Errores porcentuales
  return(c(
    me = mean(err),           # Error medio
    rmse = sqrt(mean(err^2)), # Raíz del error cuadrático medio 
    mae = mean(abs(err)),     # Error absoluto medio
    mpe = mean(perr),         # Error porcentual medio
    mape = mean(abs(perr)),   # Error porcentual absoluto medio
    r.squared = 1 - sum(err^2)/sum((obs - mean(obs))^2) # Pseudo R-cuadrado
  ))
}
accuracy(pred, obs)
```

```
##         me       rmse        mae        mpe       mape  r.squared 
## -0.6731294  4.8526718  3.6671847 -8.2322506 19.7097373  0.6086704
```

```r
accuracy(predict(fit.1se, newdata = test), obs)
```

```
##         me       rmse        mae        mpe       mape  r.squared 
## -0.9236280  5.2797360  4.1252053 -9.0029771 21.6512406  0.5367608
```


### Evaluación de un método de clasificación {#eval-class}

Para estudiar la eficiencia de un método de clasificación supervisada se obtienen las predicciones para el conjunto de datos de test y se genera una tabla de contingencia, denominada *matriz de confusión*, con las predicciones frente a los valores reales.

En primer lugar consideraremos el caso de dos categorías.
La matriz de confusión será de la forma:

  Observado\\Predicción             Positivo                       Negativo
 ----------------------- ------------------------------ ------------------------------
        Verdadero           Verdaderos positivos (TP)         Falsos negativos (FN)
          Falso               Falsos positivos (FP)        Verdaderos negativos (TN)
 ----------------------- ------------------------------ ------------------------------

A partir de esta tabla se pueden obtener distintas medidas de la precisión de las predicciones. 
Por ejemplo, dos de las más utilizadas son la tasa de verdaderos positivos y la de verdaderos negativos (tasas de acierto en positivos y negativos), también denominadas *sensibilidad* y *especificidad*:

* Sensibilidad (*sensitivity*, *recall*, *hit rate*, *true positive rate*; TPR):
    $$TPR = \frac{TP}{P} = \frac{TP}{TP+FN}$$

* Especificidad (*specificity*, *true negative rate*; TNR):
    $$TNR = \frac{TN}{TN+FP}$$

La precisión global o tasa de aciertos (*accuracy*; ACC) sería:
$$ACC = \frac{TP + TN}{P + N} = \frac{TP+TN}{TP+TN+FP+FN}$$
Sin embargo hay que tener cuidado con esta medida cuando las clases no están balanceadas^[También hay que tener cuidado las medidas que utilizan la prevalencia estimada a partir de la muestra de test, como el índice predictivo positivo y negativo, si la muestra de test no refleja lo que ocurre en la población (por ejemplo si la clase de interés está sobrerrepresentada en la muestra).].
Otras medidas de la precisión global que tratan de evitar este problema son la *precisión balanceada* (*balanced accuracy*, BA):
$$BA = \frac{TPR + TNR}{2}$$
(media aritmética de TPR y TNR) o la *puntuación F1* (*F1 score*; media armónica de TPR y TNR):
$$F_1 = \frac{2TP}{2TP+FP+FN}$$
Otra medida global es el coeficiente kappa de Cohen, que compara la tasa de aciertos con la obtenida en una clasificación al azar
(un valor de 1 indicaría máxima precisión y 0 que la precisión es igual a la que obtendríamos clasificando al azar; empleando la tasa de positivos, denominada *prevalencia*, para predecir positivo).

NOTA: La precisión global (ACC) no debe ser confundida con el índice predictivo positivo (*precision*, *positive predictive value*; PPV):
$PPV = TP/(TP+FP)$. 
<!-- $PPV = \frac{TP}{TP+FP}$ -->

Como ejemplo emplearemos los datos anteriores de valoraciones de viviendas y estatus de la población, considerando como respuesta una nueva variable `fmedv` que clasifica las valoraciones en "Bajo" o "Alto" dependiendo de si `medv > 25`.

```r
# data(Boston, package = "MASS")
datos <- Boston
datos$fmedv <- factor(datos$medv > 25, labels = c("Bajo", "Alto")) # levels = c('FALSE', 'TRUE')
# En este caso las clases no están balanceadas
table(datos$fmedv)
```

```
## 
## Bajo Alto 
##  382  124
```

```r
caret::featurePlot(datos$lstat, datos$fmedv, plot = "density",
            labels = c("lstat", "Density"), auto.key = TRUE)
```



\begin{center}\includegraphics[width=0.8\linewidth]{01-introduccion_files/figure-latex/unnamed-chunk-12-1} \end{center}

El siguiente código realiza la partición de los datos y posteriormente ajustar un modelo de regresión logística en la muestra de entrenamiento considerando `lstat` como única variable explicativa:


```r
# Particionado de los datos
set.seed(1)
nobs <- nrow(datos)
itrain <- sample(nobs, 0.8 * nobs)
train <- datos[itrain, ]
test <- datos[-itrain, ]
# Ajuste modelo
modelo <- glm(fmedv ~ lstat, family = binomial, data = train)
summary(modelo)
```

```
## 
## Call:
## glm(formula = fmedv ~ lstat, family = binomial, data = train)
## 
## Deviance Residuals: 
##     Min       1Q   Median       3Q      Max  
## -1.9749  -0.4161  -0.0890   0.3785   3.6450  
## 
## Coefficients:
##             Estimate Std. Error z value Pr(>|z|)    
## (Intercept)  3.74366    0.47901   7.815 5.48e-15 ***
## lstat       -0.54231    0.06134  -8.842  < 2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## (Dispersion parameter for binomial family taken to be 1)
## 
##     Null deviance: 460.84  on 403  degrees of freedom
## Residual deviance: 243.34  on 402  degrees of freedom
## AIC: 247.34
## 
## Number of Fisher Scoring iterations: 7
```

En este caso podemos obtener las estimaciones de la probabilidad de la segunda categoría empleando `predict()` con `type = "response"`, a partir de las cuales podemos establecer las predicciones como la categoría más probable:


```r
obs <- test$fmedv
p.est <- predict(modelo, type = "response", newdata = test)
pred <- factor(p.est > 0.5, labels = c("Bajo", "Alto")) # levels = c('FALSE', 'TRUE')
```

Podemos obtener la matriz de confusión con el siguiente código:


```r
tabla <- table(obs, pred)
# addmargins(tabla, FUN = list(Total = sum))
tabla
```

```
##       pred
## obs    Bajo Alto
##   Bajo   71   11
##   Alto    8   12
```

```r
# Porcentajes respecto al total
print(100*prop.table(tabla), digits = 2) 
```

```
##       pred
## obs    Bajo Alto
##   Bajo 69.6 10.8
##   Alto  7.8 11.8
```

```r
# Porcentajes (de aciertos y fallos) por categorías
print(100*prop.table(tabla, 1), digits = 3) 
```

```
##       pred
## obs    Bajo Alto
##   Bajo 86.6 13.4
##   Alto 40.0 60.0
```

Alternativamente se podría emplear la función `confusionMatrix()` del paquete `caret` que permite obtener distintas medidas de la precisión:


```r
caret::confusionMatrix(pred, obs, positive = "Alto", mode = "everything")
```

```
## Confusion Matrix and Statistics
## 
##           Reference
## Prediction Bajo Alto
##       Bajo   71    8
##       Alto   11   12
##                                          
##                Accuracy : 0.8137         
##                  95% CI : (0.7245, 0.884)
##     No Information Rate : 0.8039         
##     P-Value [Acc > NIR] : 0.4604         
##                                          
##                   Kappa : 0.4409         
##                                          
##  Mcnemar's Test P-Value : 0.6464         
##                                          
##             Sensitivity : 0.6000         
##             Specificity : 0.8659         
##          Pos Pred Value : 0.5217         
##          Neg Pred Value : 0.8987         
##               Precision : 0.5217         
##                  Recall : 0.6000         
##                      F1 : 0.5581         
##              Prevalence : 0.1961         
##          Detection Rate : 0.1176         
##    Detection Prevalence : 0.2255         
##       Balanced Accuracy : 0.7329         
##                                          
##        'Positive' Class : Alto           
## 
```

---

***A partir de aquí en preparación...***

---

Evaluación de las estimaciones de las probabilidades: 

Curva ROC

AUC


Caso de más de dos categorías: 

Medidas globales: precisión y kappa.

Medidas por categoría: estrategia “uno contra todos”.
`caret::confusionMatrix()$byClass`


## La maldición de la dimensionalidad

<!-- edge effect -->

En preparación...

## Introducción al paquete `caret` {#caret}    

En preparación...