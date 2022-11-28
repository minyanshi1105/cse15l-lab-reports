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
## Sample 1
<img width="1021" alt="Screen Shot 2022-11-27 at 11 10 06 PM" src="https://user-images.githubusercontent.com/114315303/204216740-f7ad9750-f2a6-4d3c-ad25-93ea79a49122.png">

## Sample 2
<img width="800" alt="Screen Shot 2022-11-27 at 11 11 46 PM" src="https://user-images.githubusercontent.com/114315303/204216769-43b54f8c-6cbb-4399-9692-5059d01bb338.png">

## Sample 3
<img width="1023" alt="Screen Shot 2022-11-27 at 11 12 44 PM" src="https://user-images.githubusercontent.com/114315303/204216788-48970c0e-34cb-4c1a-a34c-1e27d24ba69d.png">










