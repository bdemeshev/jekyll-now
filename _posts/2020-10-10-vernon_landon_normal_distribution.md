---
title: "Вернон Лэндон и нормальное распределение"
layout: post
tags: [mathematics, probability, normal distribution]
---


В 1941 году инженер-электрик Вернон Лэндон опубликовал малоизвестный вывод нормального распределения,
[The Distribution of Amplitude with Time in Fluctuation Noise](https://worldradiohistory.com/hd2/IDX-Site-Technical/Engineering-General/Archive-IRE-IDX/IDX/40s/IRE-1941-02-OCR-Page-0014.pdf). 
Вывод Лэндона пересказал [Эдвин Томпсон Джейнс](https://bayes.wustl.edu/) в книге "Теория вероятностей: логика науки".
А это мой пересказ пересказа Джейнсона :)


Предположим, что напряжение можно представить в виде основной части и некоторого шума
$$
 V' = V + \Delta
$$

Шум $\Delta$ и основная часть $V$ независимы, $Var(V)= \sigma^2$.


По формуле свёртки получаем:
$$
f_{V'}(x) = \int_{-\infty}^{+\infty} f_V(x-u \middle \sigma^2)f_{\Delta}(u) du 
$$

Разложим $f_V(x-u)$ в ряд Тейлора по $u$:

$$
f_V(x-u) = f_V(x \middle \sigma^2) - u \frac{\partial f_V(x \middle \sigma^2)}{\partial x} + \frac{1}{2!} u^2 \frac{\partial^2 f_V(x \middle \sigma^2)}{\partial x^2} + \ldots
$$

Подставляем разложение Тейлора в формулу свёртки. 
Интегрируем каждое слагаемое ряда по отдельности:

$$
 f_{V'}(x) = f_V(x \middle \sigma^2) \int_{-\infty}^{+\infty} f_{\Delta}(u) du  -  \frac{\partial f_V(x \middle \sigma^2)}{\partial x} \int_{-\infty}^{+\infty} u f_{\Delta}(u) du + \frac{1}{2!}  \frac{\partial^2 f_V(x \middle \sigma^2)}{\partial x^2} \int_{-\infty}^{+\infty} u f_{\Delta}(u) du + \ldots
$$

В терминах ожиданий получаем:
$$
f_{V'}(x) = f_V(x \middle \sigma^2) - E(\Delta) \frac{\partial f_V(x \middle \sigma^2)}{\partial x} + \frac{1}{2!} E(\Delta^2) \frac{\partial^2 f_V(x \middle \sigma^2)}{\partial x^2} + \ldots
$$


Величину шума мы представим в виде $\Delta = \alpha U$ c $E(U)=0$ и $Var(U)=1$.
Посмотрим на поведение функции при малом $\alpha$. 

В терминах ожиданий получаем:
$$
f_{V'}(x) = f_V(x \middle \sigma^2) + \alpha^2 \frac{1}{2!} \frac{\partial^2 f_V(x \middle \sigma^2)}{\partial x^2} - \alpha^3 \frac{1}{3!} E(U^3)  \frac{\partial^3 f_V(x \middle \sigma^2)}{\partial x^3} + \ldots
$$


Заметим, что $Var(V') = Var(V) + \alpha^2$. 

Лэндон предположил, что закон распределения $f_{V'}(x)$ 
совпадает с законом распределение $f_V(x \middle \sigma^2 + \alpha^2)$.

То есть прибавление шума к напряжению не изменяет семейства закона распределения, а меняет только дисперсию. 

Разложим в ряд Тейлора по $\alpha^2$:

$$
f_V(x \middle \sigma^2 + \alpha^2) = f_V(x \middle \sigma^2) + \alpha^2 \frac{\partial f_V(x \middle \sigma^2)}{\partial \sigma^2} + \frac{1}{2!}\alpha^4 \frac{\partial^2 f_V(x \middle \sigma^2)}{(\partial \sigma^2)^2} + \ldots
$$

Согласно предпосылкам Лэндона это одна и та же функция, поэтому:

$$
\frac{\partial f_V(x \middle \sigma^2)}{\partial \sigma^2} = \frac{1}{2} \frac{\partial^2 f_V(x \middle \sigma^2)}{\partial x^2}
$$

На этом вывод заканчивается. Далее Лэндон ссылается, что это известное [уравнение теплопроводности](https://en.wikipedia.org/wiki/Heat_equation).


Почитать:

* Глава 7 [про нормальное распределение](http://www-biba.inrialpes.fr/Jaynes/cc07s.pdf) из книжки Джейнса.