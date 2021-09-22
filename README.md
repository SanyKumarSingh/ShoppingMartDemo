# ShoppingMartDemo
ShoppingMartDemo - Production ready Spring Boot Rest application following RESTful Architecture. PFB the details.

Source Code Repository  https://github.com/SanyKumarSingh/DEMO/tree/main/ShoppingMart 

1. Scans products along with their quantity to calculate a running total
2. Support cancelling/adding items to the bucket.
3.  Support itemized total.
4. Available products in the Mart at application start. At Runtime this list can grow by adding new products. 
Item	Unit Price	Discount (%)	Quantity	Total
Coffee 1KG	20$	0 	1	20$
Tea 1KG	15$	0	1	15$
Oil 1L	10$	0	2	20$
Apples 1KG	5$	0	4	20$
Oranges 1KG	3$	0	5	15$
Total 	90$

5. At runtime the product Price and Discount could be updated as needed by the Mart.
6. Calculate daily revenue(total sale) of the Mart.
7. Register customers so that they could avail the benefit of the Loyalty program by getting rewarded for each purchase at the Mart.


 

To execute this SpringBootApplication run Application.java main class, it will automatically start the application on embedded Apache Tomcat and InMemory H2 database.
Deployable jar after  mvn clean install  could be found at - 
 C:\artifact.repository\com\cs\demo\ShoppingMartDemo\0.0.1-SNAPSHOT\ShoppingMartDemo-0.0.1-SNAPSHOT.jar

H2 Database Console - http://localhost:8080/h2-console/

Postman(Chrome Plugin) to test below REST API's - https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop/related?hl=en 

GET Request -
Fetch All Products - http://localhost:8080/api/v1/products/
Fetch Products By ProductCode - http://localhost:8080/api/v1/products/101
Get Bill By Billid- http://localhost:8080/api/v1/bills/1
Get Customer Details by CustomerID - http://localhost:8080/api/v1/customers/7

POST Request-
Add New Products(1 or more in a go) - http://localhost:8080/api/v1/products/  
Fetch RunningTotal or Generate Bill - http://localhost:8080/api/v1/generateBill/
Register New Customer - http://localhost:8080/api/v1/customers

PUT Request
Update Product By ProductCode- http://localhost:8080/api/v1/products/101
Update Customer Details - http://localhost:8080/api/v1/customers/1

DELETE Request -
Delete Customer - http://localhost:8080/api/v1/customers/1


CREATE TABLE PRODUCTS (
	PRODUCT_CODE INT PRIMARY KEY, 
	PERSENT_DISCOUNT FLOAT NOT NULL, 
	PRICE FLOAT NOT NULL, 
	PRODUCT_NAME VARCHAR(20) NOT NULL
);

CREATE TABLE CUSTOMERS (
	CUSTOMER_ID INT PRIMARY KEY, 
	EMAIL_ID VARCHAR(40) NOT NULL, 
	FIRST_NAME VARCHAR(20) NOT NULL, 
	LAST_NAME VARCHAR(20) NOT NULL, 
	MOBILE_NUMBER VARCHAR(15) NOT NULL, 
	REWARD_POINTS FLOAT NOT NULL
);


CREATE TABLE ITEM (
	ID INT PRIMARY KEY, 
	ITEM_NAME VARCHAR(20) NOT NULL, 
	QUANTITY INT NOT NULL, 
	PRODUCT_NAME VARCHAR(20) NOT NULL
);

CREATE TABLE BILL (
	PRODUCT_CODE INT PRIMARY KEY, 
	PERSENT_DISCOUNT FLOAT NOT NULL, 
	PRICE FLOAT NOT NULL, 
	PRODUCT_NAME VARCHAR(20) NOT NULL
);