### Query: Create 3 new dojos
```
INSERT INTO dojos (name, created_at, updated_at)
VALUES("Brandon's Dojo", NOW(), NOW()), ("Jacie's Dojo", NOW(), NOW()), ("Natalie's Dojo", NOW(), NOW());
```

### Query: Delete the 3 dojos you just created
```
DELETE FROM dojos WHERE id IN (1, 2, 3);
```

### Query: Create 3 more dojos
```
INSERT INTO dojos (name, created_at, updated_at)
VALUES("Steves's Dojo", NOW(), NOW()), ("Bennett's Dojo", NOW(), NOW()), ("Flying High Dojo", NOW(), NOW());
```

### Query: Create 3 ninjas that belong to the first dojo
```
INSERT INTO ninjas (first_name, last_name, age, created_at, updated_at, dojo_id)
VALUES ("Brandon", "Schumacher", 37,  NOW(), NOW(), 4), ("Jacie", "Schumacher", 33,  NOW(), NOW(), 4), ("Natalie", "Schumacher", 6,  NOW(), NOW(), 4);
```

### Query: Create 3 ninjas that belong to the second dojo
```
INSERT INTO ninjas (first_name, last_name, age, created_at, updated_at, dojo_id)
VALUES ("John", "Schumacher", 37,  NOW(), NOW(), 5), ("Ron", "Schumacher", 33,  NOW(), NOW(), 5), ("Dan", "Schumacher", 6,  NOW(), NOW(), 5);
```

### Query: Create 3 ninjas that belong to the third dojo
```
INSERT INTO ninjas (first_name, last_name, age, created_at, updated_at, dojo_id)
VALUES ("Jamie", "Schumacher", 37,  NOW(), NOW(), 6), ("Nellie", "Schumacher", 33,  NOW(), NOW(), 6), ("Tim", "Schumacher", 6,  NOW(), NOW(), 6);
```

### Query: Retrieve all the ninjas from the first dojo
```
SELECT * FROM dojos
JOIN ninjas ON dojos.id = ninjas.dojo_id
WHERE dojos.id = 4;
```

### Query: Retrieve all the ninjas from the last dojo
```
SELECT * FROM dojos
JOIN ninjas ON dojos.id = ninjas.dojo_id
WHERE dojos.id = (SELECT dojo_id FROM ninjas ORDER BY dojo_id DESC LIMIT 1);
```

### Query: Retrieve the last ninja's dojo
```
SELECT * FROM dojos
WHERE dojos.id = (SELECT dojo_id FROM ninjas ORDER BY dojo_id DESC LIMIT 1);
```


