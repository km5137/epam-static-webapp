# Creating a Static Web App

This guide walks you through creating a simple static web app and deploying it using GitHub and Microsoft Azure. Follow the steps below to set up your environment, create your app, and deploy it online.

## Prerequisites

Before you begin, ensure you have the following:

- A GitHub account
- A Microsoft Azure account with an active subscription
- Visual Studio Code installed on your local PC
- Git installed on your local PC

## Step 1: Create a Repository on GitHub

1. Log into GitHub.
2. Click the **New Repository** button.
   
![new_repo](https://myfirststaticwebappsa.blob.core.windows.net/screenshoots/github-new-repo.png "Optional title")

3. Create a new empty repository.

![new_repo2](https://myfirststaticwebappsa.blob.core.windows.net/screenshoots/github-create-repo.png)

4. Save the SSH URL of your repository for future use.

## Step 2: Add SSH Keys into GitHub

1. Open the command line on your local PC.
2. Type `ssh-keygen` and follow the instructions, leaving everything at default.
3. Navigate to the `~/.ssh` folder. You will find two newly generated files: `<your_key_name>.key` and `<your-key-name>.pub`.
4. Copy the content of `<your_key_name>.pub`.
5. Go to the GitHub portal and click on your account picture, then **Settings**.
6. Navigate to the **SSH and GPG keys** section.
7. Click the **New SSH key** button.
8. Give your key a name and paste the content of `<your_key_name>.pub` into the **Key** field.
9. Press the **Add SSH key** button.

## Step 3: Initialize Local Git Repository

1. Create an empty folder.
2. Open Visual Studio Code and open your new folder.
3. Open Terminal in Visual Studio Code.
4. Initialize the git repository with `git init`.
5. Go back to GitHub and add your empty repository as a remote using `git remote add origin <SSH URL>`.
6. Create a new empty `README.md` file.
7. Stage the `README.md` file using `git add README.md`.
8. Make the initial commit with `git commit -m 'Initial Commit'`.
9. Push your repository to GitHub with `git push origin main`.

## Step 4: Create Static Web App Code

1. In Visual Studio Code, create a new file named `index.html` with the following HTML structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Web App</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Welcome to My Simple Web App</h1>
    </header>
    <main>
        <p>This is a basic static web app designed to be deployed on Azure Web Apps.</p>
        <button id="clickMeBtn">Click Me!</button>
    </main>
    <script src="script.js"></script>
</body>
</html>
```

2. In Visual Studio Code, create a new file named `Style.css` with the following CSS structure:
```
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    flex-direction: column;
}

header h1 {
    color: #333;
}

main p {
    margin: 20px;
    font-size: 1.2rem;
}

button {
    padding: 10px 20px;
    font-size: 1rem;
    cursor: pointer;
}
```

3. In Visual Studio Code, create a new file named `script.js` with the following code:

```
document.getElementById('clickMeBtn').addEventListener('click', function() {
    alert('Thanks for clicking me!');
});

```

4. Launch the terminal within Visual Studio Code to start executing your commands.- 

5. Commit the changes and push them to the remote repository with the following commands:

```bash
git add .
git commit -m 'Add simple web app'
git push origin main
```

## Step 5: Create Static Web App in Azure
1. Login to Azure.
2. Click **Create a resource** and search for **Static Web App**.
3. Choose **Static Web App** in the marketplace and press **Create**.
4. Define basic parameters for your Static Web App.

![azure_config](https://myfirststaticwebappsa.blob.core.windows.net/screenshoots/Azure web-app-config.PNG)

#### Azure Static Web App Configuration Parameters

- **Subscription**: Choose your active Subscription.
- **Resource Group**: Press "create new" and type `my-first-static-web-app`.
- **Name**: `my-first-static-web-app-<your-name>` (Replace `<your-name>` with your actual name).
- **Plan type**: Select "Free".
- **Region**: Choose the closest to you region.
- **Source**: GitHub

##### GitHub Configuration

- **GitHub Account**: Press "click here to login" and login into your GitHub account and give Azure the required permissions.
- **Organization**: Choose your account name.
- **Repository**: Choose the repository we created earlier.
- **Branch**: Choose the branch "main".

5. press **Review + create** and finally **Create**.
6. Wait for the deployment to finish, then go to the resource.
7. Wait approximately 3-5 minutes for GitHub Actions to finish the deployment. Copy the URL of your Web App and open it in a new browser tab.

