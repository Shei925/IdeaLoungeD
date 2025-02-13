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

        /* Editor Styles */
        #editor {
            border: 1px solid #ccc;
            padding: 10px;
            min-height: 300px;
        }

        /* Search Results */
        #search-results {
            margin-top: 20px;
        }

        /* Toolbars */
        .toolbar {
            display: flex;
            margin-bottom: 10px;
        }

        .toolbar button {
            margin-right: 5px; /* Space between buttons */
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
            <li><a href="#create-post" onclick="showContent('create-post')">📝 Create Post</a></li>
            <li><a href="#my-posts" onclick="showContent('my-posts')">My Posts</a></li>
            <li><a href="#all-posts" onclick="showContent('all-posts')">All Posts</a></li>
            <li><a href="#drafts" onclick="showContent('drafts')">Drafts</a></li>
            <li><a href="#scheduled-posts" onclick="showContent('scheduled-posts')">Scheduled Posts</a></li>
            <li><a href="#published-posts" onclick="showContent('published-posts')">Published Posts</a></li>
            <li><a href="#trash" onclick="showContent('trash')">Trash</a></li>
            <li><a href="#edit-post" onclick="showContent('edit-post')">Edit Post</a></li>
            <li><a href="#manage-content" onclick="showContent('manage-content')">Manage Content</a></li>
            <li><a href="#account-management" onclick="showContent('account-management')">Account Management</a></li>
            <li><a href="#appearance" onclick="showContent('appearance')">Appearance</a></li>
            <li><a href="#analytics" onclick="showContent('analytics')">Analytics</a></li>
            <li><a href="#community" onclick="showContent('community')">Community</a></li>
            <li><a href="#help-support" onclick="showContent('help-support')">Help & Support</a></li>
            <li><a href="#logout" onclick="showContent('logout')">Logout</a></li>
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

        <div id="create-post-content">
            <h2>Create Post</h2>
            <div class="toolbar">
                <button onclick="document.execCommand('bold');">Bold</button>
                <button onclick="document.execCommand('italic');">Italic</button>
                <button onclick="document.execCommand('underline');">Underline</button>
                <button onclick="document.execCommand('insertOrderedList');">Numbered List</button>
                <button onclick="document.execCommand('insertUnorderedList');">Bulleted List</button>
                <select onchange="document.execCommand('foreColor', false, this.value);">
                    <option value="">Select Color</option>
                    <option value="blue">Blue</option>
                    <option value="red">Red</option>
                    <option value="green">Green</option>
                    <option value="orange">Orange</option>
                </select>
                <button onclick="document.execCommand('insertImage', false, prompt('Enter image URL:'))">Insert Image</button>
            </div>
            <div id="editor" contenteditable="true" style="border: 1px solid #ccc; padding: 10px; min-height: 300px;">
                Start writing your post here...
            </div>
            <button onclick="publishPost()">Publish Post</button>
        </div>

        <div id="my-posts-content">
            <h2>My Posts</h2>
            <p class="empty-content">My posts are currently empty. Please create one to fill in.</p>
        </div>

        <div id="all-posts-content">
            <h2>All Posts</h2>
            <p class="empty-content">No posts available.</p>
        </div>

        <div id="drafts-content">
            <h2>Drafts</h2>
            <p class="empty-content">No drafts available.</p>
        </div>

        <div id="scheduled-posts-content">
            <h2>Scheduled Posts</h2>
            <p class="empty-content">No scheduled posts.</p>
        </div>

        <div id="published-posts-content">
            <h2>Published Posts</h2>
            <p class="empty-content">No published posts available.</p>
        </div>

        <div id="trash-content">
            <h2>Trash</h2>
            <p class="empty-content">Trash is empty.</p>
        </div>

        <div id="edit-post-content">
            <h2>Edit Post</h2>
            <p>Select a post to edit. Editing tools similar to 'Create Post' will be available here.</p>
        </div>

        <div id="manage-content-content">
            <h2>Manage Content</h2>
            <p>Manage your content here.</p>
        </div>

        <div id="account-management-content">
            <h2>Account Management</h2>
            <p>Manage your account settings here.</p>
        </div>

        <div id="appearance-content">
            <h2>Appearance</h2>
            <p>Customize your dashboard appearance here.</p>
        </div>

        <div id="analytics-content">
            <h2>Analytics</h2>
            <p>View your dashboard analytics here.</p>
        </div>

        <div id="community-content">
            <h2>Community</h2>
            <p>Join our community here.</p>
        </div>

        <div id="help-support-content">
            <h2>Help & Support</h2>
            <p>Get help and support here.</p>
        </div>

        <div id="logout-content">
            <h2>Logout</h2>
            <p>Logout of your account here.</p>
        </div>
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

    <script>
        const burgerMenu = document.getElementById('burger-menu');
        const menu = document.getElementById('menu');
        const searchButton = document.getElementById('search-button');
        const searchInput = document.getElementById('search-input');
        const contentDiv = document.getElementById('content');
        const searchResultsDiv = document.getElementById('search-results');
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

            if (document.getElementById('create-post-content')) {
                allContent += document.getElementById('create-post-content').textContent.toLowerCase();
            }

            if (document.getElementById('my-posts-content')) {
                allContent += document.getElementById('my-posts-content').textContent.toLowerCase();
            }
            if (document.getElementById('all-posts-content')) {
                allContent += document.getElementById('all-posts-content').textContent.toLowerCase();
            }
            if (document.getElementById('drafts-content')) {
                allContent += document.getElementById('drafts-content').textContent.toLowerCase();
            }
            if (document.getElementById('scheduled-posts-content')) {
                allContent += document.getElementById('scheduled-posts-content').textContent.toLowerCase();
            }
            if (document.getElementById('published-posts-content')) {
                allContent += document.getElementById('published-posts-content').textContent.toLowerCase();
            }
            if (document.getElementById('trash-content')) {
                allContent += document.getElementById('trash-content').textContent.toLowerCase();
            }
            if (document.getElementById('edit-post-content')) {
                allContent += document.getElementById('edit-post-content').textContent.toLowerCase();
            }
            if (document.getElementById('manage-content-content')) {
                allContent += document.getElementById('manage-content-content').textContent.toLowerCase();
            }
            if (document.getElementById('account-management-content')) {
                allContent += document.getElementById('account-management-content').textContent.toLowerCase();
            }
            if (document.getElementById('appearance-content')) {
                allContent += document.getElementById('appearance-content').textContent.toLowerCase();
            }
            if (document.getElementById('analytics-content')) {
                allContent += document.getElementById('analytics-content').textContent.toLowerCase();
            }
            if (document.getElementById('community-content')) {
                allContent += document.getElementById('community-content').textContent.toLowerCase();
            }
            if (document.getElementById('help-support-content')) {
                allContent += document.getElementById('help-support-content').textContent.toLowerCase();
            }
            if (document.getElementById('logout-content')) {
                allContent += document.getElementById('logout-content').textContent.toLowerCase();
            }
            if (allContent.includes(searchTerm)) {
                searchResultsDiv.innerHTML = `<p>Search results for "${searchInput.value}": Found!</p>`;
            } else {
                searchResultsDiv.innerHTML = `<p>No results found for "${searchInput.value}".</p>`;
            }
        }

        // Keep burger menu visible after clicking
        burgerMenu.style.display = "block";

        function showContent(page) {
            contentDiv.innerHTML = ''; // Clear existing content
            let pageContentId;
            switch (page) {
                case 'home':
                    pageContentId = 'home-content';
                    contentDiv.innerHTML = `
                    <div id="${pageContentId}">
                        <h2>Welcome to IdeaLoungeD!</h2>
                        <p>This is the home page content. Featured published posts will be displayed here.</p>
                        <h3>About Us</h3>
                        <p>IdeaLoungeD is a platform where you can share your ideas and engage with others.</p>
                        <h3>Mission</h3>
                        <p>Our mission is to foster creativity and collaboration in a supportive online environment.</p>
                    </div>`;
                    loadPosts();
                    break;
                case 'create-post':
                    pageContentId = 'create-post-content';
                    contentDiv.innerHTML = `
                    <div id="${pageContentId}">
                        <h2>Create Post</h2>
                        <div class="toolbar">
                            <button onclick="document.execCommand('bold');">Bold</button>
                            <button onclick="document.execCommand('italic');">Italic</button>
                            <button onclick="document.execCommand('underline');">Underline</button>
                            <button onclick="document.execCommand('insertOrderedList');">Numbered List</button>
                            <button onclick="document.execCommand('insertUnorderedList');">Bulleted List</button>
                            <select onchange="document.execCommand('foreColor', false, this.value);">
                                <option value="">Select Color</option>
                                <option value="blue">Blue</option>
                                <option value="red">Red</option>
                                <option value="green">Green</option>
                                <option value="orange">Orange</option>
                            </select>
                            <button onclick="document.execCommand('insertImage', false, prompt('Enter image URL:'))">Insert Image</button>
                        </div>
                        <div id="editor" contenteditable="true" style="border: 1px solid #ccc; padding: 10px; min-height: 300px;">
                            Start writing your post here...
                        </div>
                        <button onclick="publishPost()">Publish Post</button>
                    </div>`;
                    break;
                case 'my-posts':
                    pageContentId = 'my-posts-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>My Posts</h2><p class="empty-content">My posts are currently empty. Please create one to fill in.</p></div>`;
                    break;
                case 'all-posts':
                    pageContentId = 'all-posts-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>All Posts</h2><p class="empty-content">No posts available.</p></div>`;
                    break;
                case 'drafts':
                    pageContentId = 'drafts-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Drafts</h2><p class="empty-content">No drafts available.</p></div>`;
                    break;
                case 'scheduled-posts':
                    pageContentId = 'scheduled-posts-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Scheduled Posts</h2><p class="empty-content">No scheduled posts.</p></div>`;
                    break;
                case 'published-posts':
                    pageContentId = 'published-posts-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Published Posts</h2><p class="empty-content">No published posts available.</p></div>`;
                    loadPosts();
                    break;
                case 'trash':
                    pageContentId = 'trash-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Trash</h2><p class="empty-content">Trash is empty.</p></div>`;
                    break;
                case 'edit-post':
                    pageContentId = 'edit-post-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Edit Post</h2>
                                             <p>Select a post to edit. Editing tools similar to 'Create Post' will be available here.</p></div>`;
                    loadPosts();
                    break;
                case 'manage-content':
                    pageContentId = 'manage-content-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Manage Content</h2><p>Manage your content here.</p></div>`;
                    break;
                case 'account-management':
                    pageContentId = 'account-management-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Account Management</h2><p>Manage your account settings here.</p></div>`;
                    break;
                case 'appearance':
                    pageContentId = 'appearance-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Appearance</h2><p>Customize your dashboard appearance here.</p></div>`;
                    break;
                case 'analytics':
                    pageContentId = 'analytics-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Analytics</h2><p>View your dashboard analytics here.</p></div>`;
                    break;
                case 'community':
                    pageContentId = 'community-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Community</h2><p>Join our community here.</p></div>`;
                    break;
                case 'help-support':
                    pageContentId = 'help-support-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Help & Support</h2><p>Get help and support here.</p></div>`;
                    break;
                case 'logout':
                    pageContentId = 'logout-content';
                    contentDiv.innerHTML = `<div id="${pageContentId}"><h2>Logout</h2><p>Logout of your account here.</p></div>`;
                    break;
            }
        }

        function aboutUs() {
            let aboutUsContent = `
                <h2>About Us</h2>
                <p>IdeaLoungeD is a platform where you can share your ideas and engage with others.</p>
                <p>Our mission is to foster creativity and collaboration in a supportive online environment.</p>
            `;
            contentDiv.innerHTML += aboutUsContent;
        }

        function mission() {
            let missionContent = `
                <h2>Mission</h2>
                <p>Our mission is to foster creativity and collaboration in a supportive online environment.</p>
                <p>We believe that everyone has unique ideas and perspectives to share, and we strive to create a space where they can come together and grow.</p>
            `;
            contentDiv.innerHTML += missionContent;
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
    </script>
</body>
</html>
