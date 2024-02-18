# GitLab Repository Setup Guide: Implementing GitFlow

Here is the explanation of how to setup GitFlow branching strategy In GitLab repositories
[You can look at an overview of this strategy here](https://gitversion.net/docs/learn/branching-strategies/gitflow/). 

Prerequisites : 
- A GitLab account
- Basic understanding of Git and the GitFlow branching strategy
- Appropriate permissions to create new repositories in GitLab

# 1. Create a New Project (Skip this if you are working on an existing project)

## Step 1: Create a New Project in Gitlab

- Click on the "New project" button from the dashboard.
- Choose a project name that reflects your naming conventions. For projects following GitFlow, consider a name that easily identifies your project's scope and purpose.
- Fill in the project description, visibility level (private, internal, or public), and any other necessary details.
- It's recommended to select "Initialize repository with a README" to enable immediate cloning and workflow setup.
- Click on the "Create project" button. 

## Step 2: Cloning the Project Locally

After the project is created, navigate to the project's main page on GitLab. Find the "Clone" button and copy the URL for cloning.Open your terminal, navigate to where you want to place your project, and run:

   ```bash
   git clone <REPOSITORY_URL>
   ```

## Step 3: Preparing Initial Files

1. **Add .gitignore File**

   Create a .gitignore file in your project directory to specify intentionally untracked files to ignore. We can use template for the different kind of project. 

2. **Add GitLab CICD Configuration File (if exists)** 

   Create a file named .gitlab-ci.yml at the root of your repository. This file will define your CI/CD pipeline in GitLab.

## Step 4: Preparing the Code and pushing the First Version to Main

Before pushing your first version, make sure your codebase is clean and follows the project's coding standards. Perform any necessary cleanup, refactoring, or organization of your project structure.

1. **Commit and Push**

   ```bash
   git add .
   git commit -m "Initial commit with project setup"
   git push origin main
   ```

# 2. Creating the Develop Branch (If Not Already Done)

1. **switch to your main branch and pull the latest changes**

   ```bash
   git checkout main
   git pull origin main
   ```

2. **Create the develop branch and Push the develop branch to the remote repository**

   ```bash
   git checkout -b develop
   ```

3. **Push the develop branch to the remote repository**

   ```bash
   git push origin develop
   ```

# 3. Setting Up User Permissions (To be defined)

## Step 1: Add Team Members and Assign Roles

[You can look at the documentation Gitlab here](https://docs.gitlab.com/ee/user/project/members/).  

Select the appropriate role for each team member. GitLab roles include Guest, Reporter, Developer, Maintainer, and Owner, each with different levels of access and permissions.

Assign a "Maintainer" role to team members who need to create protected branches or manage project settings.
Developers who contribute to the codebase should be assigned the "Developer" role.

# 4. Configuring Branch Protection Rules (Optional and To be defined)

[You can look at the documentation Gitlab here](https://docs.gitlab.com/ee/user/project/protected_branches.html).

## Step 1: Protect the main Branch

1. **Navigate to Repository Settings Protected Branches section** 

Within your project in GitLab, go to "Settings" > "Repository."

Scroll down to find the "Protected Branches" section.

3. **Configure the protection settings**

Allowed to merge: Choose "Maintainers" and "developer" to ensure only maintainers and "developer" can merge changes into main.

Allowed to push: Typically, you would also restrict push access to "Maintainers" and "developer" to safeguard your production code.


## Step 2: Protect the developer Branch

Repeat the protection process for the develop branch.

This ensures that direct pushes are controlled and that changes are introduced through merge requests, maintaining the integrity of your development efforts.

# 5. Configure Merge Request Approvals and CI/CD Checks in GitLab (Optional and To be defined)

[You can look at the documentation Gitlab here](https://docs.gitlab.com/ee/user/project/merge_requests/approvals/rules.html).

## Step 1: Add Approval rules

Within your project in GitLab, go to "Settings" > "Merge requests"

Scroll down to find the "Merge request approvals" section.

**Add rules example** : 

- In the "Approval rules" section, you can define who can approve merge requests and how many approvals are required.
- Click on "Add approval rule."
- Name your rule (e.g., "Developer Approval").
- Set the number of required approvals to 1.
- Under "Eligible approvers," select the roles or individuals who are allowed to approve merge requests. To fulfill the requirement of at least one developer   approving, ensure you include the "Developer" role or specific individuals with developer permissions.
- Click "Add rule" to save your configuration.

## Step 2: Ensuring CI Passes Before Merging

- Make sure you have a .gitlab-ci.yml file in your repository root that defines your CI pipeline. This file specifies the jobs that need to be run and under what conditions.
- Within your project in GitLab, go to "Settings" > "Merge requests"
- Ensure the option "Pipelines must succeed" is enabled. This setting ensures that merge requests can only be merged if the associated pipeline has passed successfully, indicating no issues were found in the CI process.