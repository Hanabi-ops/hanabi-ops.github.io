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
        <form id="passwordForm">
            <label for="password">Enter Password:</label>
            <input type="password" id="password" name="password" required>
            <button type="submit">Enter</button>
        </form>
        <div id="expenseTracker" class="hidden">
            <!-- Expense tracking form and summary will go here -->
        </div>
    </div>
    <div id="expenseTracker" class="hidden">
    <form id="expenseForm">
        <label for="date">Date:</label>
        <input type="date" id="date" name="date" required><br><br>

        <label for="category">Category:</label>
        <select id="category" name="category" required>
            <option value="food">Food</option>
            <option value="utilities">Utilities</option>
            <option value="travel">Travel</option>
            <option value="other">Other</option>
        </select><br><br>

        <label for="amount">Amount:</label>
        <input type="number" id="amount" name="amount" min="0" step="0.01" required><br><br>

        <label for="description">Description:</label>
        <textarea id="description" name="description"></textarea><br><br>

        <button type="submit">Add Expense</button>
    </form>

    <div id="expenseList">
        <!-- Display added expenses here -->
    </div>

    <div id="expenseSummary">
        <!-- Display total expenses here -->
    </div>
</div>


    <script src="script.js"></script>
<script>
// Password validation
const passwordForm = document.getElementById('passwordForm');
const passwordInput = document.getElementById('password');
const expenseTracker = document.getElementById('expenseTracker');

passwordForm.addEventListener('submit', function(event) {
    event.preventDefault();
    const password = passwordInput.value.trim();
    if (password === '6969') {
        passwordForm.style.display = 'none';
        expenseTracker.classList.remove('hidden');
    } else {
        alert('Incorrect password. Please try again.');
    }
});

// Expense tracking
// You can implement further JavaScript for tracking expenses and displaying summaries.
// Use localStorage or sessionStorage to store expenses and retrieve them.

// Example: Adding an expense
function addExpense(category, amount, description) {
    // Implement logic to add expense to storage and update UI
}

// Example: Displaying total expenses by category
function displayTotalExpenses() {
    // Implement logic to calculate and display total expenses in tabular form
}
    // Expense tracking
let expenses = [];

// Function to add an expense
function addExpense(date, category, amount, description) {
    expenses.push({ date, category, amount, description });
    updateExpenseList();
    updateExpenseSummary();
}

// Function to update the expense list display
function updateExpenseList() {
    const expenseListDiv = document.getElementById('expenseList');
    expenseListDiv.innerHTML = '';

    expenses.forEach((expense, index) => {
        const expenseItem = document.createElement('div');
        expenseItem.classList.add('expense-item');
        expenseItem.innerHTML = `
            <p><strong>Date:</strong> ${expense.date}</p>
            <p><strong>Category:</strong> ${expense.category}</p>
            <p><strong>Amount:</strong> $${expense.amount}</p>
            <p><strong>Description:</strong> ${expense.description}</p>
            <button class="delete-button" onclick="deleteExpense(${index})">Delete</button>
        `;
        expenseListDiv.appendChild(expenseItem);
    });
}

// Function to delete an expense
function deleteExpense(index) {
    expenses.splice(index, 1);
    updateExpenseList();
    updateExpenseSummary();
}

// Example: Displaying total expenses by category
function updateExpenseSummary() {
    const summaryDiv = document.getElementById('expenseSummary');
    const categories = ['food', 'utilities', 'travel', 'other'];
    const totalExpenses = {};

    // Initialize total expenses for each category
    categories.forEach(category => {
        totalExpenses[category] = 0;
    });

    // Calculate total expenses
    expenses.forEach(expense => {
        totalExpenses[expense.category] += parseFloat(expense.amount);
    });

    // Display total expenses in tabular form
    let summaryHTML = '<h3>Total Expenses</h3>';
    summaryHTML += '<table>';
    summaryHTML += '<tr><th>Category</th><th>Total Amount</th></tr>';

    categories.forEach(category => {
        summaryHTML += `<tr><td>${category}</td><td>$${totalExpenses[category].toFixed(2)}</td></tr>`;
    });

    summaryHTML += '</table>';
    summaryDiv.innerHTML = summaryHTML;
}

// Event listener for expense form submission
const expenseForm = document.getElementById('expenseForm');
expenseForm.addEventListener('submit', function(event) {
    event.preventDefault();
    const date = document.getElementById('date').value;
    const category = document.getElementById('category').value;
    const amount = document.getElementById('amount').value;
    const description = document.getElementById('description').value;
    addExpense(date, category, amount, description);

    // Clear form inputs after submission
    expenseForm.reset();
});

// Display the expense tracker section after password validation
const passwordForm = document.getElementById('passwordForm');
const expenseTracker = document.getElementById('expenseTracker');

passwordForm.addEventListener('submit', function(event) {
    event.preventDefault();
    const password = document.getElementById('password').value.trim();
    if (password === '6969') {
        passwordForm.style.display = 'none';
        expenseTracker.classList.remove('hidden');
    } else {
        alert('Incorrect password. Please try again.');
    }
});

</script>
<div id="expenseTracker" class="hidden">
    <form id="expenseForm">
        <label for="date">Date:</label>
        <input type="date" id="date" name="date" required><br><br>

        <label for="category">Category:</label>
        <select id="category" name="category" required>
            <option value="food">Food</option>
            <option value="utilities">Utilities</option>
            <option value="travel">Travel</option>
            <option value="other">Other</option>
        </select><br><br>

        <label for="amount">Amount:</label>
        <input type="number" id="amount" name="amount" min="0" step="0.01" required><br><br>

        <label for="description">Description:</label>
        <textarea id="description" name="description"></textarea><br><br>

        <button type="submit">Add Expense</button>
    </form>

    <div id="expenseSummary">
        <!-- Display total expenses here -->
    </div>
</div>

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
    text-align: center;
}

form {
    margin-bottom: 20px;
}

form label, form input, form button {
    margin: 5px;
}

.hidden {
    display: none;
}
.expense-item {
    border: 1px solid #ccc;
    padding: 10px;
    margin-bottom: 10px;
}

.delete-button {
    margin-top: 5px;
    background-color: #f44336;
    color: white;
    border: none;
    padding: 5px 10px;
    cursor: pointer;
    border-radius: 3px;
}

.delete-button:hover {
    background-color: #d32f2f;
}
>
</html>
