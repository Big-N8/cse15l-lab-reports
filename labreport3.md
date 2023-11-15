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

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/2d1c09c3-fb13-40c3-a5d4-7185608c55d3)


**It gave me a total of 13 alternative uses of the 'grep' command**

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/289d75d8-d962-47bd-9712-7d99860a4d3c)
![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/a36f7cc5-e0ae-4649-b3ea-4c833d4a5691)
![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/34492da4-f277-44ed-985d-e6e057b58cbe)
![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/ff135cac-9d0e-43c5-9e41-cfac96697eba)


**Out of the 13, I chose the following 4**
- **grep-o**
- **grep-n**
- **grep-c**
- **grep-w**

# **grep -o**

This variation of the command only prints the pattern that matches exactly. 

~~~
// Example 1 
$ grep -o "DECLA" technical/911report/chapter-2.txt
DECLA
DECLA
~~~

Since this text file uses captialzation for headers of certain sections, the command is essentially behaves similarly as the shortcut "Control+f" where it will find every sort of matching character, regardless of how incomplete the word is. Only difference being, it is more. This can be useful to help make navigation through long texts slightly easier. 

~~~
// Example 2
$ grep -o "Clinical" technical/biomed/1468-6708-3-1.txt
Clinical
Clinical
Clinical
Clinical
~~~

This example is showing how many times the word "Clinical" on its own shows up in the text file. This can be useful when trying to find how many times a word appears in a text in an exact form (same capitalization and not jointed with another word. 

# **grep -n**

This variation of the command shows the matching lines along with the line number 

~~~
// Example 1
$ grep -n "handler" Server.java
20:    URLHandler handler;
21:    ServerHttpHandler(URLHandler handler) {
22:      this.handler = handler;
27:            String ret = handler.handleRequest(exchange.getRequestURI());
44:    public static void start(int port, URLHandler handler) throws IOException {
48:        server.createContext("/", new ServerHttpHandler(handler));
~~~

The command is finding all of the lines in Server.java that match the pattern, "handler" and listing the lines along with the line numbers. This can be useful when you change a variable name and don't want to go line for line looking for the old variable names. Instead, this command will directly give you all of the lines with them, making the adjustment a lot easier. 

~~~
// Example 2
$ grep -n "Pakistan" technical/911report/chapter-5.txt
27:                traces his ethnic lineage to the Baluchistan region straddling Iran and Pakistan.
39:                soon after graduating from college. Visiting Pakistan for the first time in early
53:                Pakistan, he moved his family to Qatar at the suggestion of the former minister of
58:                position there until early 1996, when he fled to Pakistan to avoid capture by U.S.
95:                Islamabad by Pakistani authorities on February 7, 1995, after an accomplice turned
148:                frequently between Pakistan and Afghanistan in 1997 and the first half of 1998,
311:                returned to Pakistan following the 1993 World Trade Center bombing. Like Yousef, KSM
493:                to Karachi, Pakistan. There KSM instructed them on Western culture and travel. Much
537:                their Saudi passports to conceal their prior travels to and from Pakistan. KSM had
591:                return to Pakistan, so he traveled to Yemen instead.
875:                Pakistani visas and then return to him for further directions on how to reach
987:                were concerned that the Pakistani visas in their old passports would raise
1028:                Pakistan, then on his return to Saudi Arabia his passport, bearing a Pakistani
1029:                stamp, would be confiscated. So operatives either erased the Pakistani visas from
1124:            Bin Ladin relied on the established hawala networks operating in Pakistan, in Dubai,
~~~

Similar to the **grep -o**, it shows all the lines where "Pakistan" is used. This is a very useful improvement since now it shows exactly where the string was found throughout the whole text. 

# **grep-c**
~~~
// Example 1
$ grep -c "Alcohol" technical/government/Alcohol_Problems/Session2-PDF.txt
47
~~~

This command just finds the counts each string that matches "Alcohol" and outputs the total amount of matches that were found in the text file. This can be useful when you want to see how finite 

~~~
// Example 2
$ grep -c "Alcohol" technical/government/Alcohol_Problems/*.txt
technical/government/Alcohol_Problems/DraftRecom-PDF.txt:1
technical/government/Alcohol_Problems/Session2-PDF.txt:47
technical/government/Alcohol_Problems/Session3-PDF.txt:32
technical/government/Alcohol_Problems/Session4-PDF.txt:31
~~~

Similar to the example above, it counts the amount of matches found. However, now it is reading the matches found in each file in the **Alcohol_Problems** directory which is useful since we can find out with one command instead of reusing the line used in the first example. 

# **grep-w**

~~~
// Example 1
$ grep -w "Pre" technical/plos/*.txt
~~~

You might be confused why nothing is printing. This variation only intakes string patterns that consist of only whole words. This can be useful when we want to avoid any unecessary "matched" string patterns. For example, the word I am looking for is "President". If this were a normal grep command, it would show all the matches with "pre", such as "predecessor", which is what we do not want.

~~~
// Example 1
$ grep -w "President" technical/911report/chapter-8.txt
            He in turn met daily with President Bush, who was briefed by the CIA through what is
                known as the President's Daily Brief (PDB). Each PDB consists of a series of six to
            Reports similar to many of these were made available to President Bush in morning
                intelligence briefings with DCI Tenet, usually attended by Vice President Dick
            To enlist more international help, Vice President Cheney contacted Saudi Crown Prince
                airport during the G-8 summit, which President Bush attended.
            During the spring and summer of 2001, President Bush had on several occasions asked
                attack in the United States. The President told us the August 6 report was
                historical in nature. President Bush said the article told him that al Qaeda was
                dangerous, which he said he had known since he had become President. The President
                President George W. Bush on August 6, 2001.37 Redacted material is indicated by
                President and his top advisers of the possibility of a threat of an al Qaeda attack
                in the United States. DCI Tenet visited President Bush in Crawford, Texas, on August
                17 and participated in PDB briefings of the President between August 31 (after the
                President had returned to Washington) and September 10. But Tenet does not recall
                any discussions with the President of the domestic threat during this period.
                the summer. In addition to his daily meetings with President Bush, and weekly
                to the President. Thus, these individual cases did not become national priorities.
~~~

Since the pattern is now a whole word, it printed out every line in that file that contained said pattern. This can only be useful when you want a specific whole word for your string pattern instead of a particular prefix or suffix.







































