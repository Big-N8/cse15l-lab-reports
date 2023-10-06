# Lab Report 1
In this lab, we learned about the usage of the following file system commands
* **"cd"**
* **"ls"**
* **"cat"**

**Change Directory (cd)**
---
**cd** when it is used with no arguements

![Screenshot 2023-10-05 195035](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/72342861-ea31-48c5-a99a-1bda07dd9a46)

The working directory at the time is still **home**. This is because that even though the **cd** command followed through, it was not pointed anywhere. Since it was not pointed anywhere, it decided to stay with the **home** directory.This is not error, it is just more of an empty answer. The command did not recieve an error but it just did not do what it was intended since it was not pointed in any direction. 

**cd** when it has a directory for an arguement

![Screenshot 2023-10-05 204426](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/2aae3aa9-ac32-4fe8-a791-b53a921235c0)

The working director has now been changed to **lecture1** since we followed with a directory after the CD command, meaning we were now able to actually change the directory from **home** to **lecture1**. This is not an error as indicated within the brackets, which now shows as **[user@sahara ~lecture1]**

**cd** when it has a file for an arguement 

![Screenshot 2023-10-05 205230](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/a036c55d-bb23-4ba7-9f02-765a07807925)

When I first directly used a text file from the home directory, I recieved an error because it stated "no such file or directory". I figured I should change the directory to messages first and then try it again. It then stated, "Not a directory". This error occured since the command (as stated in the acronym) only works with directories. It would not make sense to change the new directory to a text file. The point of a directory is to hold files. 

**List (ls)**
---
**ls** with no arguement 

![Screenshot 2023-10-05 210244](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/c70a3143-54bc-4db7-a698-27a780237064)

Resetted the directory to home. When **ls** was used, the output was **lecture1**, meaning it is not an error. The point of this command is to list the files and folders within the given path. In this case, we only have **/home**, so the only folder it can show is **lecture1**, not its contents.

**ls** with a directory for an arguement

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/531ea777-f98f-4df4-8e3c-480806fc49b3)

If the directory is at **/home**, and use **ls lecture1**, it will print out the contents of **lecture1**, as shown above not making it an error. However, if we want to access the embedded folders within **lecture1**, we need to change directories. In this case, we changed directories from **/home** to **/home/lecture1**. We were then able to print out the contents of an embedded folder of our choosing. In this example, we chose **messages** which listed the text files for us. 

**ls** with a text file for an arguement

![Screenshot 2023-10-05 212324](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/0c87fa1d-37c2-4c8e-87e8-b2067baf0177)

I changed the directory to **lecture1** first then realized it would not work since there were no text files in that directory, where I changed it again to **messages**. Used the command again with the english text file and it simply only listed the text file. This is reasonable since I asked it to simply list that file and it as prompted.

**Concatenate (cat)**
---
**cat** used with no arguement
















