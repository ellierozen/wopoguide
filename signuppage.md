---
layout: home
search_exclude: true
permalink: /signup
---
<head>
    <style>
        body {
            background-color: #006FB9;
            font-size: 20px;
        }
        .button {
            color: #000000;
            font-size: 20px;
            font-family: sans-serif;
            line-height: auto;
            border-style: hidden;
            outline: none;
            background: none;
            border: none;
            cursor: pointer;
            text-align: center;
        }
        .button:hover {
            text-decoration: underline;
        }
        .dropdown-content {
            display: none;
            position: absolute;
            background-color: #f9f9f9;
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
          width: 50%;
          background-color: #7ea7f4;
          margin: 0 auto; /* Center the card */
        }
        .card:hover {
          box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
        }
        .container {
          padding: 2px 16px;
          background-color: #ADD8E6;
        }
        /* Style the dropdown button */
        .dropbtn {
        background-color: #4CAF50;
        color: white;
        padding: 16px;
        font-size: 16px;
        border: none;
        cursor: pointer;
        }
        /* Dropdown button on hover & focus */
        .dropbtn:hover, .dropbtn:focus {
        background-color: #3e8e41;
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
        background-color: #f9f9f9;
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
        .dropdown-content a:hover {background-color: #f1f1f1;}
        /* Show the dropdown menu on hover */
        .dropdown:hover .dropdown-content {
        display: block;
        }
        /* Change the background color of the dropdown button when the dropdown content is shown */
        .dropdown:hover .dropbtn {
        background-color: #3e8e41;
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

