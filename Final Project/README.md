# Final Project: Flask API Using sqlalchemy

## About the Project:
My project built a Flask CRUD API that uses sqlalchemy to initialize a database of more than seventy of the most popular skincare products on the market. I wanted to create an API for users to find skincare products within their budget (which can be inferred by brand), for their skin type, and without ingredients that could be triggering for their specific skin. This Flask API has endpoints that not only initialize a basic skincare products database, but will also allow users to add products (using JSON format), update/edit products, delete products, and of course, query the database with parameters relating to product id, product name, brand name, skin type, product type (i.e., serum, moisturizer, retinol, etc.), and ingredients(specifically ingredients they do NOT want in their skincare). The HTTP "GET" requests allow for multi-level query parameters, some of which allow multiple values, while "PUT", "POST", and "DELETE" requests allow products to be updated, added, and deleted respectively. 
    
The two major class themes I selected for this project was databases and APIs and I selected these two particularly because I wanted to work more with Postgres and also gain a deeper understanding of APIs because it is a topic that I found more confusing and difficult in this course. To implement these concepts, I used Flask to create an API and sqlalchemy to create and populate a database of skincare products. I am glad that through this project I was able to refresh and build upon some of my basic knowledge of SQL and get a better grasp of what APIs are and why they are necessary. If I had the opportunity to redo this project, I would try to use render_templates to implement HTML templates that would help "prettify" API responses.

This project was definitely very challenging, especially conceptually. It took me some time to even fully get a hold on what I had to do, especially because to best streamline this process, I used Docker. As a novice user of Docker, I had to spend a decent amount of time trying to get a grasp of why I needed Docker and how to run the Docker container properly for my purposes, etc. I learned by doing this project that using a Docker container significanly cuts down on runtime, allows me to work in a consistent environment and isolate processes if needed (ex. did not have to constantly reinstantiate the skin_prods database everytime I made edits and wanted to test my code). In addition, as mentioned earlier, I have very minimal knowledge of SQL and a lot of time and effort was spent on being able to properly query my database to do what I wanted it to do. I can say with certainty that this project was quite complex and the five windows each with 12+ tabs on researching SQL query statements, sqlalchemy query syntax, and generally building Flask APIs is definitely a testament to that. 

The extra credit I attempted was using libraries/modules not specifically covered in class, namely Flask and to some extent sqlalchemy (from flask_sqlalchemy) because although we superficially went over it during this course, we did not really implement it in any of our assignments. I also implemented "try, except" for "GET" requests in the cases that multiple values were specified for parameters that allow for it. 

### How to run the project:
1) Ensure app.py, Dockerfile, requirements.txt, wait-for-it.sh, and docker-compose.yml are in the same directory
2) Create a virtual environment using the provided requirements.txt file
3) Then build the Docker container using the terminal commands:

```bash
    $ docker-compose build
    $ docker-compose up -d
```

4) Basic queries (HTTP "GET" requests) can be tested the following endpoint:
    to which query parameters can be specified; examples of some queries that can be tested are:
     1. /api/v2/resources/skincareproducts?brand=INNISFREE, the ordinary(which asks for all products by the brands innisfree and The Ordinary)
     2. /api/v2/resources/skincareproducts?skinTypes=Dry&productType=Face Mask (which asks for face mask products for a dry skin type)
     3. /api/v2/resources/skincareproducts?name=The Water Cream Oil-Free Pore Minimizing Moisturizer (which asks for details about the specific product called The Water Cream Oil-Free Pore Minimizing Moisturizer)
     4. /api/v2/resources/skincareproducts?id=4 (gets product details for the product with the database id of 4)

    - ** NOTE: all API responses will be of JSON type **
    - *** Alternatively, "GET" requests with specified parameters can be tested with the provided Postman collection(recommended)
5) To test endpoints involving updating existing products, deleting products and posting new products, it would be useful to use a testing application like Postman through which you can easily send product information in JSON format and specify the type of request you are doing (i.e. "POST", "DELETE")
6) To shut down the processes, run 
```bash
    $ docker-compose down
    $ docker volume rm -f final-project_skdata 
```
in another terminal that is not running the container. This will stop the process and remove the volume the Docker container was running on.

*7) To interact directly with the database in Postgres, use the command:

```bash
    docker exec -it db psql -U postgres
```

#### SOURCES:
1) https://www.digitalocean.com/community/tutorials/how-to-use-one-to-many-database-relationships-with-flask-sqlalchemy --> was integral in helping me learn how to use Flask and sqlalchemy to build my API and database
2) https://blog.teclado.com/query-string-arguments-in-flask-rest-apis/ --> helped me figure out how to take in multiple values for a single query parameter as this was a large part of me being able to achieve what I wanted with this API
3) https://www.tutorialspoint.com/sqlalchemy/sqlalchemy_orm_filter_operators.htm --> was key in guiding me through sqlalchemy syntax which helped me write the database queries I wanted
