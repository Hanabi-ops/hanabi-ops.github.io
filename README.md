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
        <form id="login-form" class="login-form">
            <label for="password">Enter Password:</label>
            <input type="password" id="password" name="password" required>
            <button type="button" onclick="authenticate()">Login</button>
        </form>
        <div id="expense-form" class="expense-form hidden">
            <h2>Enter Your Expenses</h2>
            <label for="food">Food:</label>
            <input type="number" id="food" name="food" min="0" value="0">
            <br>
            <label for="utilities">Utilities:</label>
            <input type="number" id="utilities" name="utilities" min="0" value="0">
            <br>
            <label for="travel">Travel:</label>
            <input type="number" id="travel" name="travel" min="0" value="0">
            <br>
            <label for="other">Other:</label>
            <input type="number" id="other" name="other" min="0" value="0">
            <br>
            <label for="description">Description (optional):</label>
            <textarea id="description" name="description" rows="3"></textarea>
            <br>
            <button type="button" onclick="addExpense()">Add Expense</button>
            <br><br>
            <div id="expenses-summary" class="expenses-summary">
                <h3>Expense Summary</h3>
                <ul>
                    <li>Food: <span id="food-total">0</span></li>
                    <li>Utilities: <span id="utilities-total">0</span></li>
                    <li>Travel: <span id="travel-total">0</span></li>
                    <li>Other: <span id="other-total">0</span></li>
                </ul>
                <p>Total Expenses: <span id="total-expenses">0</span></p>
            </div>
        </div>
    </div>
    <script>
const password = "6969"; // Your password

function authenticate() {
    const passwordInput = document.getElementById("password").value;
    if (passwordInput === password) {
        document.getElementById("login-form").classList.add("hidden");
        document.getElementById("expense-form").classList.remove("hidden");
    } else {
        alert("Incorrect password. Please try again.");
    }
}

let foodTotal = 0;
let utilitiesTotal = 0;
let travelTotal = 0;
let otherTotal = 0;

function addExpense() {
    const food = parseFloat(document.getElementById("food").value);
    const utilities = parseFloat(document.getElementById("utilities").value);
    const travel = parseFloat(document.getElementById("travel").value);
    const other = parseFloat(document.getElementById("other").value);
    const description = document.getElementById("description").value;

    foodTotal += food;
    utilitiesTotal += utilities;
    travelTotal += travel;
    otherTotal += other;

    updateExpenseSummary();
    resetForm();
}

function updateExpenseSummary() {
    document.getElementById("food-total").textContent = foodTotal.toFixed(2);
    document.getElementById("utilities-total").textContent = utilitiesTotal.toFixed(2);
    document.getElementById("travel-total").textContent = travelTotal.toFixed(2);
    document.getElementById("other-total").textContent = otherTotal.toFixed(2);

    const totalExpenses = foodTotal + utilitiesTotal + travelTotal + otherTotal;
    document.getElementById("total-expenses").textContent = totalExpenses.toFixed(2);
}

function resetForm() {
    document.getElementById("food").value = "0";
    document.getElementById("utilities").value = "0";
    document.getElementById("travel").value = "0";
    document.getElementById("other").value = "0";
    document.getElementById("description").value = "";
}
</script>

    <script src="script.js"></script>
</body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 800px;
    margin: 0 auto;
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.login-form {
    margin-bottom: 20px;
}

.expense-form {
    display: none;
}

.hidden {
    display: none;
}

.expenses-summary {
    margin-top: 20px;
    border-top: 1px solid #ddd;
    padding-top: 10px;
}

.expenses-summary ul {
    list-style-type: none;
    padding: 0;
}

.expenses-summary ul li {
    margin-bottom: 5px;
}

button {
    padding: 8px 16px;
    background-color: #4CAF50;
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 4px;
}

button:hover {
    background-color: #45a049;
}

input[type="number"], textarea {
    width: 100%;
    padding: 8px;
    margin-top: 5px;
    margin-bottom: 10px;
    box-sizing: border-box;
}

input[type="password"] {
    padding: 8px;
    margin-right: 10px;
    border-radius: 4px;
    border: 1px solid #ccc;
}

label {
    display: block;
    margin-bottom: 5px;
}
>
</html>

