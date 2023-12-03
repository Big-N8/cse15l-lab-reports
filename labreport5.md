# **Lab Report 5**
**Part 1: Debugging Scenario**

Following Scenario: Student has trouble finding bug in their code. Student asks for help on EdStem and makes the following post. 

---

**General: Issues with Lab 7 test**

Anonymous Gopher 

Hello, 
In preparation for Skill Demo 3, I am praciticing writing my own tests for the code we got in Lab 7. However, I am not sure where I am going wrong in the test writing. I keep getting this weird error whenever I am writing the test for the reversed method in ArrayExamples.  Here is my code and bash script for reference. 

ArrayExamples

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/b5732b59-4df6-4a86-84c0-987c048c5705)

ArrayTests

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/c5f49f32-123f-444e-8cd4-7de0787cfffc)

test.sh

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/f7fe1054-ce3b-49b3-8e52-4830afa11198)


This is what showed up on my terminal. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/316b7fbd-2f1e-4b77-9008-52d2354f20b6)


Any help would be appreciated. 

---





The TA responds to the post sometime later in that day. 

---
Hi, 
The error is actually not in your test but in your code for ArrayExamples. Take a look at line 17. Here is where you want to set the elements to newArray. As seen in your terminal output, it mentions that it was expecting 60


---

