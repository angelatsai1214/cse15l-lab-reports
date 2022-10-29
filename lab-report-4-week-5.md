# Week 5 Lab Report

## Command-Line Options

`less`

1. `-X` prevents the terminal from clearing the screen after quitting `less` so that we can still refer back to the results of `less` later on.

   ![Image](/Images/-X.png)

2. `-N` displays a line number for every line in the beginning.

   ![Image](/Images/-N.png)

   ![Image](/Images/-N-result.png)

3. `-p` searches files with a specific patterns and output the contents of matching files.
   ![Image](/Images/-p.png)

`find`

1. `-empty` finds files that are empty.
   ![Image](/Images/-empty.png)

2. `-newer` finds files that were created newer than a particular file.
   ![Image](/Images/-newer.png)

3. `-mmin -n` find files that were modified in the last `n` minutes/
   ![Image](/Images/last60min.png)

`grep`

1. `-v` makes `grep` search for non-matching files.
   ![Image](/Images/-v.png)

2. `-c` makes `grep` return the count of files matching the search case.
   ![Image](/Images/-c.png)

3. `-i` makes the search non-case-sensitive.
   ![Image](/Images/-i.png)
