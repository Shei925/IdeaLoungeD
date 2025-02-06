<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Welcome to IdeaLoungeD! Explore creative ideas and insights.">
    <title>Welcome to IdeaLoungeD</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        header {
            background-color: #333;
            color: #fff;
            padding: 10px 20px;
            text-align: center;
        }
        main {
            padding: 20px;
        }
        h1 {
            color: #333;
        }
        p {
            line-height: 1.6;
        }
        footer {
            text-align: center;
            padding: 20px;
            background-color: #333;
            color: #fff;
            position: relative;
            bottom: 0;
            width: 100%;
        }
        
        /* Burger menu styles */
        #burger-menu {
            background-color: #333;
            color: #fff;
            padding: 10px 20px;
            text-align: center;
            display: none;
        }
        
        /* Burger menu items */
        #burger-menu ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }
        #burger-menu li {
            padding: 10px;
            border-bottom: 1px solid #333;
        }
        #burger-menu a {
            color: #fff;
            text-decoration: none;
        }
        
        /* Comment section styles */
        #comment-section {
            padding: 20px;
            background-color: #f4f4f4;
            border: 1px solid #333;
        }
        #comment-form {
            padding: 20px;
            background-color: #fff;
            border: 1px solid #333;
        }
        #comment-form input, #comment-form textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #333;
        }
        
        /* Responsive design */
        @media only screen and (max-width: 600px) {
            header, footer {
                padding: 10px 20px;
            }
            main {
                padding: 10px;
            }
            #comment-form {
                padding: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Welcome to IdeaLoungeD</h1>
            <button id="burger-menu-button">Menu</button>
            <ul id="burger-menu">
                <li>
                    <a href="#">Home</a>
                </li>
                <li>
                    <a href="#">About Us</a>
                </li>
                <li>
                    <a href="#">Get Involved</a>
                </li>
                <li>
                    <a href="#">Contact Us</a>
                </li>
            </ul>
        </header>
        
        <main>
            <h2>About Us</h2>
            <p>At IdeaLoungeD, we believe in fostering creativity and innovation. Our platform is dedicated to sharing ideas that inspire and inform.</p>
            
            <h2>Our Mission</h2>
            <p>We aim to provide a space for individuals to explore new concepts, collaborate, and bring their ideas to life.</p>
            
            <h2>Get Involved</h2>
            <p>Join us on our journey by contributing your ideas, participating in discussions, and helping us build a vibrant community.</p>
            
            <h2>Comment Section</h2>
            <div id="comment-section">
                <div id="comment-form">
                    <textarea id="comment-textarea" placeholder="Enter your comment..."></textarea>
                    <input id="comment-name" type="text" placeholder="Your name">
                    <button id="comment-post-button">Post Comment</button>
                </div>
                <div id="comment-list">
                    <!-- Display comments here -->
                </div>
            </div>
        </main>
        
        <footer>
            <p>2023 IdeaLoungeD. All Rights Reserved.</p>
        </footer>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
