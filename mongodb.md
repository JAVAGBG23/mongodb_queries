# MongoDB

use examples

## ONE TO ONE EMBEDDED

db.journals.insertOne({history: ["caugh", "broken arm"]})

db.patients.insertOne({name: "Nisse",age: 45, journal: "6571fa8c37dbe2f2218dd97c"})

db.patients.findOne()

db.journals.findOne({}, {\_id: '6571fa8c37dbe2f2218dd97c'})

db.patients.deleteMany({})

db.patients.insertOne({name: "Nisse",age: 45, journal: {history: ["cough", "broken arm"]}})

db.patients.findOne()

## ONE TO ONE REFERENCES

db.persons.insertOne({name: "Nisse", car: {model: "Volvo", color: "Red", regnr: 12345}})

db.persons.findOne()

db.persons.deleteMany({})

db.persons.insertOne({name: "Nisse", age: 45})

db.cars.insertOne({model: "Volvo", color: "Red", regnr: 12345, owner: "6571ffdb37dbe2f2218dd980"})

## ONE TO MANY EMBEDDED

db.answers.insertMany([{text: "Yes"}, {text: "No"}])

db.questions.insertOne({question: "JavaScript > Java?", answers: ["6572027f37dbe2f2218dd982", "6572027f37dbe2f2218dd983"]})

db.questions.findOne()

db.questions.deleteMany({})

db.questions.insertOne({question: "JavaScript > Java?", answers: [{text: "Yes"}, {text: "No"}]})

db.questions.findOne()

## ONE TO MANY REFERENCES

db.cities.insertOne({name: "New York", coordinates: {lat: 21, lng: 55}})

db.cities.findOne()

db.citizens.insertOne({name: "Nisse Pisse", cityId: "657204d037dbe2f2218dd986"})

db.citizens.findOne()

## MANY TO MANY EMBEDDED

db.products.insertOne({title: "T-shirt", price: 199})

db.products.findOne()

db.customers.insertOne({name: "Janne"})

db.customers.findOne()

db.orders.insertOne({productId: "6572065237dbe2f2218dd988", customerId: "6572066237dbe2f2218dd989"})

db.orders.deleteMany({})

db.customers.updateOne({}, {$set: {orders: [{productId: ObjectId("6572065237dbe2f2218dd988")}]}})

db.customers.findOne()

db.customers.updateOne({}, {$set: {orders: [{title: "T-shirt", price: 199}]}})

db.customers.findOne()

## MANY TO MANY REFERENCES

db.books.insertOne({name: "My Book", author: [{name:"Nisse Pisse"}, {name: "Janne"}]})

db.books.findOne()

db.authors.insertMany([{name: "Nisse Pisse"}, {name: "Janne"}])

db.authors.findMany({})
