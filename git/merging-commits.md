# Merging multiple commits in single commit in GIT

Use

    git rebase --interactive ref


This will pick up editor with the list of commits to rebase where we can choose what to do with each commit. To merge multiple commits in the single commit we need to keep first commit and squash all the others:

    keep b76d157 first commit after ref
    s    a931ac7 second commit after ref
    s    23987dd third commit after ref

On the next step you'll be prompted to put new commit message for rebased commit. 


### Links

* [Question on StackOverflow](http://stackoverflow.com/questions/2563632/how-can-i-merge-two-commits-into-one)
