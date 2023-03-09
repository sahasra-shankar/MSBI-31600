# Final Project: Flask API Using sqlalchemy

## About the Project:
My project built a Flask CRUD API that uses sqlalchemy to initialize a database of more than seventy of the most popular skincare products on the market. I wanted to create an API for users to find skincare products within their budget (which can be inferred by brand), for their skin type, and without ingredients that could be triggering for their specific skin. This Flask API has endpoints that not only initialize a basic skincare products database, but will also allow users to add products (using JSON format), update/edit products, delete products, and of course, query the database with parameters relating to product id, product name, brand name, skin type, product type (i.e., serum, moisturizer, retinol, etc.), and ingredients(specifically ingredients they do NOT want in their skincare). The HTTP "GET" requests allow for multi-level query parameters, some of which allow multiple values, while "PUT", "POST", and "DELETE" requests allow products to be updated, added, and deleted respectively. 
    
The two major class themes I selected for this project was databases and APIs and I selected these two particularly because I wanted to work more with Postgres and also gain a deeper understanding of APIs because it is a topic that I found more confusing and difficult in this course. To implement these concepts, I used Flask to create an API and sqlalchemy to create and populate a database of skincare products. I am glad that through this project I was able to refresh and build upon some of my basic knowledge of SQL and get a better grasp of what APIs are and why they are necessary. If I had the opportunity to redo this project, I would try to use render_templates to implement HTML templates that would help "prettify" API responses.

This project was definitely very challenging, especially conceptually. It took me some time to even fully get a hold on what I had to do, especially because to best streamline this process, I used Docker. As a novice user of Docker, I had to spend a decent amount of time trying to get a grasp of why I needed Docker and how to run the Docker container properly for my purposes, etc. I learned by doing this project that using a Docker container significanly cuts down on runtime, allows me to work in a consistent environment and isolate processes if needed (ex. did not have to constantly reinstantiate the skin_prods database everytime I made edits and wanted to test my code). In addition, as mentioned earlier, I have very minimal knowledge of SQL and a lot of time and effort was spent on being able to properly query my database to do what I wanted it to do. I can say with certainty that this project was quite complex and the five windows each with 12+ tabs on researching SQL query statements, sqlalchemy query syntax, and generally building Flask APIs is definitely a testament to that. 

The extra credit I attempted was using libraries/modules not specifically covered in class, namely Flask and to some extent sqlalchemy (from flask_sqlalchemy) because although we superficially went over it during this course, we did not really implement it in any of our assignments. I also implemented "try, except" for "GET" requests in the cases that multiple values were specified for parameters that allow for it. 

### How to run the project:
1) Ensure app.py, Dockerfile, requirements.txt, and docker-compose.yml are in the same directory
2) Create a virtual environment using the provided requirements.txt file
3) Then build the Docker container using the terminal commands:
    - "docker-compose build"
    - "docker-compose up -d db"
    - "docker-compose up skincare-svc"
4) Creation of the skincare products database can be verified in another terminal with the command:
    - "docker exec -it db psql -U postgres"
    which will allow you interact with the database directly in postgres
5) To test the API endpoints, first initialize the database with skincare products using the route:
    "http://localhost:8181/dbinit"
6) Basic queries (HTTP "GET" requests) can be tested using the base route:
    "http://localhost:8181/api/v2/resources/skincareproducts"
    to which query parameters can be specified; examples of some queries that can be tested are:
    a) "http://localhost:8181/api/v2/resources/skincareproducts?brand=INNISFREE, the ordinary"(which asks for all products by the brands innisfree and The Ordinary)
    b) "http://localhost:8181/api/v2/resources/skincareproducts?skinTypes=Dry&productType=Face Mask" (which asks for face mask products for a dry skin type)
    c) "http://localhost:8181/api/v2/resources/skincareproducts?name=The Water Cream Oil-Free Pore Minimizing Moisturizer" (which asks for details about the specific product called The Water Cream Oil-Free Pore Minimizing Moisturizer)
    d) "http://localhost:8181/api/v2/resources/skincareproducts?id=4" (gets product details for the product with the database id of 4)

    ** NOTE: all API responses will be of JSON type **

7) To test endpoints involving updating existing products, deleting products and posting new products, it would be useful to use a testing application like Postman through which you can easily send product information in JSON format and specify the type of request you are doing (i.e. "POST", "DELETE")


#### SOURCES:
1) 
2) https://blog.teclado.com/query-string-arguments-in-flask-rest-apis/ --> helped me figure out how to take in multiple values for a single query parameter as this was a large part of me being able to achieve what I wanted with this API
3) https://www.tutorialspoint.com/sqlalchemy/sqlalchemy_orm_filter_operators.htm --> was key in guiding me through sqlalchemy syntax which helped me write the database queries I wanted