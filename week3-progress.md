LOGIN PAGE CODE: 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Green Commute Planner</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #e8f5e9;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .login-box {
      background-color: white;
      padding: 30px;
      border-radius: 8px;
      border: 1px solid #ccc;
      width: 320px;
    }

    h2 {
      text-align: center;
      color: #2e7d32;
      margin-bottom: 20px;
    }

    label {
      display: block;
      margin-bottom: 5px;
      font-size: 14px;
      color: #333;
    }

    input {
      width: 100%;
      padding: 9px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 4px;
      font-size: 14px;
      box-sizing: border-box;
    }

    button {
      width: 100%;
      padding: 10px;
      background-color: #2e7d32;
      color: white;
      border: none;
      border-radius: 4px;
      font-size: 14px;
      cursor: pointer;
    }

    button:hover {
      background-color: #1b5e20;
    }

    .register-link {
      text-align: center;
      margin-top: 12px;
      font-size: 13px;
    }

    .register-link a {
      color: #2e7d32;
      text-decoration: none;
    }

    .error {
      color: red;
      font-size: 12px;
      margin-top: -10px;
      margin-bottom: 10px;
      display: none;
    }
  </style>
</head>
<body>

  <div class="login-box">
    <h2>Green Commute Planner</h2>

    <label for="email">Email</label>
    <input type="email" id="email" placeholder="Enter your email" />

    <label for="password">Password</label>
    <input type="password" id="password" placeholder="Enter your password" />

    <p class="error" id="error-msg">Invalid email or password!</p>

    <button onclick="handleLogin()">Login</button>

    <div class="register-link">
      <p>Don't have an account? <a href="register.html">Register</a></p>
    </div>
  </div>

  <script>
    function handleLogin() {
      var email = document.getElementById("email").value;
      var password = document.getElementById("password").value;
      var errorMsg = document.getElementById("error-msg");

      if (email === "" || password === "") {
        errorMsg.innerText = "Please enter email and password!";
        errorMsg.style.display = "block";
        return;
      }

      // Check default demo account
      if (email === "user@gmail.com" && password === "1234") {
        window.location.href = "dashboard.html";
        return;
      }

      // Check registered users from localStorage
      var users = JSON.parse(localStorage.getItem("gcp_users") || "[]");
      var found = false;
      for (var i = 0; i < users.length; i++) {
        if (users[i].email === email && users[i].password === password) {
          found = true;
          break;
        }
      }

      if (found) {
        window.location.href = "dashboard.html";
      } else {
        errorMsg.innerText = "Invalid email or password!";
        errorMsg.style.display = "block";
      }
    }
  </script>

</body>
</html>


REGISTER CODE:
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Green Commute Planner - Register</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #e8f5e9;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .register-box {
      background-color: white;
      padding: 30px;
      border-radius: 8px;
      border: 1px solid #ccc;
      width: 320px;
    }

    h2 {
      text-align: center;
      color: #2e7d32;
      margin-bottom: 20px;
    }

    label {
      display: block;
      margin-bottom: 5px;
      font-size: 14px;
      color: #333;
    }

    input {
      width: 100%;
      padding: 9px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 4px;
      font-size: 14px;
      box-sizing: border-box;
    }

    button {
      width: 100%;
      padding: 10px;
      background-color: #2e7d32;
      color: white;
      border: none;
      border-radius: 4px;
      font-size: 14px;
      cursor: pointer;
    }

    button:hover {
      background-color: #1b5e20;
    }

    .login-link {
      text-align: center;
      margin-top: 12px;
      font-size: 13px;
    }

    .login-link a {
      color: #2e7d32;
      text-decoration: none;
    }

    .error {
      color: red;
      font-size: 12px;
      margin-top: -10px;
      margin-bottom: 10px;
      display: none;
    }

    .success {
      color: green;
      font-size: 12px;
      margin-bottom: 10px;
      display: none;
      text-align: center;
    }
  </style>
</head>
<body>

  <div class="register-box">
    <h2>Create Account</h2>

    <label for="name">Full Name</label>
    <input type="text" id="name" placeholder="Enter your name" />

    <label for="email">Email</label>
    <input type="email" id="email" placeholder="Enter your email" />

    <label for="password">Password</label>
    <input type="password" id="password" placeholder="Enter your password" />

    <label for="confirm">Confirm Password</label>
    <input type="password" id="confirm" placeholder="Re-enter your password" />

    <p class="error" id="error-msg">Something went wrong!</p>
    <p class="success" id="success-msg">Account created! Redirecting...</p>

    <button onclick="handleRegister()">Register</button>

    <div class="login-link">
      <p>Already have an account? <a href="login.html">Login</a></p>
    </div>
  </div>

  <script>
    function handleRegister() {
      var name     = document.getElementById("name").value;
      var email    = document.getElementById("email").value;
      var password = document.getElementById("password").value;
      var confirm  = document.getElementById("confirm").value;
      var errorMsg   = document.getElementById("error-msg");
      var successMsg = document.getElementById("success-msg");

      errorMsg.style.display   = "none";
      successMsg.style.display = "none";

      if (name === "" || email === "" || password === "" || confirm === "") {
        errorMsg.innerText = "Please fill in all fields!";
        errorMsg.style.display = "block";
        return;
      }

      if (password !== confirm) {
        errorMsg.innerText = "Passwords do not match!";
        errorMsg.style.display = "block";
        return;
      }

      // Get existing users from localStorage
      var users = JSON.parse(localStorage.getItem("gcp_users") || "[]");

      // Check if email already registered
      for (var i = 0; i < users.length; i++) {
        if (users[i].email === email) {
          errorMsg.innerText = "This email is already registered!";
          errorMsg.style.display = "block";
          return;
        }
      }

      // Save new user
      users.push({ name: name, email: email, password: password });
      localStorage.setItem("gcp_users", JSON.stringify(users));

      successMsg.style.display = "block";
      setTimeout(function() {
        window.location.href = "login.html";
      }, 1500);
    }
  </script>

</body>
</html>

DASHBOARD CODE:
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Green Commute Planner - Dashboard</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      padding: 0;
    }

    /* Navbar */
    .navbar {
      background-color: #2e7d32;
      color: white;
      padding: 12px 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .navbar h3 {
      margin: 0;
      font-size: 18px;
    }

    .navbar a {
      color: white;
      text-decoration: none;
      margin-left: 16px;
      font-size: 14px;
    }

    .navbar a:hover {
      text-decoration: underline;
    }

    /* Main content */
    .container {
      max-width: 850px;
      margin: 30px auto;
      padding: 0 16px;
    }

    h2 {
      color: #2e7d32;
      margin-bottom: 20px;
    }

    /* Stats row */
    .stats-row {
      display: flex;
      gap: 16px;
      margin-bottom: 24px;
    }

    .stat-box {
      background-color: white;
      border: 1px solid #ccc;
      border-radius: 6px;
      padding: 20px;
      flex: 1;
      text-align: center;
    }

    .stat-box h3 {
      margin: 0 0 6px 0;
      font-size: 28px;
      color: #2e7d32;
    }

    .stat-box p {
      margin: 0;
      font-size: 13px;
      color: #555;
    }

    /* Route search */
    .search-box {
      background-color: white;
      border: 1px solid #ccc;
      border-radius: 6px;
      padding: 20px;
      margin-bottom: 24px;
    }

    .search-box h3 {
      margin-top: 0;
      color: #333;
      font-size: 16px;
    }

    .search-row {
      display: flex;
      gap: 10px;
      margin-bottom: 10px;
    }

    .search-row input {
      flex: 1;
      padding: 9px;
      border: 1px solid #ccc;
      border-radius: 4px;
      font-size: 14px;
    }

    .search-row button {
      padding: 9px 20px;
      background-color: #2e7d32;
      color: white;
      border: none;
      border-radius: 4px;
      font-size: 14px;
      cursor: pointer;
    }

    .search-row button:hover {
      background-color: #1b5e20;
    }

    /* Route results */
    .results {
      display: none;
      margin-top: 16px;
    }

    .route-card {
      border: 1px solid #ccc;
      border-radius: 6px;
      padding: 14px 16px;
      margin-bottom: 10px;
      background-color: #fafafa;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .route-card.eco {
      background-color: #f1f8e9;
      border-color: #a5d6a7;
    }

    .route-card h4 {
      margin: 0 0 4px 0;
      font-size: 15px;
      color: #333;
    }

    .route-card p {
      margin: 0;
      font-size: 12px;
      color: #666;
    }

    .eco-badge {
      background-color: #2e7d32;
      color: white;
      font-size: 11px;
      padding: 3px 8px;
      border-radius: 4px;
    }

    /* Recent trips */
    .trips-box {
      background-color: white;
      border: 1px solid #ccc;
      border-radius: 6px;
      padding: 20px;
    }

    .trips-box h3 {
      margin-top: 0;
      color: #333;
      font-size: 16px;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 13px;
    }

    table th {
      background-color: #2e7d32;
      color: white;
      padding: 8px 10px;
      text-align: left;
    }

    table td {
      padding: 8px 10px;
      border-bottom: 1px solid #eee;
    }

    table tr:last-child td {
      border-bottom: none;
    }
  </style>
</head>
<body>

  <!-- Navbar -->
  <div class="navbar">
    <h3>Green Commute Planner</h3>
    <div>
      <a href="dashboard.html">Dashboard</a>
      <a href="history.html">History</a>
      <a href="profile.html">Profile</a>
      <a href="login.html">Logout</a>
    </div>
  </div>

  <!-- Main Content -->
  <div class="container">
    <h2>Dashboard</h2>

    <!-- Stats -->
    <div class="stats-row">
      <div class="stat-box">
        <h3>12</h3>
        <p>Total Trips</p>
      </div>
      <div class="stat-box">
        <h3>8.4 kg</h3>
        <p>CO2 Saved</p>
      </div>
      <div class="stat-box">
        <h3>3</h3>
        <p>Bike Trips</p>
      </div>
      <div class="stat-box">
        <h3>Rs. 240</h3>
        <p>Money Saved</p>
      </div>
    </div>

    <!-- Route Search -->
    <div class="search-box">
      <h3>Plan Your Route</h3>
      <div class="search-row">
        <input type="text" id="from" placeholder="From (e.g. Kukatpally)" />
        <input type="text" id="to" placeholder="To (e.g. Hitech City)" />
        <button onclick="findRoute()">Find Route</button>
      </div>

      <!-- Results -->
      <div class="results" id="results">
        <div class="route-card eco">
          <div>
            <h4>Cycling</h4>
            <p>Time: 30 min &nbsp;|&nbsp; Cost: Rs.0 &nbsp;|&nbsp; CO2: 0 kg</p>
          </div>
          <span class="eco-badge">Eco Friendly</span>
        </div>
        <div class="route-card eco">
          <div>
            <h4>Walking</h4>
            <p>Time: 45 min &nbsp;|&nbsp; Cost: Rs.0 &nbsp;|&nbsp; CO2: 0 kg</p>
          </div>
          <span class="eco-badge">Eco Friendly</span>
        </div>
        <div class="route-card">
          <div>
            <h4>Bus</h4>
            <p>Time: 25 min &nbsp;|&nbsp; Cost: Rs.20 &nbsp;|&nbsp; CO2: 0.08 kg</p>
          </div>
        </div>
        <div class="route-card">
          <div>
            <h4>Car</h4>
            <p>Time: 15 min &nbsp;|&nbsp; Cost: Rs.120 &nbsp;|&nbsp; CO2: 0.17 kg</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Recent Trips -->
    <div class="trips-box">
      <h3>Recent Trips</h3>
      <table>
        <tr>
          <th>From</th>
          <th>To</th>
          <th>Mode</th>
          <th>CO2 Saved</th>
          <th>Date</th>
        </tr>
        <tr>
          <td>Kukatpally</td>
          <td>Hitech City</td>
          <td>Cycling</td>
          <td>0.7 kg</td>
          <td>08 Mar 2026</td>
        </tr>
        <tr>
          <td>Ameerpet</td>
          <td>Begumpet</td>
          <td>Bus</td>
          <td>0.3 kg</td>
          <td>07 Mar 2026</td>
        </tr>
        <tr>
          <td>Miyapur</td>
          <td>Madhapur</td>
          <td>Walking</td>
          <td>1.2 kg</td>
          <td>06 Mar 2026</td>
        </tr>
      </table>
    </div>

  </div>

  <script>
    function findRoute() {
      var from = document.getElementById("from").value;
      var to = document.getElementById("to").value;

      if (from === "" || to === "") {
        alert("Please enter both locations!");
        return;
      }

      document.getElementById("results").style.display = "block";
    }
  </script>

</body>
</html>
