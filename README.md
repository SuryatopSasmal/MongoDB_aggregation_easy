# MongoDB_aggregation_easy
</br>
MongoDB server installed and running.</br>
mongosh (recommended) or the legacy mongo shell installed.</br>
</br>
Setup: Sample Data</br>
Open your mongosh or mongo shell.</br>
Switch to a new database (or an existing test database):</br>
<pre>use aggregationAssignmentDB</pre>
Insert the following sample data into a collection named products:</br>
<img src="https://github.com/user-attachments/assets/a932e128-2f0f-4b57-a6ae-7d9e317558aa">
<pre>
  To see the data enter is correct or not:
  db.products.find().pretty()</pre>
  
# Easy Difficulty
**1. List All Products in the "Electronics" Category:**

- **Task:** Write an aggregation query to find all documents where the `category` is "Electronics".
- **Hint:** Use the `$match` stage.
- **Expected Output (structure, `_id` will vary):**
<pre>
db.products.aggregate([
{
$match: {
	category: "Electronics"
	}
}
])
</pre>
![image](https://github.com/user-attachments/assets/8bb45ea7-339b-4301-919c-553017a0d721)
</br>
**2. Count Products per Category:**</br>

- **Task:** Write an aggregation query to count how many products belong to each `category`.</br>
- **Hint:** Use the `$group` stage with the `$sum` accumulator.</br>
- **Expected Output (order might vary):**</br>
<pre>
  db.products.aggregate([
  {
    $group: {
      _id: "$category",
      count: { $sum: 1 }
    }
  },
])
</pre>
![image](https://github.com/user-attachments/assets/7a962aff-a4e0-44ad-a0e0-b03c08149136)
![image](https://github.com/user-attachments/assets/1a706cac-54bc-43db-a245-17c1745dbee3)
**3. Product Names and Prices, Sorted by Price (Descending):**

- **Task:** Write an aggregation query to display only the `name` and `price` of each product, sorted by `price` from highest to lowest. Do not include the `_id` field.
- **Hint:** Use `$project` and `$sort`.
- **Expected Output:**
<pre>
  db.products.aggregate([
  {
    $project: {
      _id: 0,
      name: 1,
      price: 1
    }
  },
  {
    $sort: {
      price: -1
    }
  }
]);
</pre>
![image](https://github.com/user-attachments/assets/39e83f32-d817-43f6-861e-95143353dd6e)
![image](https://github.com/user-attachments/assets/df7978f6-7cb9-4e11-b9ef-cf00566efa18)

