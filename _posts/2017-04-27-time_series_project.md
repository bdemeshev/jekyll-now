---
layout: post
title: "Проект по временным рядам"
---


1. Выбираем любой алгоритм:

* ARIMA с автоподбором

Древний игрок на арене прогнозирования временных рядов. Много материала. Хорошо изучен. Однако простого русского пересказа статьи про автоподбор для чайников я не видел!

[Automatic Time Series Forecasting: The forecast Package for R](https://www.jstatsoft.org/article/view/v027i03)

[Hyndman, Forecasting Principles and Practice](http://robjhyndman.com/uwafiles/fpp-notes.pdf)

[PyFlux: python time series library](http://www.pyflux.com)

* ETS с автоподбором

Не менее древний игрок, чем ARIMA. По каким-то неведомым мне причинам используется гораздо реже, чем заслуживает. Большинство университетских курсов по временным рядам содержат блок про ARIMA и полный ноль про ETS, хотя это два лидера в прогнозировании одномерных временных рядов.  

[Automatic Time Series Forecasting: The forecast Package for R](https://www.jstatsoft.org/article/view/v027i03)

[Hyndman, Forecasting Principles and Practice](http://robjhyndman.com/uwafiles/fpp-notes.pdf)

[PyFlux: python time series library](http://www.pyflux.com)

* TBATS с автоподобором

Мощь старых приёмов (ARMA + преобразование Бокса-Кокса) и сезонность сложной структуры.

[Hyndman, Forecasting with complex seasonality](http://robjhyndman.com/papers/ComplexSeasonality.pdf)



* gaussian state space models

Родственник ETS.

[PyFlux: python time series library](http://www.pyflux.com)

* bayesian structural time series

Довольно молодой игрок. Байесовский подход, но по сути, прямой родственник ETS. Готовый пакет от гугла.

[Steven Scott, Short course on BSTS](https://sites.google.com/site/stevethebayesian/googlepageforstevenlscott/course-and-seminar-materials/bsts-bayesian-structural-time-series)

[Hal Varian, Steven Scott, Predicting the present](http://people.ischool.berkeley.edu/~hal/Papers/2013/pred-present-with-bsts.pdf)

* prophet

[Prophet: Automatic Forecasting Procedure](https://github.com/facebookincubator/prophet)

Совсем юный игрок для дневных рядов. Аналогично с bsts: байесовский подход и родственник ETS. Готовый код в STAN. Готовый пакет от фейсбука.

* SSA, «Гусеница»

Собственные значения и собственные векторы приходят на помощь :)

[Rssa, R package](https://cran.r-project.org/web/packages/Rssa/)


* xgboost/lightgbm

Градиентный бустинг применительно к рядам. Вопрос в том, как создавать объясняющие переменные. 

[xgboost](https://xgboost.readthedocs.io/en/latest/)

[lightgbm](https://github.com/Microsoft/LightGBM)

[R package to forecast timeseries with the xgboost](http://ellisp.github.io/blog/2016/11/06/forecastxgb)

* random forest

Случайные лес применительно к рядам. Аналогично, вопрос в том, как создавать объясняющие переменные. 

[ranger: fast random forests in R](https://www.jstatsoft.org/article/view/v077i01)

* Тета-метод

Неожиданно простой метод для коротких рядов.

[Hyndman, Forecasting Principles and Practice](http://robjhyndman.com/uwafiles/fpp-notes.pdf)

* VAR + lasso

Лассо применительно к векторным авторегрессиям. 

[Nicholson, BigVAR User’s Guide](http://www.wbnicholson.com/BigVAR.pdf)


Если есть желание изложить другой алгоритм, спрашивайте!

2. Излагаешь алгоритм простым языком. Насколько подробно писать? Представь, что ты излагаешь себе самому этот алгоритм в тот момент, когда ты его не знаешь. Если какой-то переход  никак не становится ясен, так честно и пишем «как из ... следует ... я не понял». 

3. Приводим примеры с разными опциями. Для каждого примера объясняем аккуратно модель и код для оценивания.

4. Код очень желательно привести не менее чем в двух языках. Можно использовать julia, R, python. 

5. Оформление: латех или маркдаун.

6. Не менее 10 рядов для анализа. Желательно больше. Не забывайте про графики рядов! Помните также, что графики не исчерпываются осями (t, $y_t$). При желании можно обработать 1000 рядов :) 

7. Сравниваем качество прогнозов с двумя наивными методами: «завтра будет также, как сегодня» и «усредним прошлые значения». В качестве меры качества прогноза берём сумму квадратов ошибок прогноза вне обучающей выборки.


Ссылки:

* Теория

[Hyndman, Forecasting Principles and Practice](http://robjhyndman.com/uwafiles/fpp-notes.pdf)

[Краткий трёхдневный семинар по прогнозированию рядов в R](http://robjhyndman.com/eindhoven/)

[Forecasting with R workshop](http://kourentzes.com/forecasting/wp-content/uploads/2016/06/Forecasting-with-R-notes.pdf)

* Много рядов:

[M3-competition](https://forecasters.org/resources/time-series-data/m3-competition/)

[Tourism forecasting competition](https://cran.r-project.org/web/packages/Tcomp/vignettes/tourism-comp.html)

[sophisthse: российские макро ряды](https://github.com/bdemeshev/sophisthse)


* Взаимодействие python-R-julia

[R from python: rpy2](http://blog.yhat.com/posts/rpy2-combing-the-power-of-r-and-python.html)

[R from julia](https://github.com/JuliaInterop/RCall.jl)

[julia from R](https://github.com/armgong/RJulia)

[python from julia](https://github.com/JuliaPy/PyCall.jl)

[julia from python](https://github.com/JuliaPy/pyjulia)

[python from R](https://www.r-bloggers.com/calling-python-from-r-with-rpython/)


