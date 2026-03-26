# standard ebooks how-tos



## initial tool setup 

### **Typora**:

 for my own notes, installed typora and activated my license: nardella.anna@gmail.com GS82EQ-RZVDCY-NNZCYV-3XP9MR

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

### Testing with a new repository (mac-setupnotes)

over on GitHub I created a new repository called mac-setupnotes for holding the text in this file. 

![image-20260326122148679](image-20260326122148679.png)

Now I want to populate this repo with the contents of my SetupNotes folder on the mac

<img src="image-20260326122347601.png" alt="image-20260326122347601" style="zoom: 33%;" />

I decided to do this in the only way I know how, meaning I first upload my files (so this .md file plus its images) to the repository on GitHub.



## Test run for the Grey Mask

For my first production I will produce a book only for myself. I found the Grey Mask here, done by distributed proofreaders in Canada:

Text: https://www.fadedpage.com/showbook.php?pid=20140339 

Scans: https://archive.org/details/bwb_W9-ANO-109/page/192/mode/2up 

The book is published in 1929 so is out of copyright also in the US

### select the starting file to use

There are both html and epub versions. The instructions say to pick the one that appears most accurate. 
In this case the epub and the html seem pretty much the same. I decided to start with the epub.