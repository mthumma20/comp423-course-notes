# Setting up a dev container for Rust

* Primary author: [Megha Thumma](https://github.com/mthumma20)

* Reviewer: [Nithya Indlamuri](https://github.com/nithyaindla)

## What is rust?

Rust is a systems-level programming language that focuses on safety, performance, and productivity. It is highly reliable and can be used for a variety of applications, leading it to gain in popularity over recent years. 


## Prerequisites

Before starting, make sure you have:

- Git installed: Install Git if you don't already have it.
- Docker installed and running.
- Visual Studio Code (VS Code) installed.
- The Dev Containers extension installed in VS Code.
- A GitHub account: Sign up at GitHub if not.

!!! warning
    Do **not** install Rust directly on your host machine. Always use the dev container to maintain a consistent environment.

---

## Step 1: Initialize a Git Repository

1. Open your terminal or command prompt. Create a new directory for your project and initialize a Git repository:

    ```title="Initialize Git Repository"
    mkdir rust-dev-container
    cd rust-dev-container
    git init
    ```

2. Create a README file:

    ```title="Add a README File"
    echo "# Rust Dev Container Project" > README.md
    git add README.md
    git commit -m "Initial commit with README"
    ```

3. Navigate to GitHub to the Create a New Repository page. Create a new repo named rust-dev-container, set it to public visibility, and do not initialize any files. Push to a remote repository:

    ```title="Push to Remote Repository"
    git remote add origin https://github.com/<your-username>/rust-dev-container.git
    git branch -M main
    git push -u origin main
    ```

---

## Step 2: Set Up a Development Container

1. Install the Dev Containers extension for VS Code. Create a `.devcontainer` directory in root of your project:

    ```title="Create Dev Container Directory"
    mkdir .devcontainer
    ```

2. Add the `devcontainer.json` file: 

This includes the name of the DevContainer, the Docker image used to create the development environment, customizations, and a command to run after the container is created.

    ```json title=".devcontainer/devcontainer.json"
    {
      "name": "Rust Dev Environment", 
      "image": "mcr.microsoft.com/devcontainers/rust:latest",
      "customizations": {
        "vscode": {
          "extensions": ["rust-lang.rust-analyzer"]
        }
      },
      "postCreateCommand": "cargo install cargo-edit"
    }
    ```

3. Reopen the project in the dev container:

    1. Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac) in VS Code.
    2. Select **Dev Containers: Reopen in Container**.

4. Verify the Rust version inside the dev container:

    ```title="Check Rust Version"
    rustc --version
    ```

!!! note
    The `rustc --version` command makes you are using a recent version of Rust.

---

## Step 3: Create a Rust Project

1. Inside the dev container, use this code to create a new Rust project:

    ```title="Create a New Rust Project"
    cargo new hello-comp423 --vcs none
    cd hello-comp423
    ```

    !!! note
        The `--vcs none` flag makes sure no new Git repository is created in the Rust project.

2. Open and update the `main.rs` file to print "Hello COMP423":

    ```title="src/main.rs"
    fn main() {
        println!("Hello COMP423!");
    }
    ```

---

## Step 4: Build and Run the Program

1. **Build the program**:

    ```title="Build the Program"
    cargo build
    ```

    - This compiles the project into executable in the `target/debug` directory.

    !!! note
        `cargo` handles dependency management and builds the entire project, while `gcc` from COMP 211 focuses on compiling individual source files.

2. **Run the program**:

    ```title="Run the Program"
    cargo run
    ```

    - The `cargo run` command combines building and executing the program in one step, while `cargo build` only compiles without running.


---

## Step 5: Add Your Changes to Git

1. Add and commit your changes:

    ```title="Add and Commit Changes"
    git add .
    git commit -m "Add Rust dev container setup and Hello COMP423 program"
    ```

2. Push to your remote repository:

    ```title="Push Changes to Remote Repository"
    git push origin main
    ```

---

Congrats! You have created a Dev Container project for the Rust language and basic "Hello COMP423" program! 

