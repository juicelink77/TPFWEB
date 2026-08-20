# NeoGeo Web Player Template

This repository is a **Template** that allows you to easily create a website to play a homebrew NeoGeo game directly in the browser, without any programming knowledge!

## 🚀 How to publish your own game?

### Step 1: Create your own repository
1. Click on the green **"Use this template"** button (top right of this page), then choose **"Create a new repository"**.
2. Give a name to your repository (e.g. `my-awesome-neogeo-game`).
3. Leave it as **Public** and click on **Create repository**.
4. You now have an exact copy of this code on your own GitHub account!

### Step 2: Add your game (ROM), your hash file, and your image
In your new GitHub repository, we are going to replace the example files with yours.

**For the game ROM:**
1. Go into the `roms/` folder.
2. Click on **Add file** -> **Upload files**.
3. Import your NeoGeo game `.zip` file (the homebrew game).
4. Click on **Commit changes**.

**For the game hash file:**
1. Go into the `hash/` folder.
2. Click on **Add file** -> **Upload files**.
3. Import the `NeoGeo.xml` file specific to your game.
4. Click on **Commit changes**.

**For the presentation image:**
1. Go into the `images/` folder.
2. Click on **Add file** -> **Upload files**.
3. Import an image that will serve as background / presentation. IMPORTANT: Name it EXACTLY `cover.png` (replacing the one already there).
4. Click on **Commit changes**.

### Step 3: Configure the site
This is the last configuration step!

1. At the root of your repository, click on the `config.js` file.
2. Click on the pencil icon ✏️ (top right of the file) to edit it.
3. Modify the information inside the quotes so they match your game:
   - `romName`: The exact name of your zip file added in step 2 (WITHOUT writing `.zip`).
   - `gameTitle`: The title of your game as it will appear in the browser tab.
   - `gameUrl`: A link to the official page of your game (itch.io, website, etc.).
   - `linkText`: The text for the link displayed below the game.
   - `linkColor`: The color of the link (e.g. `#4caf50`, `red`, `white`).
4. Click on **Commit changes** at the top right.

### Step 4: Put the site online (GitHub Pages)
Now that your game is configured, we need to make it accessible on the Internet!

1. Go to the **Settings** ⚙️ tab of your repository (at the top).
2. In the left menu, scroll down and click on **Pages**.
3. Under "Build and deployment", in the **Branch** section, click on "None" and choose **main**.
4. Click on **Save**.
5. Wait about 1 to 2 minutes. If you refresh the "Pages" settings page, you will see a link appear at the top: *"Your site is live at..."*.
6. Click on this link: **Congratulations, your game is playable online! 🎉**
