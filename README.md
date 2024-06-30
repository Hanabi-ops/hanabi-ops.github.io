<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Monthly Expense Tracker</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Monthly Expense Tracker</h1>
    
    <form id="expense-form">
        <label for="category">Category:</label>
        <select id="category">
            <option value="food">Food</option>
            <option value="utilities">Utilities</option>
            <option value="travel">Travel</option>
            <option value="other">Other</option>
        </select>

        <label for="description">Description:</label>
        <input type="text" id="description" required>

        <label for="amount">Amount:</label>
        <input type="number" id="amount" step="0.01" required>

        <button type="submit">Add Expense</button>
    </form>

    <h2>Expenses</h2>
    <table>
        <thead>
            <tr>
                <th>Category</th>
                <th>Description</th>
                <th>Amount</th>
            </tr>
        </thead>
        <tbody id="expense-table-body">
        </tbody>
    </table>

    <h2>Totals</h2>
    <div id="totals">
        <p>Food: $<span id="total-food">0.00</span></p>
        <p>Utilities: $<span id="total-utilities">0.00</span></p>
        <p>Travel: $<span id="total-travel">0.00</span></p>
        <p>Other: $<span id="total-other">0.00</span></p>
    </div>

    <script src="script.js"></script>
    <script>
    document.getElementById('expense-form').addEventListener('submit', function(e) {
    e.preventDefault();

    // Get form values
    const category = document.getElementById('category').value;
    const description = document.getElementById('description').value;
    const amount = parseFloat(document.getElementById('amount').value);

    // Add expense to the table
    const tableBody = document.getElementById('expense-table-body');
    const newRow = tableBody.insertRow();
    newRow.innerHTML = `
        <td>${category}</td>
        <td>${description}</td>
        <td>$${amount.toFixed(2)}</td>
    `;

    // Update totals
    updateTotals(category, amount);

    // Clear form
    document.getElementById('expense-form').reset();
    });

    function updateTotals(category, amount) {
    const totalElement = document.getElementById(`total-${category}`);
    const currentTotal = parseFloat(totalElement.innerText);
    const newTotal = currentTotal + amount;
    totalElement.innerText = newTotal.toFixed(2);
    }
    </script>
</body {
    font-family: Arial, sans-serif;
    background-color: #f9f9f9;
    color: #333;
    padding: 20px;
}

h1, h2 {
    text-align: center;
}

form {
    display: flex;
    flex-direction: column;
    max-width: 400px;
    margin: 0 auto 20px auto;
    background-color: #fff;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

label {
    margin-top: 10px;
}

input, select, button {
    padding: 10px;
    margin-top: 5px;
}

button {
    background-color: #007bff;
    color: white;
    border: none;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
}

th, td {
    padding: 10px;
    border: 1px solid #ddd;
}

th {
    background-color: #f2f2f2;
}

#totals {
    max-width: 400px;
    margin: 0 auto;
    background-color: #fff;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
>
</html>
