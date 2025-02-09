# Docker Basics

1. What is Docker? \
A: Docker is a platform for `running`, `building` and `shipping` application.

2. Why an applications works on your machine but doesn't elsewhere/ Need for Docker? \
 a. Missing one or more files \
 b. Software version mismatch. The software which it's dependent on is of different version. \
 c. Different configuration settings.

3. How does docker do? \
 A: With docker we `package` the application with `all that it needs` and run it anywhere.

4. Container vs Virtual machine \
    `Container`- An isolated environment for running an app. \
    `Virtual machine`- An abstraction of a machine (physical hardware). \
    (Add more from hand written notes AV)

5. Problems with virtual machine? \
    a. Each virtual machine needs a `full-blown OS` \
    b. `Slow` to start \
    c. `Resource` intensive

6. Containers \
    a. Allow *multiple* apps **in isolation** \
    b. Are **lightweight** \
    c. Use Host's OS \
    d. Starts **quickly** \
    d. Needs **less hardware resources**

7. Docker Archtecture \
A.  Docker works on `client-server` architecture. The client is connected and talks to the server component by **Rest API** and the server is known as `Docker Engine/ Docker Daemon`. ***Docker Daemon*** sits in the background and takes care of building and running containers.
    Container don't use full-blown OS. Instead, all the containers of the host share the OS. Infact, all containers share the kernel of the host.

8. Kernel \
A: A kernel manages the application and hardware resources.

    Explaination:
    The kernel in Linux is the core program that acts as a bridge between your applications and the physical hardware. It manages resources (CPU, memory, storage) and controls communication between everything running on your system. Think of it as the conductor of the computer orchestra.

9. Docker Image:

A:  Contains: \
    a. A `cut-down OS` \
    b. A `runtime environment` \
    c. `Application files` \
    d. Third-party `libraries` \
    e. `Environment variables`

 Google Gemini: (Just to add some details)
 is essentially a self-contained blueprint for creating a Docker container. Here's a breakdown:

 - `Immutable`: Once built, the image itself cannot be changed. Think of it as a fixed recipe.
 - `Versioned`: Images can have versions, allowing you to track changes and ensure consistency across deployments.
 - `Shareable`: Images can be easily shared with others through public registries (like Docker Hub or ECR) or private ones within your organisation.
 - `Reusable` : A single image can be used to create multiple running containers, ensuring consistent environments.


10. Container:
    A container is a `process`. But is it a ***special*** kind of process which has its own `filesystem`.

    Google Gemini:
    A Docker container, building on the image analogy, is the cooked pizza from the Docker image recipe. Here's a breakdown:

    - `Executable Instance`: A container is a running instance of a Docker. It's the actual application or service you want to deploy.
    - `Isolated Environment`: Each container runs in its own isolated space, sharing the operating system kernel with other containers but keeping applications separate.
    - `Lightweight & Portable`: Containers are lightweight and efficient because they share the kernel. This also makes them portable and able to run consistently across environments.
    - `Dynamic`: Unlike the image, a container can be modified while running. You can add files, install additional software, or change configurations.

6. docker images
    or (alternate command)
    docker image ls
    -lists all the images

7. docker version
    - displays the docker version

# Linux

11. Linux is an opensource OS

2. Using ubuntu on docker: \
a. Instead of using "docker pull ubuntu" the shortcut can be: \
    docker run ubuntu \
    (If the image exists then it will simply run but if it doesn't exists, 
    it will pull(download from the repo/dockerhub) and run)

3. To display all the containers:
```bash
docker ps 
    - checks all the docker process it is running (running container is a 
    process)
```

4. To display all the containers even if it's stopped:
```bash
docker ps -a
    - displays all the containers even if it is stopped 
```
6. To run a container from an image:
```bash
docker run <docker_image_name>
    -runs a container. 
```
7. If you start a container and if it is not in `interactive mode`, it will *stop*.

8. If you don't want it to stop, keep it in interactive mode. To put it in interactie mode, use the flag `-it`

E.g., 
```bash
docker run -it ubuntu
    -runs a container in interactive mode.
```
---------------------
Henceforth, lesson-wise

#### lesson12- Linux Distributions
1. Linux is an opensource OS

2. Linux comes with a lot of Distributions

3. Eg., \
    a. ubuntu \
    b. Debian \
    c. Alpine \
    d. CentOS

#### lesson13 - Running Linux

1. To use Linuxs' particular OS say ubuntu we can type:
```bash
    docker pull ubuntu
    - pulls the ubuntu image
```

or instead of using `pull`, we can use:
```bash
docker run ubuntu
    - runs the ubuntu container but if it's not available, it will download it and then run
```
2. Although we have downloaded the container and run it, since we didn't interact with it, so it stopped.
    - so if we do not interact with a container, it will stop

To check, we can write:
```bash
docker ps 
    - (to check the running processes, since a container is a process)
```
We will find nothing
But when we write:
```bash 
docker ps -a
    - checks all the process, even if any container has stopped
```
3. To start a container and interact with it:
docker run -it <container_name>
```bash
docker run -it ubuntu
    -starts a container in interaction mode.
    -this will open a shell prompt
```

4. Linux is a case sensitive OS

5. You can use up and down arrow keys to navigate between the commands

6. A shell prompt typically looks something like this:
```bash
root@1a2345:/#
```
Here is a breakdown of the above shell command: \
a. `root`  - means the user, if you login with a differet user you will get a the user's name \
b. `1a2345`- means the machine ID. This ID is generated by docker \
c. `/`     - means where we are in the filesystem. A forward slash represents the root directory. \
d. `#`     - denotes the privileges. A hash means that we have the highest priviledges as the root user. 
            If we login as a different user, we will get a $ (dollar) of # (hash).

7. To list down all the commands entered type:
```bash
histroy
    - lists down all the commands in a serial order.
    - to execute the commands from the list type below:
    !<command serial> (exclaimation mark and the serial no.). 
    E.g.,

    !2
    - executes the 2nd command in the serial
```

#### lesson14 - Managing Packages

8. A Linux package manager is a tool that helps you easily `install`, `update` and `remove` softwares. 

In ubuntu we have `apt`. 
apt stands of ***Advanced Package Tool***

If you type:
```bash
apt
    - lists sub-commands, like list, install, remove, search, etc.,
```

Suppose we want to install `nano`. If we type `nano`, we get nothing because it has not been installed currently.
To install it, we type:

```bash
apt install nano
    - it might still not get installed, because we might not have the package of nano in the database of the ubuntu packages.
```
You can list the all the packages that are available in this OS by typing:
```bash
apt list
    - lists all the packages. Some packages may be installed while others might not be installed.
```
So, we update the db of the packages by typing:

```bash
apt update
    - updates the dbs of the packages
```
and now when we type:
```bash
apt list
    - more packages will get displayed along with nano
```
Now, we  can install nano by typing:
```bash
apt install nano
    - installs nano from the package list
```
Take Away: 
So, before installing any package, make sure you have updated the package db

9. To remove any package:
```bash
apt remove nano
    - uninstalls the package
```
#### lesson 16 - Linux filesystem

1. In linux, we have the root directory on top which is represented as "/". \
Below that, we have some standard directories:

```bash
    / 
    bin 
    boot 
    dev 
    etc 
    home 
    root 
    lib 
    var 
    proc 
```
Just a brief explaination:
    
`/`    - root
`bin`  - contains mainly binary files or programmes
`boot` - contains files related to booting
`dev`  - short for devices (Yes, in linux everything is a file, including directories)
`etc`  - General belief is it stands of Editable Text Config (configuration files)
`home` - This is where home directories of users are stored. Each user is going to have their home directory here.
`root` - root directory for the root user. Only the root user will be able to see this
`lib`  - used for keeping library files like software library dependencies
`var`  - stands for variable. This is where files are updated frequently like log files, application data, etc.
`proc` - contains files represent running processes. (Yes, even processes are files in linux)

#### lesson16: Navigating the File System

`Relative Path` vs `Absolute Path`:

`Relative path`: Starts with "./" or "../", navigates relative to your current location. Like giving directions. \
    **Example**: *./report.pdf* (This file is in the current directory) \
    **Example**: *../downloads/music.mp3* (This file is in the "downloads" folder, one level up from the current directory)

`Absolute path`: Starts with "/", tells the exact location from the root directory. \
    Think full address.
    *Example*: */home/user/documents/report.pdf* (This file is in the "documents" folder inside the user's home directory)

Very basic commands:

1. pwd

2. ls

3. ls -1
    - lists one file per line

4. ls -l
    - lists one file per line with details

5. cd

6. cd ..

#### lesson 17 - Manipulating Files and Directories

1. To take you to the home dir:
```bash
cd ~
    - takes you to the home directory
```
2. Move/cut or Rename a file/dir:
```bash
mv
    - moves files or directories. Requires more options here.
```
3. To create a file in *.txt* format:
```bash
touch hello.txt
    - to create a file in txt. touch command is used to create files and mkdir to create directories.
```
4. To remove a file/files:
```bash
rm
    - removes file/files (deletes)
```
5. To remove a file/dir:
```bash
rm -r
    - removes directories '-r' stands for `recursive` which means all its content also.
```
6. Create a dir:
```bash
mkdir
    - makes a new directory
```    
 
7. Creating multiple files at once:
```bash
touch <file_name1> <file_name2> <file_name3>
    - creates multiple files at opensource
```
8. List all the files/dir one per line:
```bash
ls -1
    - lists the files. One file in one line.
```
9. List files/dir in detail:
```bash
ls -l
    - lists the files. One file in one line but with details.
```
10. Removing a file using the *rm command*. Variations on the *rm command*:
```bash
rm
    - removes a file. There are different ways you can used as shown below:

rm <file_name1>
    - removes a file

rm <file_name1> <file_name2> <file_name3>
    - removes multiple files at once.

rm file*
    - removes all directory using a pattern. This will remove all directories having "file" in it

rm -r <directory_name>
    - removes directory having files inside. "-r" is recursive
```
#### lesson17 - Editing and Viewing files

**Nano** is a simple text editor in Linux. To install nano type:

1. Installing nano with apt package manager in ubuntu:
```bash
apt install nano
    - installs nano text editor
```
2. Create a file and open nano editor:
```bash
nano file_name1.txt
    - creates a txt file and opens in nano editor
```
3. Displaying file content:
```bash
cat
    - displays what is inside the file. It is short for concatenate
```
4. Similar to "cat" command we have the following command to view large files. Here, we don't have to scroll and see our file, instead, we get an interface with some options. We can simply type: \
```bash
more
    - displays what is inside the file
    - press space to go to the next page (we will get a percentage (%) at the bottom. Denoting 
    how much % is getting displayed)
    - press enter to go one line at a time
    - to exit we press 'q'
```
5. Similar to "more", we have "less" command. The problem with "more" command is we can't scroll up. Means we can go to the next page by pressing space but we can't go the previous page. In less, we can view the files in interactive way. \
If you do not get the less command then simply install it using 
```bash
apt install less
```
Type:
```bash
less <file_name>
    - displays the content of the file.
    - press up and down arrow keys to navigate
    - to exit we press 'q'
```

6. Alternate options are (not so important):

```bash
head -n 5 <file_name>
    - displays 5 lines from the top
```
```bash
tail -n 5 <file_name>
```
#### lesson19 - Redirection

In Linux, redirection lets you change where the output of a command goes. \
By default, commands send their output to the terminal screen. \
Redirection allows you to: \
Send output to a file (>):
```bash
ls > files.txt 
    - saves the list of files to files.txt.
```
Append output to a file (>>): 
```bash
ls >> files.txt 
    - adds the output to the end of files.txt.
```
Discard output (> /dev/null): 
```bash
ls > /dev/null 
    - hides the output (useful for commands that just need to run)
```

#### lesson20 - Searching for Text

grep = Global Regular Expression Print

We will see how this works using some commands and their explaination

1. Using grep:
```bash
grep hello file.txt
    - searches for the word/string "hello" in the file
    - use "-i" option/flag to make it case in-sensitive. E.g.,
    grep -i hello file.txt
    - searches for the word hello. Now this will display even if it is written in uppercase.
```
2. E.g.,
```bash
grep -i root /etc/passwd
    - displays the word root in the file 
```
3. An example to search for a keyword `hello`:
```bash
grep -i hello file1.txt file2.txt
    - or
grep -i hello file*
    - means the same thing as above. We have used a wildcard which means any file having "file" written in the beginning and whatever after that.
```

2. To search in a directory:
```bash
grep -i -r hello .
    - searches the word "hello" in the current directory in all the files
    - In linux we can combine the options or flags also. So the the above command can be written as:
grep -ir hello .
    - same as above with flags merged
```

#### lesson21 - Finding Files and Directories

1. Listing all the files and directories in the current dir recursively:
```bash
find
    - lists all the files and the directory in the current directory recursively. Lists even the hidden ones.
```
2. Listing everything including hidden files/directories:
```bash
ls -a
    - lists everything in a directory including the hidden ones
```
3. find /etc
    - we can add a path and it will work in the same way
    - lists all files in ...

4. find -type d
    - lists all the DIRECTORIES only

5. files -type f
    - lists files only

6. find -type f -name "f*"
    - lists all files starting with the "f"
    this is again case sensitive
    to make it case in-sesitive we can use:
    find -type f -iname "f*"
    - finds only files and it is NOT case sensitive

7.  find / -type f -name "*.py"
    - finds all the python file (since with .py extension) 

    find / -type f -name "*.py" > python-files.txt
    - just redirects the result in a txt file.

#### lesson22 - Chaining commands

We can chain or combine different commands like

1. Chaining commands:
```bash
mkdir test ; cd test ; echo done
    - all the above commands can get executed one after the other
    - adding space is optional
    - using semicolon, we can combine/chain linux commands
```
2. If we execute the same command again, we will get an error for the first command because directory 'test' already exists but the rest commands will be executed.

3. We can use the *and* operator (*&&*). If one command fails, other commands won't get executed:
```bash
mkdir test && cd test && echo done
```
4. We can also use the *or* operator (*||*). If the 1st command gets executed the 2nd command doesn't get executed but if the 1st command doesn't get executed the 2nd  gets executed:
```bash
mkdir test || echo "Directory Exists"
```
5. Another way to chain commands is piping. What it essentially do here is get the output of the 1st command and put it to the next command.
```bash
ls /bin | less
    - lists all the output of the ls /bin commmand and displays in 'less'.
    - Ref. lesson17, serial 5
```
```bash
ls /bin | head -n 5
    - displays 5 lines from the head (top)
```
6. Splitting commands in multiple lines. We can use '\' to end the line and after that we can press enter and write other commands. This ensure that whenever we have a long command we don't have to scroll horizontally to go through the entire command. \
So, instead of:
```bash
mkdir hello ; cd hello ; echo done
```
We can write:
```bash
mkdir hello;\
> cd hello; \
> echo done
```

#### lesson23 - Environment Variables

**Explaination**: Environment variables in Linux are basically `name-value pairs` that control how programs run. They're like mini settings menus for your shell and applications.
It is used for `storing configuration setting` for our applications. So, our applications can read configuration settings from this env variables.

1. To display all the env variables:
```bash
printenv
    - displays all the environmental variables in this machine
```
2. Printing a particular env value:
```bash
printenv <variable>

```
E.g., 
```bash
printenv PATH
    - displays the value of 'PATH'
```
3. You can also view value of a particular variable by `echo` but here you have to prefix it with `'$'`. 
E.g.,:
```bash
echo $<variable>
echo <PATH>
```
4. We can set a variable using 'export' command:
```bash
export DB_USER=zaman
    - puts 'zaman' in DB_USER as an environmental variable.
    - this is active for the current session only. So, if we were to close this terminal session 
    and open another session. We will `not` get the environmental variable.
    - So, we can get the value we can either type:
        echo $DB_USER
        or
        printenv DB_USER
        and we will get the same result as 'zaman' set earlier
```
5. To make a variable `persistent`, we have to write the variable in a `special file`. The name of the file is `".bashrc"`. You will find this file in your home directory. So, to be able to see it type:
```bash
ls -a
    - lists all the files and dir including the hidden ones
    - Here you will find '.bashrc'
    - You can either type 'vi .bashrc' and start editing the file and declare you variable 
    here or simple append by:

echo DB_USER=zaman >> .bashrc
    - adds another line 'DB_USER=zaman' in the file 'bashrc'
    - now, there is a small limitation to this is that the appended environment variable will 
    be active in another session of the terminal. Meaning you have to stop this session and 
    begin a new one to see the result.
```
6. We can use the source command to reload the `'.bashrc'` file.
```bash
source .bashrc
    - reloads the '.bashrc' file.
    - we have to execute it from our home directory.
```
If you are not in your home directory use the below command:
```bash
source ~/.bashrc
    - reloads the '.bashrc' file WHEN YOU ARE NOT IN YOUR HOME DIRECTORY
```
#### lesson24 - Managing Processes

A process is an instance of a running programme. To see all the running 
programme or all the running processes we type:
```bash
ps
    - displays all the running processes
```
1. To kill a process:

```bash
kill <process_ID>
    - kills a particular process.
```

#### lesson25 - Managing Users

1. Adding a user:
```bash
useradd
    - adding a new user
    - this command lists all the options/flag that can be used with this command.
useradd -m zaman
    - adds a new user 'zaman'
    - '-m' flag means creating a user's home directory (use 'useradd' for
        explaination)
```
2. Modifying a user:
```bash
usermod
    - modifying a user
```
3. Deleting a user:
```bash
userdel
    - deleting a user
```
4. To view all the users we can view the folder `'/etc/passwd'` like:
```bash
cat /etc/passwd
- lists all the users. Not Password. Name is misleading.
```

5. Let us understand what a single line means in the file `'/etc/passwd'`:
```bash
zaman:x:1000:1000::/home/zaman:/bin/sh
    - 'zaman' is the user's name
    - ':' is a separator
    - '1000' - first one is the user ID
    - '1000' - second one is group ID
    - '/home/zaman' - home directory of the user
    - '/bin/sh' - shell programme used when this user logs in
```
6. After seeing the above details from the user `'zaman'`. Let us say that we decide to modify the user and use another shell programme for the user. \
So, first of all, let us check which option do we have to user along with 'usermod'. \
To explore the flag, simple type:
```bash
usermod
    - all the options/flags will be listed
```
```bash
usermod -s /bin/bash zaman
    - modifies the user to use '/bin/bash' shell when the user logs in
```
To login as 'zaman' using the bash shell. We type:
```bash
docker exec -it -u zaman 2f75e699 bash
    - logs in inside a container using bash
    - This is not general. Related to containers
```
To check if the changes has been made we type:
```bash
cat /etc/passwd 
    - we will see all the user information. Here we will find that the shell has been changed.
```
7. Passwords are saved in the */etc/shadow*. We can access this directory by:
```bash
cat /etc/shadow
    - only the root user can access this directory
    - passwords are encrypted here
```
8. We have another command for adding user which is very interactive:
```bash
adduser
    - adds a user
adduser zaman
    - you will get many info as well as options here one after the other
```
#### lesson26 - Managing Groups

We use group so that all users in the same group can have the same previlages. Just like users, in groups also we have similar commands like:
*groupadd*, *groupmod*, *addgroup*, etc.

1. Creating a group:
```bash
groupadd developers
    - makes a group by the name 'developers'
```
2. We can view all the groups by:
```bash
cat /etc/groups
    - displays all the groups
```
3. Lets us add 'zaman' in this group.
Simply type:
```bash
usermod
    - lists all the flags/options.
    '-G' is to add supplementary groups for this user
    '-g' force use GROUP as new primary group
```
Every linux user has 1 primary group and 0 or more supplementary groups. When a user creates a file it can be owned by 1 user and 1 group only. \
So, the user who created the file will own the file along with the primary group. Primary group is created while creating the user with the same name. \
So, we use -G (uppercase G) to put 'zaman' into the group. So, the
command is:
```bash
usermod -G developers zaman
    - add zaman in a new supplementery group - delevelopers
```
Let us view if 'zaman' is really in 'developers' group:
```bash
cat /etc/passwd | grep zaman
or
grep zaman /etc/passwd
```
We have a command to see the groups of the user:
```bash
group zaman
    - lists all the groups zaman is part of.
```

#### lesson27 - File Permission
 
To get the permission of any file we have to view the long listing:

1. Long listing command:
```bash
ls -l
    - lists all files and directories along with permissions.
```
2. In long listing, here is an example of how we see files/directories:
```bash
drwxr-xr-x 2 bob  bob  4096 Mar 12 19.18 bob
-rw-r--r-- 1 root root   11 Mar 13 20:03 deploy.sh

    Explaintation: 
    Now, let us have the breakup of the info we see:
    drwxr-xr-x : The first character that we see here tells us whether it 
                    is a file or a directory. 'd' means directory while 
                    '-' means a file.
                 After the 1st character, we have 9 characters- a set of 3
                    characters actually.
                    Here, each character refers to permissions:
                    r = read
                    w = write
                    x = execute
                    - = no permission
                The first set of 3-characters belong to the owner
                The second set of 3-characters belong to group
                The third set of 3-characters belong to others
```

3. To execute any file. We need to type '.'(*period/dot*) refering to the current directory followed by `/<file_name>`. 
E.g.,
```bash
./deploy.sh
    - executes the file 'deploy.sh'
```
4. To change permission of a particular file, we use 'change mode' command:
```bash
chmod <entity><+/-><permission> <file_name>
    - <entity> can be u/g/o (user that owns the file/group/others)
    - <+/-> '+' to add permission; '-' to remove permission
    - <permission> what permission you want to add/remove. This could be 
        any permission 'r', 'w', 'x' (read, write or execute)
    E.g., 
    chmod o+x deploy.sh
    - changes permission for others to execute
```
5. Variations of the above command. We will only use an example to understand:
```bash
chmod og+x+w-r deploy.sh
    - changes permission for others and group; adds execute; adds write;
        removes read permissions.
    - Here we can also add multiple filenames or use a pattern:
        E.g., 
        chmod og+x+w-r deploy.sh deploy2.sh deploy3.sh
        chmod og+x+w-r *.sh (wildcard to denote all files having .sh 
            extension)
```

# Docker 

Section 4

#### lesson28 - Building Images

In this section we will learn:
    - Creating Docker files
    - Versioning images
    - Sharing images
    - Saving and loading images
    - Reducing the image size
    - Speeding up builds

#### lesson29 - Images and Containers

1. Image: An image contains everything an application needs to run. It contains all the files and configuration settings needed to run an application. Once we have an image we can start a container from it.

2. An image contains: \
    a. A cut-down OS \
    b. Third-party libraries \
    c. Application files \
    d. Environment variable

    From Gemini (Google)
    Image:
    - Template: A blueprint that defines the contents and configuration of a container.
    - Immutable: Once created, the image itself cannot be modified.
    - Versioned: Images can be versioned to track changes and ensure consistency.
    - Shareable: Images can be easily shared across machines and registries for deployment.
    - Reusable: The same image can be used to create multiple containers.

3. Container: A container is like an isolated Operating System. \
    Features:
    - Provides an isolated environment
    - Can be stopped & restarted (Similar to virtual machines)
    - Technically, it is just a process.
        but it's a special kind of process which has it own file System provided by the image.

    From Gemini (Google)
    Containers:
    - Package: Contains an application and its dependencies (libraries, frameworks) all bundled together.
    - Isolated: Runs in its own isolated environment, not directly on the host system.
    - Portable: Works consistently across different environments (dev, test, prod) due to self-contained nature.
    - Lightweight: Shares the OS kernel with other containers, making them efficient.
    - Scalable: Containers can be easily spun up and down, making them ideal for microservices architectures.

    Difference between Containers and Virtual machines
    - Level of Virtualization:
        Container: Virtualizes the operating system layer.
        VM: Virtualizes the entire hardware layer (CPU, memory, storage).
    - Isolation:
        Container: Shares the kernel with other containers, but applications 
            are isolated.
        VM: Each VM has its own isolated operating system and applications.
    - Resource Usage:
        Container: Lightweight and fast to start.
        VM: More resource-intensive and slower to start.
    - Portability:
        Container: Highly portable due to self-contained nature.
        VM: Less portable due to potential hardware dependency.
    - Use Cases:
        Container: Ideal for microservices architectures and deploying 
            stateless applications.
        VM: Suitable for running legacy applications, different operating 
            systems, or environments requiring more isolation.

    Tabular format:

| Feature           | Containers                                    | Virtual Machines                             |
|------------------|--------------------------------|----------------------------------|
| **Level of Virtualization** | Virtualizes the **OS layer**. | Virtualizes the **entire hardware layer** (CPU, memory, storage). |
| **Isolation** | Shares the kernel with other containers, but applications are isolated. | Each VM has its own **isolated OS** and applications. |
| **Resource Usage** | Lightweight and fast to start. | More resource-intensive and slower to start. |
| **Portability** | Highly portable due to self-contained nature. | Less portable due to potential hardware dependency. |
| **Use Cases** | Ideal for **microservices** and **stateless apps**. | Suitable for **legacy apps**, different OS environments, and workloads needing strong isolation. |



#### lesson30 - Sample Web Application

Just a front-end react app

1. To start this app:
    - Install Node
    - npm install (using npm we have to install 3rd party dependencies)
    - npm start

2. This process will be followed for any other stack also. like c sharp or whatever

#### lesson 31 - Dockerfile Instructions

1. Dockerfile: A Dockerfile contains instructions for building an image

2. Contains:
    - FROM    - To specify the base image. (The cut-down OS mentioned earlier)
    - WORKDIR - Working Directory. Once we specify this directory all the following command will be executed here
    - COPY    - for copying files/ directories
    - ADD     - for copying files/ directories (will add more)
    - RUN     - to use Operating System commands
    - ENV     - for setting environment variables
    - EXPOSE  - for telling docker that our container is starting on a given port.
    - USER    - for specifying the user that should run the application. 
                Typically, we want to run our application using a user with limited privileges.
    - CMD     - for specifying the command that has to be executed when we start a container.
    - ENTRYPOINT - for specifying the command that has to be executed when we start a container. (MORE INFO LATER)

#### lesson32 - Choosing the Right Base Image

A Dockerfile is a list of instructions

**Dockerfile**: \
    A Dockerfile is a plain text document containing instructions for Docker to build a specific image.  \
    Each line specifies a step, like installing software, copying files, or configuring settings. \
    It essentially automates the image building process for consistency and reusability.

1. `Base Image`: **FROM** \
    FROM is used to specify the base image. \
    The base image can be an OS like Linux or Windows or it can be an OS plus a runtime environment.

2. `Full URLs` in **FROM**: \
    So an image can be in any registry. The default registry docker uses is dockerhub. \
    If the image is in some other registry, we have to type the full URL

3. `latest` tag:
    ```bash
    FROM node:latest
    ```
    Avoid using the latest tag in `FROM` because the registry might get updated and your app might not be compatible with the new version. \
    So, always use a `specific version`.

4. To run a container, we need to do the following: \
    a. Make a Dockerfile \
    b. Build a docker image with the docker build command and \
    c. Run the container

    a. Dockerfile: 
    ```bash
    FROM node:14.16.0-alpine3.13 
    - this is just an example
    ```

    b. Build the image with following command:
    ```bash
    docker build -t <tag-a-name> <Dockerfile_path>
    docker build -t react-app .
    - '-t' is used to tag
    - 'react-app' is the tag name
    - '.' is the path where Dockerfile is located. Here, it is current
    ```

    c. Run the container:
    ```bash
    docker run -it <image_name>
    docker run -it react-app
        - '-it' tag is used to start the container in interactive mode.
        - Like mentioned earlier, if we don't interact with the container, it will be stopped.
    ```
        
    To run it on bash (and not the default terminal) type:
    ```bash
    docker run -it react-app bash
        - if bash is not available, use shell (bash is sometimes not available when the image is very small)
    ```
    ```bash
    docker run -it react-app sh
        - runs shell
    ```
        


5. To check all the images we can type:
    ```bash
    docker images 
    or 
    docker image ls
    - lists all the docker images
    ```

#### lesson33 - Copying Files and Directories

1. `COPY` and `ADD` \
    These are used to copy the application files into the image. For this, we have two instructions, COPY and ADD. They are basically similar but ADD has some features more discussed later.

2. `COPY` \
    With this we can copy one or more files/directories into our image.
    The files and directories we can copy from has to be the **CURRENT** directory only (not from elsewhere). 

3. E.g.,
    ```bash
    COPY package.json /app \
    - In this instruction, if the directory 'app' doesn't exists, docker will create it for you.
    ```
4. Other version for understanding:
    ```bash
    COPY package.json README.md /app
    - copies two files in the 'app' directory
    - However, the above instruction has a syntax error. The error is that when using COPY for 
    more than 1 source file, the destination must be a directory and 
    must end in '/' (forward slash).
    ```
    
    So, the correct syntax is:
    ```bash
    COPY package.json README.md /app/
    - no need
    COPY package*.json README.md /app
    - no need
    ```

5. To copy everything in this directory:
    ```bash
    COPY . /app/
    - to copy everything, we use a '.' (period)
    ```
6. `WORKDIR` \
    Used to set the working directory. Whatever instruction we type after this, will be executed in the directory mentioned in **WORKDIR**.
    ```bash
    WORKDIR /app
    COPY . .
    - copies everything from the current directory to the current working
        directory of the image - '/app'
    ```
7. `ADD` \
    ADD has two additional features: \
    a. You can add a URL. E.g.,
    ```bash
    ADD https://abc.com/file.json .
    - adds some file from the internet to the WORKDIR
    ```
    b. It uncompresses while adding it to the WORKDIR. E.g.,
    ```bash
    ADD file.zip .
    - adds a directory upzipped into the WORKDIR
    ```
    Best practice is to use COPY* 

    Build Context - The Directory from where content is being taken. Also known as the ***Context Directory***. \
        So docker client takes everything from here and sends it to docker engine or docker daemon.

    

#### lesson34 - Excluding Files and Directories


`Build Context` - The Directory from where content is being taken. Also known as the Context Directory. \
        So docker client takes everything from here and sends it to docker engine or docker daemon.

1. There will be few files/directories which we will not want the docker 
    client to copy from the 'context directory' to the image.
    In order to instruct docker engine to ignore files or directory, we
    have to create a file by the name:


    `.dockerignore`
    - create the file as it is (no extension etc.)
    - this is similar to '.gitignore' file


    So, suppose we have a directory we want docker engine to ignore. We
    open the '.dockerignore' file and simply type the name of the 
    directory followed by '/' forward slash. E.g.,


    `node_modules/`
    - this will ignore the above directory.

Here are few terms we should read. \
Taken from Google Gemini: \
`Docker Engine (dockerd)`: \
The behind-the-scenes boss, a program that builds, runs, and manages your containers. \
It's like a factory for creating and controlling your containerised applications.


`Docker Client (docker)`: \
Your interface to the engine. It's the command-line tool you use to give orders (build, run, stop) to the Docker engine. \
Think of it as the remote control for the container factory.


`Docker Daemon`: \
Always on duty, this program listens for instructions from the client and carries them out using the Docker engine. 
It's the tireless worker that builds and manages your containers based on the client's commands.


#### lesson35 - Running Commands

1. RUN Command
    With this command, we can execute any command we normally execute in
    a terminal session. E.g.,
    ```bash
    RUN npm install
    RUN apt install python
    ```

#### lesson36 - Setting Environment Variables

1. ENV \
    Sometimes we need to set an environment variable. We can set it by:
    ```bash
    ENV API_URL=https://api.myapp.com/ 
    - sets an environmental variable
    ```

Now rebuild the image and inspect the environment variable:
```bash
docker build -t react-app .
docker run -it react-app sh
- this will open the terminal and now we can inspect our environmental
variable here. There are 2 commands for it:
printenv
- lists all env variable
printenv API_URL
- prints a particular env variable
echo $API_URL
- with echo you have to add '$'
```


#### lesson37 - Exposing Ports

`EXPOSE` command

1. `EXPOSE` is the instruction to tell on which port this container will listening on. \
    The EXPOSE command doesn't automatically publish the port on the host, it is just a form of documentation that tells us this container will eventually listen on the port mentioned. E.g.,

```bash
EXPOSE 3000
- conveys that this container will be listening of this port- 3000
```
Later on when we run an application on a container, we have to map this port with our host to the container.

#### lesson38 - Setting the User

The `RUN` and `USER` commands

Here we will create a new 'system' user and put it in a group to work in the container

1. By default docker builds our application with the root user which has all the privileges but it makes it risky. \
    So, to run any application on docker we should create a regular user with limited privileges.
      
2. We type 'useradd' in the command line, we get to see all the options available. \
    These are flags:
```bash
-S 
- creates a 'system' user
-G
- creates/sets up the primary group of the user
```
3. Type the following command and understand it:
```bash
    addgroup app
    - creates a group
    adduser -S -G app app
    - format: add user -S -G <group_name> <users_name>
    - adds a new user as a system user and put it in a group named 'app'
```
4. To check in which group the user is:
```bash
    groups app
    - checks the group of the user
```
5. Single command to perform the above:
```bash
    adduser mosh && adduser -S -G mosh mosh
    - 
```
6. In our Dockerfile we will use the above command as follows:
```bash
    RUN adduser mosh && adduser -S -G mosh mosh
```

7. USER command is used to set the user inside the container. Henceforth, all the commands will be executed using the user mentioned:
```bash
    USER app
    - switches the user to app
```

#### lesson39 - Defining Entrypoints

Ensure that the user that you have created is pushed to the top so that we don't get any permission errors. 

`RUN`, `CMD` and `ENTRYPOINT`

1. We use the following command to start the starting point to start using our container: \
```bash
    docker run react-app npm start
    - runs the container and starts npm start
    - now we do not have to write 'npm start' to start the container so,
        we include this in the Dockerfile.
```

1. CMD is used to use the default command to be executed:
```bash
    CMD npm start
```
2. Because the command instruction is for supplying the default command, it doesn't make sense to type multiple CMD commmand. If you have multiple of them in a Dockerfile, only the last of it will take take effect.

3. `RUN` vs `CMD` \
    With both of these commands we can run commands but here is the difference: \
    `RUN` instruction is a `build-time instruction`.

    Google Gemini:
    `RUN`: This is for building the image. RUN instructions execute commands during the build process, adding layers to the final image. \
        Imagine it as adding ingredients to a recipe (image). \
    `CMD`: This sets the default command for the container. The CMD instruction specifies what the container will run when you start it. \
        Think of it as the starting instruction for your cooked dish (container).

4. CMD instruction has two forms: \
    a. Shell form \
    b. Exec form (Execute form)

    `Shell form`: \
        When we use this syntax, docker will execute the command in separate shell. That is why it is so called. \
        In linux, it is '/bin/sh'
        In Windows, it is 'cmd' or the command prompt
    `Exec form`: \
        This takes an array of strings. 

    E.g., 
    ```bash
    CMD ["npm", "start"]
    ```
    The common best practice is to use the Exec form. Because here we can execute the command directly and don't have to spin up another shell process. Also, it makes it easier and faster to clean up resources when you stop a container.

5. `ENTRYPOINT`
    This is similar to CMD and this also has 2 forms: \
    a. Shell form \
    b. Exec form

    The difference is we cannot easily `override` ENTRYPOINT. To override we have to use a flag: --entrypoint \
    A lot of people forget to override so it is slightly harder to override but you can `easily over-ride CMD`


### lesson40: Speeding Up Builds

1. `Layers`: An image in docker is collection of layers. Each layer is like a small filesystem that only includes modified files. \
    Each command is layer and that layer only modifies the image based on this instruction.
    
    We can read the info from bottom to top.

2. Optimisation in docker is that it sees the instruction and build the layer **if there is any modification**. \
    If there are no modification in the instruction, it is not going to re-build the layer it is going to *reuse it its cache*. \
    If there is any change in the layer then docker has to rebuild the layer and then entire layers following it. \
    So, to optimise our builds, we have to separte the installation of third party dependencies of our application files.

    COPY . .
    - instead of copying the entire files in one go. We can separte what is require in the subsequent command so that this particular layer can be reused and we can save time while creating the image.

3. `Takeaway`: While writing a Dockerfile. We should keep the instruction that do not change frequently on the top so that the layer can be reused from the cache.

#### lesson41 - Removing Images

1. `Dangling Images` with no name and no tag are known as Dangling Images. \
    To remove these images, we use the ***prune*** command:
```bash
docker image prune
- removes the dangling images
```
2. To remove all stopped container:
```bash
docker container prune
- removes all the stopped containers
```
3. Use the following command to get all the options related to containers:
```bash
docker images
- lists all the option we can use with 'docker images'
```
4. docker rm <image_name>
    docker rm <image_id>
    - removes the image

lesson42 - Tagging Images

1. If we don't tag our images it will be tagged as 'latest' by default.
    An image can have multiple tags.

2. There are 2 ways to tag an image:
    a. While building the image
    b. Tag the image after it is build

    While Building an image:
        Use the version number at the end after a colon ':'. E.g.,
        docker build -t react-app:1
        - build the image with the tag as '1'

    Tag the image after it is build:
        Here, we use the 'tag' command. This is like renaming the old
        name with the new one. E.g.,
        docker image tag <old_image_name:version> <new_image_name:version>
        docker image tag react-app:latest react-app:1

3. Instead of image name we can also use image ID

4. The 'latest' tag doesn't necessarily mean the latest image. We should
    fix it.


lesson43 - Sharing Images

hub.docker.com - it is a repo

Create a Repository

1. docker login
    - asks username and password to login

2. docker image tag <image_id> <image_name:tag>
    - tags the image. Since we can have multiple tags of an image we
        are tagging it in this format 'zamanmd/react-app:1'

2. docker push
    docker push zamanmd/react-app:1
    - pushes the image to docker hub
    - docker pushes each layer at a time. So the first time it pushes it 
        takes some time then later it becomes quick assuming we have not 
        changed our application dependencies.

3. After pushing it on docker we can pull it in machine using docker.


lesson44 - Saving and Loading Images

1. Saving an image into a file:
    If you have an image on your machine and want to share it to another 
    machine without going through dockerhub, you can simply save and 
    compress the image in '.tar' file (.tar is a zip file for linux) then 
    copy it to your desired machine and then load it. (unzip it
    basically). Here is the command:
    docker image save -o react-app.tar react-app:3
    - saves and compresses the image 'react-app:3' to 'react-app.tar'
    - '-o' option means to output the file in 'react-app.tar'

2. Loading (uncompressing the image) an image from a file:
    Once we have the '.tar' file, we can load or unzip the image and 
    get it on the machine. The command for this is:
    docker image load -i react-app.tar
    - loads an image from the '.tar' file
    - option '-i' mean the input file which here is 'react-app.tar'


lesson45 - Working with Containers


Intro about the Section that we are going to learn about containers here.

lesson46 - Starting Containers

1. Using containers in detached mode:
    If you start a container, it will start running but you cannot do 
    anything in it. If you press 'ctrl+c' the container stops. So, to
    ensure that if runs in the background and you can use the terminal, 
    we can run the container in detached mode:
    docker run -d react-app
    - runs 'react-app' container in detached mode (in the background)
    - meanwhile, we can use the terminal

2. Naming a container:
    Docker give each container a random name. We can use the name as a 
    reference. We can also give that name using the following command:
    docker run -d --name blue-sky react-app
    - runs the 'react-app' container in detached mode and names it 
        'blue-sky'

lesson47 - Viewing the Logs

1. To view all the logs inside a container:
    docker logs 655
    - displays the logs of the container having the ID '655' 

2. Viewing the flags associated with docker commands:
    Whenever you want to play around with a docker command, always use 
    '--help' after the command. E.g.,
    docker logs --help
    - displays all the options related with the command 'docker logs'

3. Few important options/flags:
    - f : follows the logs in realtime
    - n : No. of lines of the logs to show from the end of the logs
    - t : Show timestamps


lesson48 - Publishing Ports

1. We cannot access a container on our localhost in the above example 
    although we have exposed it to the port '3000' in its Dockerfile 
    because 'PORT 3000' in the Dockerfile means it is exposed to the 
    container's '3000' port not our machine's localhost.

2. To map a port we use the following command:
    docker run -d -p 80:3000 --name c1 react-app
    - runs a container. 
    - the flag '-p 80:3000' means port mapping the 1st port is the host 
        port and 2nd port is container's port. So,
        '80' is host port
        '3000' is container's port

lesson49 - Executing Commands in Running Containers

1. We can execute commands in a running container using the following
    by:
    docker exec c1 ls
    - displays the content of our '/app' directory. It is viewing the 
        '/app' directory because in the Dockerfile of c1. We had 
        mentioned '/app' as the WORKDIR.
    - using the exec command, we can also open up a shell session:
    docker exec -it c1 sh
    - opens a container in interactive mode and in shell session.


2. Difference between 'run' and 'exec':
    run is used to start a NEW container. 
    exec is used to access the existing container


lesson50 - Stopping and Starting Containers

1. To stop a running container:
    docker stop c1
    - stops a running container

2. docker start c1
    - start a new container

3. Difference between 'start' and 'run' is 
    'start' is used in stopped containers while 'run' is used in new 
        containers.


lesson51 - Removing Containers

1. There are two command to remove a container:
    a. docker container rm c1
    b. docker rm c1 (We will be using this one henceforth)

2. Remove a container:
    docker rm c1
    
3. A container cannot be removed if it is running. So, if you want to 
    remove it either stop it first and then remove it or you can force 
    remove it by:
    docker rm -f c1
    - removes a container by force

4. To remove all the stopped containers in one go:
    docker container prune


lesson52 - Containers File System

1. Each container has its own file system invisible to other containers.
    Once a containers is deleted its file system will be deleted, so we 
    never store anything in our containers. We should use volumes for 
    that.

lesson53 - Persisting Data using Volumes

1. A volume is a storage outside of containers. It can be directory in 
    host or somewhere in the cloud.

    docker volume
    - lists other sub-commands

2. Create a volume:
    docker volume create app-data
    - creates a volume

3. To inspect the volume:
    docker volume inspect app-data
    - shows details about the volume
    - looks something like:
    [
        {
        "CreatedAt": "2021-03-16T21:16:41Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/app-data/_data",
        "Name": "app-data",
        "Options": {},
        "Scope": "local"
        }
    ]

4. An example of how to map and few explainations:
    docker run -d -p 4000:3000 -v app-data:/app/data react-app
    - maps a volume in host directory
    - in case we don't create 'app-data' directory, docker will create a
        volume
    - in case we don't have a directory '/app/data' already created,
        docker will create the same
    - in this example, we may get the error of permission when we go 
        inside the container and try to create a file. This is because
        when we run this container we let the 'data' directory created 
        by the docker itself, meaning the 'root' user so 'app' user will 
        not have the access of modifying the file.
    - So, we need to ensure that the 'app' user creates the directory 
        and we can make these changes in the Dockerfile.

        This is 'named' volume.

5. Even if a container is deleted the data persists because of the volume

6. We can map this volume with other containers as well


lesson54 - Copying Files between the Host and Containers

1. We can copy files from the container to our host

2. we can use the 'cp' command to copy to and from a container

3. Copy from a container to our host:
    docker cp <container_id>:<container_path> <host_path>
    docker cp e1c90:/app/log.txt .
    - copies a file from a container to host

4. Copy from from the host to the container:
    docker cp <host_path/file_name> <container_id:container_path>
    docker cp secret.txt e1c90:/app
    

lesson55 - Sharing the Source Code with a Container

1. We can publish the application changes using volumes and in this way 
    we don't have to copy or build our images every now and then.
    This way whenever we make any changes in our source code, it will be 
    reflected in our dockerized application.
    We can do so by mapping/ binding  between our directory on the host 
    with the directory inside our container.
    docker run -d -p 5001:3000 -v $(pwd):/app
    - mapped our project directory with the directory in the container


lesson56 - Running Multi-Container Application

Front-end
Back-end
Database

lesson57 - Installing Docker Compose

1. Docker compose is a tool which is built on top of Docker Engine. 
    Using this we can start an application with multiple containers.
    
    Use the instruction to install from the official website.
    docker-compose --version

lesson58 - Cleaning Up our Workspace

1. docker container -f rm $(docker container ls -aq)

2. docker image -f rm $(docker image ls -aq)

3. You can use the Docker UI as well. Here you can use the 
    'Clean/ Purge data'
    This will restart the docker engine

lesson59 - The Sample Web Application

An application with frontend and backend and it has a docker-compose.yml

lesson60 - JSON and YAML Formats

1. Discussed about JSON and YAML.
2. Key Value Pairs
3. For lists we use '-' hyphens with same indentations
4. For objects we use indentations for properties
 

lesson61 - Creating a Compose File

1. The name has to be 'docker-compose.yml'. The is the default name.

2. version: "3.8"
    - use double quotes otherwise it will be evaluated as a number
3. services:
    frontend:
    backend:
    db:

    - these can be named as anything. E.g.,
    services:
        web:
        api:
        db:
    inside we have properties

4.  version: "3.8"
    services:                [Each service will have its own Dockerfile]
        web:
          build: ./frontend  [location of Dockerfile]
          ports:
            - 3000:3000
        api:
          build: ./backend
          ports:
            - 3001:3001
          environment:
            DB_URL: mongodb://db/vidly
        db:
          image: mongo:4.0-xenial
          ports:
            - 27017:27017
          volumes:
            - vidly:/data/db  [mongo db stores its data in '/data/db']
    volumes:
      vidly:            [We have to define volume before we can use it]


lesson62 - Building Images
 
1. Use the following command to explore options in docker compose:
    docker-compose
    - lists all options


2. docker-compose --help
    - more options

3. docker-compose build
    - builds an image from 'docker-compose.yml'

4. docker-compose build --no-cache
    - doesn't used the cached memory to build images

5. docker-compose up
    - get the appliaction up and running



lesson63 - Starting and Stopping the Application

1. docker-compose up --build
    - we can combine to the two

2. docker-compose build
     - forces a rebuild


2. docker-compose ps
    - lists all the containers relevant to this application

3. docker-compose down
    - stop and remove the containers


lesson64 - Docker Networking

1. When we start our appliaction using docker-compose, it will 
    automatically create a network and add our containers on that 
    network so these containers can talk to each other.
    You can see this network while building the docker-compose up

2. docker network ls
    - lists all the network in this machine

3. To verify that these containers can talk to each other we can exec in 
    any of the containers and we will be able to ping :

    docker exec -it 8c6 sh
    ping api
    - you can get a permission error. So use the following command to 
        login using the root user.
    docker exec -it -u root 8c6 sh
    - uses the 'root' user to login
    ping api
    - pings api

4. Docker comes with embedded DNS server which contains name and IP of 
    these containers. Inside each containers we have a component called 
    'DNS resolver'. This DNS resolver talks to the DNS server to find the 
    IP address of the target containers.
    So, when we ping the api container, this DNS resolver asks the DNS 
    server what is the IP address of the api container or API machine 
    and the DNS server returns the IP address and then the 'web' 
    container can directly talk to the 'api' container using its IP 
    address.
    Each container has an IP address and is part of a network.


lesson65 - Viewing Logs

1. docker-compose logs
    - views the logs across all the containers

2. docker-compose logs --help
    - lists the available options

3. docker logs <container_id>
    - views the logs of a particular container

lesson66 - Publishing Changes

1. Mapping a volume like we did earlier

lesson67 - Migrating the Database

??

lesson68 - Running Tests

??

Section 7 - Deployment

1. How to deploy our dockerised applications

lesson70 - Deployment Options

1. To deploy our dockerised applications, we have 2 options:
    a. Single-host deployment
    b. Cluster deployment

2. Single-host deployment:
    If our server goes offline our application will not be accessible.
    If our application goes rapidly our single server may not be able 
    to handle this load.

3. Clusters deployment:
    With clusters, we get high availability and scalability.


lesson71 - Get a Virtual Private Server

VPS

1. Options:
    a. Digital Ocean
    b. GCP
    c. Azure
    d. AWS

lesson72 - Installing Docker Machine

1. Once we have a server, we need a tool docker machine to talk to the 
    docker engine on that server this way we can execute docker commands 
    in the terminal and the commands will be sent to our docker engine
    server on our server.

    It is just copy the command and execute on cli

    docker-machine --version
    - prints the version


lesson73 - Provisioning a host

lesson74 - Connecting to the Host

ssh to connect

lesson75 -  Defining the Production configuration

lesson76 - Reducing the Image Size

1. We can add a label by adding 'AS'. E.g.,
    FROM node:14.16 AS build-stage


lesson77 - Deploying the Application.
