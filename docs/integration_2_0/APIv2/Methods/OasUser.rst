######################################################################
**Отримання інформації по авторизованому користувачу**
######################################################################

Для роботи з цим методом користувач повинен бути `авторизованим <https://wiki.edin.ua/uk/latest/integration_2_0/APIv2/Methods/Authorization.html>`__ .

За допомогою метода **api/oas/user** можливо отримати інформацію про користувача, наприклад ID користувача, ID аккаунта, логін, чи має користувач "права адміністратора" (true / false), дані про платформу і інші ідентифікатори.

.. csv-table:: 
  :file: OasUser.csv
  :widths:  10, 41
  :stub-columns: 0

**RESPONSE**

В тілі **відповіді** передається інформація про користувача (об'єкт `User <https://wiki.edin.ua/uk/latest/integration_2_0/APIv2/Methods/EveryBody/User.html>`__).
