## Week 1 Lab Report 

This is a tutorial on how to log into a course-specific account on `ieng6`. The instructions will be assuming that you are on a Mac.

---

### Step 1 - Installing VScode

Here is a link to the [Visual Studio Code](https://code.visualstudio.com) website where you can download the VSCode integrated development environment. Once you download the installer, run the installer. Below is an image of the [Visual Studio Code](https://code.visualstudio.com) website.

![Image](/week-1-images/week-1-image-0.png)

---

### Step 2 - Remotely Connecting

Here are a couple substeps to connecting to a remote computer:

1. Open a terminal in VSCode. In the menu bar, click on `Terminal` → `New Terminal`
2. Then enter the command `ssh cs15lfa22**@ieng6.ucsd.edu` into the terminal, but replace the `**` with letters for your specific course account
3. If it is your first time connecting to the server, I would just say `yes` when prompted if you would like to continue connecting. Then press the `enter` key
4. If you do not have a SHH key set up, you will then have to type in your password. **WARNING:** The text for your password will not show up while typing your password, so you just have to trust your typing skills.
5. If you successfully entered your password, your terminal should look somewhat like the image below.

![Image](/week-1-images/week-1-image-1.png)

---

### Step 3 - Trying Some Commands

This step is pretty easy. After logging in remotely, try out some commands like `cd ~` or `ls`. The image below includes a few examples of some commands I did on the remote system.

![Image](/week-1-images/week-1-image-2.png)

---

### Step 4 - Moving Files with `scp`

The `scp` command is very useful when you want to import files from your own computer to the remote system. First, you have to make sure that your current directory is where you stored the file you would like to upload to the remote system. To upload the file to the remote system you would run this command (replacing the `**` and `file` with the correct letters and filename appropriately):
```scp file cs15lfa22**@ieng6.ucsd.edu:~/```

These images below is an example of me uploading the file `WhereAmI.java` to the remote system from my computer.

![Image](/week-1-images/week-1-image-3.png)

![Image](/week-1-images/week-1-image-4.png)

---

### Step 5 - Setting an SSH Key

Unfortunately, if you don't have a SSH Key set up yet, you have to type in your password when you want to upload files and every time you log in. This can be solved with the `ssh-keygen` command. Follow these steps to set up your public and private key:

1. Run the command `ssh-keygen` on your client
2. You can just press enter for the next prompt to save the file in the default location
3. Press enter again if you do not want a passcode
4. Reenter whatever passcode you came up with (just press enter if you did not set one up)
5. Log onto the server with the command `ssh cs15lfa22**@ieng6.ucsd.edu`
6. Once on the server run the command `mkdir .ssh`
7. Log out of the remote system
8. Enter this command on your client `scp /Users/*username*/.ssh/id_rsa.pub cs15lfa22**@ieng6.ucsd.edu:~/.ssh/authorized_keys`

Once these steps are complete, you shouldn't have to use your password every time you log in to the remote server. Below is an image of me going through these steps.

![Image](/week-1-images/week-1-image-5.png)

---

### Step 6 - Optimizing Remote Running

There are multiple ways you can make your time using a remote system better. For example:

* Adding commands in quotations after your ssh login to run everything in 1 line
* Using semicolons to separate lines of code to run in a single line.

Below is an example of me running optimized lines of code.

![Image](/week-1-images/week-1-image-6.png)
