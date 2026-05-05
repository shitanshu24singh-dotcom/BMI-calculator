<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>BMI Calculator</title>
    <link rel="stylesheet" href="style.css">
    <style>
      body {
          font-family: Arial, sans-serif;
          display: flex;
          justify-content: center;
          align-items: center;
          height: 100vh;
          margin: 0;
          background-color: #f4f4f9;
          }

      .container {
                background: white;
                padding: 2rem;
                border-radius: 8px;
                box-shadow: 0 4px 6px rgba(0,0,0,0.1);
                width: 300px;
                text-align: center;
                } 

      .input-group {
                  margin-bottom: 1rem;
                  text-align: left;
                  }

      input {
          width: 100%;
          padding: 8px;
          margin-top: 5px;
          box-sizing: border-box;
          }

      button {
            width: 100%;
            padding: 10px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            }

      button:hover {
                  background-color: #0056b3;
                  }

      .hidden { display: none; }

      #result-container {
                      margin-top: 20px;
                      padding: 10px;
                      background: #e9ecef;
                      border-radius: 4px;
                      }
    </style>

</head>
<body>
    <div class="container">
        <h1>BMI Calculator</h1>
        <div class="input-group">
            <label for="height">Height (cm)</label>
            <input type="number" id="height" placeholder="Enter height">
        </div>
        <div class="input-group">
            <label for="weight">Weight (kg)</label>
            <input type="number" id="weight" placeholder="Enter weight">
        </div>
        <button id="calculate">Calculate BMI</button>
        <div id="result-container" class="hidden">
            <p id="bmi-value"></p>
            <p id="bmi-category"></p>
        </div>
    </div>
    <script>
    document.getElementById('calculate').addEventListener('click', function() {
    const height = parseFloat(document.getElementById('height').value);
    const weight = parseFloat(document.getElementById('weight').value);
    const resultContainer = document.getElementById('result-container');
    const bmiValueText = document.getElementById('bmi-value');
    const bmiCategoryText = document.getElementById('bmi-category');

    if (height > 0 && weight > 0) {
       
        const bmi = (weight / ((height / 100) ** 2)).toFixed(1);
        
        let category = "";
        if (bmi < 18.5) category = "Underweight";
        else if (bmi < 25) category = "Normal weight";
        else if (bmi < 30) category = "Overweight";
        else category = "Obese";

        bmiValueText.textContent = `Your BMI: ${bmi}`;
        bmiCategoryText.textContent = `Category: ${category}`;
        resultContainer.classList.remove('hidden');
    } else {
        alert("Please enter valid height and weight values.");
    }
});
</script>
</body>
</html>
