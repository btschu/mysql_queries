1. What query would you run to get the total revenue for March of 2012?
```
SELECT MONTHNAME(charged_datetime) AS month, SUM(amount) AS revenue FROM billing
WHERE MONTH(charged_datetime) = '03' AND YEAR(charged_datetime) = "2012"
```

2. What query would you run to get total revenue collected from the client with an id of 2?
```
SELECT client_id, SUM(amount) AS total_revenue FROM billing
WHERE client_id = 2;
```

3. What query would you run to get all the sites that client with an id of 10 owns?
```
SELECT domain_name AS website, client_id FROM sites
WHERE client_id = 10;
```

4. What query would you run to get total # of sites created per month per year for the client with an id of 1? What about for client with an id of 20?
```
SELECT client_id, COUNT(domain_name) AS number_of_websites, MONTHNAME(created_datetime) AS month_created, YEAR(created_datetime) AS year_created FROM sites
WHERE client_id = 1
GROUP BY created_datetime;

SELECT client_id, COUNT(domain_name) AS number_of_websites, MONTHNAME(created_datetime) AS month_created, YEAR(created_datetime) AS year_created FROM sites
WHERE client_id = 20
GROUP BY created_datetime;
```

5. What query would you run to get the total # of leads generated for each of the sites between January 1, 2011 to February 15, 2011?
```
SELECT sites.domain_name AS website, COUNT(leads.leads_id) AS number_of_leads FROM sites
JOIN leads ON leads.site_id = sites.site_id
WHERE registered_datetime between "2011/01/01" and "2011/02/15"
GROUP BY domain_name;
```

6. What query would you run to get a list of client names and the total # of leads we've generated for each of our clients between January 1, 2011 to December 31, 2011?
```
SELECT CONCAT(clients.first_name, ' ',clients.last_name) AS client, COUNT(leads.leads_id) FROM clients
JOIN sites ON clients.client_id = sites.client_id
JOIN leads ON leads.site_id = sites.site_id
WHERE leads.registered_datetime between "2011/01/01" and "2011/12/31"
GROUP BY clients.client_id;
```

7. What query would you run to get a list of client names and the total # of leads we've generated for each client each month between months 1 - 6 of Year 2011?
```
SELECT CONCAT(clients.first_name, ' ',clients.last_name) AS client, COUNT(leads.leads_id) AS number_of_leads, MONTHNAME(leads.registered_datetime) AS month_generated FROM clients
JOIN sites ON clients.client_id = sites.client_id
JOIN leads ON leads.site_id = sites.site_id
WHERE YEAR(leads.registered_datetime) = "2011" AND MONTH(leads.registered_datetime) BETWEEN "01" AND "06"
GROUP BY leads.registered_datetime;
```

8. What query would you run to get a list of client names and the total # of leads we've generated for each of our clients' sites between January 1, 2011 to December 31, 2011? Order this query by client id.  Come up with a second query that shows all the clients, the site name(s), and the total number of leads generated from each site for all time.
```
SELECT CONCAT(clients.first_name, ' ',clients.last_name) AS client, sites.domain_name AS website, COUNT(leads.leads_id) AS number_of_leads FROM clients
JOIN sites ON clients.client_id = sites.client_id
JOIN leads ON sites.site_id = leads.site_id
GROUP BY sites.domain_name
ORDER BY clients.client_id;
```

9. Write a single query that retrieves total revenue collected from each client for each month of the year. Order it by client id.  First try this with integer month, second with month name.  A SELECT subquery will be needed for the second challenge.  Look at this for a hint.
```
SELECT CONCAT(clients.first_name, ' ',clients.last_name) AS client, SUM(billing.amount) AS revenue, MONTH(billing.charged_datetime) AS month_charged, YEAR(billing.charged_datetime) AS year_charged FROM billing
JOIN clients ON billing.client_id = clients.client_id
GROUP BY MONTH(billing.charged_datetime), YEAR(billing.charged_datetime)
ORDER BY clients.client_id, YEAR(billing.charged_datetime), MONTH(billing.charged_datetime);
```

10. Write a single query that retrieves all the sites that each client owns. Group the results so that all of the sites for each client are displayed in a single field. It will become clearer when you add a new field called 'sites' that has all the sites that the client owns. (HINT: use GROUP_CONCAT)
```
SELECT CONCAT(clients.first_name, ' ',clients.last_name) AS client, GROUP_CONCAT(sites.domain_name,' / ') AS sites FROM clients
JOIN sites ON clients.client_id = sites.client_id
GROUP BY clients.client_id
ORDER BY clients.client_id;
```