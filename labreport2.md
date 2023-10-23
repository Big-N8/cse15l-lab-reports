# Lab Report 2
In this lab, we covered Servers and SSH keys.

**Part 1**

Here is the code that I used for **StringServer**


![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/df66ef50-1297-4cae-a293-c728e90be5a2)

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/61b9efc4-4dbc-49b6-a124-6c7c8896ed91)


Here are the results I got when I changed the queries in the URL when the server was running. 


![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/38a726fd-8a62-41b3-8874-709154d53755)

The methods that are called in this are the handleRequest, followed by *.contains* and then the *.split*.
The fields of the values were not changed since it was a string to begin with so a change of field was not needed. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/3ed7e386-eac9-4f9f-8887-f9a6a4830a93)

The methods that are called in this are the same as the one above. 
One of the intaken values had their field changed since they are integers that were taken as strings and eventually listed. 

**Part 2**

Before starting, I needed to go to the terminal and generate SSH keys using **ssh-keygen** in our terminal. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/1f116773-3ec6-418b-9f18-682325f8c8d9)

After this was made, I was now able to begin with the **ls** commands as follows


* **ls** with path to *private* key (on my computer)

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/86b48fbd-1703-4435-8bc5-be645087952c)


* **ls** with path to *public* key for SSH (within ieng6 account)

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/d5478745-0e37-442e-9dc9-dd824e438fd3)

The contents of the public key was sent to the **authorized_keys** file as shown below

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/7fa4c405-6497-4786-bdae-2dd1efeada54)



* Terminal reaction with login into ieng6 account (without using password)

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/37f7052f-c53d-49a0-a858-94515408298e)


**Part 3**

I learned a lot of new things from both week 2 and 3. An example is the **scp** command. It was fascinating how we were able to directly copy contents of a file to another file on another computer. Learning about all the different commands that can be used in queries was also cool, I was not aware of how much variety there can be. 



