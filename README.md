# mathsolver
A website that give detailed answer of math question
<html lang="en">
<head><!DOCTYPE html>

    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Step-by-Step Math Solver</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjs/11.8.0/math.js"></script>
    <style>
        :root {
            --primary-color: #4a90e2;
            --bg-color: #f4f7f6;
            --card-bg: #ffffff;
        }

        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: var(--bg-color); margin: 0; padding: 20px; }
        .container { max-width: 800px; margin: 0 auto; }
        
        /* Ad Space Styling */
        .ad-space {
            background: #e0e0e0;
            border: 2px dashed #bbb;
            text-align: center;
            padding: 20px;
            margin: 20px 0;
            color: #666;
            font-size: 0.9em;
        }

        .solver-card {
            background: var(--card-bg);
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        input[type="text"] {
            width: 100%;
            padding: 15px;
            font-size: 1.2rem;
            border: 2px solid #ddd;
            border-radius: 8px;
            box-sizing: border-box;
            margin-bottom: 15px;
        }

        button {
            background: var(--primary-color);
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1rem;
            border-radius: 8px;
            cursor: pointer;
            transition: background 0.3s;
        }

        button:hover { background: #357abd; }

        .result-section { margin-top: 30px; display: none; }
        .step {
            padding: 10px;
            border-left: 4px solid var(--primary-color);
            background: #f9f9f9;
            margin-bottom: 10px;
            animation: fadeIn 0.5s ease;
        }

        .final-answer {
            font-size: 1.5rem;
            font-weight: bold;
            color: #2c3e50;
            margin-bottom: 20px;
            padding: 15px;
            background: #e8f4fd;
            border-radius: 8px;
        }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    </style>
</head>
<body>

<div class="container">
    <div class="ad-space">
        ADVERTISEMENT: Header Banner (728x90)
    </div>

    <div class="solver-card">
        <h1>Math Solver</h1>
        <p>Enter an equation (e.g., 2 * (3 + 5) / 4 or 2^3 + sqrt(16))</p>
        <input type="text" id="equationInput" placeholder="Enter math here...">
        <button onclick="solveMath()">Solve Steps</button>

        <div id="resultSection" class="result-section">
            <h3>Final Answer:</h3>
            <div id="finalAnswer" class="final-answer"></div>
            
            <h3>Step-by-Step Breakdown:</h3>
            <div id="stepsContainer"></div>
        </div>
    </div>

    <div class="ad-space">
        ADVERTISEMENT: Bottom Content (Responsive)
    </div>
</div>

<script>
    function solveMath() {
        const input = document.getElementById('equationInput').value;
        const stepsContainer = document.getElementById('stepsContainer');
        const finalAnswerDiv = document.getElementById('finalAnswer');
        const resultSection = document.getElementById('resultSection');

        // Clear previous results
        stepsContainer.innerHTML = '';
        
        try {
            // 1. Calculate Final Result
            const result = math.evaluate(input);
            finalAnswerDiv.innerText = result;

            // 2. Generate Simulated Steps
            // Note: For complex algebraic steps, a specialized CAS (Computer Algebra System) 
            // backend like WolframAlpha or Algebrite is usually needed. 
            // This script breaks down a basic arithmetic expression.
            
            let steps = [];
            steps.push(`Analyzing expression: <strong>${input}</strong>`);
            
            if (input.includes('(')) {
                steps.push("Step 1: Identified parentheses. Evaluating inner terms first.");
            }
            
            if (input.match(/[\^*\/]/)) {
                steps.push("Step 2: Applying Order of Operations (PEMDAS/BODMAS). Handling multiplication/division or exponents.");
            }

            steps.push(`Step 3: Simplifying numerical constants...`);
            steps.push(`<strong>Final Detail:</strong> The expression simplifies directly to ${result}.`);

            // Render Steps
            steps.forEach((stepText, index) => {
                const div = document.createElement('div');
                div.className = 'step';
                div.innerHTML = stepText;
                stepsContainer.appendChild(div);
            });

            resultSection.style.display = 'block';

        } catch (error) {
            alert("Invalid Equation. Please check your syntax!");
            resultSection.style.display = 'none';
        }
    }
</script>

</body>
</html>
