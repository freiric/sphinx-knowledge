R
===

test de student

    Comparaison de moyenne d'une loi normale à une valeur si la variance est connue.
    Comparaison de deux moyennes issues de deux lois normales si leurs variances sont égales et inconnues, ou si leurs variances sont différentes et inconnues (Test t de Welch).
    Test sur les coefficients dans le cadre d'une régression linéaire.
    Test sur des échantillons appariés
    
test de corrélation

test du khi²

  le test du χ² de Pearson ou test du χ² d'indépendance est un test statistique qui s'applique sur des ensembles de données catégorielles pour évaluer la probabilité qu'une différence observée entre les ensembles soit due au hasard. Il convient aux données non-appariées prises sur de grands échantillons (n>30). 

regression linéaire (``lm()``) ~ test de corrélation de pearson (``cor.test()``)

   .. math::

      r = b * \frac{e.t.(\text{âge})}{e.t.(\text{durée entretien})}


regression linéaire (``lm()``) avec x binaire ~ test t destudent pour comparer 2 moyenne

regression logistique:

   .. math::

      Log[\frac{proba}{1-proba}]=a+b*x

  
.. code-block:: R
		
   var <- read.csv2(nomDuFichier)
   str(var)
   barplot(table(var$var))
   pie(table(var$var))
   hist(var$var)
   boxplot(var$var)
   plot(x, jitter(y))
   library(gplots)
   plotmeans(x~y)
   interaction.plot()
   summary()
   library(prettyR)
   describe()
   mean()
   sd()
   sqrt()
   library(binom)
   binom.confint(nb_mesure, taille_echantaillon, method="all")
   cor(var1, var2) 
   factor()
   library(Epi
   twoby2(var_risque1, var_risque2)
   ifelse(cond, res1, res2)
   chisq.test()
   fisher.test()
   qqnorm()
   qqline()
   by(var1, var2, sd, na.rm=TRUE)
   t.test(var1~var2, var.equal=TRUE) # test de student 
   wilcox.test(var1~var2)
   cor.test(var1, var2, method="spearman")
   t.test(var, mu=mmoyenne)
   mcnemar.test(b.debut(), b.fin())
   t.test(b.debut(), b.fin(), paired=true)
   lm(y~x)
   abline(lm(y~x))
   m <- lm(y~a+b+c)
   drop1(m, .~., test="F")
   hist(resid(m))
   glm()
