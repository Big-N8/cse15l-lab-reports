# **Lab Report 4**

We learned how to use vim by running and editing test on one of the files from our past labs. 

# **Logging into our SSH account and accessing the remote terminal**

*Terminal Inputs* 
- Type on your local terminal the following: "ssh cs15lfa23xx@ieng6.ucsd.edu" (Your ieng6 account should have its own unique letters, put them where the "xx" go)
- ~~~
  <enter>
  ~~~
The following should show

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/1a28cccf-059f-4c3d-a235-0ebf7163f51e)

These inputs just get us logged into our remote terminal through the use of the "ssh" command, a task we have done several times throughout this course. **<enter>** helps us use the 

# **Cloning the repository from our Github Account (using the ssh url)**

Once on the remote server, we need to clone our repository on the remote terminal. Before inputting any commands, go to your Github account, specifically your repositories. Go to the forked lab7 repository, hit the green "code" button and then select the ssh url. Copy it. 

Should look like this 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/096a93a9-fce1-4f75-be17-ea5c429b3963)

From now on, we will be using the remote terminal. 

*Terminal Inputs*
- git clone (paste your copied url, using **ctrl-v**)
- ~~~
  <enter>
  ~~~

The following should show 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/67779d8d-0ed9-4e4c-91c0-8c7b1e95fb0c)

Same as the previous step, we have used git clone several times to access the repositories on the terminal. Only difference now is that we are cloning it on our remote terminal instead of our local one, meaning the files are on the computer we accessed. 

# **Running the tests and making edits to files using vim**

We want to see if our tests will run for the **ListExamples.java** file. 

Let's run the bash script **test.sh** to see if the tests passed. 

- bash test.sh
- ~~~
  <enter>
  ~~~

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/5da4b83b-e1cc-4e52-a42f-aa68b071b5fe)

Let us make the necessary changes to get both tests to pass. But how? We can't access the files on the remote terminal .... or can we? 

Input the following into the terminal. 
- vim ListExamples.java

Should look like the following

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/15192610-2f54-468d-8ed9-324b9c03e4a5)

Literally shows us the whole file like a text editor and even gives us our own little cursor (circled in blue). 

This is where things get weird since vim has different controls than normal text editors we are used to like google docs, microsoft word, etc. 

Remember, the change we have to make to the file is to change **index1** to **index2** in the final loop for **merge**. 

Follow these directions to make the correction.

Vim opens in "normal" mode, we navigate our cursor using the following diagram
~~~
         up:<k>
left:<h>         right:<l>
        down:<j>
~~~

In this case hold the down key (in reference to the diagram above), until we reach the line below the comment that starts with "change index1 below to index2..."

Now hit 
~~~
<i>
~~~

At the bottom of the screen it should show as 

~~~
-- INSERT --
~~~

This means we are now in vim's "insert" mode which now allows us to treat it like a normal text editor. Type the following key pattern.

~~~
<right arrow key> (hit until you reach the end of 'index1')
<backspace> 
<2>
<esc>
~~~

When in insert mode, we can treat it like a normal text editor like google docs. The first three keys do the same actions. The right arrow moves the cursor, the backspace deletes, and "2" is a number you can put. The more important command is the "esc" key. This key puts us back in normal mode (meaning now we have to navigate the cursor with <h>, <j>, <k>, and <l> again)

# Saving the change and pushing it to github. 










