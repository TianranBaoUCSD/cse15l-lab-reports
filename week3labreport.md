# File Exploration and Text Analysis from the Command Line
## Part 1 - Bugs
### Chosen Bug 
In ```ArrayExamples.java```, there is a method to reverse in place that does not work for arrays greater than size 1.   
Original Code: 
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
### Failure Inducing Input 
The code above fails for all arrays that are greater than size 1.  
The following block of code induces a failure in the code.
```
@Test
public void testReverseInPlace2(){
  int[] input2 = {1,2,3,4,5};
  ArrayExamples.reverseInPlace(input2);
  assertArrayEquals(new int[]{5,4,3,2,1}, input2);
}
```
### Successful Input
The code from the original code works for arrays that are size 1.
The following block of code doesn't induce a failure in the code.
```
@Test 
public void testReverseInPlace() {
  int[] input1 = { 3 };
  
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3 }, input1);
}
```
### Symptoms
Successful Input:  
![bugtestsuccess](week3bugtestsuccess.png)
Unsuccessful Input:   
![bugtestfailure](week3bugtestfailure.png)
### Fixing the Bug
Before Fix:
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
After Fix: 
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length/2; i += 1) {
    int temp = arr[i];
    arr[i] = arr[arr.length - i - 1]; 
    arr[arr.length - i - 1] = temp;
  }
}
```

The bug from before would cause the entire array to be overwritten by the second to last element. This fix works because it implements a temporary variable to store the value and essentially works its way inward from the ends of the array and swaps values from the sides until it reaches the center of the array.
## Part 2 - Researching Commands - ```grep```
The command I chose to explore further was ```grep```. 
### ```grep -v```
The ```-v``` option causes ```grep``` to return the lines that do not match the given query. 
Example 1: 
```
tianr@BAO-LAPTOP MINGW64 ~/UCSDgithub/CSE15L/docsearch (main)
$ grep -v "," technical/biomed/1468-6708-3-1.txt




        Introduction
        even though there is little evidence that overweight is
        associated with increased mortality in those over age 65.
        Six large controlled population-based studies of
        non-smoking older adults have investigated the association
        for relevant covariates [ 1 2 3 4 5 6 ] . All studies found
        with moderately high BMI had little or no extra risk except
```
In example 1, ```grep``` searches for lines in ```technical/biomed/1468-6708-3-1.txt``` that do not contain commas, and this results in some lines of the text file, such as "Older adults are frequently counseled to lose weight," and "excess risk for persons with very low BMI, but that persons" to not be included in the output.
Example 2: 
```
tianr@BAO-LAPTOP MINGW64 ~/UCSDgithub/CSE15L/docsearch (main)
$ grep -v "to" technical/plos/journal.pbio.0020001.txt 





        challenges of building bridges across these gaps that should bring the United Nations and
        importance of reducing the inequalities in science between developed and developing
        countries, asserting that “This unbalanced distribution of scientific activity generates
        serious problems not only for the scientific community in the developing countries, but for
        development itself.” Indeed, Mr. Annan's sentiments have also been echoed recently by
```
In example 2, ```grep``` searches for lines in ```technical/plos/journal.pbio.0020001.txt ``` that do not contain the word "to", and this results in the first two lines of text ("Kofi Annan, the Secretary-General of the United Nations, recently called attention to
        the clear inequalities in science between developing and developed countries and to the") and the fourth line of text "the world scientific community closer to each other (Annan 2003). Mr. Annan stressed the" being removed.

### ```grep -????```
The ```-???``` option causes ```grep``` to ???. 
Example 1: 
```
```
EXPLAIN
Example 2: 
```
```
EXPLAIN

### ```grep -????```
The ```-???``` option causes ```grep``` to ???. 
Example 1: 
```
```
EXPLAIN
Example 2: 
```
```
EXPLAIN

### ```grep -????```
The ```-???``` option causes ```grep``` to ???. 
Example 1: 
```
```
EXPLAIN
Example 2: 
```
```
EXPLAIN
