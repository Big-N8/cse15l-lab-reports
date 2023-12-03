# **Lab Report 4**

We learned how to use vim by running and editing test on one of the files from our past labs. 

# **Logging into our SSH account and accessing the remote terminal**

*Terminal Inputs* 
- ~~~
  cd lab7
  ~~~
- Type on your local terminal the following: 
- ~~~
  ssh cs15lfa23xx@ieng6.ucsd.edu //(Your ieng6 account should have its own unique letters, put them where the "xx" go)
  <enter>
  ~~~
The following should show

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/1a28cccf-059f-4c3d-a235-0ebf7163f51e)

These inputs just get us logged into our remote terminal, a task we have done various times throughout the course. 

# **Cloning the repository from our Github Account (using the ssh url)**

Once on the remote server, we need to clone our repository on the remote terminal. Before inputting any commands, go to your Github account, specifically your repositories. Go to the forked lab7 repository, hit the green "code" button and then select the ssh url. Copy it. 

Should look like this 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/096a93a9-fce1-4f75-be17-ea5c429b3963)

From now on, we will be using the remote terminal. 

*Terminal Inputs*
- ~~~
  git clone <ctrl-v> //ctrl-v to paste copied url.
  <enter>
  ~~~

The following should show 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/67779d8d-0ed9-4e4c-91c0-8c7b1e95fb0c)

Same as the previous step, we have used git clone several times to access the repositories on the terminal. Only difference now is that we are cloning it on our remote terminal instead of our local one, meaning the files are on the computer we accessed. 

# **Running the tests and making edits to files using vim**

We want to see if our tests will run for the **ListExamples.java** file. 

Let's run the bash script to see if the tests passed. 
- ~~~
  bash test.sh
  <enter>
  ~~~

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/5da4b83b-e1cc-4e52-a42f-aa68b071b5fe)

Let us make the necessary changes to get both tests to pass. But how? We can't access the files on the remote terminal .... or can we? 

Input the following into the terminal. 
- ~~~
  vim ListExamples.java
  <enter>
  ~~~

Should look like the following

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/15192610-2f54-468d-8ed9-324b9c03e4a5)

Literally shows us the whole file like a text editor and even gives us our own little cursor (circled in blue). 

This is where things get weird since vim has different controls than normal text editors we are used to like google docs, microsoft word, etc. 

Remember, the change we have to make to the file is to change **index1** to **index2** in the final loop for **merge**. 

Follow these directions to make the correction.

Vim opens in "normal" mode, we navigate our cursor using the following diagram
~~~
Left  Down  Up  Right   
<H>   <J>  <K>  <L>
~~~

Side Note: For those who are used to using the arrow keys or WASD like in video games, the easier way to manage this change is to have your fingers set like this
~~~
Left Middle Finger  Left Index Finger  Right Index Finger  Right Middle Finger   
       <H>                 <J>                <K>                  <L>
~~~

In this case hold the down key (in reference to the diagram above), 
~~~
<j> 
~~~

Now hit 
~~~
<i>
~~~

At the bottom of the screen it should show as 

~~~
-- INSERT --
~~~

This means we are now in vim's "insert" mode which now allows us to treat it like a normal text editor. I typed the following key pattern.

~~~
<right arrow key> (held it until I reached the end of 'index1' or about 10-12 individual key presses)
<ctrl-a> (increments any first integer it sees) 
<esc>
~~~

When in insert mode, we can treat it like a normal text editor like google docs or microsoft word. 

~~~
<right arrow key> //moves the cursor to the right
<backspace> // deletes anything around the cursor
<2>

// alternatively

<ctrl-a> // appends the integer like changing index1 to index2.

// Hit the key once change is done.

<Esc> // returns back to normal mode. 
~~~

Below you can see the before and after returning to normal mode. 

~~~
Before hitting <esc> 
~~~

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/920ca0fd-3295-4dbd-a837-25292294b4c2)

~~~
After hitting <esc>
~~~

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/181e72e5-01c1-476c-8a0b-54626c8dcc5e)

Remember that we have to save our change to the file! Double check you are on normal mode, by hitting 
~~~
<esc>
~~~
To save the file change, 
~~~
:wq!
~~~

Should show as the following 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/a4592d5a-dff5-4537-b788-232f30ab254e)

It will then be taken back to your remote terminal's directory. This means our changes to the file should have been saved. 

Run the bash script again to check the tests passed, recall using the up arrow key to refer back to your past commands. My key pattern was the following. 

~~~
<up arrow key> 
<up arrow key>
<enter>
~~~

And bingo. 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/956b0aea-b3e5-43f8-adcf-34c36a664bd1)

# Saving the change and pushing the commit to our github account

Remember that we needed the SSH URL for this forked repository, not the "https". Let's double check to make sure we have the correct URL. 
- ~~~
  vim .git/config
  ~~~
- ~~~
  <enter>
  ~~~

Should show the following 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/6d070c4f-3246-436d-902f-ba76b44a07b1)

Looks like we have the wrong URL. Let's go back to our github repository and get the correct one. 
Recall, we need to do the following. 

- Go to our Github, then repositories
- Choose the forked lab7 repository
- Hit the green **code** button
- Choose the ssh tab and copy its url using 
~~~
<ctrl-c> // copies 
~~~

Looks like this 

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/096a93a9-fce1-4f75-be17-ea5c429b3963)

Go back to VS Code. 

Here was my key pattern. 
~~~
<j> (pressed/held key until the line with the url)
<dd> // deletes a whole line. 
<i> // goes into insert mode
<enter>
<tab> // shifts cursor over a good amount of space. 
"url ="
<right arrow key> (until after the "=")
ctrl-v // paste
<esc> // back to normal mode
:q! // Saves and Quits in Normal Mode
<enter>
~~~

Which now looks like the following

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/41cad06b-803d-4158-b7a6-97085f806828)

One of the new commands we see here is 

~~~
dd
~~~

This command deletes a whole line and then moves the cursor back a line. Once insert mode is activated, keys can now be considered as an actual text editor. Recall, we need to resume to normal mode with

~~~
<esc> // back to normal
:q! // quits and saves the file.
<enter>
~~~

Now we need to commit the change and then push it to Github. 

Type following commands
~~~
git add ListExamples.java 
git commit 
~~~

Shown as follows

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/ff882046-f32e-441b-a869-9acc2dda8507)

Type a message of some sort at the very top. Should appear in orange color.

Be sure to this key for insert mode.
~~~
<i> // Enters insert mode
~~~

Do the following after your message
~~~
<esc> (Back to normal mode)
:wq! (overwrites and saves.
~~~

Now push the commit to github. 
~~~
git push
~~~

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/36c9611a-d898-45a4-bdf2-faeb244c584a)

Go back to the lab7 forked repository and check the file you made and edit to. See if the change went through

![image](https://github.com/Big-N8/cse15l-lab-reports/assets/146897977/52e8fb69-2770-4b92-a422-2d96a340b1f9)

And that's how you make edit files and push them to Github, all from the terminal :)





















