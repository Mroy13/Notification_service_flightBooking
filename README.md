# Notification Service for Flight Booking System

This microservice, `notification_service`, is an integral part of the Flight Booking System. It's responsible for handling notifications to specific users based on messages received from RabbitMQ queues. The service is built using Node.js, Express.js, MySQL for data storage, Sequelize as the ORM, Nodemailer for email functionality, and RabbitMQ for message queue management.

## Tech Stack

- **Node.js**: JavaScript runtime environment for executing code.
- **Express.js**: Web application framework for Node.js, facilitating API creation.
- **MySQL**: Relational database used for persistent data storage.
- **Sequelize**: Promise-based ORM for Node.js that supports multiple databases.
- **Nodemailer**: Node.js module for sending emails.
- **RabbitMQ**: Message queueing system for handling messages from other services.

## Features

### Message Consumption

The `notification_service` listens to RabbitMQ message queues to consume messages originating from other services within the Flight Booking System. These messages contain specific notification needs for users.

### Notification Delivery

Upon receiving messages from the RabbitMQ queue, this service processes the data and uses Nodemailer to send notifications to the intended users based on the message content.


# project Structure_MVC architecture
`src` -> Inside the src folder all the actual source code regarding the project will reside, this will not include any kind of tests. (You might want to make separate tests folder)

Lets take a look inside the `src` folder

 - `config` -> In this folder anything and everything regarding any configurations or setup of a library or module will be done. For example: setting up `dotenv` so that we can use the environment variables anywhere in a cleaner fashion, this is done in the `server-config.js`. One more example can be to setup you logging library that can help you to prepare meaningful logs, so configuration for this library should also be done here. 

 - `routes` -> In the routes folder, we register a route and the corresponding middleware and controllers to it. 

 - `middlewares` -> they are just going to intercept the incoming requests where we can write our validators, authenticators etc. 

 - `controllers` -> they are kind of the last middlewares as post them you call you business layer to execute the budiness logic. In controllers we just receive the incoming requests and data and then pass it to the business layer, and once business layer returns an output, we structure the API response in controllers and send the output. 

 - `repositories` -> this folder contains all the logic using which we interact the DB by writing queries, all the raw queries or ORM queries will go here.

 - `services` -> contains the buiness logic and interacts with repositories for data from the database

 - `utils` -> contains helper methods, error classes etc.

### Setup the project

 - Download this template from github and open it in your favourite text editor. 
 - Go inside the folder path and execute the following command:
  ```
  npm install
  ```
 - In the root directory create a `.env` file and add the following env variables
    ```
        PORT=<port number of your choice>
        MAIL_USERNAME='<enter user name>'
       MAIL_APP_PASSWORD='<enter app pwd>'
    ```
    ex: 
    ```
       PORT=3002
       MAIL_USERNAME=''
       MAIL_APP_PASSWORD=''
    ```
    
- To get message_queue(here RABBITMQ) set-up:
 ```
 RabbitMQ Installation
Follow the official RabbitMQ installation guide to install RabbitMQ on your system.

Then you will get local server of rabbitmq.
```
```
NOTE:
Here rabbitmq(with amqplib) is used to consume message from the message queue.
 ```
 - To run the server execute
 ```
 npm start
 ```