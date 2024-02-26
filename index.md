---
layout: home
search_exclude: true
---
<html>
<head>
    <style>
        body {
            background-color: #006FB9;
        }
        .button {
            color: #000;
            font-size: 18px;
            font-family: serif;
            line-height: auto;
            outline: none;
            background: #FAE29C;
            border: none;
            cursor: pointer;
            text-align: center;
            border-radius: 10px;
        }
        .button:hover {
            text-decoration: underline;
            background: #DAC17C;
            box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
            transform: scale(1.05);
        }
        .arthub {
            font-size: 36px;
            width: auto;
        }
        .dropdown-content {
            display: none;
            position: absolute;
            background-color: #F9F9F9;
            min-width: 160px;
            box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
            z-index: 1;
        }
        h1 {
            font-size: 40px;
            color: #111;
            text-align: center;
            margin-top: 20px;
        }
        .card {
          box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
          transition: 0.3s;
          width: 30%; 
          background-color: #7ea7f4;
          border-radius: 15px; 
          display: inline-block; 
          vertical-align: top; 
          margin-right: 2.5%; 
          margin-bottom: 20px; 
          height: 450px;
        }
        .card:last-child {
          margin-right: 0; 
        }
        .card:hover {
          box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
          transform: scale(1.05);
        }
        .container {
          padding: 2px 16px;
        }
        .dropbtn {
        background-color: #006FB9;
        color: white;
        padding: 16px;
        font-size: 16px;
        border: none;
        cursor: pointer;
        }
        /* Dropdown button on hover & focus */
        .dropbtn:hover, .dropbtn:focus {
        background-color: #3E8E41;
        }
        /* The container <div> - needed to position the dropdown content */
        .dropdown {
        position: relative;
        display: inline-block;
        }
        /* Dropdown content (hidden by default) */
        .dropdown-content {
        display: none;
        position: absolute;
        background-color: #F9F9F9;
        min-width: 160px;
        box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
        z-index: 1;
        }
        /* Links inside the dropdown */
        .dropdown-content a {
        color: black;
        padding: 12px 16px;
        text-decoration: none;
        display: block;
        }
        /* Change color of dropdown links on hover */
        .dropdown-content a:hover {background-color: #F1F1F1;}
        /* Show the dropdown menu on hover */
        .dropdown:hover .dropdown-content {
        display: block;
        }
        /* Change the background color of the dropdown button when the dropdown content is shown */
        .dropdown:hover .dropbtn {
        background-color: #3e8e41;
        }
        img {
          max-width: 100%; 
          height: auto; 
        }
    </style>
</head>
<body>
<!-- Title -->
    <img src="https://cdn.discordapp.com/attachments/879557685253664768/1204205967869218826/Screenshot_2024-02-05_at_3.24.25_PM.png?ex=65e65833&is=65d3e333&hm=1ab443b72af209a4803f44a2ff103e71d52e6480b3dcaec872cc4f1189c23388&" alt="image" style="width:96%; height:200px">
    <div class="dropdown">
    <button class="dropbtn">. . .</button>
    <div class="dropdown-content">
        <a href="waterpoloquiz.html">Waterpolo Quiz</a>
    </div>
    </div>
    <br>
    <meta name="viewport" content="width=device-width, initial-scale=1">
<!-- Card 1 -->
    <div class="card">
        <img src="https://cdn.discordapp.com/attachments/879557685253664768/1204202021599846480/Screenshot_2024-02-05_at_3.08.07_PM.png?ex=65e65486&is=65d3df86&hm=37b546ef67823e88a9d7eb03204520766505b0b6f828d721e337b62f357940dd&" alt="Avatar" style="width:100%; height:250px;">
        <div class="container">
            <center><h4><b>Use our AI platform to help answer any of your pressing questions about WaterPolo.</b></h4></center>
           <center> <button class="button" onclick="location.href='//127.0.0.1:4100/wopoguide/ai';">Go To Search</button></center>
            <br>
        </div>
    </div>
<!-- Card 2 -->
    <div class="card">
        <img src="https://cdn.discordapp.com/attachments/879557685253664768/1207082423020429322/Screenshot_2024-02-13_at_1.53.43_PM.png?ex=65e7949c&is=65d51f9c&hm=884e3407b674f568ce1e02489b8b83fa9e1da2c1b312649b9b6cd7719653e581&" alt="Avatar" style="width:100%; height:250px;">
        <div class="container">
            <center><h4><b>Interested in tracking local games? Use our catalog below to enter any teams you’re interested in watching!</b></h4></center>
            <center><button class="button" onclick="location.href='//ellierozen.github.io/wopoguide/login';">Search</button></center>
            <br>
        </div>
    </div>
<!-- Card 3 -->
    <div class="card">
        <img src="https://cdn.discordapp.com/attachments/879557685253664768/1207803997038321705/Screenshot_2024-02-15_at_1.40.18_PM.png?ex=65e0fa20&is=65ce8520&hm=51e9a4e784a932253dcda78a532a91b73415a17b8cca23b33641f18b261e0e1d&" alt="Avatar" style="width:100%; height:250px">
        <div class="container">
            <center><h4><b>Learn more about the Del Norte Varsity Girls WOPO Team!</b></h4></center>
            <center><button class="button" onclick="location.href='//ellierozen.github.io/wopoguide/score';">Search</button></center>
        </div>
    </div>
<!-- Gif -->
    <img src="https://cdn.discordapp.com/attachments/879557685253664768/1207445276508299274/dgcrl11-19db592b-2427-44de-b7e4-8c317c14eda1.gif?ex=65dfac0b&is=65cd370b&hm=be9b878b6715fd585b69f5349b15b30c61b98b890034205ede26eecf3eff6880&" alt="Avatar" style="width:100%; height:150px">
    <br>
    <br>
</body>
</html>
