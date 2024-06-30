<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Monthly Expense Tracker</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Monthly Expense Tracker</h1>
        <form id="passwordForm">
            <label for="password">Enter Password:</label>
            <input type="password" id="password" name="password" required>
            <button type="submit">Submit</button>
        </form>
        <div id="expenses" style="display: none;">
            <h2>Expense Categories</h2>
            <div id="food" class="category">
                <h3>Food</h3>
                <ul id="foodList"></ul>
                <p>Total: <span id="foodTotal">0</span></p>
            </div>
            <div id="utilities" class="category">
                <h3>Utilities</h3>
                <ul id="utilitiesList"></ul>
                <p>Total: <span id="utilitiesTotal">0</span></p>
            </div>
            <div id="travel" class="category">
                <h3>Travel</h3>
                <ul id="travelList"></ul>
                <p>Total: <span id="travelTotal">0</span></p>
            </div>
            <div id="other" class="category">
                <h3>Other</h3>
                <ul id="otherList"></ul>
                <p>Total: <span id="otherTotal">0</span></p>
            </div>
        </div>
    </div>
<script>
document.getElementById("passwordForm").addEventListener("submit", function(event) {
    event.preventDefault();
    const password = document.getElementById("password").value;
    if (password === "6969") {
        document.getElementById("passwordForm").style.display = "none";
        document.getElementById("expenses").style.display = "block";
        // You can add further JavaScript functionality here to handle expense tracking
    } else {
        alert("Incorrect password. Please try again.");
    }
});
</script>
    <script src="script.js"></script>
</body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
}

.container {
    max-width: 800px;
    margin: 20px auto;
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1, h2, h3 {
    text-align: center;
}

form {
    text-align: center;
}

form input[type="password"] {
    padding: 10px;
    font-size: 16px;
    border-radius: 4px;
    border: 1px solid #ccc;
}

form button {
    padding: 10px 20px;
    font-size: 16px;
    border-radius: 4px;
    background-color: #4CAF50;
    color: white;
    border: none;
    cursor: pointer;
}

.category {
    margin-top: 20px;
    border: 1px solid #ccc;
    padding: 10px;
    border-radius: 8px;
}

ul {
    list-style-type: none;
    padding: 0;
}

ul li {
    margin-bottom: 5px;
}

.category p {
    font-weight: bold;
}
>
</html>
