<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Monthly Expense Tracker</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Monthly Expense Tracker</h1>
        <form id="loginForm">
            <label for="password">Enter Password:</label>
            <input type="password" id="password" name="password" required>
            <button type="submit">Login</button>
        </form>
        <div id="expenseForm" style="display: none;">
            <h2>Add Expense</h2>
            <form id="expenseEntry">
                <label for="category">Category:</label>
                <select id="category" name="category" required>
                    <option value="food">Food</option>
                    <option value="utilities">Utilities</option>
                    <option value="travel">Travel</option>
                    <option value="other">Other</option>
                </select><br><br>
                <label for="description">Description:</label>
                <input type="text" id="description" name="description" required><br><br>
                <label for="amount">Amount (INR):</label>
                <input type="number" id="amount" name="amount" min="0" step="0.01" required><br><br>
                <button type="submit">Add Expense</button>
            </form>
        </div>
        <div id="expenseList">
            <!-- Expenses will be displayed here -->
        </div>
    </div>
    <script src="script.js"></script>
<script>
document.getElementById('loginForm').addEventListener('submit', function(event) {
    event.preventDefault();
    var password = document.getElementById('password').value;
    if (password === '6969') {
        document.getElementById('loginForm').style.display = 'none';
        document.getElementById('expenseForm').style.display = 'block';
        showExpenses();
    } else {
        alert('Incorrect password. Please try again.');
    }
});

document.getElementById('expenseEntry').addEventListener('submit', function(event) {
    event.preventDefault();
    var category = document.getElementById('category').value;
    var description = document.getElementById('description').value;
    var amount = parseFloat(document.getElementById('amount').value);

    // You can add further validation if needed

    // Example: Store expenses in localStorage for simplicity
    var expense = {
        category: category,
        description: description,
        amount: amount
    };

    var expenses = JSON.parse(localStorage.getItem('expenses')) || [];
    expenses.push(expense);
    localStorage.setItem('expenses', JSON.stringify(expenses));

    showExpenses();
    document.getElementById('expenseEntry').reset(); // Reset form
});

function showExpenses() {
    var expenses = JSON.parse(localStorage.getItem('expenses')) || [];
    var expenseList = document.getElementById('expenseList');
    expenseList.innerHTML = '';

    expenses.forEach(function(expense) {
        var expenseItem = document.createElement('div');
        expenseItem.className = 'expense-item';
        expenseItem.innerHTML = `
            <p><strong>Category:</strong> ${expense.category}</p>
            <p><strong>Description:</strong> ${expense.description}</p>
            <p><strong>Amount:</strong> INR ${expense.amount}</p>
            <hr>
        `;
        expenseList.appendChild(expenseItem);
    });
}
</script>
</body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    text-align: center;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 600px;
    margin: 0 auto;
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
}

h1, h2 {
    color: #333;
}

form {
    margin-bottom: 20px;
}

label {
    display: block;
    margin-bottom: 8px;
}

input[type="text"],
input[type="password"],
input[type="number"],
select {
    width: calc(100% - 20px);
    padding: 8px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    background-color: #007bff;
    color: #fff;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 4px;
    font-size: 16px;
}

button:hover {
    background-color: #0056b3;
}
>
</html>
