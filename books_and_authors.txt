# Query: Create 5 different authors: Jane Austen, Emily Dickinson, Fyodor Dostoevsky, William Shakespeare, Lau Tzu
INSERT INTO authors (first_name, last_name, created_at, updated_at)
VALUES("Jane", "Austen", NOW(), NOW()), ("Emily", "Dickinson", NOW(), NOW()), ("Fyodor", "Dostoevsky", NOW(), NOW()), ("William", "Shakespeare", NOW(), NOW()), ("Lau", "Tzu", NOW(), NOW());

# Query: Create 5 books with the following names: C Sharp, Java, Python, PHP, Ruby
INSERT INTO books (title, num_of_pages, created_at, updated_at)
VALUES("C Sharp", 245, NOW(), NOW()), ("Java", 321, NOW(), NOW()), ("FPython", 211, NOW(), NOW()), ("PHP", 123, NOW(), NOW()), ("Ruby", 342, NOW(), NOW());

# Query: Change the name of the C Sharp book to C#
UPDATE books SET title = 'C #'
WHERE id = 1

# Query: Change the first name of the 4th author to Bill
UPDATE authors SET first_name = 'Bill'
WHERE id = 4

# Query: Have the first author favorite the first 2 books
INSERT INTO favorites (author_id, book_id)
VALUES (1,1),(1,2);

# Query: Have the second author favorite the first 3 books
INSERT INTO favorites (author_id, book_id)
VALUES (2,1),(2,2),(2,3);

# Query: Have the third author favorite all 5 books
INSERT INTO favorites (author_id, book_id)
VALUES (3,1),(3,2),(3,3),(3,4),(3,5);

# Query: Retrieve all the authors who favorited the 3rd book

# Query: Remove the first author of the 3rd book's favorites

# Query: Have the 5th author favorite the 2nd book

# Query: Find all the books that the 2nd author favorited

# Query: Find all the authors that favorited to the 5th book

# Query: Find all the authors that favorited to the 2nd book

# Query: Display all the book titles that the 2nd author favorited

# Query: Display all the book titles that the 2nd author favorited (Hint: Don't SELECT *)
