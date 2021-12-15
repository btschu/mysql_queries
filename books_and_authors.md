### Query: Create 5 different authors: Jane Austen, Emily Dickinson, Fyodor Dostoevsky, William Shakespeare, Lau Tzu
<per>
INSERT INTO authors (first_name, last_name, created_at, updated_at)
VALUES("Jane", "Austen", NOW(), NOW()), ("Emily", "Dickinson", NOW(), NOW()), ("Fyodor", "Dostoevsky", NOW(), NOW()), ("William", "Shakespeare", NOW(), NOW()), ("Lau", "Tzu", NOW(), NOW());
</per>

### Query: Create 5 books with the following names: C Sharp, Java, Python, PHP, Ruby
INSERT INTO books (title, num_of_pages, created_at, updated_at)
VALUES("C Sharp", 245, NOW(), NOW()), ("Java", 321, NOW(), NOW()), ("FPython", 211, NOW(), NOW()), ("PHP", 123, NOW(), NOW()), ("Ruby", 342, NOW(), NOW());

### Query: Change the name of the C Sharp book to C#
UPDATE books SET title = 'C #'
WHERE id = 1

### Query: Change the first name of the 4th author to Bill
UPDATE authors SET first_name = 'Bill'
WHERE id = 4

### Query: Have the first author favorite the first 2 books
INSERT INTO favorites (author_id, book_id)
VALUES (1,1),(1,2);

### Query: Have the second author favorite the first 3 books
INSERT INTO favorites (author_id, book_id)
VALUES (2,1),(2,2),(2,3);

### Query: Have the third author favorite all 5 books
INSERT INTO favorites (author_id, book_id)
VALUES (3,1),(3,2),(3,3),(3,4),(3,5);

### Query: Retrieve all the authors who favorited the 3rd book
SELECT * FROM books
JOIN favorites on books.id = favorites.book_id
JOIN authors on authors.id = favorites.author_id
WHERE books.id = 3;

### Query: Remove the first author of the 3rd book's favorites
DELETE FROM favorites
WHERE book_id = 3
AND author_id = 2;

### Query: Have the 5th author favorite the 2nd book
INSERT INTO favorites (author_id, book_id)
VALUES (5,2);

### Query: Find all the books that the 2nd author favorited
SELECT * FROM books
JOIN favorites ON books.id = favorites.book_id
JOIN authors ON authors.id = favorites.author_id
WHERE books.id = 2;

### Query: Find all the authors that favorited to the 5th book
SELECT * FROM authors
JOIN favorites ON authors.id = favorites.author_id
JOIN books ON books.id = favorites.book_id
WHERE authors.id = 5;

### Query: Find all the authors that favorited to the 2nd book
SELECT * FROM authors
JOIN favorites ON authors.id = favorites.author_id
JOIN books ON books.id = favorites.book_id
WHERE authors.id = 2;

### Query: Display all the book titles that the 2nd author favorited
SELECT * FROM books
JOIN favorites ON books.id = favorites.book_id
JOIN authors ON authors.id = favorites.author_id
WHERE books.id = 2;
