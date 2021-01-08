---
title: "Gretl"
layout: post
tags: [econometrics, soft]
---

Есть замечательная альтернатива Eviews/Stata для тех, кто совсем не хочет программировать, 
а хочет обойтись кнопочным интерфейсом: [gretl](http://gretl.sourceforge.net/)

Готовые бинарные файлы под max/windows прямо на главной страничке есть. 

А мне для себя инструкция как поставить на ubuntu свежую версию. Ибо в репозиториях ubuntu-LTS всегда лежит замшелая версия.

После скачивания архива разархивируем его:
````bash
tar -xvf gretl-2020e.tar.xz
````

Компилируем:
````bash
cd gretl2020e
./configure
make
make check
sudo make install
````

Пробуем запустить из командной строки
````bash
gretl
````

Если при запуске выдаёт
````bash
/usr/local/bin/gretl_x11: error while loading shared libraries: libgretl-1.0.so.36: cannot open shared object file: No such file or directory
````

То 
````bash
sudo ldconfig
````