# Node.js TypeORM and Database Relations

Node.js fundamentals challenge applied for the GoStack Bootcamp

## :rocket: About the challenge

In this challenge, I will be creating a new application to learn new things and train what I have learned so far in Node.js alongside TypeScript, including using a database with TypeORM, and ManyToMany relationships!

This will be an application that should allow the creation of customers, products and orders, where the customer can generate new purchase orders for certain products, such as a small e-commerce.

## :hammer: Do you want to check it out?

- ### **Prerequisites**

  - It's **necessary** to have **[Node.js](https://nodejs.org/en/)** installed on the computer
  - It's **necessary** to have **[Git](https://git-scm.com/)** installed and configured on the computer
  - Also, it's **necessary** to have a package manager either **[NPM](https://www.npmjs.com/)** or **[Yarn](https://yarnpkg.com/)**.
  - Finally, it is **essential** to have **[Docker](https://www.docker.com/)** installed to run database Postgres.
  
 
Creating database Postgres:

```sh
  $ docker run --name gostack_desafio09 -e POSTGRES_PASSWORD=docker -p 5432:5432 -d postgres
  $ docker run --name gostack_desafio09_tests -e POSTGRES_PASSWORD=docker -p 5432:5432 -d postgres
``` 

Clone the repository:

```sh
  $ git clone https://github.com/paulo-carvalho93/desafio-typeorm-relations-nodejs.git
```

```sh
  $ desafio-typeorm-relations-nodejs
  # Installing project dependencies
  $ yarn # or npm install
  
  # Running unit tests
  $ yarn test # or npm test

  # Start API
  $ yarn dev:server # or npm dev:server

```

## POST - http://localhost:3333/customers
```sh
{
	"name": "Paulo Carvalho",
	"email": "paulo@gmail.com"
}

```

## POST - http://localhost:3333/products
```sh
{
	"name": "Capacete",
	"price": 80.00,
	"quantity": 9
}
```

## POST - http://localhost:3333/orders
```sh
{
	"customer_id": "dd292423-8cb5-4c5f-b6cd-080ede4a5b5e",
	"products": [
		{
			"id": "50abd039-cbff-466e-83d8-55fa3183329f",
			"quantity": 5
		}
	]
}

```

## GET - http://localhost:3333/orders/:id
```sh
{
  "id": "4aaf7163-ec91-4ae9-bf69-1807b24792fd",
  "created_at": "2020-12-12T23:09:48.119Z",
  "updated_at": "2020-12-12T23:09:48.119Z",
  "order_products": [
    {
      "id": "2a090b0e-5e57-4618-8b3d-b0eba95b3964",
      "product_id": "50abd039-cbff-466e-83d8-55fa3183329f",
      "order_id": "4aaf7163-ec91-4ae9-bf69-1807b24792fd",
      "price": "80.00",
      "quantity": 5,
      "created_at": "2020-12-12T23:09:48.119Z",
      "updated_at": "2020-12-12T23:09:48.119Z"
    }
  ],
  "customer": {
    "id": "dd292423-8cb5-4c5f-b6cd-080ede4a5b5e",
    "name": "Paulo Carvalho",
    "email": "paulo@gmail.com",
    "created_at": "2020-12-12T21:56:13.846Z",
    "updated_at": "2020-12-12T21:56:13.846Z"
  }
}
```


