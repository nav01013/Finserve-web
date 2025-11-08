# Finserve-web
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>FinServe - Investment & Calculators</title>
<style>
  :root {
    --primary: #2a9d8f;
    --secondary: #e9c46a;
    --accent: #f4a261;
    --background: #f0f3f4;
    --text: #264653;
  }
  body {
    font-family: Arial, sans-serif;
    background-color: var(--background);
    margin: 0; padding: 0; color: var(--text);
  }
  header {
    background-color: var(--primary);
    color: white;
    padding: 1rem;
    text-align: center;
  }
  header h1 {
    margin: 0;
    font-weight: 700;
  }
  nav {
    margin-top: 0.5rem;
  }
  nav button {
    background: var(--secondary);
    border: none;
    cursor: pointer;
    font-size: 1rem;
    margin: 0 0.25rem;
    padding: 0.5rem 1rem;
    border-radius: 0.5rem;
    transition: background 0.3s ease;
  }
  nav button:hover {
    background: var(--accent);
  }
  main {
    max-width: 900px;
    margin: 1rem auto;
    padding: 1rem;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  }
  section {
    margin-bottom: 2rem;
  }
  h2 {
    font-weight: 700;
    border-bottom: 3px solid var(--primary);
    padding-bottom: 0.25rem;
    margin-bottom: 1rem;
    display: flex;
    align-items: center;
  }
  h2 span.emoji {
    margin-right: 0.5rem;
  }
  label {
    display: block;
    margin-top: 0.5rem;
    font-weight: 600;
  }
  input, select {
    width: 100%;
    padding: 0.4rem;
    margin-top: 0.25rem;
    font-size: 1rem;
    border: 2px solid var(--primary);
    border-radius: 0.25rem;
  }
  button.calc-btn {
    margin-top: 1rem;
    background: var(--primary);
    color: white;
    border: none;
    padding: 0.7rem 1.5rem;
    font-size: 1.1rem;
    border-radius: 0.5rem;
    cursor: pointer;
  }
  button.calc-btn:hover {
    background: var(--accent);
  }
  #result {
    margin-top: 1rem;
    font-weight: 700;
    font-size: 1.2rem;
    color: var(--secondary);
  }
  .product-list {
    display: grid;
    grid-template-columns: repeat(auto-fit,minmax(280px,1fr));
    gap: 1rem;
  }
  .product-card {
    border: 2px solid var(--primary);
    border-radius: 0.5rem;
    padding: 1rem;
    background-color: #ffffffdd;
    transition: box-shadow 0.3s ease;
  }
  .product-card:hover {
    box-shadow: 0 4px 15px rgba(0,0,0,0.15);
  }
  .product-card h3 {
    margin-top: 0;
    margin-bottom: 0.5rem;
    font-size: 1.2rem;
    color: var(--primary);
  }
  .product-card p {
    font-size: 0.95rem;
  }
  footer {
    text-align: center;
    padding: 1rem;
    background: var(--primary);
    color: white;
    margin-top: 2rem;
  }
</style>
</head>
<body>
<header>
  <h1>FinServe 🌟</h1>
  <nav>
    <button onclick="showSection('calculator')">📊 Calculators</button>
    <button onclick="showSection('products')">💼 Investment Products</button>
    <button onclick="showSection('contact')">📞 Contact / Leads</button>
  </nav>
</header>
<main>
  <section id="calculator" style="display: block;">
    <h2><span class="emoji">🎯</span>Goal Calculator</h2>
    <label for="goalAmount">Goal Amount (₹):</label>
    <input type="number" id="goalAmount" placeholder="Eg: 1000000" />
    <label for="currentSavings">Current Savings (₹):</label>
    <input type="number" id="currentSavings" placeholder="Eg: 50000" />
    <label for="monthlyInvestment">Monthly Investment (₹):</label>
    <input type="number" id="monthlyInvestment" placeholder="Eg: 10000" />
    <label for="expectedReturn">Expected Annual Return (%):</label>
    <input type="number" id="expectedReturn" step="0.01" placeholder="Eg: 12" />
    <label for="timeYears">Time to Goal (Years):</label>
    <input type="number" id="timeYears" placeholder="Eg: 10" />
    <button class="calc-btn" onclick="calculateGoal()">Calculate 🧮</button>
    <div id="result"></div>
  </section>

  <section id="products" style="display:none;">
    <h2><span class="emoji">💼</span>Our Investment Products</h2>
    <div class="product-list">
      <div class="product-card">
        <h3>Mutual Funds</h3>
        <p>Choose from various mutual fund schemes to diversify your portfolio and grow wealth.</p>
      </div>
      <div class="product-card">
        <h3>Stocks & Equities</h3>
        <p>Invest in blue-chip and growth stocks with expert research backing.</p>
      </div>
      <div class="product-card">
        <h3>Fixed Deposits</h3>
        <p>Secure your money with guaranteed returns through bank fixed deposits.</p>
      </div>
      <div class="product-card">
        <h3>Insurance Plans</h3>
        <p>Protect your family with life, health, and general insurance policies.</p>
      </div>
    </div>
  </section>

  <section id="contact" style="display:none;">
    <h2><span class="emoji">📞</span>Contact Us / Get a Callback</h2>
    <p>Contact details and lead generation coming soon!</p>
  </section>
</main>

<footer>© 2025 FinServe. All rights reserved.</footer>

<script>
  function showSection(id) {
    document.querySelectorAll('main section').forEach(sec => {
      sec.style.display = (sec.id === id) ? 'block' : 'none';
    });
  }

  function calculateGoal() {
    const goal = parseFloat(document.getElementById("goalAmount").value);
    const current = parseFloat(document.getElementById("currentSavings").value);
    const monthly = parseFloat(document.getElementById("monthlyInvestment").value);
    const rate = parseFloat(document.getElementById("expectedReturn").value) / 100;
    const years = parseFloat(document.getElementById("timeYears").value);

    if (isNaN(goal) || isNaN(current) || isNaN(monthly) || isNaN(rate) || isNaN(years)) {
      document.getElementById("result").textContent = "Please enter valid numbers in all fields.";
      return;
    }

    const fvCurrent = current * Math.pow(1 + rate, years);
    const fvMonthly = monthly * ((Math.pow(1 + rate/12, years*12) - 1) / (rate/12));
    const total = fvCurrent + fvMonthly;

    if (total >= goal) {
      document.getElementById("result").textContent = `🎉 Your goal of ₹${goal.toLocaleString()} is achievable! Projected value: ₹${total.toFixed(0).toLocaleString()}`;
    } else {
      const shortfall = goal - total;
      document.getElementById("result").textContent = `⚠️ You may fall short by ₹${shortfall.toFixed(0).toLocaleString()}. Consider increasing investments or time.`;
    }
  }
</script>

</body>
</html>