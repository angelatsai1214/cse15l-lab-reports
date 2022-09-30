## Get your Username and Password for CSE15L Account
1. Enter your UCSD active directly username and your student ID to lookup your account
2. Jot down your username 
3. Reset your password on [Educational Technology Services](https://sdacs.ucsd.edu/~icc/index.php)
4. Wait for at least 5 minutes

## Setup the Working Environment
1. Follow this link to download [Visual Studio Code](https://code.visualstudio.com/) on your computer.

    When you first open up your Visual Studio Code, it should look like the image below. Feel free to customize it as you like.

    ![Image](/Images/vscode.png) 

2. Grab the code you have for CSE 15L Week 0 Lab from GitHub to Visual Studio through GitHub Desktop. Download Github Desktop [here](https://desktop.github.com/) if you don't have it yet. 

    Click on the green button that says **Code**, then click on **Open with GitHub Desktop** after you have installed GitHub Desktop on your computer.

    ![Image](/Images/githubPage.png)
    
3. The GitHub Desktop will open automatically, then you just click on **Open in Visual Studio Code**

    ![Image](/Images/githubDesktop.png)

3. In Visual Studio Code, on the top toolbar, select **Terminal** > **New Terminal** to open up the terminal if it is not already open

    ![Image](/Images/openTerminal.png)

---

## Connect to Remote Computer
1. In your terminal, enter `ssh` followed by your CSE15L account username + `@ieng.ucsd.edu`

    It should look something like this:

    ```
    ssh cs15lfa22bi@ieng6
    ```

    Then you may press Enter.

    Note: If you are connecting to a remoate computer for the first time, you will see the following in your terminal:

    ```
    The authenticity of host 'ieng6-202.ucsd.edu (128.54.70.227)' can't be established. RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec. Are you sure you want to continue connecting (yes/no/[fingerprint])?
    ```
    Please proceed by entering **yes**.

2. Afterward, you will be prompted to enter your password for CSE15L account. 

    Note: Your actual password will not appear in the terminal as you type for security reasons, but you just need to make sure that you enter your password correctly, and then press the Enter key.

3. The terminal will print out several lines of information once you are logged in, the final line you should see is the current date and time as well as 

    `- Prepping [your username]`

    Overall, your terminal should look something like this:
    
    ![Image](/Images/login.png)

    Congratulations! You have successfully logged into your remote computer!

---

## Try Some Commands

- `ls` will show you the folders/files (not including the hidden ones) in your current directory

    ![Image](/Images/ls.png)

- `ls -a` will show you all the folders/files, including the hidden ones in your current directory

    ![Image](/Images/ls-a.png)

- Now that we know what we have, you can use the `cd` command to get into a particular folder.

    ![Image](/Images/cd.png)

    Since nothing is in this file, nothing is printed after you input this command. 

- Now we want to get out of `cd per15` directory and go back to our home directory. You can do this by doing `cd ~`

    ![Image](/Images/tilde.png)

- Feel free to try out some other commands including
    `ls -lat`, `cp`, `cat`, and `ls <directory>` with `<directory>` being one of your group member's home directory!

---

## Moving Files with `scp`

Next, we will learn how to move files from your local computer to your remote computer.

1. Before we start, you need to logout of your remote computer first. To do so, you may either use `ctrl+D` on your keyboard or enter `exit` in the terminal.

2. Now, go to the Explorer, which is located at the left hand side of your Visual Studio Code. 

    ![image](/Images/explorer.png)

3. Right click and select **New File** and enter `WhereAmI.java` as the file name.

4. Copy and paste the following code into the file:

    ```
    class WhereAmI {
    public static void main(String[] args) {
        System.out.println(System.getProperty("os.name"));
        System.out.println(System.getProperty("user.name"));
        System.out.println(System.getProperty("user.home"));
        System.out.println(System.getProperty("user.dir"));
        }
    }
    ```

5. Now, back to your terminal, run the following two lines of code:

    ```
    javac WhereAmI.java
    java WhereAmI
    ```

    The first line compiles your code and creates a `.class` file for you. The second line runs the code in the file. After running the second line you will see something similar to this:

    ![Image](/Images/running.png)

6. Next, run the `scp` command in the terminal as such:

    `scp WhereAmI.java cs15lfa22bi@ieng.ucsd.edu:~/`

    `scp` stands for **secure copy**, you enter the file you want to copy over immediately after `scp`, and following the file name, you enter the destination of copying.

    Your will be prompted to enter your password, please do so. 

7. Login to your remote computer again using `ssh`.

8. After logging in, run the command `ls`, you should see the file `WhereAmI.java`

9. You can print the content of the file using the command `cat` followed by the desired file name. 

    ![Image](/Images/WhereAmI.png)

---

## Set Up an SSH Key

Note: I am on the Windows system.

1. Logout of the remote computer by using `ctrl+D` or `exit`

2. Run the command `ssh-keygen -t ed25519`. You will be prompted to enter the location for the file, simply press Enter again if you want it to be the default location, which is the one inside the parenthesis. For the purpose of this assignment, I chose not to enter any passphrase.

    ![Image](/Images/ed255.png)

3. After you have ran this, a public and private key files are created on your system, stored in the location you chose to store them. 

    ![Image](/Images/privateAndPubLocation.png)

4. Now, login to your remote computer using `ssh`, and then enter the command `mkdir .ssh`. If it says `mkdir: cannot create directory '.ssh': File exists` then don't worry about it, you are all good.

5. Logout of your remote computer.

6. Awesome, the last thing to do now is to copy your public key into your remote computer. Run the following command:
    ```
    scp \Users\29316/.ssh/id_ed25519.pub cs15lfa22bi@ieng6.ucsd.edu:~/.ssh/authorized_keys
    ```

    Make sure to change the username *29316* to your laptop username and the two letters after *fa22* to your username letters!

7. You will be prompted to enter your password, please do so. 

8. Now, to test if you have done everything correctly, login to your remote computer again using `ssh`! This time (hopefully) you won't be asked to enter a password anymore, yay!

    ![Image](/Images/doneSSHKey.png)

---

## Optimize Remote Running


