# PuppetSubSync

## Description

Two scripts to create puppet environments for testing with submodules. The script
will create a folder in $DEPLOYDIR and clone the puppet super project with --recursive
. Then it will cd into the submodule directory and checkout the branch that was pushed.

The motivation for this is to return to the branch, commit, test, commit, test, merge 
workflow with submodules. It will only work if whatever class you are working on is 
already included in the node definition in the super project. It will also only work 
in the context of a git-hook. 

## Usage

Put the git-hook in post-receive in the git repository. Put the ruby script in 
/usr/share/bin/puppetsubsync or a different directory and update the git hook. 
Push a branch with the branch name beginning with s_ (or remove this functionality
in the git hook if you prefer). The output of the git hook will show you a to test 
string. You can copy and paste that to test with puppet. Something like:

puppet agent --test --noop --environment=puppet_module_ubuntu_s_dev


