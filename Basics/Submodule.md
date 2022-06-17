# Add submodule to secure your data
adding private directory in a public directory
[Check](https://ohgyun.com/711)

Creat a public directory 
Creat private directory

Clone your public directory in desktop

Move into the public directory
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
cd Desktop/AD_microbiome/AD_microbiome_R
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Add a submodule in public directory
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git submodule add https://github.com/rosebaesj/submodule
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Done.

You need to commit submodule first,
then commit bublic directory

push submodules automatically 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git push --recurse-submodules=on-demand
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

