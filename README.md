# hugo-mock-landing-page-autodeployed

# hugo-mock-landing-page

# TabTastic - A Chrome Extension Mock Landing Page

TabTastic is a Chrome Extension that transforms your new tab page into a personalized, customizable experience!

## Overview

TabTastic aims to enhance your productivity and browsing experience by offering a range of customizable features directly on your new tab page. Whether you want quick access to your favorite websites, see your to-do list at a glance, or enjoy a fresh wallpaper every day, TabTastic has you covered.

This repository contains the source code for the mock landing page of the TabTastic Chrome Extension, built using Hugo and Bootstrap.

## Features

- **Quick Access Links:** Easily access your most visited websites with just a click. Add, remove, or reorder links as per your preference.
- **To-Do List:** Keep track of your tasks and stay organized. Add new tasks, mark them as completed, and remove tasks once done.
- **Custom Backgrounds:** Enjoy a new wallpaper every day or set your own custom background image or color to personalize your browsing experience.
- **Weather Updates:** Get the latest weather information for your location right on your new tab page. Stay informed about the current weather conditions and forecast.
- **Notes:** Jot down quick notes and ideas directly on your new tab page. Never lose track of your thoughts and to-dos.
- **Inspirational Quotes:** Start your day with a dose of motivation. Display a new inspirational quote each time you open a new tab.

## Installation

### Prerequisites

To set up this project locally, you need to have the following tools installed:

- [Hugo](https://gohugo.io/getting-started/installing/): A fast and flexible static site generator written in Go.
- [Node.js](https://nodejs.org/): JavaScript runtime built on Chrome's V8 JavaScript engine, used for managing dependencies.

### Clone the Repository

First, clone the repository to your local machine using Git:

```bash
git clone https://github.com/<your-username>/hugo-mock-landing-page.git
cd hugo-mock-landing-page
Install Dependencies
Navigate to the project directory and install the necessary dependencies:

bash
Copy code
npm install
Run the Development Server
Start the Hugo development server to view the mock landing page locally:

bash
Copy code
hugo server
Open your browser and go to http://localhost:1313 to see the landing page in action.

Usage
Setting Up the Extension
Open Google Chrome and go to chrome://extensions/.
Enable "Developer mode" by toggling the switch in the top right corner.
Click on "Load unpacked" and select the directory where your TabTastic extension files are located.
The TabTastic extension should now appear in the list of installed extensions.
Customizing Your New Tab
Open a new tab to see the TabTastic interface.
Use the options available to customize your new tab page according to your preferences:
Set Quick Access Links: Add your most frequently visited websites for easy access.
Manage To-Do List: Add new tasks, mark them as done, and remove tasks when completed.
Choose Custom Backgrounds: Select a daily changing wallpaper or set your own background image/color.
Get Weather Updates: Enter your location to receive real-time weather updates.
Write Notes: Use the notes section to jot down anything important.
Read Inspirational Quotes: Get inspired with new quotes every time you open a tab.
Saving Your Preferences
Your custom settings will be saved automatically, ensuring a consistent experience every time you open a new tab.

Automating the Deployment of the Hugo Website
This repository includes a GitHub Actions workflow to automate the process of building and deploying the Hugo website to GitHub Pages.

Step-by-Step Workflow Description
Import Your Repository:

Import your hugo-mock-landing-page repository as hugo-mock-landing-page-autodeployed using GitHub Importer.
Adjust the baseURL in the config.toml File:

Update the baseURL in the config.toml file to reflect the new repository name:
toml
Copy code
baseURL = 'https://<GitHub username>.github.io/hugo-mock-landing-page-autodeployed/'
Commit and push this change.
Configure the Repository Settings:

Configure the default GITHUB_TOKEN permissions to have Read and write permissions.
Set the publishing source to gh-pages for GitHub Pages.
Allow all actions and reusable workflows in the GitHub Actions permissions settings.
Add a GitHub Actions Workflow to Automate the Deployment:

Create a .github/workflows/gh-pages-deployment.yaml file with the following content:
yaml
Copy code
#######################################################
## Build and Deploy Hugo Website to GitHub Pages
## Author: Jérémie Lumbroso <lumbroso@seas.upenn.edu>
## Date: 2024-02-24
#######################################################

name: 🏗️ Build and Deploy GitHub Pages

on:
  push:
    branches:
      - main # Set a branch to deploy

jobs:
  deploy:
    runs-on: ubuntu-22.04
    steps:
      - name: 🔄 Check Out Source Repository
        uses: actions/checkout@v3.5.1
        with:
          submodules: true # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0 # Fetch all history for .GitInfo and .Lastmod

      - name: 🛠️ Initialize Hugo Environment
        uses: peaceiris/actions-hugo@v2.6.0
        with:
          hugo-version: "0.123.4"
          extended: true

      - name: 🏗️ Compile Hugo Static Files
        run: hugo -D --gc --minify

      - name: 🚀 Publish to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3.9.3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_branch: gh-pages
          user_name: "github-actions[bot]"
          user_email: "github-actions[bot]@users.noreply.github.com"
          ## NOTE: uncomment below if using a custom domain
          ## cname: mydomain.com
Commit and push the changes to your hugo-mock-landing-page-autodeployed repository.
Check the Deployment of the Website:

Go to the “Actions” tab in your repository to see the workflow running.
Once the workflow is complete, the deployed website should be accessible at:
bash
Copy code
https://<GitHub username>.github.io/hugo-mock-landing-page-autodeployed/
Make a Change to the Website and Check the Deployment:

Make a change to the website (e.g., update content/contact.md) and commit and push the change.
This should trigger the GitHub Actions workflow again, and the change should be reflected on the website.
Understanding the GitHub Actions Workflow
In the README.md file of the hugo-mock-landing-page-autodeployed repository, the GitHub Actions workflow for building and deploying the Hugo website to GitHub Pages is detailed. The workflow, triggered by changes pushed to the main branch, consists of essential steps such as checking out the source repository, initializing the Hugo environment with a specific version, compiling static files, and publishing to GitHub Pages using the peaceiris/actions-gh-pages action. The workflow leverages the GitHub token stored in secrets.GITHUB_TOKEN for authentication, ensuring secure access for pushing changes to the repository. Notably, the "publish_branch" parameter specifies the branch (gh-pages) where the compiled website is deployed. The README captures insights from a conversation with Claude, emphasizing the nested structure of keys in YAML, the syntax for accessing secrets, and the use of [bot] in user credentials to denote automated accounts. By incorporating these details, the README provides a comprehensive overview of the automated deployment process, enhancing understanding for repository visitors and collaborators.

Contributing
We welcome contributions to improve TabTastic! If you have suggestions or encounter issues, please open an issue or submit a pull request on the GitHub repository.

Steps to Contribute
Fork the repository.
Create a new branch (git checkout -b feature-branch).
Make your changes and commit them (git commit -m 'Add some feature').
Push to the branch (git push origin feature-branch).
Open a pull request.
License
This project is licensed under the MIT License. See the LICENSE file for details.

Contact
For any inquiries or feedback, please contact us at kjonny3@gmail.com.

Thank you for using TabTastic! We hope it enhances your browsing experience and productivity.
