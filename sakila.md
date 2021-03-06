## What query would you run to get all the customers inside city_id = 312? Your query should return customer first name, last name, email, and address.
```
SELECT address.city_id, city.city, customer.first_name, customer.last_name, customer.email, address.address FROM customer
LEFT JOIN address ON address.address_id = customer.address_id
LEFT JOIN city ON city.city_id = address.city_id
WHERE address.city_id = 312;
```

## What query would you run to get all comedy films? Your query should return film title, description, release year, rating, special features, and genre (category).
```
SELECT film.film_id, film.title, film.description, film.release_year, film.rating, film.special_features, category.name AS genre FROM film
LEFT JOIN film_category ON film.film_id=film_category.film_id
LEFT JOIN category ON category.category_id = film_category.category_id
WHERE category.name = 'Comedy';
```

## What query would you run to get all the films joined by actor_id=5? Your query should return the actor id, actor name, film title, description, and release year.
```
SELECT actor.actor_id, CONCAT(actor.first_name, ' ', actor.last_name) AS actor_name, film.title, film.description, film.release_year FROM film
LEFT JOIN film_actor ON film.film_id = film_actor.film_id
LEFT JOIN actor ON actor.actor_id = film_actor.actor_id
WHERE actor.actor_id = 5;
```

## What query would you run to get all the customers in store_id = 1 and inside these cities (1, 42, 312 and 459)? Your query should return customer first name, last name, email, and address.
```
SELECT customer.first_name, customer.last_name, customer.email, address.address FROM customer
JOIN address ON address.address_id = customer.address_id
JOIN city ON city.city_id = address.city_id AND city.city_id IN (1, 42, 312, 459)
WHERE customer.store_id = 1;
```

## What query would you run to get all the films with a "rating = G" and "special feature = behind the scenes", joined by actor_id = 15? Your query should return the film title, description, release year, rating, and special feature. Hint: You may use LIKE function in getting the 'behind the scenes' part.
```
SELECT title, description, release_year, rating, special_features FROM film
LEFT JOIN film_actor ON film.film_id = film_actor.film_id
LEFT JOIN actor ON actor.actor_id = film_actor.actor_id
WHERE rating = "G" AND special_features LIKE "%Behind the Scenes%" AND actor.actor_id = 15;
```

## What query would you run to get all the actors that joined in the film_id = 369? Your query should return the film_id, title, actor_id, and actor_name.
```
SELECT film.film_id, film.title, actor.actor_id, CONCAT(actor.first_name, ' ',actor.last_name) AS actor_name FROM film
LEFT JOIN film_actor ON film.film_id = film_actor.film_id
LEFT JOIN actor ON actor.actor_id = film_actor.actor_id
WHERE film.film_id = 369;
```

## What query would you run to get all drama films with a rental rate of 2.99? Your query should return film title, description, release year, rating, special features, and genre (category).
```
SELECT film.title, film.description, film.release_year, film.rating, film.special_features, category.name AS genre FROM film
LEFT JOIN film_category ON film.film_id = film_category.film_id
LEFT JOIN category ON category.category_id = film_category.category_id
WHERE category.name = "Drama" AND film.rental_rate = 2.99
```

## What query would you run to get all the action films which are joined by SANDRA KILMER? Your query should return film title, description, release year, rating, special features, genre (category), and actor's first name and last name.
```
SELECT film.title, film.description, film.release_year, film.rating, film.special_features, category.name AS genre, CONCAT(actor.first_name, ' ',actor.last_name) AS actor_name FROM film
LEFT JOIN film_category ON film.film_id= film_category.film_id
LEFT JOIN category ON category.category_id = film_category.category_id
LEFT JOIN film_actor ON film.film_id = film_actor.film_id
LEFT JOIN actor ON actor.actor_id = film_actor.actor_id
WHERE CONCAT(actor.first_name, ' ',actor.last_name) = 'SANDRA KILMER' AND category.name LIKE 'action'
```