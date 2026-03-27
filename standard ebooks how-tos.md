# standard ebooks how-tos



## initial tool setup 

### **Typora**:

 for my own notes, installed typora and activated my license: the license code is in my quaderno di lavoro.

### **Xcode**: 

it seems you need to install Xcode before you install homebrew. (note, I looked at this tutorial https://www.geeksforgeeks.org/installation-guide/homebrew-installation-on-macos/, however note the spacing on some of the commands given is wrong)

1. Installed Xcode command line tool:  Open **Finder**, then from **Go** menu select **Utilities** and open **Terminal**  (nb you can also open terminal from apps I think)
2. then in the terminal window paste `xcode-select --install` and choose Install, accept the terms<img src="image-20260324133124150.png" alt="image-20260324133124150" style="zoom:33%;" />
3. Verify Xcode installation in terminal with `xcode-select -p` 

### **Homebrew**:

Now as per the website brew.sh, the terminal command for installing homebrew is: 

```
/bin/bash -c "$(curl -fsSLhttps://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

I had to enter my mac password to proceed.

![image-20260324133745198](image-20260324133745198.png)

it tells you what it's going to do and then you press enter to proceed. 

To verify the installation use `brew doctor`

And to update it use `brew update`

  ![image-20260324133941224](image-20260324133941224.png)

### **Standard ebooks tools**

Finally, you can now use homebrew to install the standard ebooks toolset with: 

```
brew update
brew install standardebooks
```

It takes a while to complete, then you can check the outcome with 

```
se --version
```

Nb it is not clear in the instructions if the pipx instructions are an alternative to the ones using homebrew, I think they are. The above steps do not themselves install pipe

Presumably the other commands you can use are 

To update, the instructions say to use `pipx upgrade standardebooks`

but I suppose for an installation with homebrew you would instead do:

```
brew upgrade standardebooks
```

nb I tried this command and it seemed to work, it told me I already had the latest version installed

## github desktop

This isn't strictly necessary but it might help with authentication and viewing diffs, and I don't want to install VS code just yet.

### Installation

I downloaded github desktop for macbook (intel chip) from here: https://desktop.github.com/download/. This downloads a zip. You double click to extract it and then end up with the application file in the downloads folder, which you then copy to your applications folder in Finder. 

When I launched Github desktop it automatically asked if I wanted to use my github account (acnard, etc.) and I said yes, and had to enter my password for it (the same one I used to sign in to github). Then it asked me to configure git with my account name and email address. 

I didn't accept the defaults offered (the github account name and email address) and instead used just Anna Nardella and nardella.anna@gmail.com. 

<img src="image-20260326120310851.png" alt="image-20260326120310851" style="zoom: 33%;" />

<img src="image-20260326121022874.png" alt="image-20260326121022874" style="zoom:33%;" />

## new repository for testing

I will do this on the command line, not using github desktop, to review my knowledge.

### Create new repo on GitHub

over on GitHub I created a new repository called mac-setupnotes for holding the text in this file. 

![image-20260326122148679](image-20260326122148679.png)

### upload files to github and do inital commit

Now I want to populate this repo with the contents of my SetupNotes folder on the mac

<img src="image-20260326122347601.png" alt="image-20260326122347601" style="zoom: 33%;" />

I decided to do this in the only way I know how, meaning I first upload my files (so this .md file plus its images) to the repository on GitHub. So I uploaded all the files in my SetupNotes folder and made an initial commit (directly on github)

![image-20260326123249183](image-20260326123249183.png)

### now clone the github repo to local machine

Now I can use a git command to clone this repo to my local machine. 

So to do this, I need to cd into the folder where I want the repo to be cloned and then use the git clone command. In my case: 

![image-20260326124042995](image-20260326124042995.png)

So to do this I cd into the folder I want to use (MyNotes)

and then enter the command `git clone https://github.com/acnard/mac-setupnotes.git`

where the https address is obtained from github.

![image-20260326124331834](image-20260326124331834.png)

![image-20260326124448072](image-20260326124448072.png)

after doing this, I can cd into the newly created subfolder (called mac-setupnotes) and do a git status: it tells me I am up to date with origin.

![image-20260326124903112](image-20260326124903112.png)

### update the files on local machine

Now I have been working on the old setup notes folder where I have been taking notes. I need to move those changes (updated .md file plus new images) to the mac-setupnotes folder that is under version control, after which  I can delete my initial setupnotes folder. 

Then I can do a `git add -A` followed by a `git commit` and a `git push`.

![Screenshot 2026-03-26 at 13.00.59](Screenshot 2026-03-26 at 13.00.59.png)

![Screenshot 2026-03-26 at 13.01.34](Screenshot 2026-03-26 at 13.01.34.png)

I was able to do the commit using the -m option to enter the commit message directly in the terminal: 

![image-20260326131231564](image-20260326131231564.png)

but then the git push failed. It asked me for my github user name and pw but then said that :

> remote: Invalid username or token. Password authentication is not supported for Git operations.fatal: Authentication failed for 'https://github.com/acnard/mac-setupnotes.git/'

### create a token on github 

You can no longer use your username and pw to do a git push from local to remote. Instead, you need to generate a token on github and then, when prompted for your pw on git push paste in that token. Note that the token has an expiration date.

Following the instructions here:

<img src="image-20260326133438325.png" alt="image-20260326133438325" style="zoom:33%;" />

I created a personal access token in GitHub

![image-20260326133417517](image-20260326133417517.png)

And then copied it to a file on my local machine (you can't access this token again on github).

### do a git push to remote using the token

Then, when after git push, when prompted for my credentials entered acnard for username and then pasted in the token for the password (CAREFUL: do command-V only once, it doesn't show you anything in the command line when you paste). 

![image-20260326133822226](image-20260326133822226.png)

## Summary of git process (command line)

This is assuming you have a repo whose origin is a remote on github and you have cloned it to the local machine using https. 

### Tip: Open terminal at desired folder

Navigate to the folder in Finder and then right click and select **New Terminal at Folder.**

<img src="image-20260327093240547.png" alt="image-20260327093240547" style="zoom:50%;" />

### making changes only on local and pushing to remote

1. On your local machine, always do a **git fetch** first to retrieve any changes from the remote (especially if you work on the same repo from multiple computers)

2. Then work on the files in your local folder (in this case, mac-setupnotes), updating or adding files as needed. 

3. When you do a **git status** you will be shown the non-commited changes you have made.
   ![image-20260326134759051](image-20260326134759051.png)

4. Use **git add -A t**o add all chanced or new files to the staging area. Then with **git status** you will see that all those files are staged for the next commit. 

   ![image-20260326135054583](image-20260326135054583.png)

5. Now you can do **git commit** **-m "enter message here"** to commit those changes (You need the -m option if you have not set up a default editor). ![](image-20260326135401862.png)

6. Finally, do a git push to publish those changes to the remote. 

   NOTE: The second time I did this, at least in the same terminal window, I didn't have to re-paste my github token.

### making changes also on remote

Now suppose you do a change directly on github: 

1. You edit the file on github and then do the commit there. <img src="image-20260326135845610.png" alt="image-20260326135845610" style="zoom:33%;" />
2. Then notice that, on local machine, if you do git status **it won't notice about the change done in the origin**. Right now it's only showing the non-commited changes I've done on the local machine. But it says the commits are up to date: 
   ![image-20260326140023245](image-20260326140023245.png)
3. This is because you need to first to a **git fetch**. If you do that, then git status will tell you the correct situation. Basically, there is on commited change on the origin, and I need to do a git pull to update my local branch with those same changes. 
   ![image-20260326140142975](image-20260326140142975.png)
4. But if I try to do a git pull now, it warns me that the git pull would be overwritten by my local changes to the same .md file. ![image-20260326140518442](image-20260326140518442.png)
5. I try to commit my local changes but then I still can't push them. I've ended up in a situation with divergent changes on local and remote. Basically, I have one commit on the remote and a different commit to the same file on local. Following these instructions

   <img src="image-20260326141552633.png" alt="image-20260326141552633" style="zoom:33%;" />
   I did a **git pull --rebase**. This basically means (I think) that it does the remote commit first and on top of that my local commits. And those two sequential commits are now on my local machine. I still need to do a **git push** to publish the result to the remote. 
   ![image-20260326141740060](image-20260326141740060.png)

## About remote and origin

see quote from geeksforgeeks article below. In my case there is one remote (the one on GitHub and my local repo is pointing to it as its origin). I can check this with the **git remote -v** command:

<img src="image-20260327093918283.png" alt="image-20260327093918283" style="zoom:50%;" />

>  **Overview of Git and Remote Repositories**
>
> A [remote repository](https://www.geeksforgeeks.org/git/how-to-reset-a-git-branch-to-a-remote-repository/) in [Git](https://www.geeksforgeeks.org/git/git-tutorial/) is a version of your project that is hosted on the internet or another network. It serves as a centralized location where developers can push their changes and pull updates. This setup is important for collaborative development, ensuring all team members have access to the latest code.
>
> **What Does "origin" Mean in Git?**
>
> In Git, "origin" is a conventional name used to refer to the default remote repository where your code is stored. It is not a reserved keyword but a naming convention that Git automatically assigns when you clone a repository. Understanding "origin" helps in managing remote connections effectively. 
>
> **How "origin" is Automatically Created When Cloning?**
>
> When you clone a repository using the git clone command, Git automatically creates a remote called "origin" that points to the URL of the cloned repository. This setup saves you from manually adding the remote and ensures that you can immediately begin interacting with the remote repository.
>
> ```
> git clone https://github.com/user/repository
> ```

## Github desktop - work with existing repo

Now that I have the repo created and ready, I can try interacting with it using github desktop:

### Add the repo to github desktop

The problem is, it seems that adding an existing repository to Github desktop may create a new remote for it on GitHub? But I already have all that... 

<img src="image-20260327094801716.png" alt="image-20260327094801716" style="zoom:50%;" />

I asked chat gpt and got the below instructions: So I picked **Add an existing repository from the local drive** and then selected the folder **mac-setupnotes**. 
Then I also did the check (menu > **Repository > Repostitory Settings** ) and verified the origin was correct:

<img src="image-20260327095458302.png" alt="image-20260327095458302" style="zoom:50%;" />

> You don’t need to create a new remote repo at all—since your project already has a GitHub remote, you just need to **add the existing local repository to GitHub Desktop**.
>
> Here’s how to do it:
>
> **Option 1: Add existing repository**
>
> 1. Open GitHub Desktop
> 2. Go to **File → Add local repository…**
> 3. Click **Choose…** and select your repo’s folder (the one with the `.git` directory)
> 4. Click **Add repository**
>
> That’s it—GitHub Desktop will detect the existing Git setup, including your remote.
>
> **Important check (optional but recommended)**
>
> After adding:
>
> 1. Go to **Repository → Repository settings… → Remotes**
> 2. Confirm that `origin` points to your existing GitHub repo (e.g., `https://github.com/username/repo.git`)
>
> ------
>
> **If the remote is missing (rare case)**
>
> If for some reason the remote isn’t there:
>
> ```
> git remote add origin https://github.com/username/repo.git
> ```
>
> Then GitHub Desktop will pick it up automatically

### Now my repo looks like this on github desktop

I see that it is doing fetch from origin automatically (there is also a menu command to fetch manually). It seems to have found the modified .md file plus six new image files.  This corresponds to what I see when I do a git status (the slight discrepancy in the screenshots is because as I am taking notes I am adding more new images to the repo! I see that whenever I add a new image, GitHub desktop automatically adds it to the list:  

<img src="image-20260327095855796.png" alt="image-20260327095855796" style="zoom:50%;" />

<img src="image-20260327100238796.png" alt="image-20260327100238796" style="zoom:50%;" />

So the **Changed files panel** is both new (untracked) files and existing (already tracked) files that have been changed. I suppose you can use the checkboxes to select which of the files you want to include in your commit (and I suppose it will manually do the add for those). Also when you select a file it's very nice, you can see all the diffs.





## Test run for the Grey Mask

For my first production I will produce a book only for myself. I found the Grey Mask here, done by distributed proofreaders in Canada:

Text: https://www.fadedpage.com/showbook.php?pid=20140339 

Scans: https://archive.org/details/bwb_W9-ANO-109/page/192/mode/2up 

The book is published in 1929 so is out of copyright also in the US

### select the starting file to use

There are both html and epub versions. The instructions say to pick the one that appears most accurate. 
In this case the epub and the html seem pretty much the same. I decided to start with the epub.
