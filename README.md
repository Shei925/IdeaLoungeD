<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Welcome to IdeaLoungeD! A place for creativity and ideas.">
    <title>Welcome to IdeaLoungeD!</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f1e6; /* Creamy Beige */
        }

        header {
            background-color: rgba(75, 58, 47, 0.9); /* Darker Brown */
            color: #ffffff;
            padding: 10px;
            text-align: center;
        }

        h1 {
            font-family: 'Dancing Script', cursive; /* Apply the new font */
            font-size: 2.5em; /* Adjust size as needed */
            margin: 0; /* Remove default margin */
        }

        .burger-menu {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background-color: rgba(75, 58, 47, 0.95); /* Darker Brown with transparency */
            color: white;
            padding: 20px;
            overflow-y: auto;
            z-index: 10;
        }

        .burger-menu.visible {
            display: block;
        }

        #main-content {
            padding: 20px;
            position: relative;
            background-color: #ffffff; /* White for content area */
        }

        .content {
            padding: 20px;
            position: relative;
            width: 80%;
            float: right;
        }

        .menu-item {
            padding: 5px 0;
            cursor: pointer;
        }

        .menu-item:hover {
            text-decoration: underline;
            color: #d4b993; /* Soft Dusty Gold */
        }

        footer {
            text-align: center;
            padding: 20px;
            background-color: rgba(75, 58, 47, 0.9); /* Darker Brown with transparency */
            color: #fff;
            clear: both;
        }

        .editor {
            border: 1px solid #d4b993; /* Dusty Gold for borders */
            padding: 10px;
            height: 400px;
            overflow-y: auto;
            background-color: #fdf6e3; /* Soft Beige */
        }

        .create-icon {
            font-size: 24px;
            cursor: pointer;
            color: #4B3C31; /* Dark Coffee Color */
        }
    </style>
</head>

<body>
    <header>
        <h1>Welcome to IdeaLoungeD!</h1>
        <button id="toggle-menu">☰</button>
    </header>

    <div class="burger-menu" id="burger-menu">
        <div id="menu-content">
            <h2>Menu</h2>
            <div class="menu-item" id="home-button">Home</div>
            <div class="menu-item" id="create-post-button">📝 Create Post</div>
            <div class="menu-item" id="my-posts-button">My Posts</div>
            <div class="menu-item" id="all-posts-button">All Posts</div>
            <div class="menu-item" id="drafts-button">Drafts</div>
            <div class="menu-item" id="scheduled-posts-button">Scheduled Posts</div>
            <div class="menu-item" id="published-posts-button">Published Posts</div>
            <div class="menu-item" id="trash-button">Trash</div>
            <div class="menu-item" id="edit-post-button">Edit Post</div>
            <div class="menu-item" id="manage-content-button">Manage Content</div>
            <div class="menu-item" id="account-management-button">Account Management</div>
            <div class="menu-item" id="appearance-button">Appearance</div>
            <div class="menu-item" id="analytics-button">Analytics</div>
            <div class="menu-item" id="community-button">Community</div>
            <div class="menu-item" id="help-support-button">Help & Support</div>
            <div class="menu-item" id="logout-button">Logout</div>
        </div>
    </div>

    <div id="main-content">
        <div class="content" id="home" style="display:block;">
            <h2>Welcome to the Home Page!</h2>
            <div class="create-icon" id="create-new-post-icon">✍️</div>
        </div>
        <div class="content" id="create-new-post" class="hide" style="display:none;">
            <h2>Create New Post</h2>
            <div class="editor" contenteditable="true" id="post-editor" placeholder="Start writing your post..."></div>
            <button id="save-draft-button">Save Draft</button>
            <button id="publish-post-button">Publish Post</button>
            <h3>Saved Drafts:</h3>
            <div id="drafts" class="post-list"></div>
        </div>
    </div>

    <footer>
        <p>At IdeaLoungeD, we believe in fostering creativity and innovation. Our platform is dedicated to sharing ideas that inspire.</p>
        <p><a href="#about-us" style="color:#d4b993;">About Us</a> | <a href="#privacy-policy" style="color:#d4b993;">Privacy Policy</a> | <a href="#mission" style="color:#d4b993;">Mission</a></p>
        <p>&copy; 2023 IdeaLoungeD. All Rights Reserved.</p>
    </footer>

    <script>
        const toggleMenuButton = document.getElementById('toggle-menu');
        const burgerMenu = document.getElementById('burger-menu');
        const createNewPostIcon = document.getElementById('create-new-post-icon');
        const homeButton = document.getElementById('home-button');
        const createPostButton = document.getElementById('create-post-button');
        const saveDraftButton = document.getElementById('save-draft-button');
        const publishPostButton = document.getElementById('publish-post-button');

        // Toggle burger menu visibility
        toggleMenuButton.addEventListener('click', () => {
            burgerMenu.classList.toggle('visible');
            if (burgerMenu.classList.contains('visible')) {
                showHomeSection(); // Show home when menu opens
            }
        });

        // Show home section
        function showHomeSection() {
            document.querySelectorAll('.content').forEach(section => section.style.display = 'none');
            document.getElementById('home').style.display = 'block';
        }

        // Show create post section
        createNewPostIcon.addEventListener('click', () => {
            burgerMenu.classList.remove('visible'); // Close menu
            showSection('create-new-post');
        });

        createPostButton.addEventListener('click', () => {
            burgerMenu.classList.remove('visible'); // Close menu
            showSection('create-new-post');
        });

        // Show a specific content section
        function showSection(sectionId) {
            document.querySelectorAll('.content').forEach(section => section.style.display = 'none');
            document.getElementById(sectionId).style.display = 'block';
        }

        // Save draft functionality
        saveDraftButton.addEventListener('click', () => {
            const postContent = document.getElementById('post-editor').innerHTML;
            if (postContent) {
                const drafts = JSON.parse(localStorage.getItem('drafts')) || [];
                drafts.push(postContent);
                localStorage.setItem('drafts', JSON.stringify(drafts));
                renderDrafts();
                document.getElementById('post-editor').innerHTML = ''; // Clear editor
            }
        });

        // Publish post functionality
        publishPostButton.addEventListener('click', () => {
            const postContent = document.getElementById('post-editor').innerHTML;
            if (postContent) {
                // Here you can add functionality to publish the post
                alert('Post published!'); // Placeholder for publishing action
                document.getElementById('post-editor').innerHTML = ''; // Clear editor
            }
        });

        // Render saved drafts
        function renderDrafts() {
            const drafts = JSON.parse(localStorage.getItem('drafts')) || [];
            const draftsList = document.getElementById('drafts');
            draftsList.innerHTML = '';
            drafts.forEach((draft, index) => {
                const draftDiv = document.createElement('div');
                draftDiv.className = 'comment';
                draftDiv.innerHTML = `Draft ${index + 1}: ${draft}`;
                draftsList.appendChild(draftDiv);
            });
        }

        // Initial render of drafts
        renderDrafts();
    </script>
</body>

</html>
