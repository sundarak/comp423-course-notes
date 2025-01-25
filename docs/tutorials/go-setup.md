# Setting up a dev container for Go
* Primary author: [Akshaya Sundar] (https://github.com/sundarak)

## Prerequisites:
* Visual Studio Code
* Docker
* Git

## Part 1: Creating the Repository
### Step 1: Create local directory and initialize git

* Open your terminal or command prompt.
* Create a new directory for your project.
```bash
mkdir go-tutorial
cd go-tutorial
```
* Initialize a new Git repository:
```bash
git init
```
* Create a README file
```bash
echo "# COMP423 Go Tutorial" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Step 2: Create a remote repository on GitHub

* Log in to your GitHub account and navigate to the Create a New Repository page.
* Fill in the details as follows:

    * **Repository Name**: go-tutorial

    * **Description**: "Tutorial to create basic hello program in GO"

    * **Visibility**: Public

* Do **NOT** initialize the repository with a README, .gitignore, or license.
* Click **Create Repository**.

### Step 3: Link your Local Repository to GitHub

* Add the GitHub repository as a remote:
``` bash
git remote add origin https://github.com/<your-username>/go-tutorial.git
```

* Check your default branch name with the subcommand git branch. If it's not main, rename it to main with the following command: git branch -M main. Old versions of git choose the name master for the primary branch, but these days main is the standard primary branch name.

* Push your local commits to the GitHub repository:
``` bash
git push --set-upstream origin main
```

* Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been pushed to remote. You can use git log locally to see the commit ID and message which should match the ID of the most recent commit on GitHub. This is the result of pushing your changes to your remote repository.

## Part 2: Setting Up the Development Environment

#### What is a Development (Dev) Container?
A dev container ensures that your development environment is consistent and works across different machines. At its core, a dev container is a preconfigured environment defined by a set of files, typically leveraging Docker to create isolated, consistent setups for development. Think of it as a "mini computer" inside your computer that includes everything you need to work on a specific project—like the right programming language, tools, libraries, and dependencies.

Why is this valuable? In the technology industry, teams often work on complex projects that require a specific set of tools and dependencies to function correctly. Without a dev container, each developer must manually set up their environment, leading to errors, wasted time, and inconsistencies. With a dev container, everyone works in an identical environment, reducing bugs caused by "it works on my machine" issues. It also simplifies onboarding new team members since they can start coding with just a few steps.

### Step 1: Add development container configuration

* In VS Code, open the go-tutorial directory. You can do this via: File > Open Folder.
* Install the **Dev Containers** extension for VS Code.
* Create a .devcontainer directory in the root of your project with the following file inside of this "hidden" configuration directory:

    ***.devcontainer/devcontainer.json***

*






