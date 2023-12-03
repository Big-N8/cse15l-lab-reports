# **Lab Report 5**
## **Part 1: Debugging Scenario**

*Following Scenario: Student has trouble finding bug in their code. Student asks for help on EdStem and makes the following post.*

---
 **General: Issues with Lab 7 test**

Anonymous Gopher 

Hello, 
In preparation for Skill Demo 3, I am praciticing writing my own tests for the code we got in Lab 7. However, I am not sure where I am going wrong in the test writing. I keep getting this weird error whenever I am writing the test for the reversed method in ArrayExamples.  Here is my code and bash script for reference. 

ArrayExamples

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/484727e6-616a-484b-ba62-d1136d9d4607)


ArrayTests

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/c5f49f32-123f-444e-8cd4-7de0787cfffc)

test.sh

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/f7fe1054-ce3b-49b3-8e52-4830afa11198)


This is what showed up on my terminal. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/798e8d19-5492-494d-acc4-8c6754a4dee1)




Any help would be appreciated. 

---

*The TA responds to the post sometime later in that day.*

---
Hi, 

The error is actually not in your test but in your code for ArrayExamples. As seen in your terminal output, it mentions that it was expecting 60 but it actually read 55. Recall the number inside of [ ] is referring to a specific index in that array. You know that 55 is at the beginning of your inputted array and 60 is at the end. Take a look at line 10. Should the index of the old array be just "i" alone? If not, what changes should you make so that it is mapped to the correct index? Hint: its in both line 8 and line 9. Let us know if you need more help.

---

*15 minutes later, the student replies back.* 

---

I found where I was going wrong! I was assiging the indexes of the old array to the new array but in the same order it was inputted instead of the end of the array and working backwords. I replaced "i" with "arr.length-i-1" on line 10 and it worked. Thank you for your help!

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/2087b463-230d-4faf-9ba2-d0e2d2b7e05a)

---
*The post gets 3 likes from two instructors and the TA that helped the student*

## Part 2: Reflection 

Despite how confusing the navigation was at first, learning vim was actually pretty cool. I didn't think we could edit files from the terminal which can make things a lot easier. I recall when I took prior CS classes and we would have to wait on a slow IDE to load the file, make the change, and then make sure it actually saved the change. This can be useful when you finish work for the day and then your co-workers are like "yo, you left a syntax error on line 356". Instead of grunting of opening the IDE and such, you can just vim the file and then push it to github which should be more time effective and then I can go home. 

I also liked writing test scripts. This is the first time I ever wrote tests for programs. I was use to just running the program itself. But learning how to make tests makes debugging a faster process. 








