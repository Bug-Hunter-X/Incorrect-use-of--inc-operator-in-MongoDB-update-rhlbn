# Incorrect use of $inc operator in MongoDB update
This example demonstrates an uncommon error in MongoDB update operations involving the `$inc` operator.  The `$inc` operator is designed to increment a numerical value by a specified amount.  However, using a string value instead of a number will result in unexpected behavior, often leading to a failure or incorrect update.  The solution demonstrates the correct usage of the operator with a numerical value.

## Bug
The bug lies in the incorrect use of the `$inc` operator in the following MongoDB query:
```javascript
db.collection('myCollection').updateOne( { _id: 1 }, { $inc: { count: '1' } } );
```
The `count` field is incorrectly incremented with a string value.  MongoDB expects a numerical value. 
## Solution
The solution is to provide a numerical value to the `$inc` operator:
```javascript
db.collection('myCollection').updateOne( { _id: 1 }, { $inc: { count: 1 } } );
```