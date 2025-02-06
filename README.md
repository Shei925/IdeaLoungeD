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
            background-color: #e6d5d0; /* Light brown background */
        }

        header {
            background-color: #333; /* Dark background for contrast */
            color: #ffffff;
            padding: 10px 20px;
            text-align: center;
            position: relative;
        }

        /* Burger menu styles */
        #burger-menu-button {
            position: absolute;
            top: 10px;
            right: 20px;
            background-color: #333;
            color: #fff;
            border: none;
            cursor: pointer;
        }

        #burger-menu {
            display: none;
            position: absolute;
            top: 50px;
            right: 20px;
            background-color: #333;
            color: white;
            padding: 10px;
            border-radius: 5px;
        }

        #burger-menu.visible {
            display: block;
        }

        #burger-menu ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        #burger-menu li {
            padding: 10px;
            border-bottom: 1px solid #444;
        }

        #burger-menu a {
            color: #fff;
            text-decoration: none;
        }

        main {
            padding: 20px;
            color: #333; /* Dark text for easy reading */
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
        }

        /* Comment section styles */
        #comment-section {
            padding: 20px;
            background-color: #fff;
            border: 1px solid #333;
            border-radius: 5px;
        }

        #comment-form {
            padding: 20px;
        }

        #comment-form input,
        #comment-form textarea {
            width: calc(100% - 22px);
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #333;
            border-radius: 5px;
        }

        /* Comment list styles */
        #comment-list div {
            padding: 10px;
            border-bottom: 1px solid #ddd;
        }

        @media only screen and (max-width: 600px) {
            header, footer {
                padding: 10px 10px;
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
            <button id="burger-menu-button">☰</button>
            <div id="burger-menu">
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">About Us</a></li>
                    <li><a href="#">Get Involved</a></li>
                    <li><a href="#">Contact Us</a></li>
                </ul>
            </div>
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
            <p>© 2023 IdeaLoungeD. All Rights Reserved.</p>
        </footer>
    </div>

    <script src="script.js"></script>
</body>

</html>


// Burger menu script
const burgerMenuButton = document.getElementById('burger-menu-button');
const burgerMenu = document.getElementById('burger-menu');

burgerMenuButton.addEventListener('click', () => {
    burgerMenu.classList.toggle('visible');
});

// Comment section script
const commentForm = document.getElementById('comment-form');
const commentTextarea = document.getElementById('comment-textarea');
const commentNameInput = document.getElementById('comment-name');
const commentPostButton = document.getElementById('comment-post-button');
const commentList = document.getElementById('comment-list');

commentPostButton.addEventListener('click', () => {
    const commentText = commentTextarea.value.trim();
    const commentName = commentNameInput.value.trim();
    
    if (commentText && commentName) {
        const comment = document.createElement('div');
        comment.innerHTML = `
            <p><strong>${commentName}</strong>: ${commentText}</p>
        `;
        commentList.appendChild(comment);

        // Clear the input fields
        commentTextarea.value = '';
        commentNameInput.value = '';
    }
});
