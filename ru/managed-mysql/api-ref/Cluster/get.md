---
editable: false
---

# Метод get
Возвращает указанный кластер MySQL.
 
Чтобы получить список доступных кластеров MySQL, выполните запрос [list](/docs/managed-mysql/api-ref/Cluster/list).
 
## HTTP-запрос {#https-request}
```
GET https://mdb.api.cloud.yandex.net/managed-mysql/v1alpha/clusters/{clusterId}
```
 
## Path-параметры {#path_params}
 
Параметр | Описание
--- | ---
clusterId | Обязательное поле. Идентификатор возвращаемого кластера MySQL. Чтобы получить идентификатор кластера, используйте запрос [list](/docs/managed-mysql/api-ref/Cluster/list).  Максимальная длина строки в символах — 50.
 
## Ответ {#responses}
**HTTP Code: 200 - OK**

```json 
{
  "id": "string",
  "folderId": "string",
  "createdAt": "string",
  "name": "string",
  "description": "string",
  "labels": "object",
  "environment": "string",
  "monitoring": [
    {
      "name": "string",
      "description": "string",
      "link": "string"
    }
  ],
  "config": {
    "version": "string",
    "resources": {
      "resourcePresetId": "string",
      "diskSize": "string",
      "diskTypeId": "string"
    },
    "backupWindowStart": {
      "hours": "integer",
      "minutes": "integer",
      "seconds": "integer",
      "nanos": "integer"
    },
    "mysqlConfig_5_7": {
      "effectiveConfig": {
        "innodbBufferPoolSize": "integer",
        "maxConnections": "integer",
        "longQueryTime": "number"
      },
      "userConfig": {
        "innodbBufferPoolSize": "integer",
        "maxConnections": "integer",
        "longQueryTime": "number"
      },
      "defaultConfig": {
        "innodbBufferPoolSize": "integer",
        "maxConnections": "integer",
        "longQueryTime": "number"
      }
    }
  },
  "networkId": "string",
  "health": "string",
  "status": "string"
}
```
Кластер MySQL. Подробнее см. в [документации](/docs/managed-mysql/concepts).
 
Поле | Описание
--- | ---
id | **string**<br><p>Идентификатор кластера MySQL. Этот идентификатор Managed Service for MySQL генерирует при создании.</p> 
folderId | **string**<br><p>Идентификатор каталога, которому принадлежит кластер MySQL.</p> 
createdAt | **string** (date-time)<br><p>Строка в формате <a href="https://www.ietf.org/rfc/rfc3339.txt">RFC3339</a>.</p> 
name | **string**<br><p>Имя кластера MySQL. Имя должно быть уникальным в каталоге, соответствовать RFC 1035 и иметь длину 1-63 символа.</p> 
description | **string**<br><p>Описание кластера MySQL. Длина описания должна быть от 0 до 256 символов.</p> 
labels | **object**<br><p>Пользовательские метки для кластера MySQL в виде пар <code>key:value</code>. Максимум 64 на ресурс.</p> 
environment | **string**<br><p>Среда развертывания кластера MySQL.</p> <ul> <li>PRODUCTION: Стабильная среда с осторожной политикой обновления: во время регулярного обслуживания применяются только срочные исправления.</li> <li>PRESTABLE: Среда с более агрессивной политикой обновления: новые версии развертываются независимо от обратной совместимости.</li> </ul> 
monitoring[] | **object**<br><p>Описание систем мониторинга, относящихся к данному кластеру MySQL.</p> 
monitoring[].<br>name | **string**<br><p>Название системы мониторинга.</p> 
monitoring[].<br>description | **string**<br><p>Описание системы мониторинга.</p> 
monitoring[].<br>link | **string**<br><p>Ссылка на графики системы мониторинга для кластера MySQL.</p> 
config | **object**<br><p>Конфигурация кластера MySQL.</p> 
config.<br>version | **string**<br><p>Версия серверного программного обеспечения MySQL.</p> 
config.<br>resources | **object**<br>Ресурсы, выделенные хостам MySQL.<br>
config.<br>resources.<br>resourcePresetId | **string**<br><p>Идентификатор набора вычислительных ресурсов, доступных хосту (процессор, память и т. д.). Все доступные наборы ресурсов перечислены в <a href="/docs/managed-mysql/concepts/instance-types">документации</a>.</p> 
config.<br>resources.<br>diskSize | **string** (int64)<br><p>Объем хранилища, доступного хосту.</p> 
config.<br>resources.<br>diskTypeId | **string**<br><p>Тип хранилища для хоста. Возможные значения:</p> <ul> <li>network-ssd — сетевой SSD-диск;</li> <li>local-ssd — локальное SSD-хранилище.</li> </ul> 
config.<br>backupWindowStart | **object**<br>Время запуска ежедневного резервного копирования, в часовом поясе UTC.<br><p>Represents a time of day. The date and time zone are either not significant or are specified elsewhere. An API may choose to allow leap seconds. Related types are <a href="https://github.com/googleapis/googleapis/blob/master/google/type/date.proto">google.type.Date</a> and <a href="https://github.com/protocolbuffers/protobuf/blob/master/src/google/protobuf/timestamp.proto">google.protobuf.Timestamp</a>.</p> 
config.<br>backupWindowStart.<br>hours | **integer** (int32)<br><p>Hours of day in 24 hour format. Should be from 0 to 23. An API may choose to allow the value &quot;24:00:00&quot; for scenarios like business closing time.</p> 
config.<br>backupWindowStart.<br>minutes | **integer** (int32)<br><p>Minutes of hour of day. Must be from 0 to 59.</p> 
config.<br>backupWindowStart.<br>seconds | **integer** (int32)<br><p>Seconds of minutes of the time. Must normally be from 0 to 59. An API may allow the value 60 if it allows leap-seconds.</p> 
config.<br>backupWindowStart.<br>nanos | **integer** (int32)<br><p>Fractions of seconds in nanoseconds. Must be from 0 to 999,999,999.</p> 
config.<br>mysqlConfig_5_7 | **object**<br>Конфигурация сервера MySQL 5.7.<br>
config.<br>mysqlConfig_5_7.<br>effectiveConfig | **object**<br><p>Действующие параметры для кластера MySQL 5.7 (сочетание параметров, определенных в <code>userConfig</code> и <code>defaultConfig</code>).</p> <p>Поля и структура <code>MysqlConfig5_7</code> отражает параметры конфигурации MySQL 5.7.</p> 
config.<br>mysqlConfig_5_7.<br>effectiveConfig.<br>innodbBufferPoolSize | **integer** (int64)<br><p>Размер буфера InnoDB, который используется для кэширования данных таблиц и индексов.</p> <p>Подробнее см. в <a href="https://dev.mysql.com/doc/refman/5.7/en/innodb-parameters.html#sysvar_innodb_buffer_pool_size">описании переменной в документации MySQL</a>.</p> <p>Минимальное значение — 5242880.</p> 
config.<br>mysqlConfig_5_7.<br>effectiveConfig.<br>maxConnections | **integer** (int64)<br><p>Максимальное количество одновременных подключений, которые принимает MySQL.</p> <p>Подробнее см. в <a href="https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_max_connections">описании переменной в документации MySQL</a>.</p> <p>Допустимые значения — от 10 до 10000 включительно.</p> 
config.<br>mysqlConfig_5_7.<br>effectiveConfig.<br>longQueryTime | **number** (double)<br><p>Время, в течение которого запрос должен обрабатываться, прежде чем он начинает считаться медленным.</p> <p>Подробнее см. в <a href="https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_long_query_time">описании переменной в документации MySQL</a>.</p> 
config.<br>mysqlConfig_5_7.<br>userConfig | **object**<br><p>Пользовательские настройки для кластера MySQL 5.7.</p> <p>Поля и структура <code>MysqlConfig5_7</code> отражает параметры конфигурации MySQL 5.7.</p> 
config.<br>mysqlConfig_5_7.<br>userConfig.<br>innodbBufferPoolSize | **integer** (int64)<br><p>Размер буфера InnoDB, который используется для кэширования данных таблиц и индексов.</p> <p>Подробнее см. в <a href="https://dev.mysql.com/doc/refman/5.7/en/innodb-parameters.html#sysvar_innodb_buffer_pool_size">описании переменной в документации MySQL</a>.</p> <p>Минимальное значение — 5242880.</p> 
config.<br>mysqlConfig_5_7.<br>userConfig.<br>maxConnections | **integer** (int64)<br><p>Максимальное количество одновременных подключений, которые принимает MySQL.</p> <p>Подробнее см. в <a href="https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_max_connections">описании переменной в документации MySQL</a>.</p> <p>Допустимые значения — от 10 до 10000 включительно.</p> 
config.<br>mysqlConfig_5_7.<br>userConfig.<br>longQueryTime | **number** (double)<br><p>Время, в течение которого запрос должен обрабатываться, прежде чем он начинает считаться медленным.</p> <p>Подробнее см. в <a href="https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_long_query_time">описании переменной в документации MySQL</a>.</p> 
config.<br>mysqlConfig_5_7.<br>defaultConfig | **object**<br><p>Конфигурация по умолчанию для кластера MySQL 5.7.</p> <p>Поля и структура <code>MysqlConfig5_7</code> отражает параметры конфигурации MySQL 5.7.</p> 
config.<br>mysqlConfig_5_7.<br>defaultConfig.<br>innodbBufferPoolSize | **integer** (int64)<br><p>Размер буфера InnoDB, который используется для кэширования данных таблиц и индексов.</p> <p>Подробнее см. в <a href="https://dev.mysql.com/doc/refman/5.7/en/innodb-parameters.html#sysvar_innodb_buffer_pool_size">описании переменной в документации MySQL</a>.</p> <p>Минимальное значение — 5242880.</p> 
config.<br>mysqlConfig_5_7.<br>defaultConfig.<br>maxConnections | **integer** (int64)<br><p>Максимальное количество одновременных подключений, которые принимает MySQL.</p> <p>Подробнее см. в <a href="https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_max_connections">описании переменной в документации MySQL</a>.</p> <p>Допустимые значения — от 10 до 10000 включительно.</p> 
config.<br>mysqlConfig_5_7.<br>defaultConfig.<br>longQueryTime | **number** (double)<br><p>Время, в течение которого запрос должен обрабатываться, прежде чем он начинает считаться медленным.</p> <p>Подробнее см. в <a href="https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_long_query_time">описании переменной в документации MySQL</a>.</p> 
networkId | **string**<br><p>Идентификатор сети, к которой принадлежит кластер.</p> 
health | **string**<br><p>Агрегированная работоспособность кластера.</p> <ul> <li>HEALTH_UNKNOWN: Состояние кластера неизвестно (<code>health</code> для каждого хоста в кластере — UNKNOWN).</li> <li>ALIVE: Кластер работает нормально (<code>health</code> для каждого хоста в кластере — ALIVE).</li> <li>DEAD: Кластер не работает (<code>health</code> для каждого узла в кластере — DEAD).</li> <li>DEGRADED: Кластер работает неоптимально (<code>health</code> по крайней мере для одного узла в кластере не ALIVE).</li> </ul> 
status | **string**<br><p>Текущее состояние кластера.</p> <ul> <li>STATUS_UNKNOWN: Состояние кластера неизвестно.</li> <li>CREATING: Кластер создается.</li> <li>RUNNING: Кластер работает нормально.</li> <li>ERROR: На кластере произошла ошибка, блокирующая работу.</li> <li>UPDATING: Кластер изменяется.</li> <li>STOPPING: Кластер останавливается.</li> <li>STOPPED: Кластер остановлен.</li> <li>STARTING: Кластер запускается.</li> </ul> 