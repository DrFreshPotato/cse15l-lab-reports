# Lab Report 5
### Debugging Question
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/a74cf882-895b-4b3c-89e9-ebbdaaaf780f)  
### "TA" Response  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/7590928a-480d-47cb-96dd-4f7944cf1ebc)  

**Reproducing Error**  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/02e1cafa-fbd9-4026-8fbf-85980804e190)  

**Information Gained**  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/e78c8fa0-6869-4bac-8f19-6e4c5a7c1ae4)  
**Note**: This is the specific part of the link provided by the TA that showcases the command the student may have forgotten.  

## Setup  
These are the only commands needed to be inputted to set up the files and reproduce the error.
1. `git clone https://github.com/ucsd-cse15l-s23/grader-skill-demo2`  
2. `bash grade.sh https://github.com/ucsd-cse15l-s23/list-methods-nested`  
3. `vim grade.sh `(because the error results from the bash script, using vim to edit the text is needed)

![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/3ef0650f-c099-4d21-a8c8-f3017862e96a)  
**Note**: This is all of the required files that should exist
### Before Changes (Relevant Files)
**grade.sh File**  
``` 
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission
echo 'Finished cloning'

if [[ -f student-submission/ListExamples.java ]]
then
  echo 'ListExamples.java found'
else
  echo 'ListExamples.java not found'
  echo 'Score: 0/4'
  exit 1
fi

cp student-submission/ListExamples.java ./grading-area

cp TestListExamples.java grading-area/
cp -r lib grading-area/

cd grading-area

javac -cp $CPATH *.java

java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > junit-output.txt

# The strategy used here relies on the last few lines of JUnit output, which
# looks like:

# FAILURES!!!
# Tests run: 4,  Failures: 2

# We check for "FAILURES!!!" and then do a bit of parsing of the last line to
# get the count
FAILURES=`grep -c FAILURES!!! junit-output.txt`


if [[ $FAILURES -eq 0 ]]
then
  RESULT_LINE=`grep "OK " junit-output.txt`
  PASSED=${RESULT_LINE:4:1}
  TOTAL=$PASSED
else
  # The ${VAR:N:M} syntax gets a substring of length M starting at index N
  # Note that since this is a precise character count into the "Tests run:..."
  # string, we'd need to update it if, say, we had a double-digit number of
  # tests. But it's nice and simple for the purposes of this script.

  # See, for example:
  # https://stackoverflow.com/questions/16484972/how-to-extract-a-substring-in-bash
  # https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Shell-Parameter-Expansion

  RESULT_LINE=`grep "Tests run:" junit-output.txt`
  COUNT=${RESULT_LINE:25:1}
  TOTAL=${RESULT_LINE:11:1}

  PASSED=$(echo "($TOTAL-$COUNT)" | bc)

  echo "JUnit output was:"
  cat junit-output.txt
fi

echo ""
echo "--------------"
echo "| Score: $PASSED/$TOTAL |"
echo "--------------"
echo ""
```  
**TestListExamples.java File**  
```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.Arrays;
import java.util.List;

class IsMoon implements StringChecker {
  public boolean checkString(String s) {
    return s.equalsIgnoreCase("moon");
  }
}

public class TestListExamples {

  @Test(timeout = 500)
  public void testMergeRightEnd() {
    List<String> left = Arrays.asList("a", "c", "e");
    List<String> right = Arrays.asList("b", "h");
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "b", "c", "e", "h");
    assertEquals(expected, merged);
  }

  @Test(timeout = 500)
  public void testMergeLeftEnd() {
    List<String> left = Arrays.asList("a", "c", "z");
    List<String> right = Arrays.asList("b", "d");
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "b", "c", "d", "z");
    assertEquals(expected, merged);
  }

  @Test(timeout = 500)
  public void testFilterSingle() {
    List<String> input = Arrays.asList("Moon", "MOO", "moo");
    List<String> expect = Arrays.asList("Moon");
    List<String> filtered = ListExamples.filter(input, new IsMoon());
    assertEquals(expect, filtered);
  }

  @Test(timeout = 500)
  public void testFilterMulti() {
    List<String> input = Arrays.asList("Moon", "MOO", "moon", "MOON");
    List<String> expect = Arrays.asList("Moon", "moon", "MOON");
    List<String> filtered = ListExamples.filter(input, new IsMoon());
    assertEquals(expect, filtered);
  }
}
```  
**ListExamples.java File**  
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index2 += 1;
    }
    return result;
  }


}
```  

## Fixing the Error  
1. `vim grade.sh`
2. ![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/23693757-d781-4587-add1-9d8891dc1c08)  
The goal here is to use the find command to always get the exact file path. The changes made was the inclusion of the variable `find` that stores and runs the find command for ListExamples.java under the student-submission directory. With this new variable, it simply requires to replace every instance of `student-submission/ListExamples.java` with `$find` as this refers to the variable find.  
If the file ListExamples.java doesn't exist, the variable `find` will be empty. In Bash, an empty string is considered as a false value in conditional statements.  

# Reflection
Personally, this class has been very enjoyable as it taught me a lot of fundamentals of scripting, debugging, and terminal commands. The most impactful thing that was taught for this second-half of the quarter was definitely vim and bash scripts, being able to work entirely in the command line is quite useful and being able to store commands in a script saves so much hassle from going through command histories to repeat tests or other command line functions. It's a new tool to me that I look forward to continuing to use as it optimizes my workflow over time.
