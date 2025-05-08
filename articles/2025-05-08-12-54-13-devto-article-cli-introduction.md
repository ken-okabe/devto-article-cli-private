---
title: All-in-One GitHub Repository-Driven Dev.to Article Management System
published: false
tags:
  - devto
  - cli
  - nodejs
  - markdown
description: >-
  A comprehensive tool for managing Dev.to articles using GitHub repository as a
  central hub. Write in Markdown, version with Git, and publish with simple
  commands.
dev_to_article_id: 2467633
---

Welcome to `devto-article-cli`!

This repository is designed to be your **central hub for managing Dev.to articles**.

It not only contains the Node.js command-line tool itself but also serves as the primary storage and version control system for your article content (typically within the `articles/` directory). The included CLI scripts empower you to seamlessly create, edit (in Markdown), version with Git, and publish your Dev.to articles directly from this integrated, local-first environment.

<img width="100%" src="https://raw.githubusercontent.com/ken-okabe/web-images/main/note.svg">

## Features

-   Write articles locally and use Git for version control
-   Publish new articles and update existing ones on Dev.to with simple commands
-   Automatically appends Dev.to article ID to Markdown files upon publishing
-   **Automatic Image Handling**: Converts local relative image paths in your Markdown to absolute GitHub URLs when publishing to Dev.to, while keeping your local files unchanged for easy previewing
-   Check consistency between local articles and Dev.to
-   No CI needed; everything is handled in your local environment
-   Fully automates `git add`, `git commit`, and `git push` for the publishing workflow
-   Compliant with the latest [Forem API V1 (1.0.0)](https://developers.forem.com/api)

## Prerequisites

-   Node.js (LTS recommended)
-   Git
-   Dev.to account and API Key

## Setup

1.  Fork this Repository (Recommended):
    Fork the devto-article-cli repository to your own GitHub account. This creates your personal copy where your articles will be stored.
    
2.  **Clone Your Forked Repository**:
    ```bash
    git clone https://github.com/YOUR_USERNAME/devto-article-cli.git
    cd devto-article-cli
    # Replace YOUR_USERNAME with your GitHub username.
    ```
    
3.  Install Dependencies:
    ```bash
    npm install
    ```

4.  Build TypeScript:
    ```bash
    npm run build
    ```
    
5.  Set Dev.to API Key:
    
    Obtain your API key from your Dev.to Settings > Extensions page.

    ![image](https://raw.githubusercontent.com/ken-okabe/web-images5/main/img_1746675165695.png)

    ![image](https://raw.githubusercontent.com/ken-okabe/web-images5/main/img_1746675216227.png)

    Set it as an OS environment variable named `DEV_TO_API_KEY`.
    
    -   **Windows (Command Prompt/PowerShell)**:
        ```bash
        # Command Prompt
        setx DEV_TO_API_KEY "your_api_key"
        # PowerShell
        [System.Environment]::SetEnvironmentVariable('DEV_TO_API_KEY', 'your_api_key', 'User')
        ```
        
    -   macOS (if using zsh):
        ```bash
        echo 'export DEV_TO_API_KEY="your_api_key"' >> ~/.zshrc && source ~/.zshrc
        ```
        
    -   Linux (if using bash):
        ```bash
        echo 'export DEV_TO_API_KEY="your_api_key"' >> ~/.bashrc && source ~/.bashrc
        ```

6.  Configure Git:
    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your.email@example.com"
    ```

## Core Commands

### 1. Create a New Article

```bash
npm run article:new
```

This command will:
- Prompt for article title and slug
- Create a new Markdown file with proper front-matter
- Place the file in the `articles/` directory

### 2. Publish/Update Articles

```bash
npm run article:publish
```

This command will:
- Publish new articles or update existing ones
- Convert local image paths to GitHub URLs
- Handle git operations automatically
- Add article IDs to your local files

### 3. Check Consistency

```bash
npm run article:check
```

This command helps you verify that your local articles match what's on Dev.to.

## Important Note About Images

<img width="100%" src="https://raw.githubusercontent.com/ken-okabe/web-images/main/note.svg">

When posting with images from a repository, the forked repository must be public because Dev.to cannot access images in private GitHub repositories.

For text-only posts, the forked repository can be private as no such web links are generated. Alternatively, if images are hosted separately where Dev.to can access them, the forked repository can also remain private.

<img width="100%" src="https://raw.githubusercontent.com/ken-okabe/web-images/main/notefooter.svg">

