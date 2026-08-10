<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>IP Address Disclosure</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f5;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      margin: 0;
    }

    .card {
      background: white;
      max-width: 500px;
      padding: 30px;
      border-radius: 16px;
      text-align: center;
      box-shadow: 0 8px 30px rgba(0,0,0,0.1);
    }

    button {
      background: #111;
      color: white;
      border: none;
      padding: 12px 20px;
      border-radius: 10px;
      font-size: 16px;
      cursor: pointer;
    }

    #result {
      margin-top: 20px;
      font-weight: bold;
    }
  </style>
</head>

<body>

  <div class="card">
    <h1>IP Address Disclosure</h1>

    <p>
      This page will display your public IP address.
      By continuing, you acknowledge that your IP address
      is being viewed.
    </p>

    <button onclick="showIP()">
      Show My IP Address
    </button>

    <div id="result"></div>
  </div>

  <script>
    async function showIP() {
      try {
        const response = await fetch(
          "https://api.ipify.org?format=json"
        );

        const data = await response.json();

        document.getElementById("result").textContent =
          "Your public IP address is: " + data.ip;

      } catch (error) {
        document.getElementById("result").textContent =
          "Unable to retrieve IP address.";
      }
    }
  </script>

</body>
</html>