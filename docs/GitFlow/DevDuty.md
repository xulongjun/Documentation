# Developer duty

Here is the explanation of a developer's duty with GitHub. In GitHub repositories, the GitFlow is the branching strategy that has been put in place. 
[You can look at an overview of this strategy here](https://gitversion.net/docs/learn/branching-strategies/gitflow/). 

It has two branches. 
  * One call Master, that represents what has been delivered.
  * One call Develop, that represents what has been developed since the last release.

# 1. Feature to develop

In this section, we outline the process for developers to create a local feature branch for new user stories, adhering to the GitFlow branching strategy. This ensures that new features are developed in isolation, improving codebase stability and facilitating parallel development.

## Step 1: Create a New Feature Branch

To start working on a new feature, you'll need to create a feature branch based on the develop branch. Here are the steps to follow using the Git command line:

1. **Switch to the Develop Branch**

   Ensure you're on the `develop` branch, from which you'll branch out. If you're not already on `develop`, switch to it using:

   ```bash
   git checkout develop

2. **Pull the Latest Updates**

   Before creating a new feature branch, ensure your `develop` branch is up to date with the remote repository. This minimizes merge conflicts and ensures 
   you're working with the latest codebase.

   Execute the following command to pull the latest updates from the remote `develop` branch:

   ```bash
   git pull origin develop

3. **Create a New Feature Branch**

   To start working on your feature, create a branch of the `develop` branch. Use a descriptive name for your branch that reflects the feature you're working on. The convention is `feature/<feature-name>`.

   ```bash
   git checkout -b feature/<feature-name>


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

## Step 3: Keep Your Feature Branch Up to Date

It's important to regularly merge changes from the develop branch into your feature branch to minimize merge conflicts.

1. **Switch to the develop branch**

   ```bash
   git checkout develop

2. **Pull the latest changes from origin/develop**

   ```bash
   git pull origin develop

3. **Switch back to your feature branch**

   ```bash
   git pull origin develop

4. **Merge changes from develop into your feature branch**

   ```bash
   git merge develop

## Step 4: Code Review and Pull Request

Once your feature is complete and tested, it's time to merge it into the develop branch. This is done through a pull request.

1. **Push your branch to the remote repository, if you haven't already**

   ```bash
   git push origin feature/<feature-name>

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


# 2. Bug in production

## 2.1. Create a local fix branch for a bug correction.

When you have a new fix to correct, you need to create a new branch from the master branch. 
In Visual Studio :
	1. Go to "Team Explorer";
	2. Click on the project of the US in. If you don't see that option, [configure GitHub Connection in Visual Studio](./VisualStudioGitHubConnection.md);
	3. Click on or clone the repository of the project to your computer;
	4. Click on "Git Repository";
	5. Click on remotes => origin => master;
	6. Right click on master and select "New local branch from...";
	7. Name the branch like this : need to have the prefix "fix" then "/" and then the bug number or a short description title without space. Ex: "fix/ASD-8882";
	8. Click on create.
		
You now have your local branch created and can do your duty on it.
You will use this created branch until you are ready to merge to the master branch.

## 2.2. Commit to the feature branch.

1. Go to "Team Explorer";
2. Go to "Git Changes";
3. Click on the fetch down arrow to look if new commit on the branch have been done by another developer;
	* if it is the case, do a pull request (arrow just after the pull request arrow) then correct merge issues if it has.
4. Enter a message for your commit and click on commit button;
5. Click on the push arrow up button to push back your change to the server. 

** You can have multiple commits on your local computer and commit it in one time, but it is recommended to commit as you create your commit. **

## 2.3. The fix development are over.

You now have finished the development of the fix and have to merge to the master branch.  

1. Go to "Git Changes" in Visual Studio;
2. Open your branch and click on "Remotes" and select "origin/master";
3. Click on "Merge into Current branch";
4. Resolve any merge conflict then commit and push the result;
5. Go to your GitHub project;
6. Click on "pull request" and then on "New pull request";
7. Select "master" as target branch and complete the pull request information if needed then create it;
8. Wait for the review from your tech lead.

## 2.4. You have receive a pull request review to accomplish.

1. Follow the link received in the email;
2. Approve, ask for a change or refuse the pull request.

## 2.5. Your pull request review is done.

1. Click on "Attemp merge";
2. Delete your branch if the development are over.

Your code is now merged on the master branch.

## 2.6. Create pull request to develop.

1. Go to your GitHub project;
2. Click on "pull request" and then on "New pull request";
3. Select "develop" as target branch and complete the pull request information if needed then create it;
4. Wait for the review from your tech lead.
5. Click on "Attemp merge";

Your code is now merged on the develop branch.

## 3. Merge a remote branch to our branch.

1. Go to "Git Changes" in Visual Studio;
2. Click on your current branch at the top of the screen;
3. Click on "Remotes" and then right click on the branch you want to merge to your current branch. Ex : "origin/develop";
4. Choose the option "Merge into Current Branche";
5. Correct the merge issues and then the modifications on the remote branch is now included in your branch.
