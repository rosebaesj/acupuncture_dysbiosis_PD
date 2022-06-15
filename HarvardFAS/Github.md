Get connected with **Cisco AnyConnect Secure Mobility Client**

Open terminal

[Login](https://docs.rc.fas.harvard.edu/kb/terminal-access/)
~~~~~~~~~~~~~~~
$ ssh sjbae@login.rc.fas.harvard.edu
Password
Verification code
~~~~~~~~~~~~~~~

Move location to 
~~~~~~~~~~~~~~~~~
$ cd n/hpnh/Users/sjbae
~~~~~~~~~~~~~~~~


# Generate SSH key
~~~~~~~~~~~~~~~~
$ ssh-keygen -t ed25519 -C "sjbae@hsph.harvard.edu"
~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~
Enter file in which to save the key (/n/home06/sjbae/.ssh/id_ed25519):
~~~~~~~~~~~~~~~~
Don't need to type, just enter

~~~~~~~~~~~~~~~~
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
~~~~~~~~~~~~~~~~
Your identification has been saved.

# Adding your SSH key to the ssh-agent
Start the ssh-agent in the background.
~~~~~~~~~~~~~~~~
$ eval "$(ssh-agent -s)"
~~~~~~~~~~~~~~~~

# Adding a new SSH key to your GitHub account
Copy the SSH public key to your clipboard.
~~~~~~~~~~~~~~~~
$ cat ~/.ssh/id_ed25519.pub
~~~~~~~~~~~~~~~~
Then select and copy the contents of the id_ed25519.pub file displayed in the terminal to your clipboard

Follow [this](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
And add the SSH to your Github website

#Check the connection
in FAS terminal,
~~~~~~~~~~~~~~~~
$ ssh -T git@github.com
Are you sure you want to continue connecting (yes/no)? yes
~~~~~~~~~~~~~~~~

# Cloning repository 
[see](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository#cloning-a-repository)
~~~~~~~~~~~~~~~~
$ mkdir Git_omega3
$ git clone https://github.com/rosebaesj/omega3.git
~~~~~~~~~~~~~~~~
get http address from your git repository
