**In summary**

In lab for week 4 and 5, we debugged programs by observing their symptoms and running tests. We also found out new terminal commands that help us navigate through more 

# **Debugging Programs**
I will use the ArrayExamples and ArrayTests code, both were provided in Lab during Week 4. 

This is the code for ArrayExamples.java, where the bug had 
~~~
import static org.junit.Assert.assertArrayEquals;

import org.junit.Test;

public class ArrayExamples
{

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
