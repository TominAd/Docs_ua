#############################################################
**Підписання документа за допомогою MobileID**
#############################################################

.. attention:: Підписання з допомогою MobileID відбувається в два кроки:

    1) Користувачу необхідно відправити запит що містить **документ на підпис**. В відповідь на запит приходить **ID транзакції**.

    2) Користувачу необхідно відправити **ID** з пункта 1, й отримати **тіло підпису** , використовуючи метод **{url сервера}/bdoc/mobile_sign**.

Крок 1. Отримання ID транзакції
----------------------------------

Для роботи з цим методом користувач повинен бути `авторизованим <https://wiki.edin.ua/uk/latest/API_DOCflow/Methods/Authorization.html>`__ .

+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
|                       **Метод запиту**                       |                                             **HTTP POST**                                              |
+==============================================================+========================================================================================================+
| **Content-Type**                                             | application/form-data (бінарні данні в тілі HTTP запиту)                                               |
+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
| **URL запиту**                                               |   **https://doc.edin.ua/bdoc/mobile_sign**                                                             |
+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
| **Параметри, що передаються в URL (разом з адресою методу)** | В рядку заголовка (Header) "Set-Cookie" обов'язково передається SID - токен, отриманий при авторизації |
+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+

**Параметри в тілі HTTP запиту/відповіді**
*******************************************************************

``REQUEST``

В цьому методі тіло **запиту** передається в *form-data*.

+---------------+--------+-------------------------------------------------+
|   Параметр    | Формат |                      Опис                       |
+===============+========+=================================================+
| msisdn        |        | номер телефону, до якого прив'язаний сертифікат |
+---------------+--------+-------------------------------------------------+
| message       | long   | повідомлення, яке відображається на телефоні    |
+---------------+--------+-------------------------------------------------+
| positionId    | long   | ID ключа сертифіката (не потрібно для Київстар) |
+---------------+--------+-------------------------------------------------+
| document_body | long   | тіло документ на підпис                         |
+---------------+--------+-------------------------------------------------+

``RESPONSE``

Опис json-параметрів **відповіді** метода API

Таблиця 1 - Опис json-параметрів **відповіді** метода API

+----------+--------+---------------+
| Параметр | Формат |     Опис      |
+==========+========+===============+
| trans_id | long   | ID транзакції |
+----------+--------+---------------+

--------------

**Приклади**
*****************

Приклад тіла **запиту** в form-data 

.. code:: ruby


  {
    "msisdn": 380667901456
    "message": 
    "positionId": 6075
    "document_body": {}

  }


--------------

Приклад тіла **відповіді** в json форматі 

.. code:: ruby


  {
    "trans_id": 16
  }


Крок 2. Отримання тіла підпису
-------------------------------

Для роботи з цим методом користувач повинен бути `авторизованим <https://wiki.edin.ua/uk/latest/API_DOCflow/Methods/Authorization.html>`__ .

+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
|                       **Метод запиту**                       |                                                **HTTP GET**                                                |
+==============================================================+============================================================================================================+
| **Content-Type**                                             | application/octet-stream (бінарні данні в тілі HTTP відповіді)                                             |
+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
| **URL запиту**                                               |   **https://doc.edin.ua/bdoc/mobile_sign**?msisdn=380667901456&=16                                         |
+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
| **Параметри, що передаються в URL (разом з адресою методу)** | В рядку заголовка (Header) "Set-Cookie" обов'язково передається **SID** - токен, отриманий при авторизації |
|                                                              |                                                                                                            |
|                                                              | **Обов'язкові url-параметри:**                                                                             |
|                                                              |                                                                                                            |
|                                                              | **msisdn** - номер телефону                                                                                |
|                                                              |                                                                                                            |
|                                                              | **trans_id** - ID транзакції                                                                               |
+--------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+

**JSON-параметри в тілі HTTP запиту/відповіді**
***********************************************************

``REQUEST``

В цьому методі json-тіло **запиту** відсутнє (інші дані передавати не потрібно).

``RESPONSE``

У **відповідь** передається набір байт .p7s файл тіла підпису.


**Приклади**
*********************************

**При використанні методу json-тіло запиту відсутнє (дані передавати не потрібно)**

--------------

У **відповідь** передається набір байт .p7s файл тіла підпису.

