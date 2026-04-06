LOGIN PAGE.HTML

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


REGISTER.HTML

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


DASHBOARD

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Green Commute Planner</title>

<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css"/>
<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

<style>

body{
font-family:Arial;
background:#f4f4f4;
margin:0;
}

/* NAVBAR */

.navbar{
background:#2e7d32;
color:white;
padding:12px 20px;
display:flex;
justify-content:space-between;
}

.navbar a{
color:white;
text-decoration:none;
margin-left:15px;
}

/* MAIN */

.container{
max-width:900px;
margin:30px auto;
padding:10px;
}

h2{
color:#2e7d32;
}

/* DASHBOARD BOXES */

.stats-row{
display:flex;
gap:15px;
margin-bottom:20px;
}

.stat-box{
background:white;
padding:20px;
border-radius:8px;
flex:1;
text-align:center;
box-shadow:0 3px 8px rgba(0,0,0,0.1);
}

.stat-box h3{
margin:0;
color:#2e7d32;
font-size:24px;
}

/* ROUTE BOX */

.search-box{
background:white;
border:1px solid #ccc;
border-radius:6px;
padding:20px;
}

/* INPUT ROW */

.search-row{
display:flex;
gap:10px;
margin-bottom:10px;
}

.search-row input{
flex:1;
padding:8px;
border:1px solid #ccc;
border-radius:4px;
}

.search-row button{
background:#2e7d32;
color:white;
border:none;
padding:8px 18px;
border-radius:4px;
cursor:pointer;
}

/* MAP */

#map{
height:400px;
margin-top:20px;
border-radius:6px;
}

/* RESULT */

#resultBox{
margin-top:15px;
padding:15px;
background:#e8f5e9;
border-left:5px solid #2e7d32;
display:none;
font-size:16px;
}

/* POPUP */

.popup{
position:fixed;
top:50%;
left:50%;
transform:translate(-50%,-50%);
background:white;
padding:20px;
border-radius:10px;
box-shadow:0 0 15px rgba(0,0,0,0.3);
display:none;
width:300px;
z-index:1000;
}

.mode-card{
padding:10px;
margin:10px 0;
border:1px solid #ddd;
border-radius:6px;
cursor:pointer;
}

.mode-card:hover{
background:#e8f5e9;
}

/* HISTORY TABLE */

table{
width:100%;
margin-top:20px;
border-collapse:collapse;
background:white;
}

th,td{
padding:10px;
border-bottom:1px solid #ddd;
}

th{
background:#2e7d32;
color:white;
}

</style>
</head>

<body>

<div class="navbar">
<h3>Green Commute Planner</h3>

<div>
<a href="#">Dashboard</a>
<a href="#">History</a>
<a href="#">Profile</a>
<a href="login.html" onclick="localStorage.removeItem('gcp_current_user')">Logout</a>
</div>
</div>

<div class="container">

<h2>Dashboard</h2>

<div class="stats-row">

<div class="stat-box">
<h3 id="totalTrips">0</h3>
<p> Total Trips</p>
</div>

<div class="stat-box">
<h3 id="co2Saved">0 kg</h3>
<p> CO₂ Saved</p>
</div>

<div class="stat-box">
<h3 id="ecoTrips">0</h3>
<p> Eco Trips</p>
</div>

<div class="stat-box">
<h3 id="moneySpent">₹0</h3>
<p> Money Spent</p>
</div>

</div>

<div class="search-box">

<h3>Plan Your Route</h3>

<div class="search-row">
<input id="from" placeholder="From (example: Kukatpally Hyderabad)">
<input id="to" placeholder="To (example: Banjara Hills Hyderabad)">
<button onclick="findRoute()">Find Route</button>
</div>

<div id="map"></div>

<div id="resultBox"></div>

</div>

<h3>Recent Trips</h3>

<table>
<thead>
<tr>
<th>From</th>
<th>To</th>
<th>Mode</th>
<th>CO₂ Saved</th>
<th>Cost</th>
<th>Date</th>
</tr>
</thead>
<tbody id="tripTable"></tbody>
</table>

</div>

<!-- MODE POPUP -->

<div id="modePopup" class="popup">

<h3>Select Transport Mode</h3>

<div id="modeOptions"></div>

<button onclick="closePopup()">Cancel</button>

</div>

<script>

/* CURRENT USER */

const currentUser = localStorage.getItem("gcp_current_user");

if(!currentUser){
window.location.href="login.html";
}

/* USER-SPECIFIC STORAGE */

const tripKey = "gcp_trips_" + currentUser;

/* MAP */

var map = L.map('map').setView([17.385044,78.486671],12);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',{
attribution:'©️ OpenStreetMap'
}).addTo(map);

var routeLayer;

/* FIND ROUTE */

async function findRoute(){

var from=document.getElementById("from").value;
var to=document.getElementById("to").value;

if(from==""||to==""){
alert("Enter locations");
return;
}

/* GEOCODE */

var geo1=await fetch(`https://nominatim.openstreetmap.org/search?format=json&q=${from}&limit=1`);
var data1=await geo1.json();

var geo2=await fetch(`https://nominatim.openstreetmap.org/search?format=json&q=${to}&limit=1`);
var data2=await geo2.json();

var start=[data1[0].lon,data1[0].lat];
var end=[data2[0].lon,data2[0].lat];

/* ROUTE */

var apiKey="eyJvcmciOiI1YjNjZTM1OTc4NTExMTAwMDFjZjYyNDgiLCJpZCI6IjRlYThlYjcxMWU2NTQ5NTJhZDk2NWU1NzFkMGIzY2Y4IiwiaCI6Im11cm11cjY0In0=";

var response=await fetch(
"https://api.openrouteservice.org/v2/directions/driving-car/geojson",
{
method:"POST",
headers:{
"Content-Type":"application/json",
"Authorization":apiKey
},
body:JSON.stringify({coordinates:[start,end]})
}
);

var data=await response.json();

var coords=data.features[0].geometry.coordinates;
var latlngs=coords.map(c=>[c[1],c[0]]);

if(routeLayer){
map.removeLayer(routeLayer);
}

routeLayer=L.polyline(latlngs,{color:"green",weight:5}).addTo(map);

map.fitBounds(routeLayer.getBounds());

var distanceKm=data.features[0].properties.summary.distance/1000;

/* CALL BACKEND */

const emissionRes=await fetch("http://localhost:3001/api/emission",{
method:"POST",
headers:{"Content-Type":"application/json"},
body:JSON.stringify({distance:distanceKm})
});

const emissions=await emissionRes.json();

const costRes=await fetch("http://localhost:3001/api/cost",{
method:"POST",
headers:{"Content-Type":"application/json"},
body:JSON.stringify({distance:distanceKm})
});

const costs=await costRes.json();

/* MERGE DATA */

const modes=emissions.map(e=>{

const costRow=costs.find(c=>c.mode===e.mode);

return{
mode:e.mode,
carbon:e.carbon,
saved:e.carbon_saved,
cost:costRow.cost
};

});

/* SHOW POPUP */

const container=document.getElementById("modeOptions");
container.innerHTML="";

modes.forEach(mode=>{

const card=document.createElement("div");

card.className="mode-card";

card.innerHTML=`
<b>${mode.mode}</b><br>
CO₂ Produced: ${mode.carbon} kg<br>
CO₂ Saved: ${mode.saved} kg<br>
Cost: ₹${mode.cost}
`;

card.onclick=()=>selectMode(mode);

container.appendChild(card);

});

document.getElementById("modePopup").style.display="block";

}

/* MODE SELECTED */

function selectMode(mode){

document.getElementById("modePopup").style.display="none";

const resultBox=document.getElementById("resultBox");

resultBox.style.display="block";

resultBox.innerHTML=`
<b>Selected Mode:</b> ${mode.mode}<br>
CO₂ Produced: ${mode.carbon} kg<br>
CO₂ Saved vs Car: ${mode.saved} kg<br>
Cost: ₹${mode.cost}
`;

saveTrip(mode);

}

/* SAVE TRIP */

function saveTrip(mode){

var trips=JSON.parse(localStorage.getItem(tripKey)||"[]");

var trip={
from:document.getElementById("from").value,
to:document.getElementById("to").value,
mode:mode.mode,
co2:parseFloat(mode.saved),
cost:parseFloat(mode.cost),
date:new Date().toLocaleDateString()
};

trips.push(trip);

localStorage.setItem(tripKey,JSON.stringify(trips));

loadDashboard();

}

/* DASHBOARD */

function loadDashboard(){

var trips=JSON.parse(localStorage.getItem(tripKey)||"[]");

var totalTrips=trips.length;
var totalCO2=0;
var ecoTrips=0;
var money=0;

var table="";

trips.slice().reverse().forEach(t=>{

totalCO2+=Number(t.co2)||0;
money+=Number(t.cost)||0;

if(t.mode!="Car"){
ecoTrips++;
}

table+=`
<tr>
<td>${t.from}</td>
<td>${t.to}</td>
<td>${t.mode}</td>
<td>${t.co2}</td>
<td>₹${t.cost}</td>
<td>${t.date}</td>
</tr>
`;

});

document.getElementById("totalTrips").innerText=totalTrips;
document.getElementById("co2Saved").innerText=totalCO2.toFixed(2)+" kg";
document.getElementById("ecoTrips").innerText=ecoTrips;
document.getElementById("moneySpent").innerText="₹"+money.toFixed(2);

document.getElementById("tripTable").innerHTML=table;

}

window.onload=loadDashboard;

function closePopup(){
document.getElementById("modePopup").style.display="none";
}

</script>

</body>
</html>

