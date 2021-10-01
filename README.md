# Repository for testing git merge operation
# Emrys 2021-10-01

Given how often we've had to do git merge, you'd think that we'd know how it works by now. But, apparently not.
There is a question as to how git merge of B into A works when the files in A are newer than the files in B.
So, let's try it and see.

It does indeed appear that git merge does a reasonable job. When I modify and commit `file1` in branch `newCode`,
then later modify and commit `file1` in branch `main`, then merge newCode into main,
`file1` in `main` ends up with the changes from both `main` and `newCode, despite the fact that the file
modfication date and the commit date in `newCode` were both earlier than those for `main`.

Only if I modify the same line in  both branches do I get a merge conflict.
