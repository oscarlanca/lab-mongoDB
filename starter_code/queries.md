![Ironhack Logo](https://i.imgur.com/1QgrNNw.png)

# Answers

### 1. All the companies that it's name match 'Babelgum'. Retrieve only their `name` field.

<!-- Your Code Goes Here -->
query: {name:'Babelgum'} projection: {name:1,_id:0} sort: skip: limit:

### 2. All the companies that have more than 5000 employees. Limit the search to 20 companies and sort them by **number of employees**.

<!-- Your Code Goes Here -->
Filter: { number_of_employees: { $gt: 5000 } } Project: Sort: { number_of_employees: -1} Collation: Limit: 20

### 3. All the companies founded between 2000 and 2005, both years included. Retrieve only the `name` and `founded_year` fileds.

<!-- Your Code Goes Here -->
Filter: { $and: [{ founded_year: { $gte: 2000}}, { founded_year: { $lte: 2005}} ]} Project: {name: 1, founded_year: 1} Sort: Collation:

### 4. All the companies that had a Valuation Amount of more than 100.000.000 and have been founded before 2010. Retrieve only the `name` and `ipo` fields.

<!-- Your Code Goes Here -->
Filter: { $and: [{ "ipo.valuation_amount": {$gt: 100000000}}, { founded_year: { $lt: 2005}} ]} Project: {name: 1, ipo: 1} Sort: Collation:

### 5. All the companies that have less than 1000 employees and have been founded before 2005. Order them by the number of employees and limit the search to 10 companies.

<!-- Your Code Goes Here -->
Filter: { $and: [{ "number_of_employees": {$lt: 1000}}, { founded_year: { $lt: 2005}} ]} Project: Sort: {number_of_employees: -1} Collation: Limit: 10

### 6. All the companies that don't include the `partners` field.

<!-- Your Code Goes Here -->
query: {partners: {$exists: false}}

### 7. All the companies that have a null type of value on the `category_code` field.

<!-- Your Code Goes Here -->

query: {category_code: {$type: 10}}

### 8. All the companies that have at least 100 employees but less than 1000. Retrieve only the `name` and `number of employees` fields.

<!-- Your Code Goes Here -->
query: {number_of_employees:{$lt:1000,$gte:100}} projection: {name:1,number_of_employees:1,_id:0}

### 9. Order all the companies by their IPO price descendently.

<!-- Your Code Goes Here -->
sort: {"ipo.valuation_amount":-1}

### 10. Retrieve the 10 companies with more employees, order by the `number of employees`

<!-- Your Code Goes Here -->
sort: {number_of_employees:-1} limit: 10

### 11. All the companies founded on the second semester of the year. Limit your search to 1000 companies.
<!-- Your Code Goes Here -->
query: {founded_month:{$gte:6}} limit: 1000

### 12. All the companies that have been 'deadpooled' after the third year.
<!-- Your Code Goes Here -->
Filter: {$expr: {$gt:[deadpooled_year, founded_year("3")]}} Project: Sort: Collation:
### 13. All the companies founded before 2000 that have and acquisition amount of more than 10.000.000
<!-- Your Code Goes Here -->
query: {$and: [ {founded_year:{$lt:2000}}, {"acquisition.price_amount":{$gt:10000000} } ] }

### 14. All the companies that have been acquired after 2015, order by the acquisition amount, and retrieve only their `name` and `acquisiton` field.
<!-- Your Code Goes Here -->
Filter: {"acquisition.acquired_year": {$gt:2015}} Project: {name: 1,acquisition:1} Sort: {"acquisition.price_amount":-1} Collation:

### 15. Order the companies by their `founded year`, retrieving only their `name` and `founded year`.
<!-- Your Code Goes Here -->
projection: {name:1 , founded_year:1 ,_id:0} sort: {founded_year : -1}
### 16. All the companies that have been founded on the first seven days of the month, including the seventh. Sort them by their `aquisition price` descendently. Limit the search to 10 documents.
<!-- Your Code Goes Here -->
Filter: {founded_day:{$lte:7}} Project: Sort: {"acquisitions.price_amount":1, "acquisition.price_amount":1} Collation: Limit: 10

### 17. All the companies on the 'web' `category` that have more than 4000 employees. Sort them by the amount of employees in ascendant order.
<!-- Your Code Goes Here -->
query: {$and: [{ number_of_employees: { $gt: 4000 }},{ category_code: 'web'}]} sort: {number_of_employees: 1}

### 18. All the companies which their acquisition amount is more than 10.000.000, and currency are 'EUR'.
<!-- Your Code Goes Here -->
Filter: {$and:[ {"acquisition.price_amount": {$gt: 10000000}}, {"acquisition.price_currency_code": {$eq: 'EUR'}}]} Project: Sort: Collation:

### 19. All the companies that have been acquired on the first trimester of the year. Limit the search to 10 companies, and retrieve only their `name` and `acquisition` fields.
<!-- Your Code Goes Here -->
Filter: {"acquisition.acquired_month": {$lte: 3}} Project: {name:1, acquisition:1} Sort: Collation:
### 20. All the companies that have been founded between 2000 and 2010, but have not been acquired before 2011.

<!-- Your Code Goes Here -->
query: {$and:[{founded_year:{$gte:2000,$lte:2010}},{$or:[{"acquisitions.acquired_year":{$gte:2011}},{"acquisitions.acquired_year":null}]}]}