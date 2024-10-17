---
marp: true
title: Ускоряем Allure.TestOps
description: Allure.TestOps, Kubernetes, Spring, HikaryCP, PostgreSQL, Grafana, VictoriaMetrics
theme: heisenbug
template: bespoke
paginate: false
_paginate: false

---

<!-- _class: lead
-->

# Ускоряем __Allure__.__TestOps__

## Смирнов Вячеслав

### _17 октября 2024_

<!--
_footer: `Image by Vlad Gerasimov on https://vlad.studio/`
 -->
---


<!-- _class: title -->

# Ускоряю ![h:55](themes/img/miro.svg) Miro
## Пишу в ![h:55](themes/img/Telegram_logo.svg) qa_load
### Любуюсь горами

![bg cover](img/photo.jpg)



---

<!-- _class: main  -->

# Тысяча тестов автоматизирована,  ___Allure__.__TestOps__ не тормозит на нагрузке более __100 000__ результатов тестов в день_

---

<!-- _class: main  -->

# _Тысяча тестов автоматизирована,_  __Allure__.__TestOps__ не тормозит на нагрузке более __100 000__ результатов тестов в день

---

# 🟣 Allure TestOps _: Как устроена система?_

# 🔵 Главная проблема горы тестов _: Где взять диски?_

# 🟢 Масштабирование _сервисов и баз данных_

# 🟡 Оптимизации _настроек и SQL-запросов_

# 🟠 Радикальные оптимизации _: кеширование и удаление_

# 🔴 Рекомендации и скрипты _: Как автоматизировать?_ 
---

# _🟣 Allure TestOps : Как устроена система?_

# _🔵 Главная проблема горы тестов : Где взять диски?_

# 🟢 Масштабирование _сервисов и баз данных_

# 🟡 Оптимизации _настроек и SQL-запросов_

# 🟠 Радикальные оптимизации _: кеширование и удаление_

# _🔴 Рекомендации и скрипты : Как автоматизировать?_ 

---

# _🟣 Allure TestOps : Как устроена сиыстема?_

# _🔵 Главная проблема горы тестов : Где взять диски?_

# _🟢 Масштабирование сервисов и баз данных_

# 🟡 __Оптимизации__ настроек и SQL-запросов

# _🟠 Радикальные оптимизации : кеширование и удаление_

# _🔴 Рекомендации и скрипты : Как автоматизировать?_ 

---

# _🟣 Allure TestOps : Как устроена сиыстема?_

# _🔵 Главная проблема горы тестов : Где взять диски?_

# _🟢 Масштабирование сервисов и баз данных_

# _🟡 Оптимизации настроек и SQL-запросов_

# _🟠 Радикальные оптимизации : кеширование и удаление_

# 🔴 Рекомендации и скрипты _: Как автоматизировать?_ 

---

<!-- _class: main -->

# ☕️ Оптимизация вашей __Allure TestOps__

---

<!-- _class: main problem -->

## 🟣 __Allure__ __TestOps__

# Как устроена система?

---

<!-- _class: main -->

# Allure Report

---

![bg w:100%](img/allure.report.png)

---

![bg w:90%](img/allure.report.1.png)

---

<!-- _class: main -->

# Allure TestOps 


---

![bg w:90%](img/allure.testops.1.png)


---

![bg w:90%](img/allure.testops.2.png)

---

![bg w:100%](img/allure.testops.3.png)


---

![bg w:100%](img/allure.testops.5.png)


---

![bg h:80%](img/allure.test.ops.1.png)

---

![bg h:160%](img/allure.test.ops.1.png)


---

![bg h:80%](img/threads.png)

---

![bg h:80%](img/threads.2.png)

---

![bg h:80%](img/threads.3.png)


---

![bg h:80%](img/threads.4.png)


---



<!-- _class: main -->

# Потоки подключения к базам данных (__JDBC__, __SQL__) быстрее всех заканчиваются


---

<!-- _class: main -->

# Система масштабируемая


---

![bg h:80%](img/allure.test.ops.1.png)

---

![bg h:80%](img/allure.test.ops.2.png)

---

![bg h:80%](img/allure.test.ops.3.png)

---

![bg h:80%](img/allure.test.ops.4.png)

---

![bg h:80%](img/allure.test.ops.5.png)

---

![bg h:80%](img/allure.test.ops.6.png)


---


<!-- _class: main -->

# При масштабировании __сервиса__ нужно обращать внимание и на количество __подключений__ к хранилищу


---


<!-- _class: main -->

# В __PostgreSQL__ есть __несколько__ баз данных, _база данных __report__ наиболее нагруженная_

---


<!-- _class: main -->

# _В __PostgreSQL__ есть __несколько__ баз данных,_ база данных __report__ наиболее нагруженная

---

<!-- _class: main2 problem -->

# 🔵 Главная проблема горы тестов

## __Где взять диски?__



---

<!-- _class: main problem -->

# Как удалить __старые__ данные?

---

<!-- _class: main -->

# `https://help.qameta.io` > Knowledge base > General > Maintenance > __Storage and database cleanup__ 

---

![bg w:100%](img/cleanup.png)

---

# Храним __2__ недели данные со статусом __Broken__ и __Failed__
# Храним __1__ неделю данные со статусом __Passed__ и __Skipped__

# Данные это
- scenario

	- результаты выполнения шагов
- fixture
	- результаты выполнения общих шагов
- attachment
	- вложения, картинки

---

![bg w:100%](img/test.with.attachments.png)

---

![bg w:100%](img/test.without.attachments.png)

---

![bg w:100%](img/test.with.attachments.2.png)

---

scenario:
- Remove __scenario__ on __Broken__ test results after __336__ hours
- Remove __scenario__ on __Failed__ test results after __336__ hours
- Remove __scenario__ on __Passed__ test results after __168__ hours
- Remove __scenario__ on __Skipped__ test results after __168__ hours

fixture:
- Remove __fixture__ on __Broken__ test results after __336__ hours
- Remove __fixture__ on __Failed__ test results after __336__ hours
- Remove __fixture__ on __Passed__ test results after __168__ hours
- Remove __fixture__ on __Skipped__ test results after __168__ hours

attachment:
- Remove __attachment__ on __Broken__ test results after __336__ hours
- Remove __attachment__ on __Failed__ test results after __336__ hours
- Remove __attachment__ on __Passed__ test results after __168__ hours
- Remove __attachment__ on __Skipped__ test results after __168__ hours

---

![bg w:100%](img/test.with.attachments.png)

---

![bg h:100%](img/Delete.Launches.png)

---

<!-- _class: main -->

# Delete (tool) > Vacuum

---

![bg h:100%](img/clean.01.png)

---

![bg w:100%](img/clean.02.png)

---

![bg w:100%](img/clean.03.png)

---

![bg w:100%](img/clean.04.png)

---

![bg w:100%](img/clean.05.png)

---

![bg h:100%](img/clean.06.png)

---

![bg h:100%](img/clean.07.png)


---

![bg h:100%](img/clean.08.png)

---

# Выросло количество потоков:
## __rabbitConnectionFactorySharedExecutor__ -> taskExecutor
![bg w:105%](img/clean.09.png)

---

# Утилизация __CPU__ 
## на __PostgreSQL__ = 100%
![bg w:105%](img/clean.10.png)


---

<!-- _class: main -->

# Delete (tool) > __Vacuum__

---

<!-- _class: main2 error -->

# Главные проблемы горы тестов : Где взять __диски__? 

## И как не положить __PostgreSQL__ при удалении данных?

---

<!-- _class: main solution -->


# А давайте все отмасшабируем

---

<!-- _class: main2 problem -->

# 🟢 Масштабирование _сервисов и баз данных_

## __Как масштабировать?__


---

<!-- _class: main solution -->

# Мы масштабировали __report__ сервис.

---

<!-- _class: main  -->

# _Мы масштабировали __report__ сервис,_ потоков стало __кратно__ больше.

---

<!-- _class: main error -->

# _Мы масштабировали __report__ сервис, потоков стало __кратно__ больше,_ некоторых потоков __слишком__ много

---

<!-- _class: main error -->

# _Мы масштабировали __report__ сервис, потоков стало __кратно__ больше,_ некоторых потоков __слишком__ много, некоторых же __недостаточно__ много


---


![bg h:80%](img/allure.test.ops.1.png)


---

![bg h:80%](img/allure.test.ops.3.png)


---

![bg h:80%](img/size.01.png)


---

![bg h:80%](img/size.02.png)

---

# Отличаются на __200__ (потребители и исполнители)

![bg h:50%](img/size.03.png)


---

# Отличаются на уже __2000__ после масштабирования в __10__ раз

![bg h:90%](img/size.03.png)

---

# Issue #102

![bg h:100%](img/102.png)

---

# Настройки по умолчанию заданы для 1-го сервиса

```yaml
report:
  replicaCount: 1
  taskExecutorCorePoolSize: 200
  maxDBConn: 10
  maxConcurrency: 5
  maxS3Concurrency: 200

```

---

# Если у нас больше реплик, то нужно пересчитать

```yaml
report:
  replicaCount: 1
  taskExecutorCorePoolSize: 200
```

# __replicaCount__ больше, а __taskExecutorCorePoolSize__ меньше
```yaml
report:
  replicaCount: 10
  taskExecutorCorePoolSize: 20
```

---

<!-- _class: main  -->

# И нужно больше __JDBC__ подключений, значение по умолчанию __10__ это очень мало


---

# Пусть будет __100__ JDBC-подключений

```yaml
report:
  replicaCount: 10
  taskExecutorCorePoolSize: 20
  maxDBConn: 100
```

---

<!-- _class: main  -->

# Мы масштабировали __report__ сервис, _потоков стало __кратно__ больше, некоторых потоков __слишком__ много, некоторых же __недостаточно__ много_


---

<!-- _class: main  -->

# Мы масштабировали __report__ сервис, _потоков стало __кратно__ больше,_ <s> некоторых потоков __слишком__ много, некоторых же __недостаточно__ много </s>

---

<!-- _class: main solution -->

# Мы масштабировали __report__ сервис, _потоков стало __кратно__ больше,_ количество __task__-потоков снизили, а __HicaryCP__ увеличили



---

<!-- _class: main problem -->


## 🟠 __Оптимизации__ 

# настроек и __SQL-запросов__


---

<!-- _class: main solution -->

# Мы масштабировали __report__ сервис.

---

<!-- _class: main -->

# _Мы масштабировали __report__ сервис,_ активность работы с базами данных __PostgreSQL__ выросла.

---

<!-- _class: main error -->

# _Мы масштабировали __report__ сервис, активность работы с базами данных __PostgreSQL__ выросла,_ производительность __PostgreSQL__ конечна

---

<!-- _class: main  -->

# Добавим ресурсов для __PostgreSQL__

---

<!-- _class: main  -->

# Оптимизируем SQL-запросы к __PostgreSQL__


---

<!-- _class: main  -->

# _Оптимизируем SQL-запросы к __PostgreSQL__,_ возможности поменять текст запросов __Allure.TestOps__ нет

---

<!-- _class: main  -->

# _Оптимизируем SQL-запросы к __PostgreSQL__, возможности поменять текст запросов __Allure.TestOps__ нет,_ создадим индексы

---

<!-- _class: main solution -->

# Cоздадим индексы в __PostgreSQL__


---

<!-- _class: main problem -->

# А __какие__ надо ли создавать __индексы__?

---

<!-- _class: main  -->

# В __Allure__.__TestOps__ уже есть индексы на все поля

---

# Индекс

![bg h:80%](img/index.1.simple.png)

---

<!-- _class: main  -->

# Но некоторых индексов не хватает


---

# Несколько полей

![bg h:80%](img/index.2.fields.png)

---

# В другом порядке

![bg h:80%](img/index.2.fields.reverse.png)


---

# __С фильтрацией__ по значению
# browser == 'Chrome'

![bg h:80%](img/index.3.filter.png)

---

# __С фильтрацией__ по новым данным
# id >= 9995

![bg h:80%](img/index.4.new.png)

---

<!-- _class: main -->

# 10 _х 10 х 10_


---

<!-- _class: main -->

# 10 х 10 _х 10_

---

<!-- _class: main -->

# 10 х 10 х 10

---

<!-- _class: main problem -->

# На какие запросы создавать индексы?

---

<!-- _class: main2 -->

# ⚡️ Мгновенная cтатистика по __PostgreSQL__

## доступная сразу на текущий момент времени или за всю историю 

---


<!-- _class: main2 -->

# __pg_stat_activity__

## текущие активные запросы

---

<!-- _class: main2 -->

# __pg_stat_statement__

## успешно выполненные запросы

---

<!-- _class: main2 -->

# __Логи__

## тексты запросов со всеми параметрами

---

<!-- _class: main2 -->

# 🌟 Интервальная cтатистика по __PostgreSQL__

## за выбранный период, ее надо накопить


---

# __pg_stat_activity__ 
## ⚡️ данные за текущий момент
## 🌟 суммарные данные

# __pg_stat_statement__ 
## ⚡️ суммарные данные за долгое время
## 🌟 дельта данных

# __логи__ PostgreSQL 
## ⚡️ отсортированные по длительности
## 🌟 суммарные данные в отчете


---

# ___pg_stat_activity___ 
## _⚡️ данные за текущий момент_
## _🌟 суммарные данные_

# __pg_stat_statement__ 
## ⚡️ суммарные данные за долгое время
## _🌟 дельта данных_

# ___логи__ PostgreSQL_ 
## _⚡️ отсортированные по длительности_
## _🌟 суммарные данные в отчете_

---

![bg h:100%](img/normal.pg_stat_statements.raw.png)

---

# __Ложный__ TOP-1 запрос

```sql
SELECT $2 
FROM ONLY "public"."launch" x 
WHERE "id" OPERATOR(pg_catalog.=) $1 
FOR KEY SHARE OF x
update "test_result" 
set 
    "scenario_key" = $1, 
    "last_modified_by" = $2, 
    "last_modified_date" = $3 
where "test_result"."id" in ($4)
update "test_result" 
set 
    "scenario_key" = $1, 
    "last_modified_by" = $2, 
    "last_modified_date" = $3 
where "test_result"."id" in ($4, $5)
```

---

![bg w:90%](img/normal.pg_stat_statements.png)

---

![bg w:90%](img/normal.pg_stat_statements.2.png)


---

![bg w:90%](img/normal.pg_stat_statements.3.png)

---

![bg w:90%](img/normal.pg_stat_statements.4.png)

---

![bg h:70%](img/normal.pg_stat_statements.5.png)

---

![bg w:90%](img/normal.pg_stat_statements.6.png)

---

# Очень много __запросов-дубликатов__

```sql
select ... from test_result where id in ($1)

select ... from test_result where id in ($1, $2)

select ... from test_result where id in ($1, $2, 3)

select ... from test_result where id in ($1, $2, $3, $4)

select ... from test_result where id in ($1, $2, $3, $4, $5)

select ... from test_result where id in ($1, $2, $3, $4, $5, $6)

...

```

---

# Можно __схлопнуть__ дубликаты за счет регулярных выр

```sql
select query_key, query, queryid, 
    sum(total_exec_time) as time_sum
from (select
  regexp_replace(regexp_replace(regexp_replace(regexp_replace(
	regexp_replace(query, 
	' in [(][^)]+[)]', ' IN KEYS', 'g'),
	'[(]values [(].+[))]', '(VALUES (VAL))', 'g'),
	' values [(].+[)]', ' VALUES (VAL)', 'g'),
	'([0-9]+)', '1', 'g'),
	'(\n|\t|\s|\r|\v|\a|\b| )+', ' ', 'g')
	as "query_key", -- Template
	total_exec_time, query, queryid
  from pg_stat_statements
) foo
group by query_key, query, queryid
order by total_exec_time_sum desc, query_key, query
```

---

# Можно __схлопнуть__ дубликаты за счет регулярных выражений

```pl
select query_key, query, queryid, 
    sum(total_exec_time) as time_sum
from (select
  regexp_replace(regexp_replace(regexp_replace(regexp_replace(
	regexp_replace(query, 
```
```sql
	' in [(][^)]+[)]', ' IN KEYS', 'g'),
	'[(]values [(].+[))]', '(VALUES (VAL))', 'g'),
	' values [(].+[)]', ' VALUES (VAL)', 'g'),
	'([0-9]+)', '1', 'g'),
	'(\n|\t|\s|\r|\v|\a|\b| )+', ' ', 'g')
```
```pl
	as "query_key", -- Template
	total_exec_time, query, queryid
  from pg_stat_statements
) foo
group by query_key, query, queryid
order by total_exec_time_sum desc, query_key, query
```

---

# Можно посчитать изменение метрики

Создать слепок:
```sql
	select * 
	into pg_stat_statements_2024_10_10
	from pg_stat_statements
```

---

# Подождать и получить разницу


```sql
select "query_key", count(queryid) as "count", max(query) as "query",
	round(sum(total_exec_time)) as total_exec_time, sum(calls) as calls, 
	sum(total_exec_time)/sum(calls) as "mean",
	round(sum(shared_blks_hit)/sum(calls)) as "shared_blks_hit"
from ( select 
		regexp_replace(regexp_replace(regexp_replace(regexp_replace(regexp_replace(p.query,       
		' in [(][^)]+?[)]', ' IN KEYS', 'g'),
		'\(values \(.+?\)\)', '(VALUES (VAL))', 'g'),
		' values \(.+?\)', ' VALUES (VAL)', 'g'),
		'([0-9]+)', '1', 'g'),
		'(\n|\t|\s|\r|\v|\a|\b| )+', ' ', 'g') as "query_key",
		p.queryid, p.query,
		p.total_exec_time - prev.total_exec_time as total_exec_time,
		p.shared_blks_hit - prev.shared_blks_hit as shared_blks_hit,
		p.calls - prev.calls as calls,
		(p.total_exec_time - prev.total_exec_time) / (p.calls - prev.calls) as mean
	from  pg_stat_statements p join pg_stat_statements_2024_10_10 prev
		on (p.queryid = prev.queryid)
	where p.calls > prev.calls
) as stat
group by "query_key" order by total_exec_time desc
```

---

![bg w:100%](img/stat.png)

---

<!-- _class: main -->

# shared_blk_hit

---

![bg  w:100%](img/stat.2.png)

---

# ___pg_stat_activity___ 
## _⚡️ данные за текущий момент_
## _🌟 суммарные данные в VictoriaMetrics_

# __pg_stat_statement__ 
## _⚡️ суммарные данные за долгое время_
## 🌟 дельта данных

# ___логи__ PostgreSQL_ 
## _⚡️ отсортированные по длительности_
## _🌟 суммарные данные в отчете_


---

<!-- _class: main problem -->

## 🔴 __Радикальные оптимизации__

# кеширование и удаление

---

<!-- _class: main problem -->

# Есть очень медленные HTTP запросы на странице проекта /project/{ID}__/dashboards__

---

<!-- _class: main problem -->

# /api/rs/analytic/{ID}__/statistic_trend__  /api/rs/analytic/{ID}__/automation_chart__

---

![bg h:100%](img/slow_dashboard.png)

---

<!-- _class: main error -->

# 180 секунд на GET-запрос

---

<!-- _class: main -->

# __180__ секунд будут заняты __2__ JDBC-подключения к __реплике__ базы данных, на каждого пользователя, открывшего проект

---

<!-- _class: main -->

# Индексами проблему не решить _(пробовал)_

---

<!-- _class: main solution -->

# Можно __отключить__ GET-запросы вообще

---

<!-- _class: main solution -->

# Можно __отключить__ GET-запросы вообще: /api/rs/analytic/__3__/statistic_trend и /api/rs/analytic/__3__/automation_chart

---

<!-- _class: main -->

# Используя __NGinx__ мы __отключим__ или __закешируем__ два аналитических GET-запроса для самого большого проекта __(№ 3)__

---

# Закешируем

```nginx
http {
    proxy_cache_path /data/nginx/cache keys_zone=mycache:60m max_size=1g inactive=120m;
    limit_conn_zone $server_name zone=perserver:10m;
    upstream backend {server allure:443}
    server {
        listen 80;

        location /api/rs/analytic/3/statistic_trend {
            include shared.cache.conf;
        }
        location /api/rs/analytic/3/automation_chart {
            include shared.cache.conf;
        }
        location / {
            proxy_pass https://backend;
        }
    }
}
```

---
# Закешируем

```pl
http {
    proxy_cache_path /data/nginx/cache keys_zone=mycache:60m max_size=1g inactive=120m;
    limit_conn_zone $server_name zone=perserver:10m;
    upstream backend {server allure:443}
    server {
        listen 80;
```
```nginx
        location /api/rs/analytic/3/statistic_trend {
            include shared.cache.conf;
        }
        location /api/rs/analytic/3/automation_chart {
            include shared.cache.conf;
        }
```
```pl
        location / {
            proxy_pass https://backend;
        }
    }
}
```

---

# Содержимое файле __shared.cache.conf__
```nginx
# кешировать по URL-запроса
proxy_cache_key "$host$request_uri";

# на 60 минут для успешных ответов
proxy_cache_valid 200 302 60m;

proxy_cache_valid 404      1m;
proxy_cache_min_uses 1;
proxy_cache_methods GET;
proxy_cache_background_update on;
proxy_cache_revalidate on;
proxy_cache_lock on;
add_header X-Cache-Status $upstream_cache_status;
proxy_ignore_headers Cache-Control;
proxy_pass https://backend;
```

---

# Кешировать по URL-запроса
```pl
# кешировать по URL-запроса
```
```nginx
proxy_cache_key "$host$request_uri";
```
```pl
# на 60 минут для успешных ответов
proxy_cache_valid 200 302 60m;

proxy_cache_valid 404      1m;
proxy_cache_methods GET;
proxy_cache_background_update on;
proxy_cache_revalidate on;
proxy_cache_lock on;
add_header X-Cache-Status $upstream_cache_status;
proxy_ignore_headers Cache-Control;
proxy_pass https://backend;
```

---


# Кешировать на __60__ минут для успешных ответов с кодами __200__ или __302__
```pl
# кешировать по URL-запроса
proxy_cache_key "$host$request_uri";

# на 60 минут для успешных ответов
```
```nginx
proxy_cache_valid 200 302 60m;

```
```pl
proxy_cache_valid 404      1m;
proxy_cache_min_uses 1;
proxy_cache_methods GET;
proxy_cache_background_update on;
proxy_cache_revalidate on;
proxy_cache_lock on;
add_header X-Cache-Status $upstream_cache_status;
proxy_ignore_headers Cache-Control;
proxy_pass https://backend;
```

---


<!-- _class: main problem -->

## 🟣 __Рекомендации и скрипты__

# Как автоматизировать оптимизации?

---

<!-- _class: main -->

# `github.com/polarnik/` `Allure.TestOps.SpeedUp`

---

<!-- _class: main -->

# Доски мониторинга, _примеры индексов и скрипт для создания индексов на основе ваших данных_

---

<!-- _class: main -->

# _Доски мониторинга,_ примеры индексов _и скрипт для создания индексов на основе ваших данных_

---

<!-- _class: main -->

# _Доски мониторинга, примеры индексов и_ скрипт для создания индексов на основе ваших данных

---

<!-- _class: main -->

# `github.com/polarnik/` `Allure.TestOps.SpeedUp`


---

<!-- _class: main  solution -->

# __3 месяца работы сжатые в день__: мониторинг, оптимизация настроек, добавление индексов 

---

<!-- _class: main  -->

## __Ваши вопросы__

# Репозиторий: `github.com/polarnik/` `Allure.TestOps.SpeedUp`, ![h:55](themes/img/Telegram_logo.svg) qa_load

<!--
_footer: `Images from vlad.studio. Slides from https://polarnik.github.io/Allure.TestOps.SpeedUp/slides.html`

 -->
