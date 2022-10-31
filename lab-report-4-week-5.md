# Week 5 Lab Report

## Command-Line Options

`grep`

1. `-v` makes `grep` search for non-matching files.
   ![Image](/Images/-v.png)

2. `-c` makes `grep` return the count of files matching the search case.
   
   - Example 1:
     ```
     find technical/ > find-results.txt
     [cs15lfa22bi@ieng6-202]:docsearch:189$ grep -c ".Barnes" find-results.txt
     3
     ```

3. `-i` makes the search non-case-sensitive.
   ![Image](/Images/-i.png)
