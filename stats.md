---
layout: home
search_exclude: true
permalink: /stats
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Water Polo Score Tracker</title>
    <link rel="stylesheet" href="styles.css">
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
</head>
<body>
    <h1>Water Polo Stats Tracker</h1>
    <div class="container">
        <h2>Add Player Stats</h2>
        <form id="statsForm">
            <label for="number">User ID:</label>
            <input type="text" id="uid" name="uid" required>
            <label for="playerName">Player Name:</label>
            <input type="text" id="playerName" name="playerName" required>
            <label for="goals">Goals:</label>
            <input type="number" id="goals" name="goals" required>
            <label for="number">Number:</label>
            <input type="number" id="number" name="number" required>
            <button type="submit">Submit</button>
        </form>
        <h2>Player Stats</h2>
        <ul id="stats-list"></ul>
    </div>
    <script>
        // Function to fetch and display player stats
        function getPlayerStats() {
            fetch('http://127.0.0.1:8088/api/stats/') // Adjust the URL according to your API endpoint
                .then(response => response.json())
                .then(data => {
                    const statsList = document.getElementById('stats-list');
                    statsList.innerHTML = '';
                    data.forEach(stat => {
                        const listItem = document.createElement('li');
                        listItem.textContent = `uid: ${stat.uid}, Player: ${stat.playerName}, Goals: ${stat.goals}, Number: ${stat.number}`;
                        statsList.appendChild(listItem);
                    });
                })
                .catch(error => console.error('Error:', error));
        }
        // Function to handle form submission and add player stats
        document.getElementById('statsForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const playerName = document.getElementById('playerName').value;
            const goals = document.getElementById('goals').value;
            const number = document.getElementById('number').value;
            const uid = document.getElementById('uid').value;
            const data = {
                playerName: playerName,
                goals: goals,
                number: number,
                uid: uid
            };
            fetch('http://127.0.0.1:8088/api/stats/', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(data),
            })
            .then(response => {
                if (response.ok) {
                    return response.json();
                } else {
                    console.error('Error:', response.status);
                }
            })
            .then(data => {
                console.log('Success:', data);
                getPlayerStats();
                document.getElementById('statsForm').reset();
            })
            .catch(error => console.error('Error:', error));
        });

        // Get