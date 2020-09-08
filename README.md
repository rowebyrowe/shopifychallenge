# shopifychallenge
Winter 2021 Data Science Intern Challenge 

Please complete the following questions, and provide your thought process/work. You can attach your work in a text file, link, etc. on the application page. Please ensure answers are easily visible for reviewers!


Question 1: Given some sample data, write a program to answer the following: click here to access the required data set

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 

There were 17 outliers that were throwing off your AOV. Without the outliers, the average value becomes 723. Now, even this I find suspect. Shop 78 sells a sneaker that retails at $25,725 which I don't find very affordable. Taking that shop out makes the average $302.58, but I feel that I have dropped too much.

What metric would you report for this dataset?

I would use the average of the order order amount divided by the number of shoes ordered. 

What is its value?

That came out to be 387.84. Close to the after dropping average, but without the droppings.

Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

How many orders were shipped by Speedy Express in total?

SELECT count(*) FROM Orders; 196

What is the last name of the employee with the most orders?

SELECT TOP 1 count(*),LastName from Orders as o
INNER JOIN Employees as e ON o.EmployeeID=e.EmployeeID
GROUP BY LastName
ORDER BY count(*) DESC

It was Peacock with 40 orders

What product was ordered the most by customers in Germany?

SELECT top 2 productname,sum(quantity) as total,count(productname) as orders FROM ((Customers 
	Inner join Orders on Customers.customerid = Orders.customerid)
	INNER join OrderDetails on Orders.orderid = OrderDetails.orderid)
	INNER join Products on OrderDetails.productid = Products.productid
where country = 'Germany'
group by productname

I included two here because Boston crab meat had more units ordered but Gorgonzola Telino had one more order.