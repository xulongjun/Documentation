# Developer duty

Here is the explanation of a developer's duty with GitLab. In GitLab repositories, the GitFlow is the branching strategy that has been put in place. 
[You can look at an overview of this strategy here](https://gitversion.net/docs/learn/branching-strategies/gitflow/). 

It has two branches. 
  * One call Main, that represents what has been delivered.
  * One call Develop, that represents what has been developed since the last release.

The developer has 3 duty : 
1. Feature development
2. Bug fixes in production
3. Preparing releases


# 1. Feature development

In this section, we outline the process for developers to create a local feature branch for new user stories, adhering to the GitFlow branching strategy. This ensures that new features are developed in isolation, improving codebase stability and facilitating parallel development.

## Step 1: Create a New Feature Branch

To start working on a new feature, you'll need to create a feature branch based on the develop branch. Here are the steps to follow using the Git command line:

1. **Switch to the Develop Branch**

   Ensure you're on the `develop` branch, from which you'll branch out. If you're not already on `develop`, switch to it using:

   ```bash
   git checkout develop
   ```

2. **Pull the Latest Updates**

   Before creating a new feature branch, ensure your `develop` branch is up to date with the remote repository. This minimizes merge conflicts and ensures 
   you're working with the latest codebase.

   Execute the following command to pull the latest updates from the remote `develop` branch:

   ```bash
   git pull origin develop
   ```

3. **Create a New Feature Branch**

   To start working on your feature, create a branch of the `develop` branch. Use a descriptive name for your branch that reflects the feature you're working on. The convention is `feature/<feature-name>`.

   ```bash
   git checkout -b feature/<feature-name>
   ```


## Step 2: Develop Your Feature

Develop your feature locally, commit your changes frequently, and push your branch to the remote repository regularly to ensure your work is backed up.

1. **Committing Changes**

   As you make progress, commit your changes with meaningful messages. This keeps the project history clear and informative.

   ```bash
   git add .
   git commit -m "A descriptive message about the change"
   ```

2. **Push your feature branch to the remote repository**

   ```bash
   git push -u origin feature/<feature-name>
   ```

## Step 3: Keep Your Feature Branch Up to Date

It's important to regularly merge changes from the develop branch into your feature branch to minimize merge conflicts.

1. **Switch to the develop branch**

   ```bash
   git checkout develop
   ```

2. **Pull the latest changes from origin/develop**

   ```bash
   git pull origin develop
   ```

3. **Switch back to your feature branch**

   ```bash
   git pull origin develop
   ```

4. **Merge changes from develop into your feature branch**

   ```bash
   git merge develop
   ```

## Step 4: Code Review and Pull Request

Once your feature is complete and tested, it's time to merge it into the develop branch. This is done through a pull request.

1. **Push your branch to the remote repository, if you haven't already**

   ```bash
   git push origin feature/<feature-name>
   ```

2. **Go to the repository on your Git hosting service (e.g., GitHub, Bitbucket, GitLab) and create a new pull request for your feature branch into the develop branch.**

3. **Fill out the pull request form with a title and description that clearly describes the feature and any relevant details. Assign reviewers as per your project's workflow.**

4. **Once the pull request is approved and any discussions are resolved, merge your feature branch into develop.**

5. **Delete the Feature Branch**
   After your feature branch has been successfully merged, it's good practice to delete the branch from the remote repository to keep the branch list clean.
   Delete the remote feature branch:

   ```bash
   git push origin --delete feature/<feature-name>
   ```

   Optionally, delete the local branch if you no longer need it:

   ```bash
   git branch -d feature/<feature-name>
   ```


# 2. Bug fixes in production

## Step 1: Create a Hotfix Branch

Hotfix branches are created from the `main` branch, which represents the current production state.

1. **Switch to the `main` branch:**

   ```bash
   git checkout main
   ```

2. **Pull the latest changes from the remote repository to ensure your local copy is up to date**

   ```bash
   git pull origin main
   ```

3. **Create a new hotfix branch with a descriptive name that includes the version number and a brief hint about the bug, e.g.**

   ```bash
   git checkout -b hotfix/<VersionNumber>-fix-<ErrorName>
   ```
   For example hotfix/2.4.1-fix-login-error

   ```bash
   git checkout -b hotfix/2.4.1-fix-login-error
   ```

## Step 2: Fix the Bug

Work on your hotfix branch to address the bug. Keep your changes as focused as possible to avoid introducing new issues.
Commit your changes with a clear and detailed commit message. 

## Step 3: Review and Test the Hotfix

Before merging the hotfix into production, it must be reviewed and tested carefully to ensure it does not introduce new issues.

1. **Push the hotfix branch to the remote repository**

   ```bash
   git push origin hotfix/<VersionNumber>-fix-<ErrorName>
   ```

2. **Create a pull request from your hotfix branch to the main branch. Ensure that the pull request undergoes a thorough review process by the team**

3. **After approval, merge the hotfix into main. Do not delete the hotfix branch yet, as it will also need to be merged into develop**

## Step 4: Deploy the Hotfix

Once the hotfix is merged into the production branch, deploy the changes to the production environment according to your project's deployment process.

## Step 5: Merge the Hotfix into Develop

1. **Switch and pull to the develop branch**

   ```bash
   git checkout develop
   git pull origin develop
   ```

2. **Merge the hotfix branch into develop**

   ```bash
   git merge --no-ff hotfix/<VersionNumber>-fix-<ErrorName>
   ```

3. **Resolve any merge conflicts that arise and commit the merge**

4. **Push the updated develop branch to the remote repository**

   ```bash
   git push origin develop
   ```

## Step 6: Clean Up

After the hotfix has been successfully merged into both main and develop, you can delete the hotfix branch.

1. **Delete the hotfix branch**

   ```bash
   git push origin --delete hotfix/<VersionNumber>-fix-<ErrorName>
   ```

   Optionally, delete the local hotfix branch if you no longer need it:

   ```bash
   git branch -d hotfix/<VersionNumber>-fix-<ErrorName>
   ```

# 3. Preparing releases