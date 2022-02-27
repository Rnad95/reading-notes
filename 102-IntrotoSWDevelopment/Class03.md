# Git Commands

## Clone repository in Git

---

After create a Reop we can click on the green bottom `Code` then click on copy As shown in the image below :point_down: then paste the command in terminal

![](https://i.ibb.co/HVknqH3/Screenshot-from-2022-02-27-01-43-45.png)

## Open VSCode in terminal

---

> - `renad@renad-HP-Notebook:~$` Code .

**NOTE:** in visual Studio the green color indicates to add Line, and the red colour indicates to delete something. The blue arrow shows when edit something.  

## Push the work on Github

---

We need two three main commands:

1. > `renad@renad-HP-Notebook:~$` git add .
2. > `renad@renad-HP-Notebook:~$` git commit -m "Adding YOUR description"
3. > `renad@renad-HP-Notebook:~$` git push origin main.

## Pull the work from Github

- > `renad@renad-HP-Notebook:~$` git pull origin BranchName

## Generate Github Page

---

1. Go to Setting.
2. Select Pages from the left navbar.  
3. Select the branch then Save.  
4. [Option] Select the theme you want.  

## More Command

---

- git branch : to see the branch we are work on.  
- git checkout -b BranchName: to create and switch to the new branch.
- git remote -v : to know the remote name
- git init : to initial a repo.
- git status : to see the branches.
- git log : to see the commit.

**Pull Request (PR) :** is a request to tell the team (The manager of main branch (Repo)) you have an editing you want to add it.  

**fork :** to take a copy of the repo and edit it.  

**Untrack :** a green `u` we can see in vs code to indicates that we don't add the files in stage. *To Solve this warning we can use `git add .` / `git add JSName`*
