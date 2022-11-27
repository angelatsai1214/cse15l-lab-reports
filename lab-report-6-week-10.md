`rm -rf student-submission`
- stdout: no stdout (tried the command)
- stderr: no error, so no stderr
- exit code: 0

 `git clone $1 student-submission`
 - stdout: no stdout (tried the command)
 - stderr: 
   
    Cloning into 'student-submission'...
    remote: Enumerating objects: 3, done.
    remote: Counting objects: 100% (3/3), done.
    remote: Compressing objects: 100% (2/2), done.
    remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
    Receiving objects: 100% (3/3), done.
 - exit code: 0

`cd student-submission/`
- stdout: no stdout
- stderr: no stderr
- exit code: 0

```
if [ -f $FILE ]
then
        echo "Correct files submitted"
else
        echo "Submitted file has the wrong name or path"
        exit 1
fi
```
- stdout:
- stderr: 
- exit code: 


```
if [[ -s TESTFILE ]]
then
        echo "Test file already exist"
        cd ..
else
        cd ..
        cp TestListExamples.java student-submission/
        echo "Test file copied to student-submission folder"
fi
```
- stdout:
- stderr: 
- exit code: 

```
cp -r lib student-submission/
echo "lib folder copied over"
```
- stdout:
- stderr: 
- exit code: 

```
cd student-submission
echo "In student-submission"
```
- stdout:
- stderr: 
- exit code: 

`javac -cp $CP *.java 2> compiledResults.txt`
- stdout:
- stderr: 
- exit code: 

```
ERRORNUMS=$( grep -o 'error' compiledResults.txt | wc -l | xargs )
if [ $ERRORNUMS -eq 0 ]
then
        echo "Compiled"
else
        echo "You have COMPILER ERROR"
        exit 1
fi
```
- stdout:
- stderr: 
- exit code: 

TOTALTESTS=2

```
java -cp $CP org.junit.runner.JUnitCore TestListExamples > results.txt
echo "Ran Junit Tests"
```
- stdout:
- stderr: 
- exit code: 

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
