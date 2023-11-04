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

In this example, the string pattern is "Three months later". As we can see in the output, each indent starts with either "Three" or "Months". This can be useful when checking for redudancy in text. 

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


              .... (The file was really long)
~~~

The second one is a lot longer since This can be useful with documentation that uses dates to specify when it was updated. However, if the string pattern is too simple for example if we used a word like "the" it can lead to scenarios like this where you are given EVERY possible outcome of "the", which can be annoying to deal with. 



## **egrep**

I also used ChatGPT to find this command. Below is the prompt I gave and the output I received from the AI.

As a follow up from the previous prompt and after the AI being a bit misleading. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/6918821a-746b-42eb-8b0e-57111220f0de)

The output gave me a list of commands and I chose this one

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/df37a5ff-2cc2-488c-83ee-cb3aa76f495d)

This command is an alternative to **grep**, meaning the arguements can be treated the same just with a slightly different command. 

~~~
$ egrep "California" technical/911report/chapter-7.txt
~~~

~~~
$ egrep "Kingdom" chapter-2.txt
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

Similar to **findstr**, instead of using string patterns, it finds lines that contain the inputted string (in this case, "California"). This can be useful when trying to see how many times a particular word is used. 

**Second**

~~~
                Kingdom. It praised the 1983 suicide bombing in Beirut that killed 241 U.S. Marines,
                the Kingdom and other states bordering the Persian Gulf in donating money to build
                Kingdom, Bin Ladin and a number of Islamic clerics began to publicly denounce the
~~~

Same as the example before this, it is now finding all the lines where "kingdom is". Luckily, it has less amount of lines so finding those lines within the file is not as tideous. Another way how the command be useful is that it can intake particular phrases and show how many times that phrase is used. 


After testing the difference between **grep** and **egrep**, it was difficult to notice the difference between the two. I asked the AI once again what the difference between the two is. 

**Prompt**

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/469b4c06-7cac-4505-ab21-ea44cb3be5b9)

Output

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/32068ea9-c355-4b7b-87ee-1623af487a4b)


I then followed up with asking for an example to get a visual. 

**Prompt**

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/4bdb7715-44d3-49ad-98ea-47c5a75978c2)

**Output**

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/7c0a9b1a-e35f-4d95-84b6-08112668d302)


Essentially, **egrep** is a more suitable command to use if you have a large text file and inputting the string would not have to be so tideous, as shown in the example. This would be useful when you want to find similar strings in the file and do not want to worry about dealing with tideous syntax errors. The only downside is how cluttered the terminal can be, so it would be ideal to only use phrases or words that are not used as much or else you can end up almost printing out the whole text file. 

## **sed**

I once again asked ChatGPT to give me more commands that work similar to **grep**

**Prompt**

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/3597652a-f4fa-4bee-92ae-ea02f89c46fb)

**Output**

Out of the whole list, I chose this one. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/0a2bb3bf-8dcc-4da8-9859-9aebb458207f)

Following up with a prompt asking for an example. 

**Prompt** 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/1b6c64c1-e0a2-445c-add5-f818c9ebd7cd)

**Output**

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/2c90a63d-8866-407a-b51a-980a5116b2ac)
![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/3e700bfa-dc1a-40da-abc2-b235cac00e79)


Here are some examples I used using the technical directory. For reference, I will use the following texts as a reference. 

File: Session2-PDF.txt

Path: docsearch/technical/government/Alcohol_Problems
~~~
Session 2.
Identifying ED Patients with Alcohol Problems

Robert Woolard, MD
Many patients in the emergency department (ED) have alcohol
problems, and they can be identified.1 Research on techniques used
to identify these patients has been conducted, but several areas of
interest should be addressed by further research. We need to
further examine and refine alcohol-screening questionnaires in the
ED. We need to determine the sequence and combination of questions
...
~~~

For this file, I wanted to replace "Robert Woolard" with "Barry Bonds"
~~~
$ sed 's/Robert Woolard/Barry Bonds/g' Session2-PDF.txt
~~~

The output I got 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/b872c7e6-522c-46b9-bf9c-1b20a6c44994)


The command is looking for the string I want to replace and then replacing it with the new string I gave it. As shown above, "Robert Woolard" was changed to "Barry Bonds". This can be useful when official documentation needs to have updated information. 


File: Session3-PDF.txt

Path: docsearch/technical/government/Alcohol_Problems
~~~
Session 3.
Intervening with Alcohol Problems
in Emergency Settings

Carlo C. DiClemente, PhD* Carl Soderstrom, MD
Excessive alcohol consumption plays an important role in many of
the medical conditions, accidents, and injuries that cause visits
to emergency departments and trauma centers. Many studies have
documented the presence of alcohol among patients admitted to
...
~~~

For this file, I wanted to replace "alcohol" with "sugar". 
So I used the following command
~~~
$ sed 's/alcohol/sugar/g' Session3-PDF.txt
~~~
The output I got for this was actually a lot bigger since alcohol is a frequent string that shows up in the text file and the command found EVERY "alcohol" and replaced it with "sugar". 

I will not show the entire output but I will use a snippet to show the before and after of using the command. 


![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/cac2680f-1ebd-4b45-baad-f872784e14db)

Notice that the command took into consideration of only the "alcohol", not "Alcohol". So whenever it used, be mindful that grammar does matter with the **sed**. This can be useful in cases where a document happens to have a word that can be considered "offensive" and they can use this command to change that word. It would not entirely fix the problem but it definitely will easen up the tension and makes corrections easier when reviewing. 

## **perl** 
Using the same prompt as before, one of the commands I was given from the AI was **perl**

**Prompt**

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/1117bf93-b9a5-4dd8-abc5-e7f68730ead6)

**Output**

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/62fdf343-e2d0-4228-9165-956670bbe277)

Once again, I asked for the AI to elaborate and how to properly use **perl** and it gave me the following

**Prompt**

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/8be76e9b-b5a0-4569-88de-309bb5b8c4d6)

**Output**

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/f834aad8-d422-43a7-afba-215779771b66)
![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/a482f5d4-ce9c-4d59-94b0-64066281ce4e)

Here are some examples of **perl** being used.

File: 1468-6708-3-3.txt

Path: docsearch/technical/biomed 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/cbbe5c07-44d7-40fc-8e6c-fd8b8883dd2a)

Command I used

~~~
$ perl -ne 'print if /Three published/' 1468-6708-3-3.txt
~~~

Here is the output I got from that command. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/87bec7b3-26df-4407-bd51-e8ae72a53ae4)

What happened is that when **perl** printed the whole line of text under the condition of it containing the string "Three published". In this case, there is only line where it has the string "Three published". This can be useful in cases where you are asked to change a particular phrase in a big text file. Using **perl** will help with getting you straight to it. Then you can follow up with **sed** to change the string.

However, what if we want to change a string that is contained in a lot of lines? 


File: 1468-6708-3-4.txt

Path: docsearch/technical/biomed 

The file being used 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/2ca37392-0d86-4aaf-a4b5-407c8d4b2c9b)


Command that was used

~~~
$ perl -ne 'print if /multicenter/' 1468-6708-3-4.txt
~~~

The output that followed

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/e348a246-e708-4b39-a074-4a1876b6ba8f)

In this scenario, let's say I am reviewing the document that a colleague. As it is shown, you can see that the string "multicenter" is being used in the first two examples. **perl** would be useful to see how many times multicenter was used and it would print me all the lines that contained "multicenter". From here, I would suggest the colleague to change it up and not have their examples be so robotic-like. **perl** makes situations like checking grammar in a big document a lot easier, making navigation of the string a lot easier. 









































