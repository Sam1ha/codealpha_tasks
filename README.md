# codealpha_tasks
age calculator 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Age Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0c4;
        }

        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        h1 {
            margin-bottom: 20px;
        }

        .input-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
        }

        input {
            width: 100%;
            padding: 8px;
            box-sizing: border-box;
        }

        button {
            padding: 10px 20px;
            background-color: #007bff;
            color: #a3b4c3;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background-color: #0056b3;
        }

        #result {
            margin-top: 20px;
            font-size: 1.2em;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Age Calculator</h1>
        <div class="input-group">
            <label for="day">Day:</label>
            <input type="number" id="day" min="1" max="31" required>
        </div>
        <div class="input-group">
            <label for="month">Month:</label>
            <input type="number" id="month" min="1" max="12" required>
        </div>
        <div class="input-group">
            <label for="year">Year:</label>
            <input type="number" id="year" min="1900" max="2100" required>
        </div>
        <button onclick="calculateAge()">Calculate Age</button>
        <div id="result"></div>
    </div>
    <script>
        function calculateAge() {
            const day = parseInt(document.getElementById('day').value);
            const month = parseInt(document.getElementById('month').value) - 1; // JavaScript months are 0-11
            const year = parseInt(document.getElementById('year').value);

            // Check if the inputs are valid numbers
            if (isNaN(day) || isNaN(month) || isNaN(year)) {
                document.getElementById('result').innerText = "Please enter a valid date.";
                return;
            }

            // Create a date object with the input values
            const birthDate = new Date(year, month, day);

            // Check if the birthDate is valid
            if (birthDate.getFullYear() !== year || birthDate.getMonth() !== month || birthDate.getDate() !== day) {
                document.getElementById('result').innerText = "Please enter a valid date.";
                return;
            }

            const today = new Date();
            let age = today.getFullYear() - birthDate.getFullYear();
            const m = today.getMonth() - birthDate.getMonth();

            if (m < 0 || (m === 0 && today.getDate() < birthDate.getDate())) {
                age--;
            }

            document.getElementById('result').innerText = `You are ${age} years old.`;
        }
    </script>
</body>
</html>
