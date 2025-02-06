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
            top: 10px;
            left: 10px;
            width: 250px;
            height: calc(100vh - 20px);
            background-color: rgba(0, 0, 0, 0.9);
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
        }

        .content {
            padding: 20px;
            position: relative;
            width: 80%;
            float: right;
        }

        #main-content .top-btn {
            position: absolute;
            top: 0;
            right: 0;
            background-color: #ccc;
            border: none;
            padding: 10px;
            cursor: pointer;
            color: #000;
        }

        #main-content .top-btn:hover {
            background-color: #999;
        }

        footer {
            text-align: center;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.7);
            color: #fff;
            clear: both;
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

        .submenu {
            display: none;
            padding-left: 15px;
        }

        .submenu.visible {
            display: block;
        }

        .menu-item {
            padding: 5px 0;
            cursor: pointer;
        }

        .menu-item:hover {
            text-decoration: underline;
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
            <div class="menu-item" id="home-button">Home</div>
            <div class="submenu" id="home-submenu">
                <div class="menu-item" id="create-post-button">📝 Create Post</div>
                <div class="submenu" id="create-post-submenu">
                    <div class="menu-item" id="new-blog-post-button">New Blog Post</div>
                    <div class="menu-item" id="upload-media-button">Upload Media</div>
                </div>
            </div>

            <div class="menu-item" id="my-posts-button">My Posts</div>
            <div class="submenu" id="my-posts-submenu">
                <div class="menu-item" id="all-posts-button">All Posts</div>
                <div class="menu-item" id="drafts-button">Drafts</div>
                <div class="menu-item" id="scheduled-posts-button">Scheduled Posts</div>
                <div class="menu-item" id="published-posts-button">Published Posts</div>
                <div class="menu-item" id="trash-button">Trash</div>
                <div class="menu-item" id="edit-post-button">Edit Post</div>
            </div>

            <div class="menu-item" id="manage-content-button">Manage Content</div>
            <div class="submenu" id="manage-content-submenu">
                <div class="menu-item" id="categories-button">Categories</div>
                <div class="menu-item" id="tags-button">Tags</div>
                <div class="menu-item" id="featured-posts-button">Featured Posts</div>
                <div class="menu-item" id="archive-button">Archive</div>
            </div>

            <div class="menu-item" id="account-management-button">Account Management</div>
            <div class="submenu" id="account-management-submenu">
                <div class="menu-item">Profile Settings</div>
                <div class="submenu">
                    <div class="menu-item" id="update-profile-button">Update Profile</div>
                    <div class="menu-item" id="change-password-button">Change Password</div>
                    <div class="menu-item" id="manage-email-button">Manage Email Notifications</div>
                </div>
                <div class="menu-item">Privacy Settings</div>
                <div class="submenu">
                    <div class="menu-item" id="account-privacy-button">Account Privacy</div>
                    <div class="menu-item" id="data-management-button">Data Management</div>
                    <div class="menu-item" id="blocked-users-button">Blocked Users</div>
                </div>
            </div>

            <div class="menu-item" id="appearance-button">Appearance</div>
            <div class="submenu" id="appearance-submenu">
                <div class="menu-item" id="themes-button">Themes</div>
                <div class="menu-item" id="customize-theme-button">Customize Theme</div>
                <div class="menu-item" id="change-fonts-button">Change Fonts</div>
                <div class="menu-item" id="dark-mode-button">Dark Mode Toggle</div>
                <div class="menu-item" id="layout-options-button">Layout Options</div>
            </div>

            <div class="menu-item" id="analytics-button">Analytics</div>
            <div class="submenu" id="analytics-submenu">
                <div class="menu-item">View Stats</div>
                <div class="submenu">
                    <div class="menu-item" id="post-views-button">Post Views</div>
                    <div class="menu-item" id="user-engagement-button">User Engagement</div>
                    <div class="menu-item" id="likes-comments-button">Likes and Comments</div>
                </div>
                <div class="menu-item" id="audience-insights-button">Audience Insights</div>
                <div class="menu-item" id="traffic-sources-button">Traffic Sources</div>
            </div>

            <div class="menu-item" id="community-button">Community</div>
            <div class="submenu" id="community-submenu">
                <div class="menu-item" id="followers-button">Followers</div>
                <div class="menu-item" id="following-button">Following</div>
                <div class="menu-item">Comments</div>
                <div class="submenu">
                    <div class="menu-item" id="manage-comments-button">Manage Comments</div>
                    <div class="menu-item" id="approved-comments-button">Approved Comments</div>
                    <div class="menu-item" id="spam-button">Spam</div>
                </div>
            </div>

            <div class="menu-item" id="help-support-button">Help & Support</div>
            <div class="submenu" id="help-support-submenu">
                <div class="menu-item" id="faqs-button">FAQs</div>
                <div class="menu-item" id="contact-support-button">Contact Support</div>
                <div class="menu-item" id="report-problem-button">Report a Problem</div>
            </div>

            <div class="menu-item" id="logout-button">Logout</div>
        </div>
    </div>

    <div id="main-content">
        <button class="top-btn" id="top-button">&larr; Go Back</button>
        <div class="content" id="home" style="display:block;">
            <h2>Welcome to the Home Page!</h2>
        </div>
        <div class="content" id="create-new-post" class="hide">
            <h2>Create New Post</h2>
            <input type="text" id="post-title" placeholder="Post Title" required>
            <textarea id="post-content" placeholder="Post Content" required></textarea>
            <button id="save-draft-button">Save Draft</button>
            <button id="publish-post-button">Publish Post</button>
            <h3>Saved Drafts:</h3>
            <div id="drafts" class="post-list"></div>
        </div>
    </div>

    <footer>
        <p>At IdeaLoungeD, we believe in fostering creativity and innovation. Our platform is dedicated to sharing ideas that inspire.</p>
        <p>&copy; 2023 IdeaLoungeD. All Rights Reserved.</p>
    </footer>

    <script>
        const toggleMenuButton = document.getElementById('toggle-menu');
        const burgerMenu = document.getElementById('burger-menu');
        const topButton = document.getElementById('top-button');

        const createPostButton = document.getElementById('create-post-button');
        const newBlogPostButton = document.getElementById('new-blog-post-button');
        const uploadMediaButton = document.getElementById('upload-media-button');

        const myPostsButton = document.getElementById('my-posts-button');
        const allPostsButton = document.getElementById('all-posts-button');
        const draftsButton = document.getElementById('drafts-button');
        const scheduledPostsButton = document.getElementById('scheduled-posts-button');
        const publishedPostsButton = document.getElementById('published-posts-button');
        const trashButton = document.getElementById('trash-button');
        const editPostButton = document.getElementById('edit-post-button');

        const manageContentButton = document.getElementById('manage-content-button');
        const categoriesButton = document.getElementById('categories-button');
        const tagsButton = document.getElementById('tags-button');
        const featuredPostsButton = document.getElementById('featured-posts-button');
        const archiveButton = document.getElementById('archive-button');

        const accountManagementButton = document.getElementById('account-management-button');
        const updateProfileButton = document.getElementById('update-profile-button');
        const changePasswordButton = document.getElementById('change-password-button');
        const manageEmailButton = document.getElementById('manage-email-button');
        const accountPrivacyButton = document.getElementById('account-privacy-button');
        const dataManagementButton = document.getElementById('data-management-button');
        const blockedUsersButton = document.getElementById('blocked-users-button');

        const appearanceButton = document.getElementById('appearance-button');
        const themesButton = document.getElementById('themes-button');
        const customizeThemeButton = document.getElementById('customize-theme-button');
        const changeFontsButton = document.getElementById('change-fonts-button');
        const darkModeButton = document.getElementById('dark-mode-button');
        const layoutOptionsButton = document.getElementById('layout-options-button');

        const analyticsButton = document.getElementById('analytics-button');
        const postViewsButton = document.getElementById('post-views-button');
        const userEngagementButton = document.getElementById('user-engagement-button');
        const likesCommentsButton = document.getElementById('likes-comments-button');
        const audienceInsightsButton = document.getElementById('audience-insights-button');
        const trafficSourcesButton = document.getElementById('traffic-sources-button');

        const communityButton = document.getElementById('community-button');
        const followersButton = document.getElementById('followers-button');
        const followingButton = document.getElementById('following-button');
        const manageCommentsButton = document.getElementById('manage-comments-button');
        const approvedCommentsButton = document.getElementById('approved-comments-button');
        const spamButton = document.getElementById('spam-button');

        const helpSupportButton = document.getElementById('help-support-button');
        const faqsButton = document.getElementById('faqs-button');
        const contactSupportButton = document.getElementById('contact-support-button');
        const reportProblemButton = document.getElementById('report-problem-button');

        const logoutButton = document.getElementById('logout-button');

        // Submenu toggle functionality
        function toggleSubmenu(submenuId) {
            const submenu = document.getElementById(submenuId);
            submenu.classList.toggle('visible');
        }

        // Show the home section when navigating back
        function showHomeSection() {
            document.querySelectorAll('.content').forEach(section => section.style.display = 'none');
            document.getElementById('home').style.display = 'block';
        }

        // Show a specific content section
        function showSection(sectionId) {
            document.querySelectorAll('.content').forEach(section => section.style.display = 'none');
            document.getElementById(sectionId).style.display = 'block';
        }

        toggleMenuButton.addEventListener('click', () => {
            burgerMenu.classList.toggle('visible');
        });

        topButton.addEventListener('click', showHomeSection);

        createPostButton.addEventListener('click', () => toggleSubmenu('create-post-submenu'));
        myPostsButton.addEventListener('click', () => toggleSubmenu('my-posts-submenu'));
        manageContentButton.addEventListener('click', () => toggleSubmenu('manage-content-submenu'));
        accountManagementButton.addEventListener('click', () => toggleSubmenu('account-management-submenu'));
        appearanceButton.addEventListener('click', () => toggleSubmenu('appearance-submenu'));
        analyticsButton.addEventListener('click', () => toggleSubmenu('analytics-submenu'));
        communityButton.addEventListener('click', () => toggleSubmenu('community-submenu'));
        helpSupportButton.addEventListener('click', () => toggleSubmenu('help-support-submenu'));

        newBlogPostButton.addEventListener('click', () => showSection('create-new-post'));
        
        // More event listeners can be added as needed for other buttons and sections
    </script>
</body>

</html>
