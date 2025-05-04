<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EMI Calculator 💰</title>
    <style>
        * {
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            margin: 0;
            padding: 20px;
            color: #333;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            padding: 30px;
        }
        
        h1 {
            text-align: center;
            color: #4a6bdf;
            margin-bottom: 30px;
            font-size: 28px;
        }
        
        .input-section {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .input-group {
            flex: 1;
            min-width: 200px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #555;
        }
        
        input[type="number"] {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e0e3e9;
            border-radius: 8px;
            font-size: 16px;
            transition: border-color 0.3s;
        }
        
        input[type="number"]:focus {
            border-color: #4a6bdf;
            outline: none;
        }
        
        .range-container {
            margin-top: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        input[type="range"] {
            flex: 1;
            height: 8px;
            -webkit-appearance: none;
            background: #e0e3e9;
            border-radius: 5px;
        }
        
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 20px;
            height: 20px;
            background: #4a6bdf;
            border-radius: 50%;
            cursor: pointer;
        }
        
        .calculate-btn {
            background-color: #4a6bdf;
            color: white;
            border: none;
            padding: 14px 25px;
            font-size: 16px;
            font-weight: 600;
            border-radius: 8px;
            cursor: pointer;
            display: block;
            margin: 0 auto;
            transition: background-color 0.3s;
        }
        
        .calculate-btn:hover {
            background-color: #3a5ad1;
        }
        
        .results {
            margin-top: 40px;
            display: none;
        }
        
        .results h2 {
            text-align: center;
            color: #4a6bdf;
            margin-bottom: 20px;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid #f0f0f0;
        }
        
        th {
            background-color: #f8f9fd;
            font-weight: 600;
            color: #4a6bdf;
        }
        
        tr:hover {
            background-color: #f8f9fd;
        }
        
        .highlight {
            font-weight: 700;
            color: #4a6bdf;
        }
        
        .emoji {
            font-size: 20px;
            margin-right: 8px;
            vertical-align: middle;
        }
        
        @media (max-width: 600px) {
            .container {
                padding: 20px;
            }
            
            .input-group {
                min-width: 100%;
            }
            
            th, td {
                padding: 10px;
                font-size: 14px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>💰 EMI Calculator 💰</h1>
        
        <div class="input-section">
            <div class="input-group">
                <label for="principal">Loan Amount (Principal) 💵</label>
                <input type="number" id="principal" min="1000" max="10000000" step="1000" value="1000000">
                <div class="range-container">
                    <input type="range" id="principal-range" min="1000" max="10000000" step="1000" value="1000000">
                </div>
            </div>
            
            <div class="input-group">
                <label for="interest">Interest Rate (% p.a.) 📈</label>
                <input type="number" id="interest" min="1" max="30" step="0.1" value="8.5">
                <div class="range-container">
                    <input type="range" id="interest-range" min="1" max="30" step="0.1" value="8.5">
                </div>
            </div>
            
            <div class="input-group">
                <label for="tenure">Loan Tenure (Years) ⏳</label>
                <input type="number" id="tenure" min="1" max="30" step="1" value="10">
                <div class="range-container">
                    <input type="range" id="tenure-range" min="1" max="30" step="1" value="10">
                </div>
            </div>
        </div>
        
        <button class="calculate-btn" onclick="calculateEMI()">Calculate EMI 🧮</button>
        
        <div class="results" id="results">
            <h2>📊 Your EMI Breakdown</h2>
            <table>
                <thead>
                    <tr>
                        <th>Description</th>
                        <th>Amount</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><span class="emoji">🏦</span> Loan Amount</td>
                        <td id="loan-amount"></td>
                    </tr>
                    <tr>
                        <td><span class="emoji">📅</span> Loan Tenure</td>
                        <td id="loan-tenure"></td>
                    </tr>
                    <tr>
                        <td><span class="emoji">💯</span> Interest Rate</td>
                        <td id="interest-rate"></td>
                    </tr>
                    <tr>
                        <td><span class="emoji">💰</span> Monthly EMI</td>
                        <td class="highlight" id="emi"></td>
                    </tr>
                    <tr>
                        <td><span class="emoji">🧾</span> Total Interest</td>
                        <td id="total-interest"></td>
                    </tr>
                    <tr>
                        <td><span class="emoji">💸</span> Total Payment</td>
                        <td class="highlight" id="total-payment"></td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>

    <script>
        // Sync input fields with range sliders
        document.getElementById('principal').addEventListener('input', function() {
            document.getElementById('principal-range').value = this.value;
        });
        
        document.getElementById('principal-range').addEventListener('input', function() {
            document.getElementById('principal').value = this.value;
        });
        
        document.getElementById('interest').addEventListener('input', function() {
            document.getElementById('interest-range').value = this.value;
        });
        
        document.getElementById('interest-range').addEventListener('input', function() {
            document.getElementById('interest').value = this.value;
        });
        
        document.getElementById('tenure').addEventListener('input', function() {
            document.getElementById('tenure-range').value = this.value;
        });
        
        document.getElementById('tenure-range').addEventListener('input', function() {
            document.getElementById('tenure').value = this.value;
        });
        
        // Format currency
        function formatCurrency(amount) {
            return '₹' + amount.toFixed(2).replace(/\d(?=(\d{3})+\.)/g, '$&,');
        }
        
        // Calculate EMI
        function calculateEMI() {
            const principal = parseFloat(document.getElementById('principal').value);
            const interestRate = parseFloat(document.getElementById('interest').value) / 1200; // Monthly interest
            const tenureYears = parseInt(document.getElementById('tenure').value);
            const tenureMonths = tenureYears * 12;
            
            // EMI formula: [P x R x (1+R)^N]/[(1+R)^N-1]
            const emi = principal * interestRate * Math.pow(1 + interestRate, tenureMonths) / 
                         (Math.pow(1 + interestRate, tenureMonths) - 1);
            
            const totalPayment = emi * tenureMonths;
            const totalInterest = totalPayment - principal;
            
            // Display results
            document.getElementById('loan-amount').textContent = formatCurrency(principal);
            document.getElementById('loan-tenure').textContent = tenureYears + ' years (' + tenureMonths + ' months)';
            document.getElementById('interest-rate').textContent = interestRate * 1200 + '% per annum';
            document.getElementById('emi').textContent = formatCurrency(emi);
            document.getElementById('total-interest').textContent = formatCurrency(totalInterest);
            document.getElementById('total-payment').textContent = formatCurrency(totalPayment);
            
            // Show results
            document.getElementById('results').style.display = 'block';
            
            // Smooth scroll to results
            document.getElementById('results').scrollIntoView({ behavior: 'smooth' });
        }
        
        // Calculate on page load
        window.onload = calculateEMI;
    </script>
</body>
</html>
