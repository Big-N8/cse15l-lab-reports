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

The prompt that I gave the AI was the following: **Give me terminal that are similar to the command "grep". Provide associated code for a visual.** 

As I read the first set of commands it gave me, I noticed that some of the commands worked for windows and others worked for linux terminals (after doing some online research and finding out why some of them were not being recognized)

I then followed up with the following prompt to be more specific: **Keep in mind, I am using windows. So please give me commands that are compatible with windows.**

In response, It gave me a new set of compatible commands

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/5aa89dd0-3389-427c-82b5-2eb87409d823)


Though I will not be using them all that were give, one of them that stood out to me was the **findstr** command. 

## **findstr**

Using the technical directory, I made sure to use **cd** and changed the directory into the following path **docsearch/technical/911report** for this example. 

You would use the command in the following order: the command (findstr), the string you want it to find in quotes, the text file you want it to look through.  
~~~
$ findstr "Three months later," chapter-2.txt
~~~

~~~
$ findstr "FBI took control" chapter-3.txt
~~~

The output for the example above is the following

**First**

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/65442d25-dbc5-4462-93a9-0156168ceea3)

**Second**

~~~
   died. More than a thousand were injured. An FBI agent at the scene described the
            The New York Field Office of the FBI took control of the local investigation and, in
            Second, the FBI and the Justice Department did excellent work investigating the
                bombing. Within days, the FBI identified a truck remnant as part of a Ryder rental
                rental office to get back his $400 deposit. The FBI arrested him there on March 4,
            The FBI identified another conspirator, Ahmad Ajaj, who had been arrested by
            The arrests of Salameh, Abouhalima, and Ayyad led the FBI to the Farouq mosque in
                fight against God's enemies. An FBI informant learned of a plan to bomb major New
                "landmarks plot," the FBI in June 1993 arrested Rahman and various
            The FBI assembled, and the U.S. Attorney's office put forward, some evidence showing
            The Justice Department and the FBI At the federal level, much law enforcement
                dominant agency under Justice is the Federal Bureau of Investigation. The FBI does
                possible conflicts, the FBI designates a single office to be in charge of an entire
                FBI's institutional knowledge on Bin Ladin and al Qaeda resided there. This office
                to spend much energy on matters over which they had no control and for which they
            The FBI's domestic intelligence gathering dates from the 1930s. With World War II
                looming, President Franklin D. Roosevelt ordered FBI Director J. Edgar Hoover to
                FBI's domestic portfolio against all rivals. Hoover felt he was accountable only to
                the president, and the FBI's domestic intelligence activities kept growing. In the
                1960s, the FBI was receiving significant assistance within the United States from
                domestic dissidents. The FBI had spied on a wide range of political figures,
                "highly favorable" view of the FBI dropped from 84 percent to 37 percent. The FBI's
                Still, his guidelines, like Levi's, took account of the reality that suspicion of
                Smith's guidelines also took account of the reality that potential terrorists were
            In 1986, Congress authorized the FBI to investigate terrorist attacks against
                authority for the FBI to make arrests abroad without consent from the host country.
                Counterterrorist Center, where the FBI, the CIA, and other organizations could work
                together on international terrorism. While it was distinctly a CIA entity, the FBI
            The strengths that the FBI brought to counterterrorism were nowhere more brilliantly
                Meanwhile, FBI technicians, working with U.K. security services, gathered and
                with other evidence, the FBI put together a case pointing conclusively to the Libyan
                solve-the FBI remained capable of extraordinary investigative success.
            FBI Organization and Priorities In 1993, President Clinton chose Louis Freeh as the
~~~



As ChatGPT mentioned, the purpose of the command is to take the inputted string and find as it called "string patterns". If you look closely at each of the outputs indents for the first output, you can see the first two have the strings "Three" and the other two towards the bottom have the strings "Months" in common. The second one is a lot longer since This can be useful with documentation that uses dates to specify when it was updated. To also mention, the inputted string must be something very specific or this could lead to the command printing most or all of the contents from the file as shown in the second example. 

## **egrep**

I also used ChatGPT to find this command. Below is the prompt I gave and the output I received from the AI.

As a follow up from the previous prompt and after the AI being a bit misleading. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/6918821a-746b-42eb-8b0e-57111220f0de)

The output gave me a list of commands and I chose this one

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/df37a5ff-2cc2-488c-83ee-cb3aa76f495d)

This command is similar to **grep** in terms of the input: command, String (with quotes), path to text file

~~~
$ egrep "California" technical/911report/chapter-7.txt
~~~

~~~
$ egrep "2001" technical/911report/chapter-8.txt
~~~


The output that came out from this command was the following. 

**First**

~~~
            Why Hazmi and Mihdhar came to California, we do not know for certain. Khalid Sheikh
                Mohammed (KSM), the organizer of the planes operation, explains that California was
                that al Qaeda had any agents in Southern California. We do not credit this
                California, so that they could begin pilot training as soon as possible. KSM claims
                Culver City, one of the most prominent mosques in Southern California.
                fellow inmates at a California prison in September- October 2003 that he had known
                rest of his time in California, until mid-December; he would then leave for Arizona
                Translating between English and Arabic, he assisted them in obtaining California
                of California declined to prosecute him on charges arising out of his alleged
                impression is that soon after arriving in California, Hazmi and Mihdhar sought out
                child arrived, he could stand life in California no longer. In late May and early
                California, and Arizona; and he briefly started at a couple of them before returning
                an English as a second language program in Oakland, California, which he had
~~~

**Second**

~~~
 As 2001 began, counterterrorism officials were receiving frequent but fragmentary
                2001, it is useful to understand how threat information in general is collected and
                chosen for briefing the president and senior officials. During 2001, Director of
                2001, that related to Bin Ladin. The PDB is considered highly sensitive and is
                (NSA), CIA, or FBI. The Drumbeat Begins In the spring of 2001, the level of
            In May 2001, the drumbeat of reporting grew louder with reports to top officials that
            On July 18, 2001, the State Department provided a warning to the public regarding
            During the spring and summer of 2001, President Bush had on several occasions asked
                President George W. Bush on August 6, 2001.37 Redacted material is indicated by
            Most of the intelligence community recognized in the summer of 2001 that the number
                sleeper cells were likely in the United States. In January 2001, Clarke forwarded a
            Clarke reflected a different perspective in an email to Rice on September 15, 2001.
                procedures, none of the few that were released during the summer of 2001 increased
                briefings for specific air carriers between May 1, 2001, and September 11, 2001. Two
                such mistakes created opportunities during 2001, especially in late August.
            On four occasions in 2001, the CIA, the FBI, or both had apparent opportunities to
            January 2001: Identification of Khallad
                source who had identified Khallad. In early January 2001, two photographs from the
                    2001.
                did not have access-that information regarding the January 2001 identification of
                in January 2001, the CIA had resumed its search for him, placed him on the State
                have been found-either before or at the time he applied for a new visa in June 2001,
            Spring 2001: Looking Again at Kuala Lumpur
            By mid-May 2001, as the threat reports were surging, a CIA official detailed to the
            June 2001: The Meeting in New York
            August 2001: The Search for Mihdhar and Hazmi Begins and Fails
            During the summer of 2001 "John," following a good instinct but not as part of any
                15, 2000, and again on July 4, 2001. "Jane" and "Mary" also learned that there was
                of Justice Inspector General.86We will recap it briefly here. In July 2001, an FBI
            On August 15, 2001, the Minneapolis FBI Field Office initiated an intelligence
                United States in February 2001, and had begun flight lessons at Airman Flight School
                order was signed on August 17, 2001.
                the threat reporting during the summer of 2001.
                this information been available in late August 2001, the Moussaoui case would almost
            The FBI also learned after 9/11 that the millennium terrorist Ressam, who by 2001 was
                Khalid Sheikh Mohammed received by the intelligence community in the summer of 2001.
            When additional pieces of the puzzle arrived in the spring and summer of 2001, they
                person known as "Mukhtar" that the CIA had begun analyzing in April 2001. The CIA
                12, 2001, a CIA report said that "Khaled"was actively recruiting people to travel
            As Tenet told us, "the system was blinking red" during the summer of 2001. Officials
            Yet no one working on these late leads in the summer of 2001 connected the case in
~~~

As we saw in lab, **grep** on its own listed any 





















