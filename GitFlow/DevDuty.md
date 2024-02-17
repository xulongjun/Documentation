[Go back home](./README.md)
# Developper duty

Here is the explanation of a developer duty with GitHub. In GitHub repositories, the GitFlow is the branching strategy that has been put in place. 
[You can look an overview of this strategy here](https://gitversion.net/docs/learn/branching-strategies/gitflow/). 

It has two branches. 
  * One call master, that represent what's have been delivered.
  * One call Develop, that represent what have been developped since the last release.

# 1. Feature to develop

## 1.1. Create local feature branch for a new user story.

When you have a new US, you need to create a new branch from the develop branch. 
In Visual Studio :
	1. Go to "Team Explorer";
	2. Click on the project of the US in. If you don't see that option, [configure GitHub Connection in Visual Studio](./VisualStudioGitHubConnection.md);
	3. Click on or clone the repository of the project to your computer;
	4. Click on "Git Repository";
	5. Click on remotes => origin => develop;
	6. Right click on develop and select "New local branch from...";
	7. Name the branch like this : need to have the prefix "feature" then "/" and then the user story title without space. Ex: "feature/updatelog4net";
	8. Click on create.
		
You now have your local branch created and can do your duty on it.
You will use this created branch until you are ready to merge to the develop branch.

## 1.2. Commit to the feature branch.

1. Go to "Team Explorer";
2. Go to "Git Changes";
3. Click on the fetch down arrow to look if new commit on the branch have been done by another developer;
	* if it is the case, do a pull request (arrow just after the pull request arrow) then correct merge issues if it has.
4. Enter a message for your commit and click on commit button;
5. Click on the push arrow up button to push back your change to the server. 

** You can have multiple commits on your local computer and commit it in one time, but it is recommended to commit as you create your commit. **

## 1.3. The US development are over.

You now have finished the development of the user story and have to merge to the develop branch.  

1. Go to "Git Changes" in Visual Studio;
2. Open your branch and click on "Remotes" and select "origin/develop";
3. Click on "Merge into Current branch";
4. Resolve any merge conflict then commit and push the result;
5. Go to your GitHub project;
6. Click on "pull request" and then on "New pull request";
7. Select "develop" as target branch and complete the pull request information if needed then create it;
8. Wait for the review from your pair developer.

## 1.4. You have receive a pull request review to accomplish.

1. Follow the link received in the email;
2. Approve, ask for a change or refuse the pull request.

## 1.5. Your pull request review is done.

1. Click on "Attemp merge";
2. Delete your branch if the development are over.

Your code is now merged on the develop branch.

# 2. Bug in production

## 2.1. Create local fix branch for a bug correction.

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