---
title: "Вернон Лэндон и нормальное распределение"
layout: post
tags: [mathematics, probability, normal distribution]
---


В 1941 году инженер-электрик Вернон Лэндон опубликовал малоизвестный вывод нормального распределения,
[The Distribution of Amplitude with Time in Fluctuation Noise](https://worldradiohistory.com/hd2/IDX-Site-Technical/Engineering-General/Archive-IRE-IDX/IDX/40s/IRE-1941-02-OCR-Page-0014.pdf). 
Вывод Лэндона пересказал [Эдвин Томпсон Джейнс](https://bayes.wustl.edu/) в книге "Теория вероятностей: логика науки".
А это мой пересказ пересказа Джейнсона :)


Предположим, что напряжение можно представить в виде основной части и некоторого шума, $V' = V + \Delta$.

Шум $\Delta$ и основная часть $V$ независимы. 
Закон распределения $V$ принадлежит семейству распределений, которое полностью определяется дисперсией $Var(V)= \sigma^2$.
Другими словами плотность $V$ задаётся формулой $f_V(x|\sigma^2)$.


По формуле свёртки получаем:

$$
f_{V'}(x) = \int_{-\infty}^{+\infty} f_V(x-h | \sigma^2)f_{\Delta}(h) dh 
$$

Разложим $f_V(x-h \mid \sigma^2)$ в ряд Тейлора по $h$:

$$
f_V(x-h |\sigma^2) = f_V(x | \sigma^2) - h \frac{\partial f_V(x | \sigma^2)}{\partial x} + \frac{1}{2!} h^2 \frac{\partial^2 f_V(x | \sigma^2)}{\partial x^2} + \ldots
$$

Подставляем разложение Тейлора в формулу свёртки. 
Интегрируем каждое слагаемое ряда по отдельности:

$$
 f_{V'}(x) = f_V(x | \sigma^2) \int_{-\infty}^{+\infty} f_{\Delta}(h) dh  -  \frac{\partial f_V(x | \sigma^2)}{\partial x} \int_{-\infty}^{+\infty} h f_{\Delta}(h) dh + \frac{1}{2!}  \frac{\partial^2 f_V(x | \sigma^2)}{\partial x^2} \int_{-\infty}^{+\infty} h^2 f_{\Delta}(h) dh + \ldots
$$

В терминах ожиданий получаем:

$$
f_{V'}(x) = f_V(x | \sigma^2) - E(\Delta) \frac{\partial f_V(x | \sigma^2)}{\partial x} + \frac{1}{2!} E(\Delta^2) \frac{\partial^2 f_V(x | \sigma^2)}{\partial x^2} + \ldots
$$


Величину шума мы представим в виде $\Delta = \alpha U$ c $E(U)=0$ и $Var(U)=1$.
Посмотрим на поведение функции при малом $\alpha$. 

$$
f_{V'}(x) = f_V(x | \sigma^2) + \alpha^2 \frac{1}{2!} \frac{\partial^2 f_V(x | \sigma^2)}{\partial x^2} - \alpha^3 \frac{1}{3!} E(U^3)  \frac{\partial^3 f_V(x | \sigma^2)}{\partial x^3} + \ldots
$$


Лэндон предположил, что закон распределения $V'$ принадлежит тому же семейству, что и закон распределения $V$. 
Заметим, что $Var(V') = Var(V) + Var(\Delta) = \sigma^2 + \alpha^2$. 
Значит плотность $f_{V'}(x)$  совпадает с плотностью $f_V(x | \sigma^2 + \alpha^2)$.

Прибавление шума к напряжению не изменяет семейства закона распределения, а меняет только дисперсию. 

Разложим плотность в ряд Тейлора по $\alpha^2$:

$$
f_V(x | \sigma^2 + \alpha^2) = f_V(x | \sigma^2) + \alpha^2 \frac{\partial f_V(x | \sigma^2)}{\partial \sigma^2} + \frac{1}{2!}\alpha^4 \frac{\partial^2 f_V(x | \sigma^2)}{(\partial \sigma^2)^2} + \ldots
$$

Согласно предпосылкам Лэндона это одна и та же функция, поэтому:

$$
\frac{\partial f_V(x | \sigma^2)}{\partial \sigma^2} = \frac{1}{2} \frac{\partial^2 f_V(x | \sigma^2)}{\partial x^2}
$$

На этом вывод заканчивается. Далее Лэндон ссылается, что это известное [уравнение теплопроводности](https://en.wikipedia.org/wiki/Heat_equation).


Почитать:

* Глава 7 [про нормальное распределение](http://www-biba.inrialpes.fr/Jaynes/cc07s.pdf) из книжки Джейнса.