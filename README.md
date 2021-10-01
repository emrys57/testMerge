# Repository for testing git merge operation
# Emrys 2021-10-01

Given how often we've had to do git merge, you'd think that we'd know how it works by now. But, apparently not.
There is a question as to how git merge of B into A works when the files in A are newer than the files in B.
So, let's try it and see.

It does indeed appear that git merge does a reasonable job. When I modify and commit `file1` in branch `newCode`,
then later modify and commit `file1` in branch `main`, then merge newCode into main,
`file1` in `main` ends up with the changes from both `main` and `newCode`, despite the fact that the file
modification date and the commit date in `newCode` were both earlier than those for `main`.

Only if I modify the same line in  both branches do I get a merge conflict.
This repository has conflicting changes in file1 in branch `main` and `newCode`. If you clone it and merge `newCode` into `main`, git should report a merge conflict.

It's possible to see the edits and merges as they happened, in order. In VS Code, open `file1`. In the left column of VS Code, choose `Source Control` - `File History`. Starting from the bottom entry, "First Commit of file1 in main at 13:25", clicking each commit in `File History` will show the changes in `file1`.

`Commit file1 in newCode` added line 16 to file1 in newCode  
`Commit after distraction by nathalie at 13:38, changed file1 in newCode.` added line 18 to file1 in newCode. Sorry, I was distracted by Nathalie.  
`Commit changes to line 4 at 13:41 in newCode` added text to the line labelled "four" in newCode.  
`Change file1 in main at 13:44` added text to the line labelled "two" in `main`. So `file1` in main was modified and committed _after_ `file1` in `newCode`.  
`Merge branch 'newCode'` merged `newCode` into `main` and included the changes at line two _and_ line four. Which is what we wanted.  
