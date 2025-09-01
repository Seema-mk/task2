# task2
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Form with Validation</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 50px;
    }
    form {
      max-width: 400px;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 8px;
    }
    input, button {
      width: 100%;
      padding: 10px;
      margin: 8px 0;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .error {
      color: red;
      font-size: 14px;
    }
  </style>
</head>
<body>
  <h2>Registration Form</h2>
  
  <form id="myForm" onsubmit="return validateForm()">
    <label for="name">Name:</label>
    <input type="text" id="name" placeholder="Enter your name">
    <div id="nameError" class="error"></div>

    <label for="email">Email:</label>
    <input type="text" id="email" placeholder="Enter your email">
    <div id="emailError" class="error"></div>

    <label for="password">Password:</label>
    <input type="password" id="password" placeholder="Enter password">
    <div id="passwordError" class="error"></div>

    <button type="submit">Submit</button>
  </form>

  <script>
    function validateForm() {
      let isValid = true;

      // Clear previous errors
      document.getElementById("nameError").innerText = "";
      document.getElementById("emailError").innerText = "";
      document.getElementById("passwordError").innerText = "";

      // Get values
      let name = document.getElementById("name").value.trim();
      let email = document.getElementById("email").value.trim();
      let password = document.getElementById("password").value.trim();

      // Name validation
      if (name === "") {
        document.getElementById("nameError").innerText = "Name is required!";
        isValid = false;
      }

      // Email validation (basic pattern)
      let emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
      if (email === "") {
        document.getElementById("emailError").innerText = "Email is required!";
        isValid = false;
      } else if (!email.match(emailPattern)) {
        document.getElementById("emailError").innerText = "Enter a valid email!";
        isValid = false;
      }

      // Password validation
      if (password.length < 6) {
        document.getElementById("passwordError").innerText = "Password must be at least 6 characters!";
        isValid = false;
      }

      return isValid; // Prevent form submission if invalid
    }
  </script>
</body>
</html>
