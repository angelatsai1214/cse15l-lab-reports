# Week 7 Lab Report

## Part 1

### Task Chosen: Changing the name of the `start` parameter and its uses to `base`

Pre-steps to Perform:
- Login to remote account (because I am a Windows user)
- `cd week6-skill-demo1`
- `vim DocSearchServer.java`

Shortest vim command we came up with:

 `/start`
 
 This command allows use to search for the word `start` inside the `DocSearchServer.java` file.
 ![Image](/Images/start.png)
 
 `<Enter>`
 
 Once you pressed Enter, the only the first letter of the word is highlighted.
 ![Image](/Images/enter.png)
 
`ce base` 

After `ce` command, the current search word `start` will be deleted, and we type `base` as the replacement word.
![Image](/Images/ce.png)
![image](https://user-images.githubusercontent.com/64194102/201225874-4991a25f-88e0-41b3-b6dd-52296ef136cd.png)


`<Escape>`

Escapes the Insert mode.
![image](https://user-images.githubusercontent.com/64194102/201225917-d0e7686c-d958-498f-b886-c0fb49dd79c2.png)


`n` `.` `n` `.`

Each `n` finds the next matching word to the search word in the file and each `.` performs the previous operation done in insert mode again.

First `n`
![image](https://user-images.githubusercontent.com/64194102/201226040-e0b5e7da-8e46-4f36-902b-ae31947028e5.png)

First `.`
![image](https://user-images.githubusercontent.com/64194102/201226089-21637844-223d-4454-99e3-b0d11508b34b.png)

Second `n`
![image](https://user-images.githubusercontent.com/64194102/201226149-4d3acd1c-0696-42b9-963d-afb9c7c51807.png)

Second `.`
![image](https://user-images.githubusercontent.com/64194102/201226167-349b59bd-da6f-4fcb-b8d6-5fc59b88d707.png)

Now, we've finished editing so we use `:wq` to save and quit vim mode.
![image](https://user-images.githubusercontent.com/64194102/201226834-f3fe695e-2577-4fc2-bfcf-1538e9de244b.png)

Finished quitting vim mode:
![image](https://user-images.githubusercontent.com/64194102/201226837-73dda110-078c-473d-b690-00428c2e0b67.png)

## Part 2

- **Which of these two styles would you prefer using if you had to work on a program that you were running remotely, and why?**
I prefer making the edits locally because I am still not very familiar with all the VIM commands and scp file over to the remote server isn't very difficult either. 

- **What about the project or task might factor into your decision one way or another? (If nothing would affect your decision, say so and why!)**
If it is just making a little edit, adding/changing one line in the code or replacing a few words, then I would be able to do that in the remote server. Otherwise, it is a more significant edit, I wouldn't want to do that using VIM. 
