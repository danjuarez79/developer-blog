---
title: "Setting up VS Code to use SSH for GitHub Repositories"
date: 2024-01-05
---

# SSH with GitHub

I've recently gone through the process of setting up VS Code with GitHub. The reason for this was to move away from using Eclipse and learning a secondary tool. These are the steps I used to set up VS Code with Github. I started with a PPK key I already had on Github but I'll explain the steps to create this PPK too.

These are the steps to make an SSH key for use with Eclipse and Pageant and VS Code and command line.

- Prerequisites:

    + GitHub account
    + Git CLI
    + Visual Studio Code (Vscode)
    + Eclipse IDE
    + PuttyGen for Key Generation

- Create a new private repository on GitHub:

    + Login to GitHub.
    + Select "New repository" and make it private.
    + Add a name, .gitignore, and README.md.
    + Create the repository.

- Generate the PPK Key (for Pageant use):

    + Open Putty Key Generator (PuttyGen).
    + Select ECDSA as the Type of key. (RSA is not supported by GitHub.com).
    + Curve type: nistp256.
    + Press the "Generate" button.
    + Move your mouse around the screen till the bar fills up.
    + Optional but recommended: Enter a passphrase (you'll be asked to enter this when using it).
    + Select File > Save private key.
    + Place the key in your {user}/.ssh directory.
    + Keep PuttyGen open and the key loaded for the next step.

- Pageant with Eclipse Git (Egit).

    + For Eclipse Git (Egit) you can have the ppk loaded in Pageant. With this tool you only need to use your passphrase once.
    + However, if you don't mind entering the passphrase every time you can use .PUB in the {user}/.ssh we create next. 

- Generate the PUB Key (for VS Code use)

    + If necessary, open Putty Key Generator (PuttyGen) and press the "Load" button.
    + Select the PPK private key from your {user}/.ssh directory.
    + Select Conversions > Export OpenSSH key
    + Place the key in your {user}/.ssh directory with the .PUB extension.
    + Keep PuttyGen open and the key loaded for the next step.

- Add the public SSH key to GitHub:

    + Copy all the text in the window that says "Public key...".
    + Go to your Github account.
    + Click profile picture, select "Settings."
    + Under settings, select "SSH and GPG keys."
    + Add a new SSH key, paste the copied public key, and click "Add SSH key."

- Collect the git@repo link:

    + Go to the desired repository on GitHub.
    + Copy the SSH "git@repo" link.

- Option 1: Clone the repository using SSH:

    + In the terminal, navigate to the directory created to save the cloned repo.
    + Run `git clone <ssh-link-from-GitHub>`.
    + Type "yes" when prompted.
    + Open the cloned repository in VS Code.
    + Go to "File," open a file, and select the file with the name of the cloned repo.

- Option 2: Clone the repository using EGit:

    + Click the "Clone" button.
    + Select the "Clone URI" option.
    + Use the default options and click Finish.


Congratulations!
You have successfully cloned your private GitHub repository using SSH and Vscode.

Sources: 
[Using ssh to clone a Private Git repository with VsCode and Git Bash][1]
[Connecting to GitHub with SSH][2]

  [1]: https://medium.com/@melvingrooms/using-ssh-to-clone-a-private-hit-repository-9fbe79a589cd#:~:text=click%20add%20ssh%20key.,the%20link%20copied%20from%20GitHub
  [2]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh

