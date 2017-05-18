---
title: "Красивый график для главных компонент"
layout: post
---

Ура! У Ричарда Телфорда из Норвегии дошли руки до оживления [красивых графиков для главных компонент!](https://github.com/richardjtelford/ggbiplot/tree/experimental)


Если коротко. Ставим пакет:

```r
devtools::install_github("richardjtelford/ggbiplot", ref = "experimental")
```

Рисуем главные компоненты:

```r
library(ggbiplot)
data(wine)
cultivar <- wine.class
m <- prcomp(wine, scale = TRUE)
qplot(PC1, PC2, data = fortify(m), color = cultivar) +
  stat_ellipse(aes(group = cultivar))
```

![]({{ site.baseurl }}/images/2017-05-18-biplot_listview_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

И со стрелочками-проекциями исходных переменных

```r
df <- fortify(m, scale = 1, equalize = FALSE)
ggplot(df, aes(x = PC1, PC2)) +
  geom_point(aes(color = cultivar)) +
  geom_axis(data = attr(df, "basis"), aes(label = .name))
```

![]({{ site.baseurl }}/images/2017-05-18-biplot_listview_files/figure-html/unnamed-chunk-3-1.png)<!-- -->


А ещё недавно попался под руку пакет для визуализации списков:

```r
library(listviewer)
model <- lm(data = cars, dist ~ speed)
jsonedit(model)
```

![]({{ site.baseurl }}/images/2017-05-18-listview.png) <!-- -->