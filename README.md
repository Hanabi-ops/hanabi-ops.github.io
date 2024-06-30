<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Expense Tracker</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Expense Tracker</h1>
        
        <!-- Password Input Section -->
        <div id="passwordSection">
            <label for="password">Enter Password:</label>
            <input type="password" id="password" placeholder="Enter password">
            <button onclick="checkPassword()">Submit</button>
        </div>

        <!-- Expense Input Section -->
        <div id="expenseSection" style="display: none;">
            <label for="expenseDate">Date:</label>
            <input type="date" id="expenseDate">

            <label for="expenseCategory">Category:</label>
            <select id="expenseCategory">
                <option value="food">Food</option>
                <option value="utilities">Utilities</option>
                <option value="travel">Travel</option>
                <option value="other">Other</option>
            </select>

            <label for="expenseDescription">Description:</label>
            <input type="text" id="expenseDescription" placeholder="Description (if other)">

            <label for="expenseAmount">Amount:</label>
            <input type="number" id="expenseAmount" placeholder="Amount">

            <button onclick="addExpense()">Add Expense</button>
        </div>

        <!-- Expense Tracking Section -->
        <div id="expenseTableSection" style="display: none;">
            <h2>Expense Summary</h2>
            <label for="viewBy">View by:</label>
            <select id="viewBy">
                <option value="date">Date</option>
                <option value="week">Week</option>
                <option value="month">Month</option>
            </select>

            <table id="expenseTable">
                <thead>
                    <tr>
                        <th>Date</th>
                        <th>Category</th>
                        <th>Description</th>
                        <th>Amount</th>
                    </tr>
                </thead>
                <tbody id="expenseTableBody">
                    <!-- Expense data will be dynamically added here -->
                </tbody>
                <tfoot>
                    <tr>
                        <td colspan="3">Total</td>
                        <td id="totalExpense"></td>
                    </tr>
                </tfoot>
            </table>
        </div>
    </div>

    <script src="script.js"></script>
    <script>
      // Password validation function
function checkPassword() {
    var password = document.getElementById('password').value;
    if (password === "6969") {
        document.getElementById('passwordSection').style.display = 'none';
        document.getElementById('expenseSection').style.display = 'block';
        document.getElementById('expenseTableSection').style.display = 'block';
    } else {
        alert('Incorrect password. Please try again.');
    }
}

// Expense tracking function
function addExpense() {
    var date = document.getElementById('expenseDate').value;
    var category = document.getElementById('expenseCategory').value;
    var description = document.getElementById('expenseDescription').value;
    var amount = document.getElementById('expenseAmount').value;

    var table = document.getElementById('expenseTableBody');
    var newRow = table.insertRow();

    var cellDate = newRow.insertCell(0);
    var cellCategory = newRow.insertCell(1);
    var cellDescription = newRow.insertCell(2);
    var cellAmount = newRow.insertCell(3);

    cellDate.innerText = date;
    cellCategory.innerText = category;
    cellDescription.innerText = description;
    cellAmount.innerText = amount;

    updateTotal();
}

// Update total expense
function updateTotal() {
    var table = document.getElementById('expenseTable');
    var totalCell = document.getElementById('totalExpense');
    var total = 0;

    for (var i = 1; i < table.rows.length - 1; i++) {
        total += parseFloat(table.rows[i].cells[3].innerText);
    }

    totalCell.innerText = total.toFixed(2);
}
  
    </script>
</body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background-color: #fff;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    max-width: 600px;
    width: 100%;
}

h1, h2 {
    text-align: center;
}

label {
    display: block;
    margin-bottom: 5px;
}

input, select, button {
    margin-bottom: 10px;
    padding: 8px;
    width: 100%;
    box-sizing: border-box;
}

button {
    background-color: #4CAF50;
    color: white;
    border: none;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
}

table, th, td {
    border: 1px solid #ddd;
}

th, td {
    padding: 10px;
    text-align: left;
}

tfoot {
    font-weight: bold;
}
>
</html>
