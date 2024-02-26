---
layout: home
search_exclude: true
permalink: /login
---

<html>
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #006FB9;
            margin: 0;
            padding: 0;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            background-color: #ADD8E6;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1, h2 {
            text-align: center;
            color: #ADD8E6;
        }
        form {
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            color: #ADD8E6;
        }
        input[type="text"],
        input[type="number"],
        button {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box;
        }
        button {
            background-color: #007bff;
            color: #fff;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        button:hover {
            background-color: #0056b3;
        }
        ul {
            list-style-type: none;
            padding: 0;
            color: #ADD8E6;
        }
        li {
            padding: 10px;
            border-bottom: 1px solid #ccc;
            display: flex;
            justify-content: space-between;
            align-items: center;
            color: #ADD8E6;
        }
        li:last-child {
            border-bottom: none;
            color: #ADD8E6;
        }
        .delete-button {
            background-color: #dc3545;
            color: #fff;
            border: none;
            padding: 5px 10px;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        .delete-button:hover {
            background-color: #c82333;
        }
    </style>
<html lang="en">

<head>
<script>
    //import { uri, options } from '{{site.baseurl}}/assets/js/api/config.js';
    function login_user() {
      const enteredUid = document.getElementById("uid").value;
      const enteredPassword = document.getElementById("password").value;
      console.log("Uid = " + enteredUid)
      console.log("Password = " + enteredPassword)
      const signupHeaders = new Headers();
      signupHeaders.set('111', '222');
      signupHeaders.set("Accept", "*/*");
      signupHeaders.set("Accept-Language", "en-US,en;q=0.9");
      signupHeaders.set("Content-Type", "application/json");
      login_api(enteredUid,enteredPassword)        
      }   
    function login_api(uid, pw){
      var myHeaders = new Headers();
      myHeaders.append("Accept", "*/*");
      myHeaders.append("Accept-Language", "en-US,en;q=0.9");
      myHeaders.append("Content-Type", "application/json");
      myHeaders.append("Cookie", "jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJfdWlkIjoidG9ueSJ9.jEShka0oXI1-uCuSTfo3ed5WRw3ASLNV0Tpn1kc5GB0");
      var raw = JSON.stringify({
          "uid": uid,
          "password": pw
        });
      var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };
      fetch("http://127.0.0.1:8088/api/users/authenticate", requestOptions)
          .then(response => {
            if (response.ok) {
                console.log("User logged in successfully");
                window.location.href = "https://ellierozen.github.io/wopoguide/score"
              } else {
                console.error("User login failed");
                // You can handle failed login attempts here
                const errorMessageDiv = document.getElementById('errorMessage');
                errorMessageDiv.innerHTML = '<label style="color: red;">User Login Failed</label>';
              }
          })
          .then(result => { 
            console.log(result);            
            })
          .catch(error => console.log('error', error));      
      //return response
    }


  </script>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Login Page</title>
  <link rel="stylesheet" href="styles.css"> <!-- Include the compiled CSS file -->
</head>

<body>
<br>
<br>
<br>
  <!-- Your HTML login form -->
  <div class="container">
  <div id="errorMessage"></div>
  <form action="javascript:login_user()">
    <p><label for="uid">User ID:</label>
      <input type="text" name="uid" id="uid" required>
    </p>
    <p><label for="password">Password:</label>
      <input type="password" name="password" id="password" required>
    </p>
    <p>
     <button class="button-spacing">Log In</button>
          <button onClick = "location.href=' //ellierozen.github.io/wopoguide/signup'" class="button-spacing" >Sign Up</button>
          
    </p>
  </form>
</div>
  <!-- Your JavaScript code -->
  
</body>

</html>