# intelectsuptracker-password-reset-page
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Reset Password</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 2rem;
      max-width: 400px;
      margin: auto;
    }
    input {
      width: 100%;
      padding: 0.5rem;
      margin-bottom: 1rem;
      font-size: 1rem;
    }
    button {
      width: 100%;
      padding: 0.5rem;
      font-size: 1rem;
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background-color: #45a049;
    }
    #msg {
      margin-top: 1rem;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <h2>Reset Your Password</h2>
  <p>Enter your new password below:</p>

  <input type="password" id="password" placeholder="New password" />
  <button onclick="changePassword()">Update Password</button>

  <p id="msg"></p>

  <script type="module">
    import { createClient } from "https://cdn.jsdelivr.net/npm/@supabase/supabase-js/+esm";

    
    const supabase = createClient(
      'https://pfoovfknmamxhznrceot.supabase.co',
      'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InBmb292ZmtubWFteGh6bnJjZW90Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjMxMjU4NTEsImV4cCI6MjA3ODcwMTg1MX0.7lmLmX_6V7Mk9JZfgSSW9Ox2siYqsQerhkyj3mdNIL8'
    );

    const urlParams = new URLSearchParams(window.location.search);
    const accessToken = urlParams.get('access_token');

    async function changePassword() {
      const newPassword = document.getElementById("password").value;

      if (!accessToken) {
        document.getElementById("msg").textContent = "Invalid or missing access token.";
        return;
      }

      if (!newPassword) {
        document.getElementById("msg").textContent = "Please enter a new password.";
        return;
      }

      const { data, error } = await supabase.auth.updateUser({
        password: newPassword,
        access_token: accessToken
      });

      if (error) {
        document.getElementById("msg").textContent = error.message;
      } else {
        document.getElementById("msg").textContent = "Password updated successfully!";
      }
    }
  </script>

</body>
</html>
      document.getElementById("msg").textContent = 
        "Password updated successfully!";
    }
  }
</script>
</body>
</html>
