
**ODBC** (Open Database Connectivity) - API для доступа к базе данных.<br>
**psqlODBC** — официальный драйвер ODBC PostgreSQL. Драйвер позволяет производить операции над данными, используя стороннее ПО.
# Использование данных из СУБД PostgreSQL в стороннем ПО 
Для использования в стороннем ПО данных из СУБД PostgreSQL необходимо установить драйвер psqlODBC. Драйвер можно скачать на сайте [название][1]. 

## Установка драйвера psqlODBC в Windows 










[1]: (https://www.postgresql.org/ftp/odbc/releases/) 

## Установка драйвера psqlODBC в Unix-подобных системах 





# dblink оракл-постгре



## настройка винда



## настройка юникс






# Получение данных из ? в ..продукты MS

## в Эксель
~~ODBC можно использовать с любыми совместимыми приложениями, в том числе с MS Excel и MS Access.~~ <br>
Для получения данных в MS Excel:
1. Создайте файл с расширением .dqy в ... . Файл должен содержать следующее: <br>
   
XLODBC<br>
1<br>
DRIVER={PostgreSQL Unicode};DATABASE=Product;SERVER=127.0.0.1;PORT=5432;UID=<user>;PASSWORD=<passwordd>;SSLmode=disable;ReadOnly=0;Protocol=7.4;FakeOidIndex=0;ShowOidColumn=0;RowVersioning=0;ShowSystemTables=0;ConnSettings=;Fetch=100;Socket=4096;UnknownSizes=0;MaxVarcharSize=255;MaxLongVarcharSize=8190;Debug=0;CommLog=0;Optimizer=0;Ksqo=1;UseDeclareFetch=0;TextAsLongVarchar=1;UnknownsAsLongVarchar=0;BoolsAsChar=1;Parse=0;CancelAsFreeStmt=0;ExtraSysTablePrefixes=dd_;LFConversion=1;UpdatableCursors=1;DisallowPremature=0;TrueIsMinus1=0;BI=0;ByteaAsLongVarBinary=0;UseServerSidePrepare=0;LowerCaseIdentifier=0;GssAuthUseGSS=0;XaOpt=1<br>
select * from Product_rate_plans<br>

Примечания:
* В параметры DATABASE, UID и PASSWORD вписываются необходимые данные.
* Для корректной работы запроса необходимо писать его в одну строку. 

2. Откройте созданный файл.  
3. При запуске MS Excel *что-то про соглашение включения источника данных*.

В результате отображается MS Excel с соответствующими данными. Получение данных завершено.


## в аксес