# **Lab Report 3**
**In summary**

In lab for week 4 and 5, we debugged programs by observing their symptoms and running tests. We also found out new terminal commands that help us navigate through more 

# **Debugging Programs**

I will use the ArrayExamples and ArrayTests code, both were provided in Lab during Week 4. 

This is the code for ArrayExamples.java, which originally had a bug in it. 
~~~
import static org.junit.Assert.assertArrayEquals;

import org.junit.Test;

public class ArrayExamples
{
  // With the bug 
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr){
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }

}
~~~

This is the test that was ran on it which gave a failure inducing-input. The intent was for the inputted array to be outputted but with the elements in reverse order. 
~~~
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {

  @Test 
  public void testReversed()
  {
    int[] input1 = {2,4,6};
    assertArrayEquals(new int[]{6,4,2}, ArrayExamples.reversed(input1));
  }
}
~~~

Here is the symptom that displayed when the test was ran on the buggy program. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/3bc92732-d0f9-4e50-8312-e2ace9ad3892)

With the same program being tested, there was another JUnit test that was provided where the test was able to bypass the bug. 
~~~
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
  @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
}
~~~

The symptom for this test is the following. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/db5944cc-0c5e-43ff-a338-3b28cded1533)

It is noticiable then when the array is empty, the tests can pass. However, any other array with integers as its elements, will result in the bug occuring. Refer to the first test we ran. It can be noticed that the array is not reverting the elements and is instead just returning the one that we inputted, as stated in the first lines of the symptom. 


![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/3bc92732-d0f9-4e50-8312-e2ace9ad3892)

The bug happened because we declared new array to be set to the inputted array. However, in the contents of the for loop, we were setting the contents of the new array to the inputted array, but the new array was empty, which is what caused the bug to happen. That is why the second test passed since the inputted array was also empty.  

To debug the program, the inputted array must be stored into a new array instead and then set the elements of the inputted array (with the elements of the inputted array reversed) and then set them to the new array. You would also return the new array instead of the inputted one. 

~~~
// Fixed (no bug) 
import static org.junit.Assert.assertArrayEquals;

import org.junit.Test;

public class ArrayExamples
{
  // With the bug 
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) 
    {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
}
~~~


# **Researching Commands** 

During lab in week 5, we learned of new terminal commands that helped us find files in a more efficient and faster way. Below are some commands we used in said lab.

* **less**
* **find**
* **grep**

However, there are actually a LOT more commands that function similarly to these three. For this report, we will use ChatGPT to help us find new terminal commands that are similar to the **grep** command. 

**I asked the AI the following prompt**

"put screenshot of input"

**It gave me a total of 13 alternative uses of the 'grep' command**

"put screenshots of the output"

# **grep -o**

This variation of the command only prints the pattern that matches. 

~~~
grep -o "DECLA" 911report/chapter-2.txt
~~~







































