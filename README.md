<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IdeaLoungeD</title>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Alex Brush">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" integrity="sha512-9usAa10IRO0HhonpyAIVpjrylPvoDwiPUiKdWk5t3PyolY1cOd4DSE0Ga+ri4AuTroPR5aQvXU9xC6qOPnzFeg==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    <style>
        /* Basic CSS (you can expand this) */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            transition: margin-left 0.3s;
            text-align: center; /* Centered text in the content */
            justify-content: center; /* Justify for aesthetics */
        }

        #header {
            display: flex;
            align-items: center; 
            padding: 10px;
            background: #f0f0f0;
            position: relative; /* Position relative for proper layering */
        }

        #burger-menu {
            cursor: pointer;
            font-size: 1.5em; 
            margin-right: 10px; 
            z-index: 1000; /* Ensure it's on top */
        }

        #search-button {
            cursor: pointer;
            font-size: 1.5em; 
        }

        #search-input {
            display: inline-block; /* Ensuring it shows inline properly */
            margin-left: 10px;
            padding: 5px;
            border: 1px solid #ccc;
        }

        #menu {
            display: none;
            position: absolute;
            top: 50px;
            left: 0;
            width: 200px;
            background-color: #f0f0f0;
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
            text-align: center; /* Centering the content */
        }

        .empty-content {
            font-style: italic;
            color: #777;
        }

        #footer {
            text-align: center;
            padding: 20px;
            background-color: #f0f0f0;
            position: fixed;
            bottom: 0;
            width: 100%;
        }

        #footer .footer-text {
            margin-top: 10px; /* Add some spacing */
        }

        /* Published posts styling */
        #published-posts {
            margin-top: 20px;
            text-align: left; /* Align posts to the left */
        }

        .post {
            border: 1px solid #ddd;
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 5px;
            background-color: #f9f9f9;
        }

        .post h3 {
            margin-top: 0;
            margin-bottom: 5px;
        }

        /* Comment section styling */
        .comment-section {
            margin-top: 10px;
        }

        .comment {
            border-bottom: 1px dashed #ccc;
            padding: 5px 0;
            margin-bottom: 5px;
            text-align: left;
        }

        /* Reaction buttons styling */
        .reaction-buttons {
            margin-top: 10px;
            display: flex;
            justify-content: flex-start;
        }

        .reaction-button {
            background: none;
            border: none;
            font-size: 1.2em;
            padding: 5px;
            cursor: pointer;
        }

        .alex-brush-font {
            font-family: 'Alex Brush', cursive;
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
        <div id="home-content">
            <h2 class="alex-brush-font">Welcome to IdeaLoungeD!</h2>
            <p>This is the home page content. Featured published posts will be displayed here.</p>
        </div>
    </div>

    <div id="search-results"></div>

    <div id="footer">
        <button onclick="aboutUs()">About Us</button>
        <button onclick="mission()">Mission</button>
        <div class="footer-text">&copy; 2024 IdeaLoungeD. All Rights Reserved.</div>
    </div>

    <script>
        const burgerMenu = document.getElementById('burger-menu');
        const menu = document.getElementById('menu');
        const contentDiv = document.getElementById('content');
        const searchInput = document.getElementById('search-input');
        const searchButton = document.getElementById('search-button');

        // Generic function to generate unique IDs
        function generateId() {
            return Math.random().toString(36).substring(2, 15) + Math.random().toString(36).substring(2, 15);
        }

        // Search Functionality
        function searchPosts(searchTerm) {
            let posts = JSON.parse(localStorage.getItem('posts') || '[]');
            const searchResults = posts.filter(post => {
                return post.content.toLowerCase().includes(searchTerm.toLowerCase());
            });

            let searchResultsHTML = '';
            if (searchResults.length > 0) {
                searchResults.forEach(post => {
                    searchResultsHTML += `<div class="post">
                                            <h3>${post.title}</h3>
                                            ${post.content}
                                            </div>`;
                });
            } else {
                searchResultsHTML = `<p class="empty-content">No posts found matching your search.</p>`;
            }

            document.getElementById('search-results').innerHTML = `<h2>Search Results</h2>${searchResultsHTML}`;
        }

        searchButton.addEventListener('click', () => {
            const searchTerm = searchInput.value.trim();
            if (searchTerm) {
                searchPosts(searchTerm);
            } else {
                alert('Please enter a search term.');
            }
        });

        searchInput.addEventListener('keydown', (event) => {
            if (event.key === 'Enter') {
                event.preventDefault();
                const searchTerm = searchInput.value.trim();
                if (searchTerm) {
                    searchPosts(searchTerm);
                } else {
                    alert('Please enter a search term.');
                }
            }
        });

        // Load and Display Posts Function
        function loadPosts() {
            let posts = JSON.parse(localStorage.getItem('posts') || '[]');
            let postsHTML = '';
            posts.forEach(post => {
                postsHTML += `<div class="post">
                                <h3>${post.title}</h3>
                                ${post.content}
                                <div class="reaction-buttons">
                                    <button class="reaction-button" onclick="reactToPost('${post.id}', 'like')"><i class="fas fa-thumbs-up"></i> <span id="like-count-${post.id}">${post.reactions['like'] || 0}</span></button>
                                    <button class="reaction-button" onclick="reactToPost('${post.id}', 'heart')"><i class="fas fa-heart"></i> <span id="heart-count-${post.id}">${post.reactions['heart'] || 0}</span></button>
                                    <button class="reaction-button" onclick="reactToPost('${post.id}', 'laugh')"><i class="fas fa-laugh"></i> <span id="laugh-count-${post.id}">${post.reactions['laugh'] || 0}</span></button>
                                    <button class="reaction-button" onclick="reactToPost('${post.id}', 'care')"><i class="fas fa-hand-holding-heart"></i> <span id="care-count-${post.id}">${post.reactions['care'] || 0}</span></button>
                                    <button class="reaction-button" onclick="reactToPost('${post.id}', 'sad')"><i class="fas fa-sad-tear"></i> <span id="sad-count-${post.id}">${post.reactions['sad'] || 0}</span></button>
                                    <button class="reaction-button" onclick="reactToPost('${post.id}', 'angry')"><i class="fas fa-angry"></i> <span id="angry-count-${post.id}">${post.reactions['angry'] || 0}</span></button>
                                </div>
                                <div class="comment-section">
                                    <textarea id="comment-text-${post.id}" placeholder="Add a comment"></textarea>
                                    <button onclick="addComment('${post.id}')">Post Comment</button>
                                    <div id="comments-${post.id}">
                                        ${loadComments(post.id)}
                                    </div>
                                </div>
                            </div>`;
            });
            contentDiv.innerHTML = `<h2 class="alex-brush-font">Published Posts</h2><div id="published-posts">${postsHTML}</div>`;
        }

        // Reaction Functionality
        function reactToPost(postId, reactionType) {
            let posts = JSON.parse(localStorage.getItem('posts') || '[]');
            const postIndex = posts.findIndex(post => post.id === postId);

            if (postIndex !== -1) {
                if (!posts[postIndex].reactions) {
                    posts[postIndex].reactions = {};
                }

                posts[postIndex].reactions[reactionType] = (posts[postIndex].reactions[reactionType] || 0) + 1;
                localStorage.setItem('posts', JSON.stringify(posts));

                document.getElementById(`${reactionType}-count-${postId}`).textContent = posts[postIndex].reactions[reactionType];
            } else {
                console.log('Post not found');
            }
        }

        // Comment Functionality
        function addComment(postId) {
            const commentText = document.getElementById(`comment-text-${postId}`).value;
            if (commentText.trim() === '') return;

            let comments = JSON.parse(localStorage.getItem('comments') || '{}');
            if (!comments[postId]) {
                comments[postId] = [];
            }

            comments[postId].push(commentText);
            localStorage.setItem('comments', JSON.stringify(comments));

            document.getElementById(`comment-text-${postId}`).value = '';
            document.getElementById(`comments-${postId}`).innerHTML = loadComments(postId);
        }

        function loadComments(postId) {
            let comments = JSON.parse(localStorage.getItem('comments') || '{}');
            if (!comments[postId] || comments[postId].length === 0) {
                return '<p>No comments yet.</p>';
            }

            let commentsHTML = '';
            comments[postId].forEach(comment => {
                commentsHTML += `<div class="comment">${comment}</div>`;
            });
            return commentsHTML;
        }

        // Show/hide the menu on burger click
        burgerMenu.addEventListener('click', () => {
            menu.style.display = (menu.style.display === "none" || menu.style.display === "") ? "block" : "none";
        });

        // Show Content Function
        function showContent(page) {
            contentDiv.innerHTML = ''; // Clear existing content
            document.getElementById('search-results').innerHTML = '';  // Clear search results
            switch(page) {
                case 'home':
                    contentDiv.innerHTML = `
                        <h2 class="alex-brush-font">Home</h2>
                        <p>This is the home page content with featured posts!</p>`;
                    loadPosts();
                    break;
                case 'my-posts':
                    contentDiv.innerHTML = `<h2>My Posts</h2><p class="empty-content">My posts are currently empty. Please create one to fill in.</p>`;
                    break;
                case 'all-posts':
                    contentDiv.innerHTML = `<h2>All Posts</h2><p class="empty-content">No posts available.</p>`;
                    break;
                case 'drafts':
                    contentDiv.innerHTML = `<h2>Drafts</h2><p class="empty-content">No drafts available.</p>`;
                    break;
                case 'scheduled-posts':
                    contentDiv.innerHTML = `<h2>Scheduled Posts</h2><p class="empty-content">No scheduled posts.</p>`;
                    break;
                case 'published-posts':
                    contentDiv.innerHTML = `<h2>Published Posts</h2>`;
                    loadPosts();
                    break;
                case 'trash':
                    contentDiv.innerHTML = `<h2>Trash</h2><p class="empty-content">Trash is empty.</p>`;
                    break;
                case 'edit-post':
                    contentDiv.innerHTML = `<h2>Edit Post</h2><p>Select a post to edit. This functionality will be available soon!</p>`;
                    break;
                case 'manage-content':
                    contentDiv.innerHTML = `<h2>Manage Content</h2><p>Manage your content settings here.</p>`;
                    break;
                case 'account-management':
                    contentDiv.innerHTML = `<h2>Account Management</h2><p>Manage your account settings here.</p>`;
                    break;
                case 'appearance':
                    contentDiv.innerHTML = `<h2>Appearance</h2><p>Customize your appearance settings here.</p>`;
                    break;
                case 'analytics':
                    contentDiv.innerHTML = `<h2>Analytics</h2><p>Analyze your content performance here.</p>`;
                    break;
                case 'community':
                    contentDiv.innerHTML = `<h2>Community</h2><p>Engage with your community here.</p>`;
                    break;
                case 'help-support':
                    contentDiv.innerHTML = `<h2>Help & Support</h2><p>Find resources for your support needs.</p>`;
                    break;
                case 'logout':
                    contentDiv.innerHTML = `<h2>Logout</h2><p>You have successfully logged out.</p>`;
                    break;
                default:
                    contentDiv.innerHTML = `<h2>Error</h2><p>Page not found.</p>`;
            }
        }

        // Load Editor Function
        function loadEditor() {
            fetch('editor.html')
                .then(response => response.text())
                .then(data => {
                    contentDiv.innerHTML = data;
                    // Initialize the post publishing function from the editor
                    window.publishPost = function(postContent, postTitle) {
                        let posts = JSON.parse(localStorage.getItem('posts') || '[]');
                        const newPostId = generateId();

                        let newPost = {
                            id: newPostId,
                            title: postTitle,
                            content: postContent,
                            reactions: {},
                        };

                        posts.push(newPost);
                        localStorage.setItem('posts', JSON.stringify(posts));
                        loadPosts();
                        showContent('published-posts'); // Redirect to published posts
                    };
                })
                .catch(error => {
                    console.error('Error loading the editor:', error);
                });
        }

        function aboutUs() {
            contentDiv.innerHTML = `
                <h2 class="alex-brush-font">About Us</h2>
                <p>IdeaLoungeD is a platform where you can share your ideas and engage with others.</p>
                <p>Our mission is to foster creativity and collaboration in a supportive online environment.</p>
                &copy; 2024 IdeaLoungeD. All Rights Reserved.
            `;
        }

        function mission() {
            contentDiv.innerHTML = `
                <h2 class="alex-brush-font">Mission</h2>
                <p>Our mission is to foster creativity and collaboration in a supportive online environment.</p>
                <p>We believe everyone has unique ideas and perspectives to share, and we strive to create a supportive space for them.</p>
                &copy; 2024 IdeaLoungeD. All Rights Reserved.
            `;
        }
    </script>

</body>
</html>
