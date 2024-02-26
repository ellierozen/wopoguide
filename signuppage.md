---
layout: home
search_exclude: true
permalink: /signup
---
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
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1, h2 {
            text-align: center;
            color: #000;
        }
        form {
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            color: #000;
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
</head>
<html lang="en">
<head>
<script>
    //import { uri, options } from '{{site.baseurl}}/assets/js/api/config.js';
    function signUp_user() {
        const enteredName = document.getElementById("name").value;
        const enteredUid = document.getElementById("uid").value;
        const enteredPassword = document.getElementById("password").value;
        const enteredDOB = document.getElementById("dob").value;
        console.log("Name = " + enteredName)
        console.log("Uid = " + enteredUid)
        console.log("Password = " + enteredPassword)
        console.log("dob = " + enteredDOB)
        const signupHeaders = new Headers();
      signupHeaders.set('111', '222');  
      signupHeaders.set("Accept", "*/*");
      signupHeaders.set("Accept-Language", "en-US,en;q=0.9");
      signupHeaders.set("Content-Type", "application/json");
        signUp_api(enteredName, enteredUid, enteredPassword, enteredDOB)        
      }
    function signUp_api(name, uid, pw, dob){
      let signupHeaders = new Headers();
      signupHeaders.append('111', '222');      
      signupHeaders.append("Accept", "*/*");
      signupHeaders.append("Accept-Language", "en-US,en;q=0.9");
      signupHeaders.append("Content-Type", "application/json");
      var raw = JSON.stringify({
          "name" : name,
          "uid": uid,
          "password": pw,
          "dob": dob
        });
      var requestOptions = {
          method: 'POST',
          headers: signupHeaders,
          body: raw,
          redirect: 'follow'
        };
      fetch("http://127.0.0.1:8088/api/users/", requestOptions)
          .then(response => {
            if (response.ok) {
                console.log("Successfully Signed Up");
                alert("Account has been created. You will be directed to login page shortly.");
                window.location.href = "//ellierozen.github.io/wopoguide/login"
              } else {
                console.error("Sign Up Failed");
                // You can handle failed login attempts here
                const errorMessageDiv = document.getElementById('errorMessage');
                errorMessageDiv.innerHTML = '<label style="color: red;">User Sign Up Failed</label>';
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
    <div class="container">
    <form action="javascript:signUp_user()">
    <p><label for="Name">First Name:</label>
     <input type="text" id="name" placeholder="Your first Name" />
    </p>
    <p><label for="uid">User ID:</label> 
    <input type="text" id="uid" placeholder="User ID" />
    </p>
    <p><label for="password">Password:</label>
    <input type="password" id="password" placeholder="Password" />
    </p>
    <p><label for="dob">Date Of Birth:</label>
    <input type="text" id="dob" placeholder="Date of Birth (YYYY-MM-DD)" />
    </p>
    <button class="button-spacing">Submit</button>
    </form>
  </div>
   
</body>

</html>

