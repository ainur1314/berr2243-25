# berr2243-25
# Hello MongoDB - Week 1 Exercise

##  Project Overview
This project is part of the **Week 1 Exercise** for setting up a development environment, learning Git workflows, and working with MongoDB in Node.js. The goal is to create a simple Node.js script that connects to MongoDB, inserts a document, and retrieves it.

---

##  Tools & Dependencies
###  Tools Installed:
1. **Visual Studio Code (VS Code)** - Code editor
2. **Node.js & npm** - JavaScript runtime and package manager
3. **MongoDB (Local Instance)** - Database
4. **Git** - Version control system
5. **MongoDB Compass (Optional)** - GUI for MongoDB

###  Dependencies:
- [MongoDB Node.js Driver](https://www.npmjs.com/package/mongodb)

Install dependencies using:
```sh
npm install mongodb
```

---

##  Installation Steps

### 1️ Install Development Tools
- Download and install:
  - [VS Code](https://code.visualstudio.com/)
  - [Node.js](https://nodejs.org/)
  - [MongoDB Community Server](https://www.mongodb.com/docs/manual/administration/install-community/)
  - [Git](https://git-scm.com/)
  
### 2️ Setup Git Repository
```sh
git init
git branch -M main
git remote add origin <your-repository-url>
```

### 3️ Initialize Node.js Project
```sh
npm init -y
```

### 4️ Install MongoDB Driver
```sh
npm install mongodb
```

---

##  Running the Project

### 1️ Ensure MongoDB is Running
- Start MongoDB service:
```sh
mongod
```
- OR, if using Windows Service:
```sh
net start MongoDB
```

### 2️ Run the Node.js Script
```sh
node index.js
```

---

##  index.js Code Example
```javascript
const { MongoClient } = require('mongodb');

async function main() {
    const uri = "mongodb://localhost:27017";
    const client = new MongoClient(uri);

    try {
        await client.connect();
        console.log("Connected to MongoDB!");

        const db = client.db("testDB");
        const collection = db.collection("users");

        await collection.insertOne({ name: "Alice", age: 25 });
        console.log("Document inserted!");

        const result = await collection.findOne({ name: "Alice" });
        console.log("Query result:", result);
    } catch (error) {
        console.error("Error:", error);
    } finally {
        await client.close();
    }
}
main();
```

---
