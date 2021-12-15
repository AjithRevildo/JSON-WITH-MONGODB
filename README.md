# JSON-WITH-MONGODB
connect product.json in mongodb and perform some mongo db commands


//open mongodb and type 

//mongodb://localhost:27017

//press connect

//press create database ....give the database name as sample data base and name collection as sample..press createdatabase database

//database is created and shows sample in collection click the collection and click addfiles =import =json(from local)

//product.json file attached in this repositories..


//finally database data is created

//NEXT= programfiles=>mongodb=>server=>bin=>type cmd on the bin path its open the command prompt ....type show database..its shows the database....type use sample...its uses the created database sample ...then executed the following command..


//
1.Find all the information about each products

db.sample.find({}).pretty()

2.Find the product price which are between 400 to 800

db.sample.find({product_price:{$gte:400,$lte:800}}).sort({product_price:1}).pretty()

3.Find the product price which are not between 400 to 600

db.sample.find({product_price:{$not:{$gte:400,$lte:800}}}).sort({product_price:1}).pretty()

4.List the four product which are grater than 500 in price

db.sample.find({product_price:{$gt:500}}).sort({product_price:1}).limit(4).pretty()

5.Find the product name and product material of each products

db.sample.find({},{product_name:1,product_material:1,_id:0}).sort({product_price:1}).pretty()

6.Find the product with a row id of 10

db.sample.find({id:"10"}).pretty()

7.Find only the product name and product material

db.sample.find({},{product_name:1,product_material:1,_id:0}).sort({product_price:1}).pretty()

8.Find all products which contain the value of soft in product material

db.sample.find({product_material:{$eq:"Soft"}}).sort({product_price:1}).pretty()

9.Find products which contain product color indigo and product price 492.00

db.sample.find({ $or: [{ product_color: "indigo" }, { product_price:492 }] }).pretty()

10.Delete the products which product price value are same

db.sample.aggregate([{$group:{_id:{product_price:"$product_price"},count:{$sum:1}}},{$match: {count: 2}}])



