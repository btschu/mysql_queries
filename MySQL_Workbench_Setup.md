# Use MySQLWorkbench to connect to your localhost.
# Once you've connected the database, try the queries that you would need to make a
# CRUD application (create, read, update, delete). In other words, use the SQL commands INSERT, SELECT, UPDATE, and DELETE.

USE twitter

SELECT * FROM users

INSERT INTO users (first_name, last_name, handle, birthday, created_at, updated_at)
VALUES ("Brandon", "Schumacher", "bschu", "1984-03-30", NOW(), NOW());

SELECT * FROM users

UPDATE twitter.users SET handle = 'brandon.schumacher' WHERE id = 6;

SELECT * FROM users

DELETE FROM users WHERE id = 7;

SELECT * FROM users

DELETE FROM users WHERE id = 8;

SELECT * FROM users
