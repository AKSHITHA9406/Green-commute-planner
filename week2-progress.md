## Week 2 Progress – Login Page Implementation

```javascript
import React, { useState } from "react";

function App() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [from, setFrom] = useState("");
  const [to, setTo] = useState("");
  const [showResults, setShowResults] = useState(false);

  const options = [
    { mode: "Bus", time: "25 min", cost: "₹20", co2: "Low", eco: false },
    { mode: "Car", time: "15 min", cost: "₹120", co2: "High", eco: false },
    { mode: "Cycle", time: "30 min", cost: "₹0", co2: "Zero", eco: true }
  ];

  const handleLogin = () => {
    if (email === "user@gmail.com" && password === "1234") {
      setIsLoggedIn(true);
    } else {
      alert("Invalid login. Use user@gmail.com / 1234");
    }
  };

  const handleLogout = () => {
    setIsLoggedIn(false);
    setEmail("");
    setPassword("");
  };

  const handleSearch = () => {
    if (from && to) {
      setShowResults(true);
    } else {
      alert("Enter both locations");
    }
  };

  if (!isLoggedIn) {
    return (
      <div style={{ padding: "40px" }}>
        <h2>Green Commute Planner - Login</h2>

        <input
          type="email"
          placeholder="Email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
        />

        <br /><br />

        <input
          type="password"
          placeholder="Password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
        />

        <br /><br />

        <button onClick={handleLogin}>Login</button>

        <p>Demo: user@gmail.com / 1234</p>
      </div>
    );
  }

  return (
    <div style={{ padding: "40px" }}>
      <h2>Green Commute Planner</h2>

      <button onClick={handleLogout}>Logout</button>

      <br /><br />

      <input
        type="text"
        placeholder="From"
        value={from}
        onChange={(e) => setFrom(e.target.value)}
      />

      <br /><br />

      <input
        type="text"
        placeholder="To"
        value={to}
        onChange={(e) => setTo(e.target.value)}
      />

      <br /><br />

      <button onClick={handleSearch}>Find Route</button>

      {showResults && (
        <div>
          <h3>Available Options</h3>

          {options.map((item, index) => (
            <div key={index}>
              <p>Mode: {item.mode}</p>
              <p>Time: {item.time}</p>
              <p>Cost: {item.cost}</p>
              <p>CO2: {item.co2}</p>
              {item.eco && <p>Recommended Option</p>}
              <hr />
            </div>
          ))}
        </div>
      )}
    </div>
  );
}

export default App;
