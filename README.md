# GitHub Actions Lab – Christian Malan  
SYST38634 Software Process Management

## Overview
This repository demonstrates the use of GitHub Actions to automate workflows for the in-class 5 activity in **SYST38634 Software Process Management**.  
Two workflows were created to demonstrate job dependencies and multi-platform testing using GitHub Actions.

---

## Workflow 1: Dependent Jobs Workflow

### Purpose
The purpose of this workflow is to demonstrate how jobs can be executed in a specific order using dependencies.  
The jobs run sequentially in the following order:

- Build  
- Test  
- Deploy  

This workflow helps demonstrate a basic CI/CD pipeline where each stage must complete successfully before the next one starts.

Each job simulates part of a typical CI/CD process and includes multiple steps to show the progression of work.

---

### Key Concepts Demonstrated

**needs**  
Used to define job dependencies. For example, the test job will not start until the build job finishes successfully.

**runs-on**  
Specifies the virtual machine used for each job, such as `ubuntu-latest`.

**env**  
Demonstrates how environment variables can be used within workflows, jobs, or steps when needed.

---

### What This Workflow Shows
- How to enforce a strict execution order between jobs  
- How GitHub Actions visually displays job dependencies  
- How a typical CI/CD pipeline is structured (build → test → deploy)

---

## Workflow 2: Multi-Platform Testing Workflow

### Purpose
This workflow demonstrates how independent jobs can run in parallel on different operating systems.  
It includes three separate jobs:

- `ubuntu-job` (Ubuntu)  
- `windows-job` (Windows)  
- `macos-job` (macOS)  

Each job checks out the repository, prints operating system information, runs an OS-specific command, creates a file, and displays its contents.

---

### Key Concepts Demonstrated
- **runs-on**: Used to run jobs on different operating systems  
- **Parallel execution**: Jobs run simultaneously since no `needs` keyword is used  
- **actions/checkout@v4**: Checks out the repository code  
- **Environment variables (env)**: Displays the runner operating system  
- **OS-specific commands**: Different commands are used depending on the OS  
- **File creation and output**: Each job creates and displays a simple file

---

## Challenges Faced and Resolutions

### Branch and Workflow Triggers
One challenge I encountered was making sure the workflows triggered correctly based on the branch name.  
This was resolved by confirming the repository was using the `main` branch and updating the workflow triggers accordingly.

---

### YAML Syntax and Indentation
Another challenge was YAML syntax errors caused by incorrect indentation and formatting of multi-line commands.  
This was resolved by:
- Carefully fixing indentation  
- Using the `|` symbol for multi-line `run` commands  
- Avoiding syntax errors caused by unquoted colons in `run` statements (e.g., `Runner OS : $RUNNER_OS`)

---

### Pull Request Testing
At first, it was confusing why the multi-platform workflow was not running automatically.  
This was resolved by realizing the workflow only runs on pull requests, so a separate testing branch was created and merged into the `main` branch through a pull request.

---

## Conclusion
These workflows demonstrate how GitHub Actions can be used to automate tasks, control job execution order, and test applications across multiple platforms.  
They show the importance of CI/CD pipelines and automation in modern software development.
