# GitHub Workflow

### The team "Integrator" compiles and approves pull requests
### Pro Tip #1: Pull before you Push
    Note that in general (and especially when collaborating with other developers) 
    you need to pull changes from remote (GitHub) before pushing the local changes you have made.
### GitKraken, GitHub Desktop, and/or RStudio (Posit) are git clients that can manage GitHub content locally
    With any git client, when you "fetch" you update the associated files stored locally within the "~/GitHub/.." directory.
    ...From there is makes sense to synchronize these sub-directories across machines
### RStudio is key for interacting with GitHub via R and .Rmd.  
   * "Let's Git Started" tutorial for Rmd/RStudio/GitHub
   * .Rmd is useful for running embedded .R code and generating output in .html / .pdf / .docx / slideshow
   * Utilize RStudio GUI .Rmd new file template : writes the YAML header for you
### For Stata or other non-R code or processes, GitKraken can -clone- and then -fetch- (pull+merge) from GitHub 
   >### Stata .do files do _not_ take advantage of .Rmd features, and so .md is fine for documentation
   * although .Rmd could be useful for generating reports
   >### For python and <.ipynb> Jupyter notebooks, the Anaconda environment is required 

##
* * *
#
## Terminal / Command line syntax Overview
    A `shell` is a program that provides a user interface for executing operating system (OS) services
    
    The shell runs in the Terminal - which is a command line interface / interpreter (CLI)
    
    Applications/Utilities/Terminal
    > or... Tools -> shell
    > In RStudio -> terminal
    
## Terminal Commands   
>### pwd // print working directory - displays current wd

>### ls -a // list cd contents -including hidden files (-a flag)

>### cd <dir/> // set current directory

>### cd .. // move up/back one level

>### open . // open cd

>### touch "dir/file.ext" // creates new file (.txt ; .pdf ; .doc ; .py ; .xls ; .do ; etc)

>### mkdir <dir/> // creates new directory (in cd)

>### rm <file.ext> // delete file? // careful with these 

>### rm -rf <dir/> // delete directory

#
## Git commands Overview

>### git clone <URL> e.g., https://github.com/nyu-mhealth/place_survey
>### git clone -b <branch> <remote repo>
#
>### git branch <branchname> / switch -c // create and "check-out" branch
>### git branch -vv
>### git branch -v
#
>### git init // initiate git tracking within local directory
#
>### git remote -v OR git remote verbose
>### git remote show origin 
#
>### git diff
>### git status
#
>### git add <file.ext> // stage
>### git reset <file.ext> // unstage
>### git commit -m "commiting to branch" 
#
>### git pull = git fetch + git merge 
>### git push
#
>### git log
#
## .Git ignore 
   ### Inclusion of a .gitignore file within <cd/> allows exclusion of files from .git tracking / repo
    
   >### some input <-> output processes utilize and/or generate supporting files that should not be tracked by .git
   >### template example .gitigore file configurations: [Octocat .gitignore](https://gist.github.com/octocat/9257657) 
   >### directories ("branch/<dir>"), files, and file extensions (*.ext) can be excluded from .git by listing within .gitignore
   >### .gitignore accepts "wildcard" `*.ext` operators and excludes any files with extension `*.ext`
   >### N.B., to exclude files / extensions `.gitignore` must exist within cd/ [and/or can it specify sub-dir/paths?]
   * Within RStudio, each new .Rproj creates a custom `.gitignore` 
   * Stata utilizes many input file extensions (e.g., .csv; .xlsx), and can create its own output files (e.g., .dta; .log) 
   * This is true even when running from a remote / cloud web-data server (e.g., "Box")
   * An example Stata .gitignore file excludes the input / output data files from the tracked .git repo: [Stata.gitignore](https://BIRDN?EST.github.com/thomaskirchner/_scripts/stata.gitignore) 
  
>### To generate a `.gitignore` file within an existing directory from terminal: 
    touch .gitignore 
    open .gitignore / add + save dir/file(s)
    git status
    git add .gitignore / stage+track
    git commit -m ".gitignore" / thereafter changes to .gitignore will show up from -git status-, but NOT new files or directories listed therein

* * *
#
## In the beginning, use Terminal to Introduce yourself to Git 
    
    Enter these lines separately with GitHub user credentials:
    
    $ git config user.email "tomkirchner+github@gmail.com"
    $ git config user.name "Thomas Kirchner" // first.name last.name (order ?)

    $ git config --list  # see below email and username are present :)

* * *
#    
## Configure Git default editor (VIM is default)
    $ git commit  // w/out -m "" triggers default editor VIM to open...

    VIM secret #1: Once VIM opens, hit the "i" key to enter --INSERT-- mode
      - Now start typing commit message on the first line of the VIM window; e.g., "add file to directory"
      - Now hit ESC key once to exit --INSERT-- mode
    
    VIM secret #2: Now enter :wq (followed by Return) to exit (N.B., the completed commit)

### change the default editor to BBedit
    $ git config --global core.editor "bbedit -w"
    
### other Git editor options
    VIM: $ git config --global core.editor "vim --nofork"
    
    Sublime Text (macOS): $ git config --global core.editor "/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl --new-window --wait"
    
    TextEdit (macOS): $ git config --global core.editor "open --wait-apps --new -e"
    
    VS Code: $ git config --global core.editor "code --wait"

* * *    
#   
# Branching
    
  >### .git branch naming conventions are a key aspect of a team's `"git flow"`
  * `git check-ref-format --branch <branch/name>` inspects branch name for errors (leading . \ @)
  * `Historical note :` The branch name default changed from `Master` to `Main` late 2020/early 2021 

  >### A standardized set of semantic branch name headers allows filtering of `commits` by branch type
  * `git branch list <feature/*>` queries all branches that match each branch type keyword/tag

  >### A software development branching convention
    /main
    /develop
    /feature
    /release
    /hotfix
    
  >### Data science branching convention
    /git
    /git/admin
    /r/clean
    /r/describe
    /r/analysis
    /do/clean
    /do/analysis
    /do/describe
    /do/tables
    /ipynb/...
  
    
  ## Git HEAD -> branch reference -> commit
  >#### HEAD == a "Branch pointer" that refers to our exact location - points to a branch reference
  >#### HEAD -> Master <Master is the [root] branch reference location>
  >#### HEAD is like a bookmark location within a book (repository), which can only be open to one location
  >#### branch pointers (HEAD) can be switched (checked-out) to select different commits along different branches
  
  ### View existing Branches
  >### git branch // type "q" to exit
  >### branch with "*" is the current branch
  
  ### Create a new Branch - just add a name
  >### git branch "newbranch" // at this point, Master==newbranch -> they have the same HEAD commit location
  >### on new branch, you remain on Master, until *_Git Switch_* (older is "Checkout")
  >### git switch newbranch // HEAD is now newbranch
  >### git log // HEAD is pointing to newbranch
  >### first commit on newbranch - N.B., git status (Master) branch is left behind (log too)
  
  ### *_Branch Key #1_*: Current Branch has a direct bearing on any new Branch that is created
  
  ### *_Branch Key #2_*: Create + Switch to newbranch at once with "-c" flag
  >### $ git switch -c "namenewbranch" // GitKraken does not list `git switch` but instead `checkout`
  >### $ git checkout -b "namenewbranch" // same function as git switch
  
  ### *_Branch Key #3_*: Rename using -m _NOT_ -n (_m refers to "move")
  >### $ git branch -m "newname"
  
  ### *_Branch Key #4_*: Delete branch using -d
  >### $ git branch -d "branchtobedeleted" // BUT you must switch HEAD off of the Branch prior to delete
  
  ## N.B., Git Switch is the newer more concise version of *_Git Checkout_*
  >### Git Checkout has more options - the Swiss-Army Knife of Git
  
* * *    
#
# Merging
  
  ### *_Merge Key #1_*: You merge Branches, NOT commits
  ### *_Merge Key #2_*: You must Switch / Checkout the Merge destination
  >### Fast forward Merge: $ git Switch Master -> then fastforward merge <feature branch> into Master
  
  ##
  
  ## Problem: Parallel commits alter Master, conflicting with standard fast-forward merge
  >### IF NON-conflicting change on the Master, Git initiates a *_Merge Commit_* [with 2 different parent commits]
  >### Git opens default editor and "waits" - then on close of editor, the commit completes
  
  ##
  >### IF there is a conflicting change on 2+ changes, Git will not know how to merge, requiring manual resolution
  >### conflicting files must be opened and fixed manually 
  >### *_Conflict Markers_* indicate conflicts on the HEAD versus feature branch
  >### * Decide what to keep, Then remove conflict markers from the document
  >### * $ git add the changes and commit to resolve the conflict

* * *
#
# Stage, Commit and Push
   ### Each Git Commit creates a unique "hash" : an alpha-numeric key-code, unique identifier for each commit 

  >#### each commit references a parent commit that precedes it (other than initial commit)

  >#### commits seldom proceed in purely linear fashion, especially with multiple users

  >#### *_branching_* allows for (super-complex) parallel development while retaining the same core project features

  >#### *_merging_* reconciles differences 
  
* * *    
#
# Diff 
  
* * *
#
# Stashing
  
  
* * *
#
# GitKraken

### Each row within the "graph" represents a Commit
    The top WIP (work in progress) row / node contains *_uncommited_* changes
    Click on any Commit row to reveal right-side panel commit details -> view file -diff-
    Click to select multiple Commit rows to review combined -diff-
    Within -diff-, select each file to view in -diff- view 
      * Stage OR discard hunks of code (perhaps for separate commits)
      * Click "Edit in working directory" to make additional changes directly
    
    From Graph Commit row -> Right Click -> Create Branch
    Do this from Head of Branch for more options: Pull / Push branch _not_ checked-out 
    merging / re-basing / pull-requests
    
    N.B. undo function for only your last commit / action
    N.B., Git command pallette for reference
    
    Drag & Drop (!) Branch on Branch to reveal options - merge / rebase / interactive rebase / PR
      * Opens new view - pick among commits 
    Typically want to Drop Feature Branch ONTO Main (dev branch)
    
    N.B. PR dialogue within the left-side panel - Assign reviewer and await merge with Main
    
    When an Issue is assigned to you, right-click to create and switch to (check-out) branch 
    Make changes per issue -> PR
    
    N.B., Given changes to Main, Rebase onto Feature Branch will update local files - like a Fetch 
    
* * *
    
## Additional Resources
### diagram.net 
  Useful for creating .drawio (mindmap) files and exporting .png images.  Also a useful workflow for project planning / development

### Repository: Code Tab: -Create New File- 
  In the filename, can specify NEW _path/ and create a new folder and/or update or add a new entry / post 

*.png* portable network graphs are preferred by developers
  
GitHub ninja note:  leading a new subdirectory name with "." has the effect of hiding the folder -  as with .DS_Store
    
    
