
**ODBC** (Open Database Connectivity) - API для доступа к базе данных.<br>
**psqlODBC** — официальный драйвер ODBC PostgreSQL. Драйвер позволяет производить операции над данными, используя стороннее ПО.

# Использование данных из СУБД PostgreSQL в стороннем ПО 
Для использования в стороннем ПО данных из СУБД PostgreSQL необходимо установить драйвер psqlODBC. Драйвер можно скачать на сайте [название](https://www.postgresql.org/ftp/odbc/releases/). 

Внимание! При скачивании драйвера обратите внимание на разрядность: она должна быть такой же, как и разрядность приложения, *которому нужен доступ*. *впихнуть про ошибку*

## Установка драйвера psqlODBC в Windows 
Примечание. Рекомендуется установка из msi-пакета.

1. Откройте Панель управления -> **Административ тулс? -> Data Sources (ODBC).**
![Изображение] (!!!)
2. Перейдите на вкладку System DSN.
3. Создайте новый источник данных, выбрав драйвер Postgres (unicode) и прописав учетные данные. 


Если драйвер psqlODBC 32-битный, а Windows является 64-битной, то откройте Панель управления через командную строку:
```
c:\windows\system32\odbcad32.exe
```
Далее действуйте в соответствии с алгоритмом выше.

## Установка драйвера psqlODBC в Unix-подобных системах 





# dblink оракл-постгре



## настройка винда



## настройка юникс






# Получение данных из ? в ..продукты MS
~~ODBC можно использовать с любыми совместимыми приложениями, в том числе с MS Excel и MS Access.~~ <br>
*возможное примечание про потабличную загрузку и про все сразу*
## в Эксель
Для получения данных в MS Excel:
1. Создайте файл с расширением .dqy в *место* . Файл должен содержать следующее: <br>
``` 
XLODBC
1
DRIVER={PostgreSQL Unicode};DATABASE=Product;SERVER=127.0.0.1;PORT=5432;UID=<user>;PASSWORD=<passwordd>;SSLmode=disable;ReadOnly=0;Protocol=7.4;FakeOidIndex=0;ShowOidColumn=0;RowVersioning=0;ShowSystemTables=0;ConnSettings=;Fetch=100;Socket=4096;UnknownSizes=0;MaxVarcharSize=255;MaxLongVarcharSize=8190;Debug=0;CommLog=0;Optimizer=0;Ksqo=1;UseDeclareFetch=0;TextAsLongVarchar=1;UnknownsAsLongVarchar=0;BoolsAsChar=1;Parse=0;CancelAsFreeStmt=0;ExtraSysTablePrefixes=dd_;LFConversion=1;UpdatableCursors=1;DisallowPremature=0;TrueIsMinus1=0;BI=0;ByteaAsLongVarBinary=0;UseServerSidePrepare=0;LowerCaseIdentifier=0;GssAuthUseGSS=0;XaOpt=1
select * from Product_rate_plans
```
Примечания:
* В параметры DATABASE, UID и PASSWORD вписываются необходимые данные.
* Для корректной работы запроса необходимо писать его в одну строку. 

2. Откройте созданный файл.  
3. При запуске MS Excel *что-то про соглашение включения источника данных*.

В результате отображается MS Excel с соответствующими данными. Получение данных завершено.


## в аксес
Примечание. В зависимости от версии MS Access названия вкладок и кнопок могут незначительно различаться.

Для получения данных в MS Access:
1. Перейдите на вкладку «Внешние данные». 
2. Нажмите на кнопку «Создать источник данных».
3. В выпадающем списке выберите «Из других источников» -> «База данных ODBC».
   ![Изображение](https://sun9-29.userapi.com/impg/nM8jnIhNhXSnN_A5WsyWB2uUGo-uHtbv1Twwnw/HGJWt0HXIpU.jpg?size=1003x479&quality=96&sign=3fab328464fda46dbb4746d0fa342e7f&type=album)
4. Следуйте инструкциям MS Access.

Получение данных завершено.