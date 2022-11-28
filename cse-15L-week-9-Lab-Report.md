# Minyan Shi's CSE 15L Week 9 Lab Report
---
```
set -e

rm -rf student-submission
git clone $1 student-submission
cp TestListExamples.java student-submission
cd student-submission
FILE=ListExamples.java
CPATH=.:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar

if [[ -f "$FILE" ]]
then
        echo "File exists"
        echo "Successfully cloned"
else
        echo "Cannot find the file"
        echo "Your score is 0"
        exit 1
fi


set +e

SCORE=0

javac -cp $CPATH *.java

if [[ $? -eq 0 ]]
then
  SCORE=$(($SCORE+1))
  echo "Successfully compiled."
else
  echo "Unsuccessfully compiled. Your score is" $SCORE ""
  exit 2
fi


java -cp $CPATH org.junit.runner.JUnitCore TestListExample > result.txt
FAILED=$(grep "There " result.txt | grep -Eo "[1-3]")
if [[ $? -eq 0 ]]
then
  SCORE=$(($SCORE+2))
  echo "All test passed. Your score is" $SCORE ""
  exit 3

else
  SCORE= "$((3 - $FAILED))"
  echo "Some test failed. Your score is $SCORE "
  cat result.txt
  exit 4

fi
```
---
## Sample 1
* https://github.com/ucsd-cse15l-f22/list-methods-corrected, which has the methods corrected (I would expect this to get full or near-to-full credit)
<img width="1021" alt="Screen Shot 2022-11-27 at 11 10 06 PM" src="https://user-images.githubusercontent.com/114315303/204216740-f7ad9750-f2a6-4d3c-ad25-93ea79a49122.png">

## Sample 2
* https://github.com/ucsd-cse15l-f22/list-methods-compile-error, which has a syntax error of a missing semicolon. Note that your job is not to fix this, but to decide what to do in your grader with such a submission!
<img width="800" alt="Screen Shot 2022-11-27 at 11 11 46 PM" src="https://user-images.githubusercontent.com/114315303/204216769-43b54f8c-6cbb-4399-9692-5059d01bb338.png">

## Sample 3
* https://github.com/ucsd-cse15l-f22/list-methods-filename, which has a great implementation saved in a file with the wrong name.
<img width="1023" alt="Screen Shot 2022-11-27 at 11 12 44 PM" src="https://user-images.githubusercontent.com/114315303/204216788-48970c0e-34cb-4c1a-a34c-1e27d24ba69d.png">

---

## Trace sample 2

```
rm -rf student-submission
git clone $1 student-submission
```

At the beginning of the scrip, we remove and recreate the student-submission dir, refreshing the file every time we test a new submission. 

```
cp TestListExamples.java student-submission
cd student-submission
```
Then we copy our test file to student-submission. There isn't a standard output or standard error, and the return would be null.

```
FILE=ListExamples.java
CPATH=.:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar

if [[ -f "$FILE" ]]
then
        echo "File exists"
        echo "Successfully cloned"
else
        echo "Cannot find the file"
        echo "Your score is 0"
        exit 1
fi
```
Next, we move on to the first if-statement, checking wether the submission contains the the target file  ListExamples.java. Since, the if-statement returns true, we echo "File exists" and "Successfully cloned" which are the standard output. Therefore, the else statement won't run, and we won't exit the process. There won't be any standard error or return code. 

```
SCORE=0

javac -cp $CPATH *.java

if [[ $? -eq 0 ]]
then
  SCORE=$(($SCORE+1))
  echo "Successfully compiled."
else
  echo "Unsuccessfully compiled. Your score is" $SCORE ""
  exit 2
fi
```
However, when we test wether the file compile successfully, the if-statement return false. The else statement that "Unsuccessfully compiled. Your score is 0" (because SCORE has be initialize to 0) echos, which is the standard error. The return code will be 2 and there will be no standard out.

```
java -cp $CPATH org.junit.runner.JUnitCore TestListExample > result.txt
FAILED=$(grep "There " result.txt | grep -Eo "[1-3]")
if [[ $? -eq 0 ]]
then
  SCORE=$(($SCORE+2))
  echo "All test passed. Your score is" $SCORE ""
  exit 3

else
  SCORE= "$((3 - $FAILED))"
  echo "Some test failed. Your score is $SCORE "
  cat result.txt
  exit 4

fi
```
Since we already exit in the previous else statment, the rest of the code/if-statement won't run. As a result, there will be no standard output, standard error, or return code. 



