 <!DOCTYPE html>
<html>
<head>
    <title>AI Fertilizer Recommendation System</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: url("https://images.unsplash.com/photo-1500382017468-9049fed747ef") no-repeat center center/cover;
            height: 100vh;
        }

        .container {
            width: 400px;
            margin: 80px auto;
            padding: 30px;
            background: rgba(255,255,255,0.9);
            border-radius: 10px;
            box-shadow: 0px 0px 10px gray;
        }

        h2 {
            text-align: center;
        }

        input, select, button {
            width: 100%;
            padding: 10px;
            margin: 8px 0;
            border-radius: 5px;
            border: 1px solid gray;
        }

        button {
            background-color: green;
            color: white;
            font-weight: bold;
            cursor: pointer;
        }

        button:hover {
            background-color: darkgreen;
        }

        .hidden {
            display: none;
        }

        .result-box {
            text-align: center;
            font-size: 18px;
            font-weight: bold;
        }

        img {
            width: 100%;
            border-radius: 10px;
        }
    </style>
</head>
<body>

<!-- LOGIN PAGE -->
<div class="container" id="loginPage">
    <h2>Login</h2>
    <input type="text" id="username" placeholder="Enter Username" required>
    <input type="password" id="password" placeholder="Enter Password" required>
    <button onclick="login()">Login</button>
</div>

<!-- RECOMMENDATION PAGE -->
<div class="container hidden" id="homePage">
    <h2>Fertilizer Recommendation</h2>

    <label>Select Crop:</label>
    <select id="crop">
        <option>Rice</option>
        <option>Wheat</option>
        <option>Maize</option>
        <option>Sugarcane</option>
        <option>Cotton</option>
        <option>Barley</option>
        <option>Soybean</option>
        <option>Groundnut</option>
        <option>Tomato</option>
        <option>Potato</option>
        <option>Onion</option>
        <option>Chilli</option>
        <option>Carrot</option>
        <option>Peas</option>
        <option>Sunflower</option>
    </select>

    <input type="number" id="nitrogen" placeholder="Nitrogen Level (N)">
    <input type="number" id="phosphorus" placeholder="Phosphorus Level (P)">
    <input type="number" id="potassium" placeholder="Potassium Level (K)">

    <button onclick="recommend()">Get Recommendation</button>
</div>

<!-- RESULT PAGE -->
<div class="container hidden" id="resultPage">
    <h2>Recommended Fertilizer</h2>
    <div class="result-box" id="resultText"></div>
    <br>
    <button onclick="goBack()">Back</button>
</div>

<script>

function login() {
    var user = document.getElementById("username").value;
    var pass = document.getElementById("password").value;

    if(user === "admin" && pass === "1234") {
        document.getElementById("loginPage").classList.add("hidden");
        document.getElementById("homePage").classList.remove("hidden");
    } else {
        alert("Invalid Login!");
    }
}

function recommend() {
    var n = parseInt(document.getElementById("nitrogen").value);
    var p = parseInt(document.getElementById("phosphorus").value);
    var k = parseInt(document.getElementById("potassium").value);
    var crop = document.getElementById("crop").value;

    var fertilizer = "";

    if(n < 50) {
        fertilizer = "Urea (Nitrogen Rich Fertilizer)";
    } else if(p < 50) {
        fertilizer = "DAP (Di-Ammonium Phosphate)";
    } else if(k < 50) {
        fertilizer = "MOP (Muriate of Potash)";
    } else {
        fertilizer = "NPK Balanced Fertilizer";
    }

    document.getElementById("homePage").classList.add("hidden");
    document.getElementById("resultPage").classList.remove("hidden");
    document.getElementById("resultText").innerHTML =
        "Crop: " + crop + "<br><br>Recommended Fertilizer: <br>" + fertilizer;
}

function goBack() {
    document.getElementById("resultPage").classList.add("hidden");
    document.getElementById("homePage").classList.remove("hidden");
}

</script>

</body>
</html>
