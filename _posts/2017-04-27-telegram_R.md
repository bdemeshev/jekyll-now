---
layout: post
title: "telegram-бот из R"
---

1. В телеграм знакомимся с `BotFather`.

2. Пишем ему `\start`, далее `\newbot`.

3. Выбираем красивое и формальное имя бота. Можно одно и то же. Пусть будет `my_bot`.

4. `BotFather` сообщит API-token. Это строка вида `12345678:sdsfsdfsdfjklsdjlfldskfls`.

5. Создаём (или редактируем) файл `.Renviron`. На линуксе/макос он лежит в домашней папке `~`, например, `/users/boris`.

6. Помещаем в файл `.Renviron` строку:

  ```r
  R_TELEGRAM_BOT_my_bot=12345678:sdsfsdfsdfjklsdjlfldskfls
  ```
7. Перзапускаем R.

  ```r
  library(telegram)
  bot <- TGBot$new(token = bot_token('my_bot'))
  bot$getMe()
  ```
8. Находим `my_bot` в телеграме и пишем ему "Привет" или что-нибудь ещё.

9. Узнаём `chat.id`:

  ```r
  new_messages <- bot$getUpdates()
  new_messages$message
  ```

  Получаем номер а-ля 123456789.
10. Настраиваем `chat.id` по умолчанию:

  ```r
  bot$set_default_chat_id(123456789)
  ```
11. Ура! Можно писать сообщения и слать файлы :)

  ```r
  bot$sendMessage('Привет от бота :)')
  bot$sendDocument('map.png')
  ```
12. А ещё можно настроить скрипт R так, чтобы пересылались сообщения об ошибках:

  ```r
  options(error = function() {
    bot$sendMessage(geterrmessage())
    if (!interactive()) {
      stop(geterrmessage())
    }
  })
  ```

Добавка про `interactive()` нужна, чтобы при запуске из командной строки ошибка выполняла прерывания скрипта.

Ссылки:

[Настройка пакета telegram](https://github.com/lbraglia/telegram)

[Про .Renviron файл](https://csgillespie.github.io/efficientR/3-3-r-startup.html#renviron) в книжке Efficient R programming
