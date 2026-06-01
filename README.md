<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galaxy Guitar Jam</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="stars"></div>

<!-- Welcome Page -->
<div id="welcomePage" class="container">
    <h1>🌌 Welcome to Our Guitar Jam 🌌</h1>

    <input type="text" id="userName" placeholder="Enter Your Name">

    <button onclick="continueToStart()">
        Continue
    </button>
</div>

<!-- Start Page -->
<div id="startPage" class="container hidden">
    <h1 id="welcomeText"></h1>

    <button class="floating-btn" onclick="startVideo()">
        🎸 Get Started
    </button>
</div>

<!-- Video Page -->
<div id="videoPage" class="container hidden">

    <video id="jamVideo" controls>
        <source src="guitar-jam.mp4" type="video/mp4">
        Your browser does not support video.
    </video>

</div>

<!-- Thank You Page -->
<div id="thankPage" class="container hidden">
    <h1>✨ Thank You For Watching ✨</h1>
    <p>See you again soon 🌠</p>
</div>

<script src="script.js"></script>

</body>
</html>


*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Arial, sans-serif;
    background:linear-gradient(
    135deg,
    #050816,
    #120c36,
    #1a1a40
    );
    color:white;
    overflow:hidden;
}

.container{
    width:100%;
    height:100vh;

    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;

    text-align:center;
}

.hidden{
    display:none;
}

h1{
    margin-bottom:20px;
}

input{
    width:280px;
    padding:12px;
    border:none;
    border-radius:10px;
    font-size:16px;
    margin-bottom:20px;
}

button{
    padding:12px 25px;
    border:none;
    border-radius:30px;
    cursor:pointer;
    font-size:16px;
}

button:hover{
    transform:scale(1.05);
}

.floating-btn{
    animation:float 2s infinite ease-in-out;
}

@keyframes float{
    0%{
        transform:translateY(0px);
    }

    50%{
        transform:translateY(-10px);
    }

    100%{
        transform:translateY(0px);
    }
}

video{
    width:85%;
    max-width:900px;
    border-radius:15px;
    box-shadow:0 0 25px cyan;
}

.stars{
    position:fixed;
    width:100%;
    height:100%;
    background:
    radial-gradient(white 1px, transparent 1px);
    background-size:50px 50px;
    opacity:0.4;
    z-index:-1;
}

function continueToStart(){

    let name =
    document.getElementById("userName").value;

    if(name.trim()===""){
        alert("Please enter your name");
        return;
    }

    document.getElementById("welcomeText").innerHTML =
    "Welcome, " + name + " 🎸";

    document.getElementById("welcomePage")
    .classList.add("hidden");

    document.getElementById("startPage")
    .classList.remove("hidden");
}

function startVideo(){

    document.getElementById("startPage")
    .classList.add("hidden");

    document.getElementById("videoPage")
    .classList.remove("hidden");

    const video =
    document.getElementById("jamVideo");

    video.play();

    video.onended = function(){

        document.getElementById("videoPage")
        .classList.add("hidden");

        document.getElementById("thankPage")
        .classList.remove("hidden");

        setTimeout(function(){

            document.getElementById("thankPage")
            .classList.add("hidden");

            document.getElementById("welcomePage")
            .classList.remove("hidden");

            document.getElementById("userName").value="";

        },5000);
    };
}
