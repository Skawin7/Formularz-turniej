# Formularz-turniej
Formularz rejestracyjny do turnieju Danielos OG Cup

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rejestracja - Danielos OG Cup</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: url('https://via.placeholder.com/1920x1080.png?text=Danielos+OG+Cup') no-repeat center center fixed;
            background-size: cover;
            color: #fff;
            margin: 0;
            padding: 0;
        }
        .container {
            width: 100%;
            max-width: 400px;
            margin: 50px auto;
            padding: 20px;
            background: rgba(0, 0, 0, 0.8);
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
        }
        h1 {
            text-align: center;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input, select, button {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: none;
            border-radius: 5px;
        }
        button {
            background-color: #007BFF;
            color: #fff;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Rejestracja</h1>
        <form id="registration-form">
            <label for="username">Nazwa w Fortnite:</label>
            <input type="text" id="username" name="username" required>

            <label for="discordTag">Twój Discord Tag:</label>
            <input type="text" id="discordTag" name="discordTag" required>

            <label for="buildMode">Czy bierzesz udział w trybie Build?</label>
            <select id="buildMode" name="buildMode" required>
                <option value="Tak">Tak</option>
                <option value="Nie">Nie</option>
            </select>

            <button type="submit">Prześlij</button>
        </form>
    </div>

    <script>
        document.getElementById('registration-form').addEventListener('submit', async (event) => {
            event.preventDefault();

            const formData = {
                username: document.getElementById('username').value,
                discordTag: document.getElementById('discordTag').value,
                buildMode: document.getElementById('buildMode').value
            };

            const webhookURL = 'https://discord.com/api/webhooks/1316134943528845332/pLqMhTnGrx4OkfTEGS6ZgJYMG_sEYNOy7X8neY3MgVkJcqMBC6jor6FvZ7sRl-aKe_N0'; // Zastąp swoim webhookiem

            const payload = {
                content: `**Nowy formularz rejestracyjny:**\n- **Nazwa w Fortnite:** ${formData.username}\n- **Discord Tag:** ${formData.discordTag}\n- **Tryb Build:** ${formData.buildMode}`
            };

            const response = await fetch(webhookURL, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(payload)
            });

            if (response.ok) {
                alert('Formularz został przesłany!');
            } else {
                alert('Wystąpił problem. Spróbuj ponownie później.');
            }
        });
    </script>
</body>
</html>
