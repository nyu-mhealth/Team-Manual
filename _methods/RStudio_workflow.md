# RStudio Workflow

## Personal Access Token(s) for RStudio
>#### Use this link: [GitHub Personal Access Token (PAT) URL](http://github.com/settings/tokens)

### OR run `usethis::create_github_token()` within RStudio for the token creation dialogue: 
>#### usethis::create_github_token()

### Either way, select and generate _*Classic*_ token(s)
* Be sure to define scope with textboxes: repo; workflow; gists
  * copy token and save to file (like this note) - will not reveal more than once
  * [consider safe PAT storage within OnePassword software?]

* * *

### next: RStudio `gitcreds::gitcreds_set()` :
>### `gitcreds::gitcreds_set()`

* ? Enter password or token, e.g., : 
>#### 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
>#### -> Adding new credentials...
>#### -> Removing credentials from cache...
>#### -> Done.
 
* * *
#
## New RStudio Project from Existing Git Repo via `git clone`
* Behind the scenes, RStudio will do this for you:
  * git clone https://github.com/YOU/YOURREPO.git
   
>### After we “Create Project” and create a new directory, we will have:
   * a directory or “folder” on the local computer
   * a Git repository, linked to a remote GitHub repository
   * an RStudio Project   
   
### Option 1: Execute `usethis::create_from_github()` in the R console of RStudio:
```{r eval = FALSE}
usethis::create_from_github(
   "https://github.com/YOU/YOUR_REPO.git",
   destdir = "~/path/to/where/you/want/the/local/repo/"
)
```
>### The first argument is repo_spec and it accepts the GitHub repo specification 
   * Copy and use the URL linked to the GitHub repo

>### The second destdir argument specifies the directory for the new folder (and local Git repo). 
   * Pro Tip: customize the usethis.destdir option in your .Rprofile.
   * If you don’t specify destdir, `usethis::create_from_github()` defaults to `usethis.destdir` 
   
>### We’re accepting the default behaviour of two other arguments, rstudio and open. 

### Option 2: In RStudio IDE, start a new Project:
    File > New Project > Version Control > Git. 
   * In the “repository URL” paste the URL of your new GitHub repository. 
   * It will be something like this https://github.com/YOU/YOURREPO.git
   * choose “Open in new session”  
   * Click “Create Project” to create a new directory

>### This process should download the README.md file that we created on GitHub in the previous step. 
   > Look in RStudio’s file browser pane for the README.md file.

* * *
##
## Connect an existing [RStudio] Project to Git and GitHub with `usethis::use_git()`

If an existing R project is not already an RStudio Project, convert to .Rproj:

  * Within RStudio you can do: *File > New Project > Existing Directory* and, if you wish, "Open in new session".
  * Alternatively, from R, call `usethis::create_project("path/to/your/project")`, substituting the path to your existing project directory.

### Now use RStudio to initiate or verify the Git repo 

Open / Launch an RStudio Project: *Does it have the Git pane?*

If not, you have several options:

  * In the R Console, call `usethis::use_git()`
  * In RStudio, go to *Tools > Project Options ... > Git/SVN*. Under "Version control system", select "Git". 
  * In the shell, with working directory set to the project's directory, do `git init`.

If you used `usethis::` or RStudio to initialize the Git repo, the Project should re-launch in RStudio.
If you used the shell and `git init` then you must launch RStudio yourself
Lastly, verify that RStudio now has the Git pane.

* * *
##
### (Alternative: RStudio IDE) Connect local repo to Existing GitHub repo with RStudio IDE

Click on the "two purple boxes and a white square" in the Git pane.
Click "Add remote".
Paste the GitHub repo's URL here and pick a remote name, almost certainly `origin`.
Now "Add".

Back in the "New Branch" dialog (click on the "two purple boxes and a white square" in the Git pane).
If you want it to track `main` on GitHub (or whatever default branch you are using):
  * Enter `main` as the branch name and make sure "Sync branch with remote" is checked.
  * Click "Create" (yes, even though the branch already exists).
  * In the next dialog, choose "overwrite".

* * *
##
### (Alternative: git commands) Connect local repo to GitHub repo with `git remote add "origin"` and `git push -u`

In a shell, do this, substituting your URL:
```console
git remote add origin https://github.com/YOU/YOURrepo.git
```

Push and cement the tracking relationship between your local `main` branch and `main` on GitHub:
```console
git push --set-upstream origin main
```

* * *
##
## IF ONLY local exists: Create and connect a GitHub repo with `usethis::use_github()`

`usethis::use_github()` does the following:
* Creates a new repo on GitHub.
* Configures that new repo as the `origin` remote for the local repo.
* Sets up your local default branch (e.g. `main`) to track same on `origin` and
  does an initial push.
* Opens the new repo in your browser.

In your project, in the R Console, call:

```{r eval = FALSE}
usethis::use_github()
#> ✓ Creating GitHub repository 'YOU/YOURrepo'
#> ✓ Setting remote 'origin' to 'https://github.com/YOU/YOURrepo.git'
#> ✓ Pushing 'main' branch to GitHub and setting 'origin/main' as upstream branch
#> ✓ Opening URL 'https://github.com/YOU/YOURrepo'
```
    
```{r}
#| echo = FALSE, fig.align = "center", out.width = "60%",
#| fig.alt = "usethis::use_github() connects a local repo to a new GitHub repo."
knitr::include_graphics("img/use_github.jpeg")
```    

* * *
##
## Use command line Git to inspect the remote and tracking branch setup
```console
git remote -v or git remote --verbose
``` 
>#### shows the remotes you have setup. 
                                             _**not sure which .md we prefer here..?**_
    $ git remote -v or git remote --verbose 
   
    $ git branch -vv 
   
   >#### prints info about the current branch (-vv for “very verbose”). 
   > we can see that local main is tracking the main branch on origin, a.k.a. origin/main.

    $ git remote show origin 
   
   >#### git remote show origin gives yet another view on useful remote and branch information

* * *
##
## RStudio Workflow Overview: 
### [Remote] First, create GitHub Repo (establishing upstream origin)
### [Remote] Update .gitignore (using template R/python/other)
### [Local] Clone repo (recommend GitKraken)
### [Local] RStudio: New Session: New .Rproj -> From Existing Directory (local clone)
### [Local] Terminal [RStudio OR GitKraken or Warp]: New (local) Branch (`git checkout -b "new/branch"`) 
### [Local] RStudio: File Menu: (git touch?) New .Rproj File (e.g., Shiny Web App or .Rmd) 
### [Local] Terminal [RStudio OR GitKraken]: `git status` Stage `git add .` 
### [Local] Terminal `git status` then `git commit -m "instruction"` then `git log` (view commit #)
### [Local] (!) now `git push` in RStudio FAILS: Instead use GitKraken: push to remote origin/"new/branch"
>### Alternatively create "new/branch" manually at GitHub remote repo 
### [Remote] GitHub: create Pull Request -> merge new/branch commit into origin/main
### [Local] `git checkout -b main` Checkout (local)/main and Fetch (pull+fast-forward merge) from origin/main
### [Local] `git checkout -b new/branch` and proceed with work within this repo
>### Stage as you go and commit chunks of work regularly 

###
### 1) Save some changes to your local repo:
  * E.g., from RStudio, modify the README.md file, e.g., by adding the line “This is a line from RStudio”. 
  * Save your changes locally.

### 2) Stage the local file change(s) you would like to -commit-:
>#### Use "Diff" to review changes since the last commit, click on “Diff” for a Git pop-up
  * Use `git status` 
  * Use `git diff` 
  * use `git add .` to stage changes [`git reset` to unstage]

- [Alternative: RStudio IDE] Click the “Git” tab in upper right pane
- Check “Staged” box for any files whose existence or modifications you want to commit.
    
### 3) Commit some changes to your local repo:
- `git commit -m "type a message as if you are issuing an instruction"`
- Or, if you’re not already in the Git pop-up, click “Commit”
- Type a message in “Commit message”, such as “Commit from RStudio”
- Click “Commit”
    
### 4) Pull from GitHub before you Push (to avoid conflicts)
- Click the blue “Pull” button in the “Git” tab in RStudio. 
   * N.B., At this point you’ll likely get the message “Already up-to-date” 

### 5) Push your local changes to GitHub
>### Do this regularly, but less often than you commit.

  * You have new work in your local Git repository, but the changes are not online yet...

>#### Because other changes may have been pushed, **PULL those changes before you PUSH!**

- Click the green “Push” button to send your local changes to GitHub. 

###
### Confirm the local change propagated to the GitHub remote
- Refresh GitHub: you should see the new “This is a line from RStudio” in the README
- If you click on “commits,” you should see one with the message “Commit from RStudio”

### Commit changes directly from GitHub remote
 - Click on README.md in the file listing on GitHub.
 - In the upper right corner, click on the pencil for “Edit this file”.
 - Add a line to this file, such as “Line added from GitHub.”
 - Edit the commit message in “Commit changes” or accept the default.
 - Click the big green button “Commit changes.”
