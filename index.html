<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Welcome to IdeaLoungeD! Explore creative ideas and insights.">
    <title>Welcome to IdeaLoungeD</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f5dc; /* Beige Brown Minimalist Color Palette */
            color: #333;
            background-image: url('https://example.com/your-background-image.jpg'); /* Replace with your book cover image */
            background-size: cover;
            background-repeat: no-repeat;
        }

        header {
            background-color: rgba(0, 0, 0, 0.7);
            color: #ffffff;
            padding: 10px 20px;
            text-align: center;
            position: relative;
            z-index: 2;
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
            z-index: 2;
            position: relative;
        }

        h1 {
            color: #ffffff;
        }

        footer {
            text-align: center;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.7);
            color: #fff;
            z-index: 2;
        }

        /* Post management styles */
        #post-form {
            display: none;
            padding-top: 20px;
        }

        #post-form input,
        #post-form textarea {
            width: calc(100% - 22px);
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #333;
            border-radius: 5px;
        }

        #settings {
            display: none;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.8);
            border: 1px solid #333;
            border-radius: 5px;
        }

        /* Color picker styles */
        .color-picker {
            margin: 10px 0;
        }

        /* Comments styles */
        #comment-section {
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.8);
            border: 1px solid #333;
            border-radius: 5px;
        }

        #comment-form input,
        #comment-form textarea {
            width: calc(100% - 22px);
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #333;
            border-radius: 5px;
        }
    </style>
</head>

<body>
    <div class="container">
        <header>
            <h1>Welcome to IdeaLoungeD!</h1>
            <button id="burger-menu-button">☰</button>
            <div id="burger-menu">
                <ul>
                    <li><a href="#" id="manage-posts">Manage Posts</a></li>
                    <li><a href="#" id="view-visits">View Visits</a></li>
                    <li><a href="#" id="manage-viewers">Manage Viewers</a></li>
                    <li><a href="#" id="settings-button">Settings</a></li>
                    <li><a href="#" id="logout">Logout</a></li>
                </ul>
                <div class="post-management">
                    <h2>Post Management</h2>
                    <button id="create-post-button">Create New Post</button>
                    <div id="post-form">
                        <input type="text" id="post-title" placeholder="Post Title">
                        <textarea id="post-content" placeholder="Post Content"></textarea>
                        <button id="save-post-button">Save Post</button>
                    </div>
                    <div id="post-list"></div> <!-- Display posts here -->
                </div>
                <div id="settings">
                    <h2>Settings</h2>
                    <label for="theme-color">Select Theme Color:</label>
                    <input type="color" id="theme-color" class="color-picker"><br>
                    <label for="font-color">Select Font Color:</label>
                    <input type="color" id="font-color" class="color-picker"><br>
                    <label for="background-color">Select Background Color:</label>
                    <input type="color" id="background-color" class="color-picker"><br>
                    <button id="apply-settings">Apply Settings</button>
                </div>
            </div>
        </header>

        <main>
            <h2>About Us</h2>
            <p>At IdeaLoungeD, we believe in fostering creativity and innovation. Our platform is dedicated to sharing ideas that inspire and inform.</p>
            <h2>Comment Section</h2>
            <div id="comment-section">
                <div id="comment-form">
                    <textarea id="comment-textarea" placeholder="Enter your comment..."></textarea>
                    <input id="comment-name" type="text" placeholder="Your name">
                    <button id="comment-post-button">Post Comment</button>
                </div>
                <div id="comment-list"></div> <!-- Display comments here -->
            </div>
        </main>

        <footer>
            <p>© 2023 IdeaLoungeD. All Rights Reserved.</p>
        </footer>
    </div>

    <script>
        // Burger Menu script
        const burgerMenuButton = document.getElementById('burger-menu-button');
        const burgerMenu = document.getElementById('burger-menu');
        const settingsButton = document.getElementById('settings-button');
        const settings = document.getElementById('settings');
        const applySettingsButton = document.getElementById('apply-settings');
        const themeColorInput = document.getElementById('theme-color');
        const fontColorInput = document.getElementById('font-color');
        const backgroundColorInput = document.getElementById('background-color');

        burgerMenuButton.addEventListener('click', () => {
            burgerMenu.classList.toggle('visible');
            settings.style.display = 'none'; // Hide settings when menu is toggled
        });

        settingsButton.addEventListener('click', () => {
            settings.style.display = settings.style.display === 'none' ? 'block' : 'none';
            burgerMenu.classList.remove('visible'); // Close the menu
        });

        applySettingsButton.addEventListener('click', () => {
            const newThemeColor = themeColorInput.value;
            const newFontColor = fontColorInput.value;
            const newBackgroundColor = backgroundColorInput.value;

            document.body.style.backgroundColor = newBackgroundColor;
            document.body.style.color = newFontColor; // Apply font color
            document.querySelector('header').style.backgroundColor = newThemeColor; // Change header background color
        });

        // Post Management script
        const createPostButton = document.getElementById('create-post-button');
        const postForm = document.getElementById('post-form');
        const postTitleInput = document.getElementById('post-title');
        const postContentTextArea = document.getElementById('post-content');
        const savePostButton = document.getElementById('save-post-button');
        const postList = document.getElementById('post-list');

        createPostButton.addEventListener('click', () => {
            postForm.style.display = 'block';
        });

        savePostButton.addEventListener('click', () => {
            const postTitle = postTitleInput.value.trim();
            const postContent = postContentTextArea.value.trim();

            if (postTitle && postContent) {
                const post = document.createElement('div');
                post.innerHTML = `<h3>${postTitle}</h3><p>${postContent}</p>`;
                postList.appendChild(post);
                postForm.style.display = 'none';
                postTitleInput.value = '';
                postContentTextArea.value = '';
            }
        });

        // Comment section script
        const commentTextarea = document.getElementById('comment-textarea');
        const commentNameInput = document.getElementById('comment-name');
        const commentPostButton = document.getElementById('comment-post-button');
        const commentList = document.getElementById('comment-list');

        commentPostButton.addEventListener('click', () => {
            const commentText = commentTextarea.value.trim();
            const commentName = commentNameInput.value.trim();

            if (commentText && commentName) {
                const comment = document.createElement('div');
                comment.innerHTML = `<strong>${commentName}:</strong> ${commentText}`;
                commentList.appendChild(comment);
                commentTextarea.value = '';
                commentNameInput.value = '';
            }
        });
    </script>
</body>

</html>
