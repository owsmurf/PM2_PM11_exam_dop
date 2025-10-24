Модуль 1 — База данных «Книжный мир»

Цель:
Создать базу данных для учёта книг, пользователей и заказов.

СУБД:  
PostgreSQL 14 (WSL Ubuntu)

Таблицы:
roles, users, authors, genres, publishers, books, pickup_points, orders, order_details  

Связи: 
users.role_id - roles.role_id  
books.author_id - authors.author_id  
books.genre_id - genres.genre_id  
books.publisher_id - publishers.publisher_id  
orders.user_id - users.user_id  
orders.pickup_point_id - pickup_points.pickup_point_id  
order_details.order_id - orders.order_id  
order_details.book_id - books.book_id  

создать базу
createdb book_world

загрузить структуру
psql -U postgres -d book_world -f book_world.sql

загрузить данные
psql -U postgres -d book_world -f book_world_data_inserts.sql

Условная проверка:

SELECT COUNT(*) FROM books;
SELECT COUNT(*) FROM orders;

SELECT b.title, a.name AS author
FROM books b
JOIN authors a ON a.author_id=b.author_id
LIMIT 5;