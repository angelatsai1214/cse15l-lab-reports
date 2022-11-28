`rm -rf student-submission`
- stdout: no stdout (tried the command)
- stderr: no error, so no stderr
- exit code: 0

---

 `git clone $1 student-submission`
 - stdout: no stdout (tried the command)
 - stderr: 
   ```
    Cloning into 'student-submission'...
    remote: Enumerating objects: 3, done.
    remote: Counting objects: 100% (3/3), done.
    remote: Compressing objects: 100% (2/2), done.
    remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
    Receiving objects: 100% (3/3), done.
 - exit code: 0

---

`cd student-submission/`
- stdout: no stdout
- stderr: no stderr
- exit code: 0

---

```
if [ -f $FILE ]
then
        echo "Correct files submitted"
else
        echo "Submitted file has the wrong name or path"
        exit 1
fi
```
- stdout: "Submitted file has the wrong name or path" for the 5th and 6th submissions, "Correct files submitted" for all other submissions
- stderr: no stderr
- exit code: 1 for the 5th and 6th submissions, 0 for all other submissions

---

```
cp -r lib student-submission/
echo "lib folder copied over"
```
- stdout: no stdout for cp, stdout for echo is "lib folder copied over"
- stderr: no stderr for both commands
- exit code: 0 for both

---

```
cd student-submission
echo "In student-submission"
```
- stdout: no stdout for cd, stdout for echo is "In student-submission"
- stderr: no stderr for both
- exit code: 0 for both

---

```
javac -cp $CP *.java 2> compiledResults.txt
ERRORNUMS=$( grep -o 'error' compiledResults.txt | wc -l | xargs )
if [ $ERRORNUMS -eq 0 ]
then
        echo "Compiled"
else
        echo "You have COMPILER ERROR"
        exit 1
fi
```
- stdout: "You have COMPILER ERROR" for the 3rd submission, "Compiled" for all other submission
- stderr: The stderr for the 3rd submission (which is redirected to compiledResults.txt) is shown below, no stderr for all other submissions
  ```
  ListExamples.java:15: error: ';' expected
        result.add(0, s)
                        ^
  1 error
- exit code: 1 for the 3rd submission, 0 for all other submissions

---

```
java -cp $CP org.junit.runner.JUnitCore TestListExamples > results.txt
echo "Ran Junit Tests"
```
- stdout: 
```
JUnit version 4.13.2
..
Time: 0.014

OK (2 tests)
``` 
The stdout for echo is "Ran Junit Tests"
- stderr: No stderr
- exit code: 0 for both

`awk 'NR>=11 && NR<=13' results.txt > testResults.txt`
- stdout:
- stderr: 
- exit code: 

```
ERROR=$(grep -o 'E' testResults.txt | wc  -l | xargs )
echo "Number of tests failed: $ERROR"
CORRECT=$(( $TOTALTESTS-$ERROR ))
GRADE=$(( ($CORRECT/$TOTALTESTS)*100 ))
```
- stdout:
- stderr: 
- exit code: 

`echo "Grade: $GRADE"`
- stdout:
- stderr: 
- exit code: 
