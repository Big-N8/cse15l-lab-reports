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

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/65442d25-dbc5-4462-93a9-0156168ceea3)

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
                that the FBI's work should be done primarily by the field offices. To emphasize this
                FBI thwart terrorism before such acts can be perpetrated." Within headquarters, he
                Center at the CIA and arranged for exchanges of senior FBI and CIA counterterrorism
                counterterrorism. FBI, Justice, and Office of Management and Budget officials said
                that FBI leadership seemed unwilling to shift resources to terrorism from other
                areas such as violent crime and drug enforcement; other FBI officials blamed
                FBI's counterterrorism resource needs. In addition, Freeh did not impose his views
            In 1998, the FBI issued a five-year strategic plan led by its deputy director, Robert
                "Bear" Bryant. For the first time, the FBI designated national and economic
                FBI. The plan mandated a stronger intelligence collection effort. It called for a
            ignating "national and economic security" as its top priority in 1998, the FBI did
                not shift human resources accordingly. Although the FBI's counterterrorism budget
                tripled during the mid-1990s, FBI counterterrorism spending remained fairly constant
            Second, the new division intended to strengthen the FBI's strategic analysis
                senior managers in the FBI's operational divisions. The new division was supposed to
                identify trends in terrorist activity, determine what the FBI did not know, and
                ultimately drive collection efforts. However, the FBI had little appreciation for
                fashion-providing support for existing cases. Compounding the problem was the FBI's
            Moreover, analysts had difficulty getting access to the FBI and intelligence
                community information they were expected to analyze. The poor state of the FBI's
                FBI had never completed an assessment of the overall terrorist threat to the U.S.
            Third, the FBI did not have an effective intelligence collection effort. Collection
                on the job. The FBI did not have an adequate mechanism for validating source
                reporting, either internally or externally. The FBI did not dedicate sufficient
            Finally, the FBI's information systems were woefully inadequate. The FBI lacked the
                sharing its institutional knowledge. FBI agents did create records of interviews and
            In 1999, the FBI created separate Counterterrorism and Counterintelligence divisions.
                urgent need to increase the FBI's counterterrorism capability. His plan, called
                almost every FBI field office was assessed to be operating below "maximum capacity."
            Legal Constraints on the FBI and "the Wall" The FBI had different tools for law
                could be briefed on FISA information but could not direct or control its
                FBI shared with prosecutors information pertinent to possible criminal
                investigations was left solely to the judgment of the FBI.
                prior consultations between FBI agents and prosecutors, the judge might rule that
                Janet Reno about the lack of information-sharing controls. On his own, he began
                information sharing between Justice Department prosecutors and the FBI. They were
                there was far less information sharing and coordination between the FBI and the
                the FBI's warrant requests to the FISA Court. The information flow withered.
                not between two kinds of FBI agents, those working on intelligence matters and those
                Review, FBI leadership, and the FISA Court built barriers between agents-even agents
                serving on the same squads. FBI Deputy Director Bryant reinforced the Office's
            This perception evolved into the still more exaggerated belief that the FBI could not
            There were other legal limitations. Both prosecutors and FBI agents argued that they
                jury, and even that prohibition had exceptions. But as interpreted by FBI field
            Other Law Enforcement Agencies The Justice Department is much more than the FBI. It
                the FBI or CIA for counterterrorism use.
                watchlisting suspected terrorists and with the intelligence community and the FBI in
                cases, but the FBI possessed the classified information sometimes needed as
                Department. It focused on the FBI's priorities of Hezbollah and Hamas, and began to
                task force was managed by the New York Field Office of the FBI, and its existence
                representatives, as partners in the FBI investigation. The FBI expanded the number
                officials, its agents did become involved with those of the FBI whenever terrorist
            The Bureau of Alcohol, Tobacco, and Firearms was used on occasion by the FBI as a
            Before 9/11, with the exception of one portion of the FBI, very little of the
                prosecution. As FBI agents emphasized to us, the FBI and the Justice Department do
                not have cruise missiles. They declare war by indicting someone. They took on the
                receive a broad range of intelligence data from the FBI, CIA, and other agencies so
                United States. For example, information on the FBI's effort in 1998 to assess the
                Historically, decisive security action took place only after a disaster had occurred
                FBI and CIA four years earlier to provide terrorist watchlists to improve
                pressures from the air carriers to control security costs and to "limit the impact
                intelligence community include the national security parts of the FBI; the Bureau of
                command and control methods. With globalization and the telecommunications
                requirements. Also, the NSA was supposed to let the FBI know of any indication of
                crime, espionage, or "terrorist enterprise" so that the FBI could obtain the
                because it believed that this was an FBI role. It also did not want to be viewed as
                acquiring information and exercising command and control over their operations. The
                in World War II after having first thought the FBI might take that role. The father
                of Central Intelligence. Lobbying by the FBI, combined with fears of creating a U.S.
                    Gestapo, led to the FBI's being assigned
                CIA and the FBI.
                the FBI field offices in the United States, everyone in the Directorate of
                representation from the FBI and other agencies. In the formal table of organization
                Congress or in the president's Office of Management and Budget. Like the FBI and the
                security advisor, Zbigniew Brzezinski, took charge, and the coordination function
            Secretaries of state after Shultz took less personal interest in the problem. Only
                secretary of defense has ultimate control, under the president. Among the uniformed
                Security Advisor Zbigniew Brzezinski took charge of crisis management.
                national security advisor. When President Clinton took office, he decided right away
                worldwide, including one in New York. Neither the FBI nor the CIA had ever heard of
                by increasing wiretap and electronic surveillance authority for the FBI, requiring
                only for the FBI and CIA but also for local police.
                significantly larger budgets for the FBI, with much of the increase designated for
                the Justice Department and the FBI in charge at home and left terrorism abroad to
                medical services, air traffic control, financial services, telephone systems, and
            The most substantial change in national security oversight in Congress took place
                said, Congress still took too little action to address institutional
                Intelligence took the unprecedented step of threatening to bring down the defense
                infrequently took center stage; and when it did, the context was often terrorists'
                but there was no reorganization of national security functions. The Senate undertook
                responsibility for the FBI tightly restricted appropriations for improvements in
                information technology, in part because of concerns about the FBI's ability to
            Although individual representatives and senators took significant steps, the overall
                intelligence and other sources, including material gathered by FBI agents and Kenyan
                FBI's New York Field Office and the U.S. Attorney for the Southern District of New
            Counterterrorist Center officers briefed Attorney General Janet Reno and FBI Director
                success. The Center's chief, "Jeff," joined John O'Neill, the head of the FBI's New
                over three time zones, even bringing in personnel from the region. The FBI also
                When thanking the Saudis, Director Tenet took advantage of the opening to ask them
                as well as hitting al Shifa. The President took the Sudanese tannery off the target
                secretary, Allen Holmes, took the paper to Slocombe's chief deputy, Jan Lodal, but
                to designateTaliban-controlled Afghanistan as a state sponsor of terrorism or to
                also raised the "remote possibility" of Yemen, which offered vast uncontrolled
            The President suggested that Pakistan use its control over oil supplies to the
                Arab country. The CIA described working with FBI operatives to prevent a planned
                target. On October 26, Clarke's CSG took the unusual step of holding a meeting
                territory. Participants noted that while the FBI had been given additional resources
                to distribute versions of the report to the FBI and FAA to pass to the New York
                D.C. or New York. After investigation, the FBI could find no information to support
                than a roadside ambush because they would have better control, it would be less
                up the FBI building in Washington, D.C. In September, the CSG reviewed a possible
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

The output that came out from this command was the following. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/a510306a-24b8-47f1-a2e2-9428ed047406)

As we saw in lab, **grep** on its own listed any 





















