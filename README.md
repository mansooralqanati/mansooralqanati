<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BMI Calculator</title>
    <style>
        /* CSS styles can be placed here */
        body {
            font-family: Arial, sans-serif;
        }
        form {
            margin-bottom: 20px;
        }
        button {
            padding: 8px 16px;
        }
        #result {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>BMI Calculator</h1>
    <form id="bmiForm">
        <label for="weight">Weight (kg):</label>
        <input type="number" id="weight" name="weight" required><br>
        <label for="height">Height (m):</label>
        <input type="number" id="height" name="height" step="0.01" required><br>
        <button type="button" onclick="calculateBMI()">Calculate BMI</button>
    </form>
    <div id="result" style="display: none;">
        <p>Your BMI is: <span id="bmi"></span></p>
        <p>You are in the <span id="category"></span> category.</p>
        <p id="recommendation"></p>
    </div>
    <script>
        function calculateBMI() {
            var weight = parseFloat(document.getElementById("weight").value);
            var height = parseFloat(document.getElementById("height").value);
            var bmi = weight / (height * height);
            var category;
            if (bmi <= 18.5) {
                category = "Underweight";
            } else if (bmi <= 24.9) {
                category = "Healthy weight";
            } else if (bmi <= 29.9) {
                category = "Overweight";
            } else {
                category = "Obese";
            }
            document.getElementById("result").style.display = "block";
            document.getElementById("bmi").innerText = bmi.toFixed(2);
            document.getElementById("category").innerText = category;
            var recommendation = getDietRecommendations(category);
            document.getElementById("recommendation").innerText = recommendation;
        }

        function getDietRecommendations(category) {
            switch (category) {
                case "Underweight":
                    return "Focus on calorie-dense foods such as nuts, seeds, avocados, dairy products, whole grains, lean protein sources like chicken, turkey, fish, eggs, legumes, tofu, and healthy fats like olive oil and fatty fish. Eat smaller, more frequent meals throughout the day.";
                case "Healthy weight":
                    return "Maintain a balanced diet with a variety of fruits, vegetables, lean protein sources, whole grains, and healthy fats. Stay hydrated and limit consumption of processed foods and sugary snacks.";
                case "Overweight":
                    return "Emphasize portion control, include more fruits and vegetables, whole grains, lean protein sources, and healthy fats in your diet. Limit consumption of high-calorie and processed foods, sugary drinks, and snacks.";
                case "Obese":
                    return "Consult with a healthcare professional or dietitian to create a personalized plan for weight management. Focus on reducing calorie intake, increasing physical activity, and making long-term lifestyle changes.";
            }
        }
    </script>
</body>
</html>
