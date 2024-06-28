
**ODBC** (Open Database Connectivity) - API для доступа к базе данных.<br>
**psqlODBC** — официальный драйвер ODBC PostgreSQL. Драйвер позволяет производить операции над данными, используя стороннее ПО.

# Использование данных из СУБД PostgreSQL в стороннем ПО 
Для использования в стороннем ПО данных из СУБД PostgreSQL необходимо установить драйвер psqlODBC. Драйвер можно скачать на сайте [PostgreSQL](https://www.postgresql.org/ftp/odbc/releases/). 

> **Внимание!** При скачивании драйвера обратите внимание на разрядность: она должна быть такой же, как и разрядность приложения, *которому нужен доступ*. *возможно впихнуть про ошибку сюда*

При проблемах с установкой драйвера проверьте разрядность, версии, настройки. На сайте PostgreSQL создана страница, на которой собраны частые вопросы [ссылка](https://odbc.postgresql.org/faq.html).

## Установка драйвера psqlODBC в Windows 
> **Примечания:** 
> 1. Рекомендуется установка из msi-пакета.
> 2. Названия вкладок и окон могут незначительно различаться в зависимости от версии Windows.

Для установки драйвера:
1. Откройте Панель управления -> **Административ тулс? -> Data Sources (ODBC).**
![Изображение] (!!!)
2. Перейдите на вкладку System DSN.
3. Создайте новый источник данных, выбрав драйвер Postgres (unicode), укажите учетные данные. 

Если драйвер psqlODBC 32-битный, а Windows является 64-битной, то откройте Панель управления через командную строку:
```
c:\windows\system32\odbcad32.exe
```
Далее действуйте в соответствии с алгоритмом выше.

## Установка драйвера psqlODBC в Unix-подобных системах 

> **Примечание.** При скачивании обратите внимание на установленный дистрибутив ОС 

В файле .odbc.ini пропишите следующие настройки: 
```
[ODBC Data Sources]
  Product = PostgreSQL
[Product]
  Debug = 1
  CommLog = 1
  ReadOnly = no
  Driver = /usr/pgsql-9.1/lib/psqlodbc.so
  Servername = <PostgreSQL_IP>
  FetchBufferSize = 99
  Username = <user>
  Password = <pass>
  Port = 5432
  Database = <db_name>
[Default]
  Driver = /usr/lib64/liboplodbcS.so.1

```
Для параметров Servername, Username, Password, Database укажите реальные данные.


# Настройка dblink оракл-постгре



## настройка винда



## настройка юникс




# Получение данных из ? в ..продукты MS

*возможное примечание про потабличную загрузку и про все сразу*
## Загрузка данных в MS Excel
Для загрузки данных в MS Excel:
1. Создайте файл с расширением .dqy в *место*. 
2. Пропишите в файле следующее:<br>
``` 
XLODBC
1
DRIVER={PostgreSQL Unicode};DATABASE=Product;SERVER=127.0.0.1;PORT=5432;UID=<user>;PASSWORD=<passwordd>;SSLmode=disable;ReadOnly=0;Protocol=7.4;FakeOidIndex=0;ShowOidColumn=0;RowVersioning=0;ShowSystemTables=0;ConnSettings=;Fetch=100;Socket=4096;UnknownSizes=0;MaxVarcharSize=255;MaxLongVarcharSize=8190;Debug=0;CommLog=0;Optimizer=0;Ksqo=1;UseDeclareFetch=0;TextAsLongVarchar=1;UnknownsAsLongVarchar=0;BoolsAsChar=1;Parse=0;CancelAsFreeStmt=0;ExtraSysTablePrefixes=dd_;LFConversion=1;UpdatableCursors=1;DisallowPremature=0;TrueIsMinus1=0;BI=0;ByteaAsLongVarBinary=0;UseServerSidePrepare=0;LowerCaseIdentifier=0;GssAuthUseGSS=0;XaOpt=1
select * from Product_rate_plans
```
> **Примечания:**
>* В параметры DATABASE, UID и PASSWORD вписываются необходимые данные.
>* Для корректной работы запроса необходимо писать его в одну строку. 

3. Откройте созданный файл, MS Excel запустится автоматически.
4. При запуске MS Excel *что-то про соглашение включения источника данных, неплохо бы было приложить скрин*.

В результате отображается MS Excel с соответствующими данными. Загрузка данных завершена.


## Загрузка данных в MS Access
Примечание. В зависимости от версии MS Access названия вкладок и кнопок могут незначительно различаться.

Для получения данных в MS Access:
1. Перейдите на вкладку «Внешние данные». 
2. Нажмите на кнопку «Создать источник данных».
3. В выпадающем списке выберите «Из других источников» -> «База данных ODBC».
   ![Изображение](https://sun9-29.userapi.com/impg/nM8jnIhNhXSnN_A5WsyWB2uUGo-uHtbv1Twwnw/HGJWt0HXIpU.jpg?size=1003x479&quality=96&sign=3fab328464fda46dbb4746d0fa342e7f&type=album)
4. Следуйте инструкциям MS Access.

Получение данных завершено.