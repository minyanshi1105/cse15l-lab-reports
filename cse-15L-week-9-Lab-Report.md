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
  exit
fi


java -cp $CPATH org.junit.runner.JUnitCore TestListExample > result.txt
FAILED=$(grep "There " result.txt | grep -Eo "[1-3]")
if [[ $? -eq 0 ]]
then
  SCORE=$(($SCORE+2))
  echo "All test passed. Your score is" $SCORE ""
  exit

else
  SCORE= "$((3 - $FAILED))"
  echo "Some test failed. Your score is $SCORE "
  cat result.txt
  exit 3

fi
```
