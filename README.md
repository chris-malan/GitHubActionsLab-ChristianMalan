**
# GitHub Actions Lab – Christian Malan
# SYST38634 Software Process Management
**

## Overview
This repository demonstrates the use of GitHub Actions to automate workflows for our in-class 5 at SYST38634 Software Process Management .  
Two workflows were created to show job dependencies and multi-platform testing.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Workflow 1: Dependent Jobs Workflow

### Purpose
The purpose of this first workflow is to demonstrate how jobs can be executed in a specific order using dependencies.  
The jobs run sequentially in the following order:
1. Build
2. Test
3. Deploy

This workflow helps us shows and demonstrate a basic CI/CD pipeline.

Each job simulates part of a typical CI/CD pipeline and includes multiple steps to show progression.

### **Key Concepts Demonstrated**
- **1. needs**
  Defines job dependencies.  
  Example:  `test` will not start until `build` finishes successfully.

- **2. runs-on**  
  Specifies the virtual machine used for each job (`ubuntu-latest`).

- **3. env**  
  Demonstrates how environment variables can be set at workflow, job, or step level (if used).

### **What This Workflow Shows**
- How to enforce strict job order  
- How GitHub Actions visualizes dependencies  
- How CI/CD pipelines typically structure build → test → deploy stages  

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Workflow 2: Multi-Platform Testing Workflow

## Purpose
This workflow demonstrates how to run independent jobs in parallel on different operating systems.  
It includes three jobs:
- ubuntu-job - (Ubuntu)
- windows-job - (Windows)
- macos-job - (macOS)
**#Each job checks out the code, prints OS information, creates a file, and displays its contents.**


### Key Concepts Demonstrated
- **1. runs-on**: Used to run jobs on different operating systems.
- **2. Parallel execution**: Since no `needs` keyword is used, jobs run simultaneously.
- **3. actions/checkout@v4**: Checks out the repository code.
- **4. Environment variables (env)**: Displays the runner operating system.
- **5. OS-specific commands**: Uses different commands based on the operating system.
- **6. File creation and output**: Each job creates a file and displays its contents.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Challenges Faced and Resolutions

### Branch and Workflow Triggers
One challenge that I encounter during this inclass exercise was ensuring that the workflows triggered correctly based on the branch name.  
This was resolved by confirming the repository used the `main` branch and updating workflow triggers accordingly.

### YAML Syntax and Indentation
Another challenge was YAML syntax errors caused by incorrect indentation and multi-line commands.  
This was resolved by:
- Using proper indentation
- Using the `|` symbol for multi-line `run` commands
- Using : in  "run: echo "Runner OS : $RUNNER_OS" will give you an syntax errora

### Pull Request Testing
Understanding that the multi-platform workflow only runs on pull requests was initially confusing.  
This was resolved by creating a separate testing branch and opening a pull request to the `main` branch.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Conclusion
These workflows demonstrate how GitHub Actions can automate processes, enforce job order, and run tests across multiple platforms.  
They highlight the importance of CI/CD pipelines and automation in modern software development.
