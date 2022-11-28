# My grade.sh code:

```
# Create your grading script here

# set -e

CP=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

rm -rf student-submission
git clone $1 student-submission

cd student-submission/

FILE="ListExamples.java"

# Check if the correct files were submitted
if [ -f $FILE ]
then
        echo "Correct files submitted"
else
        echo "Submitted file has the wrong name or path"
        exit 1
fi

TESTFILE="TestListExamples.java"

cp -r lib student-submission/
echo "lib folder copied over"

cd student-submission
echo "In student-submission"

javac -cp $CP *.java 2> compiledResults.txt

# Check if there was a compiler error
ERRORNUMS=$( grep -o 'error' compiledResults.txt | wc -l | xargs )
if [ $ERRORNUMS -eq 0 ]
then
        echo "Compiled"
else
        echo "You have COMPILER ERROR"
        exit 1
fi

TOTALTESTS=2

java -cp $CP org.junit.runner.JUnitCore TestListExamples > results.txt

echo "Ran Junit Tests"

awk 'NR>=11 && NR<=13' results.txt > testResults.txt

ERROR=$(grep -o 'E' testResults.txt | wc  -l | xargs )
echo "Number of tests failed: $ERROR"
CORRECT=$(( $TOTALTESTS-$ERROR ))
GRADE=$(( ($CORRECT/$TOTALTESTS)*100 ))

echo "Grade: $GRADE"
```

---

# My 3 Screenshots:

![Img](/Images/good.png)
![Img](/Images/compileErr.png)
![Img](/Images/fileName.png)

# Trace for the 2nd Example

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
  ```
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

- stdout: "Correct files submitted"
- stderr: no stderr
- exit code: 0
- the condition of the if statement is true

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

- stdout: "You have COMPILER ERROR"
- stderr:
  ```
  ListExamples.java:15: error: ';' expected
        result.add(0, s)
                        ^
  1 error
  ```
- exit code: 1
- the condition of the if statement was false

---

```
java -cp $CP org.junit.runner.JUnitCore TestListExamples > results.txt
echo "Ran Junit Tests"
```

- not ran bc of early exit

`awk 'NR>=11 && NR<=13' results.txt > testResults.txt`

- not ran bc of early exit

```
ERROR=$(grep -o 'E' testResults.txt | wc  -l | xargs )
echo "Number of tests failed: $ERROR"
CORRECT=$(( $TOTALTESTS-$ERROR ))
GRADE=$(( ($CORRECT/$TOTALTESTS)*100 ))
```

- not ran bc of early exit

`echo "Grade: $GRADE"`

- not ran bc of early exit
