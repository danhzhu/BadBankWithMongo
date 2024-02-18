# Project Title

This project integrate mongoDB in a express based node server

## Table of Contents

- [Project Title](#project-title)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
  - [Usage](#usage)
  - [Contributing](#contributing)
  - [License](#license)
  - [Acknowledgments](#acknowledgments)

## Introduction

In this project, I will set up an Express.js DAL with MongoDB and Docker.

## Getting Started

First, download the starter files Links to an external site.and run npm install from that directory. All code you will run in this activity will be from that directory and the only file you will need to modify will be the dal.js file

use Robo 3T to check the contents of your MongoDB database

### Prerequisites

Step 1: Run Docker

First, run the following command in your terminal:

docker run -p 27017:27017 --name badbank -d mongo
Once it is running, check that it is functioning by navigating to localhost:27017 in a browser. You should see the following:

Note: If you do not complete this activity in one sitting and need to restart your MongoDB Docker container, you may need to remove the previously created “bad bank” container with the command: docker rm /badbank before re-running the command above.

Step 2: Test MongoDB

To verify that the test has been successful, you will need to download Robo 3T Links to an external site., which will allow you to browse your MongoDB database.

You will then be able to interact with your database programmatically by running the same test file as that shown in the video, as follows:

    const MongoClient = require('mongodb').MongoClient;

    const url = 'mongodb://localhost:27017';

 
    // connect to mongo

    MongoClient.connect(url, {useUnifiedTopology: true}, function(err, client) {

    console.log("Connected successfully to server");

    // database Name

    const dbName = 'myproject';

    const db = client.db(dbName);
    
    // new user

    var name = 'user' + Math.floor(Math.random()*10000);

    var email = name + '@mit.edu';

    // insert into customer table

    var collection = db.collection('customers');

    var doc = {name, email};

    collection.insertOne(doc, {w:1}, function(err, result) {

        console.log('Document insert');

    });




    var customers = db

        .collection('customers')

        .find()

        .toArray(function(err, docs) {

            console.log('Collection:',docs);




            // clean up

            client.close();            

    });    


Name the file mongo_test.js and run the node mongo_test.js command in the same directory as the file to test out your Docker MongoDB instance. 

Note: You will need to both initialize a node project in the same folder and run the npm install mongodb command in order to run the file as is.

## Usage

Once you have populated the functions, you should be able to go to your browser and navigate to localhost:3000/account/create/peter/peter@mit.edu/secret. You should receive a JSON response


## License

MIT license.

## Acknowledgments

Dr. Sanchez
