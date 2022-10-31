# Week 5 Lab Report

## Command-Line Options

`grep`

1. `-v` makes `grep` search for non-matching files.
   
   - Example 1:
     ```
     [cs15lfa22bi@ieng6-202]:docsearch:195$ find technical/911report > find-results.txt
     [cs15lfa22bi@ieng6-202]:docsearch:196$ grep -v "chapter" find-results.txt
     technical/911report
     technical/911report/preface.txt
     ```
     
   - Example 2:
     ```
     [cs15lfa22bi@ieng6-202]:docsearch:199$ find technical/government/Alcohol_Problems > find-results.txt
     [cs15lfa22bi@ieng6-202]:docsearch:200$ grep -v "Session" find-results.txt
     technical/government/Alcohol_Problems
     technical/government/Alcohol_Problems/DraftRecom-PDF.txt
     ```
     
   - Example 3:
     ```
     [cs15lfa22bi@ieng6-202]:docsearch:201$ find technical/government/Post_Rate_Comm > find-results.txt
     [cs15lfa22bi@ieng6-202]:docsearch:202$ grep -v "Cohenetal" find-results.txt
     technical/government/Post_Rate_Comm
     technical/government/Post_Rate_Comm/Gleiman_EMASpeech.txt
     technical/government/Post_Rate_Comm/Gleiman_gca2000.txt
     technical/government/Post_Rate_Comm/Mitchell_6-17-Mit.txt
     technical/government/Post_Rate_Comm/Mitchell_RMVancouver.txt
     technical/government/Post_Rate_Comm/Mitchell_spyros-first-class.txt
     technical/government/Post_Rate_Comm/Redacted_Study.txt
     technical/government/Post_Rate_Comm/ReportToCongress2002WEB.txt
     technical/government/Post_Rate_Comm/WolakSpeech_usps.txt
     ```

2. `-c` makes `grep` return the count of files matching the search case.
   
   - Example 1:
     ```
     [cs15lfa22bi@ieng6-202]:docsearch:188$ find technical/ > find-results.txt
     [cs15lfa22bi@ieng6-202]:docsearch:189$ grep -c ".Barnes" find-results.txt
     3
     ```
     
   - Example 2:
     ```
     [cs15lfa22bi@ieng6-202]:docsearch:190$ grep -c "Fund" find-results.txt
      3
     ```
     
   - Example 3:
     ```
     [cs15lfa22bi@ieng6-202]:docsearch:193$ grep -c "H." find-results.txt
     11
     ```

3. `-i` makes the search non-case-sensitive.
   
   - Example 1:
     ```
     [cs15lfa22bi@ieng6-202]:docsearch:203$ find technical/ > find-results.txt
     [cs15lfa22bi@ieng6-202]:docsearch:204$ grep -i "senior" find-results.txt
     technical/government/Media/highlight_Senior_Day.txt
     ```
     
   - Example 2:
     ```
     [cs15lfa22bi@ieng6-202]:docsearch:205$ grep -i "Chapter" find-results.txt
     technical/911report/chapter-1.txt
     technical/911report/chapter-10.txt
     technical/911report/chapter-11.txt
     technical/911report/chapter-12.txt
     technical/911report/chapter-13.1.txt
     technical/911report/chapter-13.2.txt
     technical/911report/chapter-13.3.txt
     technical/911report/chapter-13.4.txt
     technical/911report/chapter-13.5.txt
     technical/911report/chapter-2.txt
     technical/911report/chapter-3.txt
     technical/911report/chapter-5.txt
     technical/911report/chapter-6.txt
     technical/911report/chapter-7.txt
     technical/911report/chapter-8.txt
     technical/911report/chapter-9.txt
     ```
     
   - Example 3:
     ```
     [cs15lfa22bi@ieng6-202]:docsearch:208$ grep -i "mitchell" find-results.txt
     technical/government/Post_Rate_Comm/Mitchell_6-17-Mit.txt
     technical/government/Post_Rate_Comm/Mitchell_RMVancouver.txt
     technical/government/Post_Rate_Comm/Mitchell_spyros-first-class.txt
     ```
