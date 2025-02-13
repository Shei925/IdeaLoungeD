<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IdeaLoungeD</title>
    <style>
        /* Basic CSS (you can expand this) */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            transition: margin-left 0.3s; /* Smooth transition for the margin */
        }

        #header {
            position: relative; /* For positioning search relative to the header */
            display: flex;
            align-items: center; /* Vertically align items */
            padding: 10px;
            background: #f0f0f0; /* Background color of the header */
        }

        #burger-menu {
            z-index: 1000;
            cursor: pointer;
            font-size: 1.5em; /* Make the icon a bit larger */
            margin-right: 10px; /* Add some spacing */
        }

        #search-button {
            cursor: pointer;
            font-size: 1.5em; /* Make the icon a bit larger */
        }

        #search-input {
            display: none;
            margin-left: 10px;
            padding: 5px;
            border: 1px solid #ccc;
        }

        #menu {
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            width: 200px;
            background-color: #f0f0f0;
            padding-top: 40px;
            z-index: 999;
        }

        #menu ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        #menu li {
            padding: 10px;
            border-bottom: 1px solid #ccc;
        }

        #menu a {
            text-decoration: none;
            color: #333;
            display: block;
        }

        #menu a:hover {
            background-color: #ddd;
        }

        .content {
            padding: 20px;
            margin-left: 200px; /* Adjust based on menu width */
        }

        /* Style for empty content */
        .empty-content {
            font-style: italic;
            color: #777;
        }

        /* Footer Styles */
        #footer {
            text-align: center;
            padding: 20px;
            background-color: #f0f0f0;
            position: fixed;
            bottom: 0;
            width: 100%;
        }

        #published-posts {
          margin-top: 20px;
        }
    </style>
</head>
<body>

    <div id="header">
        <div id="burger-menu">☰</div>
        <div id="search-button">🔍</div>
        <input type="text" id="search-input" placeholder="Search...">
    </div>

    <nav id="menu">
        <ul>
            <li><a href="#home" onclick="showContent('home')">Home</a></li>
            <li><a href="#create-post" onclick="loadEditor()">📝 Create Post</a></li>
            <li><a href="#my-posts" onclick="loadEditor()">My Posts</a></li>
            <li><a href="#all-posts" onclick="loadEditor()">All Posts</a></li>
            <li><a href="#drafts" onclick="loadEditor()">Drafts</a></li>
            <li><a href="#scheduled-posts" onclick="loadEditor()">Scheduled Posts</a></li>
            <li><a href="#published-posts" onclick="loadEditor()">Published Posts</a></li>
            <li><a href="#trash" onclick="loadEditor()">Trash</a></li>
            <li><a href="#edit-post" onclick="loadEditor()">Edit Post</a></li>
            <li><a href="#manage-content" onclick="loadEditor()">Manage Content</a></li>
            <li><a href="#account-management" onclick="loadEditor()">Account Management</a></li>
            <li><a href="#appearance" onclick="loadEditor()">Appearance</a></li>
            <li><a href="#analytics" onclick="loadEditor()">Analytics</a></li>
            <li><a href="#community" onclick="loadEditor()">Community</a></li>
            <li><a href="#help-support" onclick="loadEditor()">Help & Support</a></li>
            <li><a href="#logout" onclick="loadEditor()">Logout</a></li>
        </ul>
    </nav>

    <div class="content" id="content">
        <!-- Content will be dynamically loaded here -->
        <div id="home-content">
            <h2>Welcome to IdeaLoungeD!</h2>
            <p>This is the home page content. Featured published posts will be displayed here.</p>
            <h3>About Us</h3>
            <p>IdeaLoungeD is a platform where you can share your ideas and engage with others.</p>
            <button onclick="aboutUs()">About Us</button>
            <button onclick="mission()">Mission</button>
        </div>

        <div id="editor-container">
            <!-- The editor will be loaded here -->
        </div>

        <div id="published-posts">
            <h2>Published Posts</h2>
        </div>

        <div id="search-results">
            <!-- Search results will be displayed here -->
        </div>

        <div id="footer">
            <button onclick="aboutUs()">About Us</button>
            <button onclick="mission()">Mission</button>
            &copy; 2024 IdeaLoungeD. All Rights Reserved.
        </div>
    </div>

    <script>
        const burgerMenu = document.getElementById('burger-menu');
        const menu = document.getElementById('menu');
        const searchButton = document.getElementById('search-button');
        const searchInput = document.getElementById('search-input');
        const contentDiv = document.getElementById('content');
        const publishedPostsDiv = document.getElementById('published-posts');

        // Load posts from localStorage on page load
        window.onload = () => {
            loadPosts();
        };

        burgerMenu.addEventListener('click', () => {
            menu.style.display = (menu.style.display === "none" || menu.style.display === "") ? "block" : "none";
        });

        searchButton.addEventListener('click', () => {
            searchInput.style.display = (searchInput.style.display === "none" || searchInput.style.display === "") ? "inline-block" : "none";
            searchInput.focus(); // Focus on the input field when it appears
            if (searchInput.style.display === "inline-block") {
                searchInput.addEventListener("keypress", function(event) {
                    if (event.key === "Enter") {
                        performSearch();
                    }
                });
            }
        });

        function performSearch() {
            const searchTerm = searchInput.value.toLowerCase();
            searchResultsDiv.innerHTML = ''; // Clear previous results

            let allContent = '';
            if (document.getElementById('home-content')) {
                allContent += document.getElementById('home-content').textContent.toLowerCase();
            }
            if (allContent.includes(searchTerm)) {
                searchResultsDiv.innerHTML = `<p>Search results for "${searchInput.value}": Found!</p>`;
            } else {
                searchResultsDiv.innerHTML = `<p>No results found for "${searchInput.value}".</p>`;
            }
        }

        function showContent(page) {
            // Clear existing content
            contentDiv.innerHTML = '<div id="editor-container"></div>';

            // Load the selected section
            if (page === 'home') {
                loadHome();
            } else {
                loadEditor();
            }
        }

        function loadEditor() {
            fetch('editor.html')
                .then(response => response.text())
                .then(data => {
                    document.getElementById('editor-container').innerHTML = data;
                });
        }

        function loadHome() {
            contentDiv.innerHTML = `
                <div id="home-content">
                    <h2>Welcome to IdeaLoungeD!</h2>
                    <p>This is the home page content. Featured published posts will be displayed here.</p>
                    <h3>About Us</h3>
                    <p>IdeaLoungeD is a platform where you can share your ideas and engage with others.</p>
                    <h3>Mission</h3>
                    <p>Our mission is to foster creativity and collaboration in a supportive online environment.</p>
                    <button onclick="aboutUs()">About Us</button>
                    <button onclick="mission()">Mission</button>
                </div>`;
            loadPosts();
        }

        function publishPost() {
            const editorContent = document.getElementById('editor').innerHTML;
            savePost(editorContent);
            loadPosts();
        }

        function savePost(content) {
            let posts = JSON.parse(localStorage.getItem('posts') || '[]');
            posts.push(content);
            localStorage.setItem('posts', JSON.stringify(posts));
        }

        function loadPosts() {
            let posts = JSON.parse(localStorage.getItem('posts') || '[]');
            let postsHTML = '';
            posts.forEach((post, index) => {
                postsHTML += `<div class="post"><h3>Post ${index + 1}</h3>${post}</div>`;
            });
            publishedPostsDiv.innerHTML = postsHTML;
        }

        function aboutUs() {
            const aboutUsContent = `
                <h2>About Us</h2>
                <p>IdeaLoungeD is a platform where you can share your ideas and engage with others.</p>
                <p>Our mission is to foster creativity and collaboration in a supportive online environment.</p>
            `;
            document.getElementById('editor-container').innerHTML += aboutUsContent;
        }

        function mission() {
            const missionContent = `
                <h2>Mission</h2>
                <p>Our mission is to foster creativity and collaboration in a supportive online environment.</p>
                <p>We believe everyone has unique ideas and perspectives to share, and we strive to create a supportive space for them.</p>
            `;
            document.getElementById('editor-container').innerHTML += missionContent;
        }
    </script>
</body>
</html>
