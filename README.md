# 🗃 Работа с базами данных

## 🗄 Запросы к базе данных
- Учебный проект тестирования веб-приложения **DemoShopping** в рамках курса
> У приложения "Интернет-магазин" есть своя база данных, в которой хранится информация про пользователей, товары, корзину, заказы и платежные данные. Практика с MongoDB - создание коллекции в MongoDB, которая будет повторять содержимое таблицы card_info в базе данных qa_shop
<table>
      <tr>
        <th>№</th>
        <th>Артефакт</th>
        <th>Ссылка</th>
      </tr>
      <tr>
        <td>1</td>
        <td>Работа с базами данных, проект_01_SELECT, отправка простых SELECT запросов</td>
        <td><a href= "https://docs.google.com/spreadsheets/d/1R8VZXV7RtH-ANwvG4QVQLe_b3JKVY86XKUx3Wp2h7iM/edit?usp=sharing"><img title="publiclink" src="https://img.icons8.com/?size=100&id=80410&format=png&color=000000" width="40" height="40" alt="gmail"/></a></td>
      </tr>
      <tr>
        <td>2</td>
        <td>Работа с базами данных, проект_02_JOIN, отправка простых JOIN запросов для слияния таблиц</td>
        <td><a href= "https://docs.google.com/spreadsheets/d/197JdjIazn0R66EFn9uer9AH19QQToc7L6DfbyRzSTkc/edit?usp=sharing"><img title="publiclink" src="https://img.icons8.com/?size=100&id=80410&format=png&color=000000" width="40" height="40" alt="gmail"/></a></td>
      </tr>
      <tr>
        <td>3</td>
        <td>Проект_03_MongoDB - создание коллекции в MongoDB</td>
        <td><a href= "https://docs.google.com/spreadsheets/d/1cnLmyHLs4YunkiBa6wE7jNr83e38KRKk3mGpodEBshk/edit?usp=sharing"><img title="publiclink" src="https://img.icons8.com/?size=100&id=80410&format=png&color=000000" width="40" height="40" alt="gmail"/></a></td>
      </tr>
</table>



## 🗄 Работа с удаленной базой данных
> Работа с удаленноой базой данных сервиса курьерской доставки. Отправка запросов на backend сервиса осуществлялся через Postman. Работа с удалённой базой данных через Cygwin64 Terminal 3.7.6
### Задание 1
Нужно проверить, отображается ли созданный заказ в базе данных.
Для этого: выведи список логинов курьеров с количеством их заказов в статусе «В доставке» (поле inDelivery = true). 

### Решение:

Запрос для [строки терминала Cygwin64](https://github.com/Morrhat/Autotests_and_SQL/blob/main/SQL_screenshoot.png):
```sql
SELECT c.login, COUNT("inDelivery") FROM "Orders" AS o LEFT OUTER JOIN "Couriers" AS c ON o."courierId" = c.id WHERE "inDelivery" is true GROUP BY c.login;
```

Запрос для SQL:
```sql
 SELECT c.login, COUNT("inDelivery") 
 FROM "Orders" AS o 
 LEFT OUTER JOIN "Couriers" AS c ON o."courierId" = c.id 
 WHERE "inDelivery" is true 
 GROUP BY c.login
```

### Задание 2
Тестирование статусов заказов. Нужно убедиться, что в базе данных они записываются корректно.
Для этого: выведи все трекеры заказов и их статусы. 
Статусы определяются по следующему правилу:
Если поле finished == true, то вывести статус 2.
Если поле canсelled == true, то вывести статус -1.
Если поле inDelivery == true, то вывести статус 1.
Для остальных случаев вывести 0.

### Решение:

Запрос для [строки терминала Cygwin64](https://github.com/Morrhat/Autotests_and_SQL/blob/main/SQL_screenshoot_1.png):
```sql
SELECT track, CASE WHEN finished IS true THEN '2' WHEN cancelled IS true THEN '-1' WHEN "inDelivery" IS true THEN '1' WHEN finished IS false AND "inDelivery" IS false THEN '0' END FROM "Orders" AS o;
```

Запрос для SQL:
```sql
 SELECT track, 
    CASE WHEN finished IS true THEN '2' 
        WHEN cancelled IS true THEN '-1' 
        WHEN "inDelivery" IS true THEN '1' 
        WHEN finished IS false AND "inDelivery" IS false THEN '0' 
    END 
 FROM "Orders" AS o
```


---
                                                          2025

