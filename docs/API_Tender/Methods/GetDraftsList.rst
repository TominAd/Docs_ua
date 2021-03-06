##########################################################################################################################
**Отримання списку тендерів з "Чернеток"**
##########################################################################################################################

.. hint::
    В "Чернетках" відображаються неопубліковані тендери, що були створені даним користувачем. Для `Супер адміністратора <https://wiki.edin.ua/uk/latest/Personal_Cabinet/PCInstruction.html#user-roles>`__ в "Чернетках" відображаються така ж інформація, але по відношенню до всіх користувачів аккаунту.

Для роботи з цим методом користувач повинен бути `авторизованим <https://wiki.edin.ua/uk/latest/API_Tender/Methods/Authorization.html>`__ .

.. csv-table:: 
  :file: GetDraftsList.csv
  :widths:  10, 41
  :stub-columns: 0

**RESPONSE**

В тілі **відповіді** передається масив тендерів (масив об'єктів `Auction <https://wiki.edin.ua/uk/latest/API_Tender/Methods/EveryBody/GetDraftsListResponse.html>`__ ).

