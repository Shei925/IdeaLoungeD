<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Welcome to IdeaLoungeD! A place for creativity and ideas.">
    <title>WELCOME TO IdeaLoungeD!</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f5dc; /* Beige Brown Minimalist Color Palette */
        }

        header {
            background-color: rgba(0, 0, 0, 0.7);
            color: #ffffff;
            padding: 10px;
            text-align: center;
        }

        .burger-menu {
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            color: white;
            padding: 20px;
            overflow-y: auto;
            z-index: 10;
        }

        .burger-menu.visible {
            display: block;
        }

        .burger-menu button {
            background: transparent;
            color: #fff;
            border: none;
            cursor: pointer;
            padding: 10px 20px;
            border-bottom: 1px solid #444444;
            width: 100%;
            text-align: left;
        }

        .content {
            padding: 20px;
            position: relative;
        }

        footer {
            text-align: center;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.7);
            color: #fff;
        }

        .post-list,
        .comment-list {
            margin-bottom: 20px;
        }

        .comment {
            background-color: #e0e0e0;
            padding: 5px;
            margin: 5px 0;
            border-radius: 5px;
        }

        input[type="text"],
        textarea {
            width: calc(100% - 20px);
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #333;
            border-radius: 5px;
        }

        #comment-form {
            margin-bottom: 20px;
        }

        #drafts {
            margin-top: 20px;
            border-top: 1px solid #ccc;
            padding-top: 10px;
        }
    </style>
</head>

<body>
    <header>
        <h1>WELCOME TO IdeaLoungeD!</h1>
        <button id="toggle-menu">☰</button>
    </header>

    <div class="burger-menu" id="burger-menu">
        <div id="menu-content">
            <h2>Menu</h2>
            <button id="home-button">Home</button>
            <button id="create-post-button">📝 Create Post</button>
            <button id="my-posts-button">My Posts</button>
            <button id="manage-content-button">Manage Content</button>
            <button id="account-management-button">Account Management</button>
            <button id="appearance-button">Appearance</button>
            <button id="analytics-button">Analytics</button>
            <button id="community-button">Community</button>
            <button id="help-support-button">Help & Support</button>
            <button id="logout-button">Logout</button>
        </div>
    </div>

    <div class="content" id="main-content">
        <div id="home" class="hide">
            <h2>Welcome to the Home Page!</h2>
        </div>
        <div id="create-post" class="hide">
            <h2>Create New Blog Post</h2>
            <input type="text" id="post-title" placeholder="Post Title" required>
            <textarea id="post-content" placeholder="Post Content" required></textarea>
            <button id="save-draft-button">Save Draft</button>
            <button id="publish-post-button">Publish Post</button>
            <h3>Saved Drafts:</h3>
            <div id="drafts" class="post-list"></div>
        </div>
        <div id="my-posts" class="hide">
            <h2>My Posts</h2>
            <div class="post-list" id="my-post-list"></div>
        </div>
        <div id="manage-content" class="hide">
            <h2>Manage Content</h2>
            <!-- Additional content goes here -->
        </div>
        <div id="account-management" class="hide">
            <h2>Account Management</h2>
            <!-- Additional content goes here -->
        </div>
        <div id="appearance" class="hide">
            <h2>Appearance Settings</h2>
            <!-- Additional content goes here -->
        </div>
        <div id="analytics" class="hide">
            <h2>Analytics</h2>
            <!-- Additional content goes here -->
        </div>
        <div id="community" class="hide">
            <h2>Community</h2>
            <!-- Additional content goes here -->
        </div>
        <div id="help-support" class="hide">
            <h2>Help & Support</h2>
            <!-- Additional content goes here -->
        </div>

        <h2>Comment Section</h2>
        <div id="comment-form">
            <input type="text" id="comment-name" placeholder="Your Name" required>
            <textarea id="comment-text" placeholder="Your Comment" required></textarea>
            <button id="post-comment-button">Post Comment</button>
        </div>
        <div class="comment-list" id="comment-list"></div>
    </div>

    <footer>
        <p>© 2023 IdeaLoungeD. All Rights Reserved.</p>
    </footer>

    <script>
        const toggleMenuButton = document.getElementById('toggle-menu');
        const burgerMenu = document.getElementById('burger-menu');
        const mainContent = document.getElementById('main-content');

        const createPostButton = document.getElementById('create-post-button');
        const saveDraftButton = document.getElementById('save-draft-button');
        const publishPostButton = document.getElementById('publish-post-button');
        const postTitleInput = document.getElementById('post-title');
        const postContentTextArea = document.getElementById('post-content');
        const draftsContainer = document.getElementById('drafts');
        const myPostList = document.getElementById('my-post-list');

        const commentNameInput = document.getElementById('comment-name');
        const commentTextArea = document.getElementById('comment-text');
        const postCommentButton = document.getElementById('post-comment-button');
        const commentList = document.getElementById('comment-list');

        // Hide all content sections
        function hideAllSections() {
            document.querySelectorAll('.content > div').forEach(section => section.classList.add('hide'));
        }

        // Show the home section when navigating back
        function showHomeSection() {
            hideAllSections();
            document.getElementById('home').classList.remove('hide');
        }

        // Show a specific content section
        function showSection(sectionId) {
            hideAllSections();
            document.getElementById(sectionId).classList.remove('hide');
        }

        toggleMenuButton.addEventListener('click', () => {
            burgerMenu.classList.toggle('visible');
            mainContent.classList.toggle('blur'); // Optional: add blur effect
        });

        createPostButton.addEventListener('click', () => {
            showSection('create-post');
        });
        
        document.getElementById('home-button').addEventListener('click', () => {
            showHomeSection();
        });
        document.getElementById('my-posts-button').addEventListener('click', () => showSection('my-posts'));
        document.getElementById('manage-content-button').addEventListener('click', () => showSection('manage-content'));
        document.getElementById('account-management-button').addEventListener('click', () => showSection('account-management'));
        document.getElementById('appearance-button').addEventListener('click', () => showSection('appearance'));
        document.getElementById('analytics-button').addEventListener('click', () => showSection('analytics'));
        document.getElementById('community-button').addEventListener('click', () => showSection('community'));
        document.getElementById('help-support-button').addEventListener('click', () => showSection('help-support'));
        document.getElementById('logout-button').addEventListener('click', () => alert('Logged out!')); // Placeholder for logout

        saveDraftButton.addEventListener('click', () => {
            const postTitle = postTitleInput.value.trim();
            const postContent = postContentTextArea.value.trim();

            if (postTitle && postContent) {
                const draft = document.createElement('div');
                draft.innerHTML = `<strong>${postTitle}</strong><p>${postContent}</p>`;
                draftsContainer.appendChild(draft);
                postTitleInput.value = ''; // Clear input fields
                postContentTextArea.value = '';
                alert("Draft saved successfully!");
            } else {
                alert("Please fill in both title and content.");
            }
        });

        publishPostButton.addEventListener('click', () => {
            const postTitle = postTitleInput.value.trim();
            const postContent = postContentTextArea.value.trim();

            if (postTitle && postContent) {
                const post = document.createElement('div');
                post.innerHTML = `<strong>${postTitle}</strong><p>${postContent}</p>`;
                myPostList.appendChild(post);
                postTitleInput.value = ''; // Clear input fields
                postContentTextArea.value = '';
                alert("Post published successfully!");
            } else {
                alert("Please fill in both title and content.");
            }
        });

        postCommentButton.addEventListener('click', () => {
            const name = commentNameInput.value.trim();
            const commentText = commentTextArea.value.trim();
            const date = new Date().toLocaleString();

            if (name && commentText) {
                const comment = document.createElement('div');
                comment.className = 'comment';
                comment.innerHTML = `<strong>${name}</strong> (${date}): ${commentText}`;
                commentList.appendChild(comment);
                commentNameInput.value = '';
                commentTextArea.value = '';
            } else {
                alert("Please fill in both name and comment.");
            }
        });
    </script>
</body>

</html>
