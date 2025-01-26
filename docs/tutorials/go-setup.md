# Setting up a dev container for Go
* Primary author: [Akshaya Sundar] (https://github.com/sundarak)

> **Note:** Some instructions (Parts 1 & 2) directly adapted from Comp 423 Mkdocs Tutorial (Kris Jordan 2025)


* Reviewer: [Lydia](https://github.com/lydiaschneider)

## Prerequisites:
Before we dive in, make sure you have:

* **A GitHub account**: If you don’t have one yet, sign up at [GitHub](https://github.com/).
* **Git installed**: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don’t already have it.
* **Visual Studio Code** (VS Code): Download and install it from [here](https://code.visualstudio.com/).
* **Docker installed**: Required to run the dev container. [Get Docker here](https://www.docker.com/products/docker-desktop).
* **Command-line basics**: Your COMP211 command-line knowledge will serve you well here. If in doubt, review the Learn a CLI text!

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
    
    The devcontainer.json file defines the configuration for your development environment. Here, we're specifying the following:

    * **name**: A descriptive name for your dev container.
    * **image**: The Docker image to use, in this case, the latest version of a Go environment. Microsoft maintains a collection of base images for many programming language environments, but you can also create your own!
    * **customizations**: Adds useful configurations to VS Code, like installing the Go extension. When you search for VSCode extensions on the marketplace, you will find the string identifier of each extension in its sidebar. Adding extensions here ensures other developers on your project have them installed in their dev containers automatically.
    ```json
    {
        "name": "Go Tutorial",
        "image": "mcr.microsoft.com/devcontainers/go:latest",
        "customizations": {
            "vscode": {
                "settings": {},
                "extensions": ["golang.go"]
            }
        }
        },
        "postCreateCommand": "go mod tidy && go install golang.org/x/tools/gopls@latest",
    }
    
    ```

### Step 2: Reopen the Project in a VSCode Dev Container

Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.

!!! warning "Ensure Docker is running before attempting to reopen"

Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running:

``` 
go version 
``` 

To see your dev container is running a recent version of Go without much effort!


## Part 3: Create simple "Hello Comp423" Go program

### Step 1: Create *main.go* file

``` go
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```

### Step 2: Initialize Go module

* Initialize a go module using:
```bash
go mod init go-tutorial
```
This creates a new go.mod file, which tracks all the dependencies in your project and makes sure it is versioned correctly. 

### Step 3: Compile and run program

* Open a terminal and navigate to the directory containing main.go.

* Run the program using:
``` bash
go run main.go
```

### Step 4: Make binary executable file

* Open a terminal and navigate to the directory containing main.go.

* Build the program:
```bash
go build main.go
```
This will create a binary executable file named main. 

* Run the executable:
```bash
./main
```
We run the executable just like always, as done in 211.

> **Note:** ``` go run ``` compiles and executes the main package in one step and is best used for quick testing. It does not create an executable file. ``` go build ``` compiles the program into a binary executable. It is similar to Comp 211's gcc subcommand, which creates the a.out file (the default ouput file given by gcc compiler), which is then executed using ./a.out. While we use the gcc subcommand for C programs, ``` build ``` is used for go.


## Conclusion
Congrats! In this Go Tutorial, you created a basic program that outputs "Hello COMP423". You also learned how to start from a blank repository and initialize git and how to set up a development container for the Go programming language from scratch.




This looks good so far!
