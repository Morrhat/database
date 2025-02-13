# Работа с базами данных
- Работа с базами данных, проект_01_SELECT - [Publick_link](https://docs.google.com/spreadsheets/d/1R8VZXV7RtH-ANwvG4QVQLe_b3JKVY86XKUx3Wp2h7iM/edit?usp=sharing)
- Работа с базами данных, проект_02_JOIN - [Publick_link](https://docs.google.com/spreadsheets/d/197JdjIazn0R66EFn9uer9AH19QQToc7L6DfbyRzSTkc/edit?usp=sharing)
- Работа с базами данных, проект_03_MongoDB - [Publick_link](https://docs.google.com/spreadsheets/d/1cnLmyHLs4YunkiBa6wE7jNr83e38KRKk3mGpodEBshk/edit?usp=sharing)

###### ###### ###### Работа с базой данных
###### Задание 1
Представь: тебе нужно проверить, отображается ли созданный заказ в базе данных.
Для этого: выведи список логинов курьеров с количеством их заказов в статусе «В доставке» (поле inDelivery = true). 

## Решение:

Запрос для строки терминала Cygwin64:
 SELECT c.login, COUNT("inDelivery") FROM "Orders" AS o LEFT OUTER JOIN "Couriers" AS c ON o."courierId" = c.id WHERE "inDelivery" is true GROUP BY c.login;

Запрос для SQL:
 SELECT c.login, COUNT("inDelivery") 
 FROM "Orders" AS o 
 LEFT OUTER JOIN "Couriers" AS c ON o."courierId" = c.id 
 WHERE "inDelivery" is true 
 GROUP BY c.login


###### Задание 2
Ты тестируешь статусы заказов. Нужно убедиться, что в базе данных они записываются корректно.
Для этого: выведи все трекеры заказов и их статусы. 
Статусы определяются по следующему правилу:
Если поле finished == true, то вывести статус 2.
Если поле canсelled == true, то вывести статус -1.
Если поле inDelivery == true, то вывести статус 1.
Для остальных случаев вывести 0.

## Решение:

Запрос для строки терминала Cygwin64:
 SELECT track, CASE WHEN finished IS true THEN '2' WHEN cancelled IS true THEN '-1' WHEN "inDelivery" IS true THEN '1' WHEN finished IS false AND "inDelivery" IS false THEN '0' END FROM "Orders" AS o;

Запрос для SQL:
 SELECT track, 
    CASE WHEN finished IS true THEN '2' 
        WHEN cancelled IS true THEN '-1' 
        WHEN "inDelivery" IS true THEN '1' 
        WHEN finished IS false AND "inDelivery" IS false THEN '0' 
    END 
 FROM "Orders" AS o
