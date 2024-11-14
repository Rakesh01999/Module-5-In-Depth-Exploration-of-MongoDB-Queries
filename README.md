# MongoDB Setup and Basic Commands

## 5-1-A Install MongoDB Compass & No SQL Booster (Windows)
1. **Download MongoDB Community Server**: Search "MongoDB Community Server Download" on Google and install it.
2. **MongoDB Compass**: After installation, open MongoDB Compass, add a new collection and click on `localhost` to connect.
3. **MongoDB Shell Setup**:
    - Open MongoDB shell via Compass.
    - **Error Fix**: If MongoDB service doesn’t start automatically, go to **Services** > find **MongoDB service** > set it to **Automatic** and **Start** if it’s stopped.
4. **Using MongoDB Shell**:
    ```shell
    test > show dbs
    use practice
    db.getCollection("test").insertOne({name: "Next Level Web Dev"})
    db.getCollection("test").find()
    ```
5. **Install MongoDB Shell for Command Line Use**:
    - Download MongoDB Shell (msi package) and add the path to environment variables.
    - Verify with `mongod --version` in cmd.

6. **NoSQLBooster Installation**:
    - Open NoSQLBooster, connect using `localhost`, and test the connection.

---

## 5-1-B Install MongoDB Compass & No SQL Booster (Mac & Linux)
(Steps similar to Windows)

---

## Basic MongoDB Operations

### Insert, find, and Field Filtering

- **Examples**:
    ```javascript
    db.test.findOne({age: 17})
    db.test.find({ gender: "Male" }, { name: 1, age: 1, gender: 1, email: 1 })
    ```

### Comparison Operators
- **Examples**:
    ```javascript
    db.test.find({ gender: { $eq: "Male" } })
    db.test.find({ age: { $gt: 12 } })
    ```

### Logical Operators
- **Examples**:
    ```javascript
    db.test.find({
        $and: [
            { age: { $ne: 15 } },
            { age: { $lt: 30 } }
        ]
    }).sort({ age: 1 })
    ```

### Array Operators
- **Examples**:
    ```javascript
    db.test.find({ interests: { $all: ["Gardening", "Gaming", "Cooking"] } })
    db.test.find({
        skills: { $elemMatch: { name: "JAVASCRIPT", level: "Intermediate" }}
    })
    ```

---

## Update Operators

### `$set`, `$addToSet`, `$push`
- **Examples**:
    ```javascript
    db.test.updateOne({ _id: ObjectId("...") }, { $set: { age: 23 } })
    db.test.updateOne({ _id: ObjectId("...") }, { $addToSet: { interests: { $each: ["Reading", "Driving"] }} })
    ```

---

## Deleting Documents and Dropping Collections
- **Examples**:
    ```javascript
    db.test.deleteOne({ _id: ObjectId("...") })
    db.createCollection("posts")
    db.posts.drop({ writeConcern: { w: 1 } })
    ```

---

## Practice Data and Task Link
- Practice Data: [practice-data.json](https://github.com/Apollo-Level2-Web-Dev/mongodb-practice/blob/main/practice-data.json)
- Task Link: [Task](https://drive.google.com/file/d/1Be22y-R8C8SIMg_FOfYm8toz0swpocTT/view?usp=sharing)

---

Happy Coding!
