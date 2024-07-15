# **Golang Microservice With Redis**

This directory contains the all files for the **Golang Microservice** built with **Redis**.

## **Requirements**

### **Go**

This project uses Go as it's main language. The version of Go used in this project is 1.22. You can install Go either directly from the [Golang website](https://go.dev/dl) or using [goenv](https://github.com/go-nv/goenv/blob/master/INSTALL.md).

### **Redis**

Redis is used in the project as the primary database. This can be installed either by following [instructions](https://redis.io/docs/latest/operate/oss_and_stack/install/install-redis/) for your operating system, or by using [Docker](https://hub.docker.com/_/redis?_gl=1*zptys*_gcl_au*NzU1MTEwMTUzLjE3MTg1MjU1MDg.*_ga*MTI5NDA3ODc2MS4xNzE4MDk2MDY2*_ga_XJWPQMJYHQ*MTcyMTAyMzI4NC41LjEuMTcyMTAyMzUyMC40MC4wLjA.).

## **Getting Started**

### **Cloning The Repo**

First create a new directory using your terminal with the command

```sh
mkdir go_micro_service
```

Move to the new directory with the command

```sh
cd go_micro_service
```

Then enter

```sh
go mod init go_micro_service

# this command installs all the required dependencies for your project.
go mod tidy
```

You will be ready to go with your project and start modifying it the way you want.

# **API Commands**

## **Getting All Orders**

### **Curl Command**

```sh
curl -sS 127.0.0.1:3000/orders | jq
```

### **Httpie/Postman/Thunder Client e.t.c.**

- Select `GET` in the method.
- Enter `http://127.0.0.1:3000/orders/` in the URL field.
- Click the "Send" button to send the request.

## **Adding An Order**

### **Curl Command**

```sh
curl -X POST -d '{"customer_id":"'$(uuidgen)'","line_items":[{"item_id":"'$(uuidgen)'","quantity":<<5>>,"price":<<2500>>}]}' 127.0.0.1:3000/orders
```

### **Httpie/Postman/Thunder Client e.t.c.**

- Select `POST` from the dropdown menu for the HTTP method.
- Enter `http://127.0.0.1:3000/orders` in the URL field.
- Switch to the `Body` tab.
- Select JSON as the body type.

**Since Httpie/Postman/Thunder Client doesn't directly support shell command execution like `uuidgen`, you need to manually generate UUIDs or use an online UUID generator to create them.
This can apply to Postman and Httpie.**

- Once you have the UUIDs, you can format the JSON data like this:

```json
{
  "customer_id": "generated-uuid-1",
  "line_items": [
    {
      "item_id": "generated-uuid-2",
      "quantity": 5,
      "price": 2500
    }
  ]
}
```

- After entering the JSON data, click the "Send" button to send the request.

## **Getting An Order By ID**

### **Curl Command**

```sh
curl -sS 127.0.0.1:3000/orders/<<enter-order-id>> | jq
```

### **Httpie/Postman/Thunder Client e.t.c.**

- Select `GET` from the dropdown menu for the HTTP method.
- Enter `http://127.0.0.1:3000/orders/<<enter-order-id>>` in the URL field.
- Click "Send" to execute the request.

## **Updating An Order - `ShippedAt` Time**

### **Curl Command**

```sh
curl -X PUT -d '{"status":"shipped"}' -sS "127.0.0.1:3000/orders/<<enter-order-id>>" -v
```

### **Httpie/Postman/Thunder Client e.t.c.**

- Select `PUT` from the dropdown menu for the HTTP method.
- Enter `http://127.0.0.1:3000/orders/<<enter-order-id>>` in the URL field.
- Add `Content-Type: application/json` if required by your API.
- Switch to the "Body" tab.
- Select JSON as the body type.
- Enter the JSON data for the request body:

```json
{
  "status": "shipped"
}
```

- After entering the JSON data, click the "Send" button to send the request.

## **Updating An Order - `CompletedAt` Time**

### **Curl Command**

```sh
curl -X PUT -d '{"status":"completed"}' -sS "127.0.0.1:3000/orders/<<enter-order-id>>" -v
```

### **Httpie/Postman/Thunder Client e.t.c.**

- Select `PUT` from the dropdown menu for the HTTP method.
- Enter `http://127.0.0.1:3000/orders/<<enter-order-id>>` in the URL field.
- Add `Content-Type: application/json` if required by your API.
- Switch to the "Body" tab.
- Select JSON as the body type.
- Enter the JSON data for the request body:

```json
{
  "status": "completed"
}
```

- After entering the JSON data, click the "Send" button to send the request.

## **Deleting An Order**

### **Curl Command**

```sh
curl -X DELETE 127.0.0.1:3000/orders/<<enter-order-id>>
```

### **Httpie/Postman/Thunder Client e.t.c.**

- Select `DELETE` from the dropdown menu for the HTTP method.
- Enter `http://127.0.0.1:3000/orders/<<enter-order-id>>` in the URL field.
- Click "Send" to execute the request.

This is the documentation of the API commands from a microservices course by [Dreams Of Code](https://www.youtube.com/@dreamsofcode) on YouTube by [Net Ninja](https://www.youtube.com/@NetNinja).

[Here](https://www.youtube.com/watch?v=wpnN3RIRSxs&list=PL4cUxeGkcC9iImF8w9FbFOc2UntutL9Wv&pp=iAQB) is the playlist to the full course.

This is the [link](https://github.com/dreamsofcode-io/golang-microservice-course-nn) to the GitHub repo of this course for more info.
