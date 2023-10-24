# MsangiO7
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <style>
        
        
      body {
            font-family: Arial, sans-serif;
            background-color: #f5f5f5;
        }

        #form, #reviews {
            display: none;
        }

        form {
            max-width: 400px;
            margin: 0 auto;
            background: #fff;
            border: 1px solid #e0e0e0;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
            padding: 20px;
        }

        form input {
            width: 100%;
            height: 8%;
            margin-bottom: 15px;
            padding: 10px;
            border: 1px solid #e0e0e0;
            border-radius: 50px;
            color: #00FFF5;
        }

        form button {
            background: #007BFF;
            color: #fff;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        form button:hover {
            background: #0056b3;
        }

        #success-message {
            color: #4CAF50;
            font-weight: bold;
        }

        #reviews div {
            background: #fff;
            border: 1px solid #e0e0e0;
            border-radius: 5px;
            padding: 15px;
            margin: 10px 0;
            box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
        }

        a {
            text-decoration: none;
            color: #007BFF;
            margin-right: 10px;
        }
   h1{
       color: #3900FF;
       font-weight: bold;
   }
   
           #loader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
        }

        .loader {
            display: inline-block;
            width: 50px;
            height: 50px;
        }

        .loader-text {
            color: #fff;
            font-size: 24px;
            margin-top: 10px;
        }

        .loader:after {
            content: " ";
            display: block;
            width: 30px;
            height: 30px;
            margin: 8px;
            border-radius: 50%;
            border: 6px solid #5800FF;
            border-color: #5800FF transparent #5800FF transparent;
            animation: loader 1.5s linear infinite;
        }

        @keyframes loader {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }
   
   
   /* Increase touch target size and provide feedback */
form button {
    width: 100%;
    padding: 15px 20px; /* Larger touch target */
    background: #007BFF;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background 0.3s; /* Smooth color transition */
}

/* Style changes when button is pressed */
form button:active {
    background: #0056b3;
}

/* Style changes on hover */
form button:hover {
    background: #0056b3;
}

   /* Style for input fields */
form input {
    width: 100%;
    height: 50px; /* Larger touch-friendly height */
    padding: 10px;
    border: 2px solid #007BFF; /* Add a border */
    border-radius: 5px;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.2); /* Add a shadow */
    transition: border-color 0.3s; /* Smooth border color transition */
}

/* Style changes when input is selected (tapped) */
form input:focus {
    border-color: #0056b3; /* Change border color on focus */
}

   
     
        
        
        
    </style>
</head>
<body>
    <!-- Your HTML structure remains the same -->
    
        <div id="reviews"></div>
    
    <form id="form">
        <label ><h1>
        Registration form</h1></label>
        <input type="text" id="name" placeholder="Name">
        <input type="text" id="institution" placeholder="Institution">
        <input type="email" id="email" placeholder="Email">
        <button type="button" onclick="registerUser()">Register</button>
        
  
    </form>

    <p id="success-message" class="hide">Registration Successful!</p>

    <a href="#" id="form-link">Register</a>
    <a href="#" id="reviews-link">Reviews</a>

    
    
    <div id="loader">
        <div class="loader">
            <div class="loader-text"><h6>Please wait....</h6></div>
        </div>
    </div>
    <div id="reviews"></div>
    <form id="form">
        <label><h2>Registration form</h2></label>
        <input type="text" id="name" placeholder="Name">
        <input type="text" id="institution" placeholder="Institution">
        <input type="email" id="email" placeholder="Email">
        
        <input type="number" id="phone" placeholder="phone number">
        
        <button type="button" onclick="registerUser()">Register</button>
    </form>
    
    <script>
        // Your JavaScript code remains the same with possible comments and corrections
        
        
            var registeredUsers = [];

        function displayReviews() {
            var reviewsSection = document.getElementById('reviews');
            reviewsSection.innerHTML = '';

            if (registeredUsers.length > 0) {
                registeredUsers.forEach(function(user, index) {
                    var review = document.createElement('div');
                    review.innerHTML = `<h3>Review ${index + 1}</h3>
                    <p><strong>Name:</strong> ${user.name}</p>
                    <p><strong>Institution:</strong> ${user.institution}</p>
                    <p><strong>Email:</strong> ${user.email}</p>`;
                    reviewsSection.appendChild(review);
                });
            } else {
                reviewsSection.innerHTML = '<p>No reviews yet fill the form first.</p>';
            }
        }

        function registerUser() {
            var name = document.getElementById('name').value;
            var institution = document.getElementById('institution').value;
            var email = document.getElementById('email').value;

            if (name && institution && email) {
                var user = {
                    name: name,
                    institution: institution,
                    email: email
                };
                registeredUsers.push(user);
                displayReviews();
                document.getElementById('success-message').classList.remove('hide');
                document.getElementById('form').reset();
            } else {
                alert('Please fill in all fields.');
            }
        }

        document.getElementById('form-link').addEventListener('click', function() {
            document.getElementById('reviews').style.display = 'none';
            document.getElementById('form').style.display = 'block';
        });

        document.getElementById('reviews-link').addEventListener('click', function() {
            document.getElementById('form').style.display = 'none';
            document.getElementById('reviews').style.display = 'block';
            displayReviews();
        });

        // Initially, show the registration form
        document.getElementById('form').style.display = 'block';
    
            window.addEventListener('load', function() {
            setTimeout(function() {
                document.getElementById('loader').style.display = 'none';
                document.getElementById('content').style.display = 'block';
            }, 4000);
        });
  </script>
</body>
</html>
