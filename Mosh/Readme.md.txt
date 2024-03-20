1. What is Docker?
A: Docker is a platform for running, building and shipping application.

2. Why an applications work on your machine but doesn't elsewhere/ Need 
    for Docker?
A:  a. Missing one or more files
    b. Software version mismatch. The software which it's dependent on is 
        of different version.
    c. Different configuration settings.

3. How does docker do?
a: With docker we package the application with all that it needs and run 
    it anywhere.

4. Container vs Virtual machine
A:  Container- An isolated environment for running an app.
    Virtual machine- An abstraction of a machine (physical hardware).
    (Add more from hand written notes from Abhishek Veeramalla)

5. Problems with virtual machine?
A:  a. Each virtual machine needs a full-blown OS
    b. Slow to start
    c. Resource intensive

6. Containers
A:  a. Allow multiple apps in isolation
    b. Are lightweight
    c. Use OS of the host
    d. Start quickly
    d. Needs less hardware resources

7. Docker Archtecture
A: Docker works on client server architecture. The client is connected and 
    talks to the server component by Rest API and the server is known as 
    "Docker Engine".
    Docker Engine sits in the background and takes care of building and 
    running containers.
    Container don't use full-blown OS. Instead, all the containers of 
    the host share the OS. Infact, all containers share the kernel of the 
    host.

8. Kernel
A: A kernel manages the application and hardware resources.

    Gemini Explaination:
    The kernel in Linux is the core program that acts as a bridge between 
    your applications and the physical hardware. It manages resources 
    (CPU, memory, storage) and controls communication between everything 
    running on your system. Think of it as the conductor of the computer 
    orchestra.

9. Docker Image:

A:  Contains:
    a. A cut-down OS
    b. A runtime environment
    c. Application files
    d. Third-party libraries
    e. Environment variables

    Google Gemini: (Just to add some details)
    is essentially a self-contained blueprint for creating a Docker 
    container. Here's a breakdown:

    - Immutable: Once built, the image itself cannot be changed. Think of 
                it as a fixed recipe.
    - Versioned: Images can have versions, allowing you to track changes 
                and ensure consistency across deployments.
    - Shareable: Images can be easily shared with others through public 
                registries (like Docker Hub) or private ones within your 
                organisation.
    - Reusable: A single image can be used to create multiple running 
                containers, ensuring consistent environments.


10. Container:
    A container is a process. But is it a special kind of process which has 
    its own filesystem.

    Google Gemini:
    A Docker container, building on the image analogy, is the cooked pizza 
    from the Docker image recipe. Here's a breakdown:

    - Executable Instance: A container is a running instance of a Docker 
            image. It's the actual application or service you want to 
            deploy.
    - Isolated Environment: Each container runs in its own isolated space, 
            sharing the operating system kernel with other containers but 
            keeping applications separate.
    - Lightweight & Portable: Containers are lightweight and efficient 
            because they share the kernel. This also makes them portable 
            and able to run consistently across different environments.
    - Dynamic: Unlike the image, a container can be modified while running. 
            You can add files, install additional software, or change 
            configurations.

6. docker images
    or (alternate command)
    docker image ls
    -lists all the images

7. docker version
    displays the docker version

LINUX

11. Linux is an opensource OS

2. Using ubuntu on docker:
a. Instead of using "docker pull ubuntu" the shortcut can be:
    docker run ubuntu
    (If the image exists then it will simply run but if it doesn't exists, 
    it will pull(download from the repo/dockerhub) and run)

3. docker ps
    - checks all the docker process it is running (running container is a 
    process)

4. docker ps -a
    displays all the containers even if it is stopped 

6. docker run <docker_image_name>
    -runs a container. 

7. If you start a container and if it is not in interactie mode. It will 
    stop.

8. If you don't want it to stop, keep it in interactive mode. To put it in 
interactie mode, use the flag "-it"

5. docker run -it ubuntu
    -runs a container in interactive mode.

---------------------
Henceforth, lesson-wise

lesson12- Linux Distributions
1. Linux is an opensource OS

2. Linux comes with a lot of Distributions

3. Eg.,
    a. ubuntu
    b. Debian
    c. Alpine
    d. CentOS

lesson13 - Running Linux

1. To use Linuxs' particular OS say ubuntu we can type 
    docker pull ubuntu
    -pulls the ubuntu image

    or instead of using pull, we can use:
    docker run ubuntu
    -runs the ubuntu container but if it's not available, it will download 
    it and then run

2. Although we have downloaded the container and run it, since we didn't 
    interact with it, so it stopped.
    -so if we do not interact with a container, it will stop

    To check we can write:
    docker ps 
    (to check the running processes, since a container is a process)
    We will find nothing
    But when we write:
    docker ps -a
    checks all the process, even if any container has stopped
3. To start a container and interact with it:
    docker run -it <container_name>
    docker run -it ubuntu
    -starts a container in interaction mode.
    -this will open a shell prompt

4. Linux is a case sensitive OS

5. You can use up and down arrow keys to navigate between the commands

6. A shell prompt typically looks something like this:
    root@1a2345:/#
    Here is a breakdown of the above shell command:
    a. root - means the user, if you login with a differet user you will 
        get a the user's name
    b. 1a2345 - means the machine ID. This ID is generated by the docker
    c. / - means where we are in the filesystem. A forward slash represents
        the root directory.
    d. # - denotes the privileges. A hash means that we have the highest 
        priviledges as the root user. If we login as a different user, we 
        will get a $ (dollar) instead of # (hash).

7. To list down all the commands entered type:
    histroy
    - lists down all the commands in a serial order.
    - to execute the commands from the list type below:
    !<command serial> (exclaimation mark and the serial no.)
    !2
    - execute the 2nd command in the serial

lesson14 - Managing Packages

8. A Linux package manager is a tool that helps you easily install, update,
    and remove softwares. 
    In ubuntu we have apt. 
    apt stands of Advanced Package Tool
    If you type:
    apt
    - lists sub-commands, like list, install, remove, search, etc.,

    Suppose we want to install nano. If we type nano, we get nothing 
    because it has not been installed currently.
    To install it, we type:
    apt install nano
    - it might still not get installed, because we might not have the 
        package of nano in the database of the ubuntu images.

    You can list the all the packages that are available in this OS by 
    typing:
    apt list
    -lists all the packages. Some packages may be installed while others 
    might not be installed.

    So, we update the db of the packages by typing:
    apt update
    -updates the dbs of the packages
    and now when we type:
    apt list
    - more packages will get displayed along with nano
    
    Now, we  can install nano by typing:
    apt install nano
    - installs nano

    Take Away: 
    So, before installing any package, make sure you have updated the 
    package db

9. To remove any package:
    apt remove nano
    -uninstalls the package

lesson 16 - Linux filesystem

1. In linux, we have the root directory on top which is represented as "/".
    below that we have some standard directories:

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

    Just a brief explaination:
    
    /    - root
    bin  - cotains mainly binary files or programmes
    boot - contains files related to booting
    dev  - short for devices (Yes, in linux everything is a file, including 
            directories)
    etc  - General belief is it stands of Editable Text Config 
            (configuration files)
    home - This is where home directories of users are stored. Each user 
            is going to have their home directory here.
    root - root directory for the root user. Only the root user will be 
            able to see this
    lib  - used for keeping library files like software library dependencies
    var  - stands for variable. This is where files are updated frequently 
            like log files, application data, etc.
    proc - contains files represent running processes. (Yes, even processes 
            are files in linux)
    
lesson16: Navigating the File System

Relative Path vs Absolute Path:

Relative path: Starts with "./" or "../", navigates relative to your 
    current location. Like giving directions.
    Example: ./report.pdf (This file is in the current directory)
    Example: ../downloads/music.mp3 (This file is in the "downloads" 
    folder, one level up from the current directory)

Absolute path: Starts with "/", tells the exact location from the 
    root directory. Think full address.
    Example: /home/user/documents/report.pdf (This file is in the 
    "documents" folder inside the user's home directory)

Very basic commands:

1. pwd

2. ls

3. ls -1
    - lists one file per line

4. ls -l
    - lists one file per line with details

5. cd

6. cd ..

lesson 17 - Manipulating Files and Directories

1. cd ~
    - takes you to the home directory
2. mv

3. touch hello.txt
    - to create a file in txt. touch command is used to create files 
    and mkdir to create directories.

4. rm
    - removes file/files (deletes)

5. rm -r
    - removes directories '-r' stands for recursive which means all 
    its content also.

6. mkdir



Very easy commands for used for editing and viewing documents. Hence
    explained in very brief.

 1. mkdir
    - creates a directory

 2. mv
    - renames/ moves the file from current directory to elsewhere.

 3. touch <file_name>
    - creates a file
 
 4. touch <file_name1> <file_name2> <file_name3>
    - creates multiple files at opensource

5. ls -1
    - lists the files. One file in one line.

6. ls -l
    - lists the files. One file in one line but with details.

7. rm
    - removes a file. There are different ways you can used in shown below:

    rm file_name1
    - removes a file

    rm <file_name1> <file_name2> <file_name3>
    - removes multiple files at once.

    rm file*
    - removes all directory using a pattern. This will remove all 
        directories having "file" in it

    rm -r <directory_name>
    - removes directory having files inside. "-r" is recursive

lesson17 - Editing and Viewing files

Nano is a simple text editor in Linux. To install nano type:

1. apt install nano
    - installs nano text editor

2. nano file_name1.txt
    - create a txt file and opens in nano editor

3. cat
    - displays what is inside the file. It is short for concatenate

4. Similar to "cat" command we have the following command to view large
    files. Here, we don't have to scroll and see our file instead we get 
    an interface with some features. We can simply type:
    more
    - displays what is inside the file
    - press space to go to the next page (we will get a percentage (%)
        at the bottom. Denoting how much % is getting displayed)
    - press enter to go one line at a time
    - to exit we press 'q'

5. Similar to "more", we have "less" command. The problem with "more" 
    command is we can't scroll up. Means we can go to the next page by 
    pressing space but we can't go to the previous page. In less we can
    view the files in interactive way.
    If you do not get the less command then simply install it using 
    "apt install less".
    Type:
    less <file_name>
    - displays the content of the file.
    - press up and down arrow keys to navigate
    - to exit we press 'q'

6. Alternate options are (not so important):
    head -n 5 <file_name>
    - displays 5 lines from the top

    tail -n 5 <file_name>

lesson19 - Redirection

In Linux, redirection lets you change where the output of a command goes. 
    By default, commands send their output to the terminal screen. 
    Redirection allows you to:
    - Send output to a file (>): ls > files.txt saves the list of files to 
        files.txt.
    - Append output to a file (>>): ls >> files.txt adds the new list to 
        the end of files.txt.
    - Discard output (> /dev/null): ls > /dev/null hides the output (useful
        for commands that just need to run)


lesson20 - Searching for Text

grep = Global Regular Expression Print

We will see how this works using some commands and their explaination

1. grep hello file.txt
    - searches for the word/string "hello" in the file
    - use "-i" option/ flag to make it case insensitive. E.g.,
    grep -i hello file.txt
    - searches for the word hello. Now this will display even if it is
        written in uppercase.

2. grep -i root /etc/passwd
    - displays the word root in the file 

3. grep -i hello file1.txt file2.txt
    - or
    grep -i hello file*
    - means the same thing as above. We have used a wildcard which means any
    file having "file" written in the beginning and whatever afterthat.

2. To search in a directory:
    grep -i -r hello .
    - searches the word "hello" in the current directory in all the files
    - In linux we can combine the options or flags also. So the the above 
        command can be written as:
        grep -ir hello .

lesson21 - Finding Files and Directories

1. find
    - lists all the files and the directory in the current directory 
        recursively. Lists even the hidden ones.

2. ls -a
     - lists everything in a directory including the hidden ones

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

lesson22 - Chaining commands

We can chain or combine different commands like

1. mkdir test ; cd test ; echo done
    - all the above commands can get executed one after the other
    - adding space is optional
    - using semicolon, we can combine/ chain linux commands

2. If we execute the same command again, we will get an error for the first
    command because directory 'test' already exists but the rest commands 
    will be executed.

3. We can use the and operator. If one command fails, other commands won't 
    get executed.
    mkdir test && cd test && echo done

4. We can also use the or operator (||). If the 1st command gets executed the 2nd 
    command doesn't get executed but if the 1st command doesn't get executed
    the 2nd command gets executed.
    mkdir test || echo "Directory Exists"

5. Another way to chain commands is piping. What it essentially do here is
    get the output of the 1st command and put it to the next command.
  ls /bin | less
  - lists all the output of the ls /bin commmand and displays in 'less'.
  - Ref. lesson17, serial 5

  ls /bin | head -n 5
  - just a command to drive away you fear when you see something new

6. Splitting commands in multiple lines. We can use '\' to end the line and
    after that we can press enter and write other commands. This ensure
    that whenever we have a long command we don't have to scroll 
    horizontally to go through the entire command
    mkdir hello ; cd hello ; echo done

    mkdir hello;\
    > cd hello; \
    > echo done

lesson23 - Environment Variables

Explaination: Environment variables in Linux are basically name-value 
    pairs that control how programs run. They're like mini settings menus 
    for your shell and applications.
    Used for storing configuration setting for our applications. So, our 
    applications can read configuration settings from this env variables.

1. printenv
    - displays all the environmental variables in this machine

2. printenv <variable>
    printenv PATH
    - displays the value of 'PATH'

3. You can also view value of a particular variable by echo but here you 
    have to prefix it with '$' by:
    echo $<variable>
    echo <PATH>

4. We can set a variable using 'export' command
    export DB_USER=zaman
    - puts 'zaman' in DB_USER as an environmental variable.
    - this is active for the current session only. So, if we were to close
        this terminal session and open another session. We will not get
        the environmental variable.
    - So, we can get the value we can either type 
        echo $DB_USER
        or
        printenv DB_USER
        and we will get the same result as 'zaman' set earlier

5. To make a variable persistent, we have to write the variable in a 
    special file. The name of the file is ".bashrc". You will find this 
    file in your home directory. So, to be able to see it type:
    ls -a
    - lists all the files and dir including the hidden ones
    Here you will find '.bashrc'
    You can either type 'vi .bashrc' and start editing the file and 
    declare you variable here or simple append by:
    echo DB_USER=zaman >> .bashrc
    - adds another line 'DB_USER=zaman' in the file 'bashrc'
    - now, there is a small limitation to this is that the appended
        environment variable will be active in another session of the
        terminal. Meaning you have to stop this session and begin a new 
        one to see the result.

6. We can use the source command to reload the '.bashrc' file.
    source .bashrc
    - reloads the '.bashrc' file.
    - we have to execute it from our home directory.
    If you are not in your home directory use the below command:
    source ~/.bashrc
    - reloads the '.bashrc' file WHEN YOU ARE NOT IN YOUR HOME DIRECTORY

lesson24 - Managing Processes

A process is an instance of a running programme. To see all the running 
programme or all the running processes we type:
    ps
    - displays all the running processes

1. To kill a process:
    kill <process_ID>
    - kills a particular process.


lesson25 - Managing Users

1. useradd
    - adding a new user
    - this command lists all the options/flag that can be used with this
        command.
    useradd -m zaman
    - adds a new user 'zaman'
    - '-m' flag means creating a user's home directory (use 'useradd' for
        explaination)

2. usermod
    - modifying a user

3. userdel
    - deleting a user

4. To view all the users we can view the folder '/etc/passwd' like:
    cat /etc/passwd
    - lists all the users. Not Password. Name is misleading.

5. Let us understand what a single line means in the file '/etc/passwd':
    zaman:x:1000:1000::/home/zaman:/bin/sh
    - 'zaman' is the user's name
    - ':' is a separator
    - '1000' - first one is the user ID
    - '1000' - second one is group ID
    - '/home/zaman' - home directory of the user
    - '/bin/sh' - shell programme used when this user logs in

6. After seeing the above details from the user 'zaman'. Let us say that 
    we decide to modify the user and use another shell progamme for the 
    user.
    So, first of all let us check which option do we have to user along with
    'usermod'. To explore the flag, simple type:
    usermod
    - all the options/ flags will be listed

    usermod -s /bin/bash zaman
    - modifies the user to use '/bin/bash' shell when the user logs in

    To login as 'zaman' using the bash shell. We type:
    docker exec -it -u zaman 2f75e699 bash
    - logs in inside a container using bash

    To check if the changes has been made we type:
    cat /etc/passwd 
    - we will see all the user information. Here we will find that the shell
        has been changed.

7. Passwords are saved in the /etc/shadow. We can access this directory by:
    cat /etc/shadow
    - only the root user can access this directory
    - passwords are encrypted here

8. We have another command for adding user which is very interactive.
    adduser
    - adds a user
    adduser zaman
    - you will get may info as well as options here.

lesson26 - Managing Groups

We use group so that all users in the same group can have the same
previlages. Just like users, in groups also we have similar commands like:
groupadd, groupmod, addgroup, etc.

1. groupadd developers
    - makes a group by the name 'developers'

2. we can view all the groups by:
    cat /etc/groups
    - displays all the groups

3. Lets us add 'zaman' in this group.
    simply type 'usermod' to find all the flags/options.
    '-G' is to add supplementary groups for this user
    '-g' force use GROUP as new primary group
    Every linux user has 1 primary group and 0 or more supplementary groups
    When a user creates a file it can be owned by 1 user and 1 group only.
    So, the user who created the file will own the file along with the 
    primary group. Primary group is created while creating the user with the 
    same name.
    So, we use -G (uppercase G) to put 'zaman' into the group. So, the
    command is:
    usermod -G developers zaman
    - add zaman in a new supplementery group - delevelopers
    Let us view if 'zaman' is really in 'developers' group.
    cat /etc/passwd | grep zaman
    or
    grep zaman /etc/passwd

    We have a command to see the groups of the user:
    group zaman
    - lists all the groups zaman is part of.


lesson27 - File Permission
 
To get the perssion of any file we have to view the long listing:

1. ls -l
    - lists all files and directories along with permissions.

2. In long listing, here is an example of how we see files/directories:
    drwxr-xr-x 2 bob  bob  4096 Mar 12 19.18 bob
    -rw-r--r-- 1 root root   11 Mar 13 20:03 deploy.sh
    Now, let have the breakup of the info we see:
    drwxr-xr-x : The first character that we see here tells us whether it is
                    a file or a directory. 'd' means directory while '-'
                    means a file.
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


3. To execute any file. We need to type '.'(period/dot) refering to the 
    current directory followed by /<file_name>. E.g.,
    ./deploy.sh
    - executes the file 'deploy.sh'

4. To change permission of a particular file, we use change mode command:
    chmod <entity><+/-><permission> <file_name>
    - <entity> can be u/g/o (user that owns the file/group/others)
    - <+/-> '+' to add permission; '-' to remove permission
    - <permission> what permission you want to add/remove. This could be 
        any permission 'r', 'w', 'x' (read, write or execute)
    E.g., 
    chmod o+x deploy.sh
    - changes permission for others to execute

5. Variations of the above command. We will only use an example to understand
    chmod og+x+w-r deploy.sh
    - changes permission for others and group; adds execute; adds write;
        removes read permissions.
    - Here we can also add multiple filenames or use a pattern:
        E.g., 
        chmod og+x+w-r deploy.sh deploy2.sh deploy3.sh
        chmod og+x+w-r *.sh (wildcard to denote all files having .sh 
            extension)

=======
Docker
=======
Section 4

lesson28 - Building Images

In this section we will learn:
    - Creating Docker files
    - Versioning images
    - Sharing images
    - Saving and loading images
    - Reducing the image size
    - Speeding up builds

lesson29 - Images and Containers

1. Image: An image contains everything an application needs to run. It 
    contains all the files and configuration settings needed to run an 
    application. Once we have an image we can start a container from it.

2. An image contains:
    a. A cut-down OS
    b. Third-party libraries
    c. Application files
    d. Environment variable

    From Gemini (Google's AI)
    Image:
    - Template: A blueprint that defines the contents and configuration of a 
        container.
    - Immutable: Once created, the image itself cannot be modified.
    - Versioned: Images can be versioned to track changes and ensure 
        consistency.
    - Shareable: Images can be easily shared across machines and registries 
        for deployment.
    - Reusable: The same image can be used to create multiple containers.

3. Container: A container is like an isolated Operating System.
    Features:
    - Provides an isolated environment
    - Can be stopped & restarted (Similar to virtual machines)
    - Technically, it is just a process.
        but it's a special kind of process which has it own file System
        provided by the image.

    From Gemini (Google's AI)
    Containers:
    - Package: Contains an application and its dependencies (libraries, 
    frameworks) all bundled together.
    - Isolated: Runs in its own isolated environment, not directly on the 
        host system.
    - Portable: Works consistently across different environments (dev, test, 
        prod) due to self-contained nature.
    - Lightweight: Shares the OS kernel with other containers, making them 
        efficient.
    - Scalable: Containers can be easily spun up and down, making them ideal 
        for microservices architectures.

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


lesson30 - Sample Web Application

Just a front-end react app

1. To start this app:
    - Install Node
    - npm install (using npm we have to install 3rd party dependencies)
    - npm start

2. This process will be followed for any other stack also. like c 
    sharp or whatever

lesson 31 - Dockerfile Instructions

1. Dockerfile: A Dockerfile contains instructions for building an image

2. Contains:
    - FROM - To specify the base image.
    - WORKDIR - Working Directory. Once we specify this directory all the 
                following command will be executed here
    - COPY - for copying files/ directories
    - ADD - for copying files/ directories (will add more)
    - RUN - to use Operating System commands
    - ENV - for setting environment variables
    - EXPOSE - for telling docker that our container is starting on a given
                port.
    - USER - for specifying the user that should run the application. 
            Typically, we want to run our application using a user with
            limited privileges.
    - CMD - for specifying the command that has to be executed when we 
            start a container.
    - ENTRYPOINT - for specifying the command that has to be executed when we 
                    start a container. (MORE INFO)

lesson32 - Choosing the Right Base Image

A Dockerfile is a list of instructions

Dockerfile: A Dockerfile is a plain text document containing instructions 
    for Docker to build a specific image.  Each line specifies a step, 
    like installing software, copying files, or configuring settings. It 
    essentially automates the image building process for consistency and 
    reusability.

1. Base Image: FROM
    FROM is used to specify the base image. The base image can be an OS
        like Linux or Windows or it can be an OS plus a runtime 
        environment.

2. Full URLs in FROM:
     So an image can be in any registry. The default registry docker uses
        is dockerhub. If the image is in some other registry, we have to
        type the full URL

3. latest tag:
    FROM node:latest
    Avoid using the latest tag in FROM because the registry might get 
        updated and your app might not be compatible with the new version.
        So, always use a specific version.

4. To run a container we need to do the following:
    a. Make a Dockerfile
    b. Build a docker image with the docker build command and
    c. Run the container

    a. Dockerfile:
    FROM node:14.16.0-alpine3.13
    (*just an example)

    b. Build the image with following command:
    docker build -t <tag-a-name> <Dockerfile_path>
    docker build -t react-app .
    - '-t' is used to tag
    - 'react-app' is the tag name
    - '.' is the path where Dockerfile is located. Here, it is current

    c. Run the container:
        docker run -it <image_name>
        docker run -it react-app
        - '-it' tag is used to start the container in interactive mode.
            Like mentioned earlier, if we don't interact with the 
            container, it will be stopped.
        
        To run it on bash (and not the default terminal) type:

        docker run -it react-app bash
        - if bash is not available, use shell (bash is sometimes not 
            available when the image is very small)
        
        docker run -it react-app sh
        - runs shell

        


5. To check all the images we can type:
    docker images 
    or 
    docker image ls
    - lists all the docker images


lesson33 - Copying Files and Directories

1. COPY and ADD
    These are used to copy the application files into the image. For this, 
    we have two instructions, COPY and ADD. They are basically similar
    but ADD has some features more discussed later.

2. COPY
    With this we can copy one or more files/ directories into our image.
    The files and directories we can copy from has to be the CURRENT 
    directory only (not from elsewhere). 

3. COPY package.json /app
    - In this instruction, if the directory 'app' doesn't exists, docker
        will create it for you.

4. Other version for understanding:
    COPY package.json README.md /app
    - copies two files in the 'app' directory
    - However, the above instruction is has a syntax error. The error is 
        that when using COPY for more than 1 source file, the destination
        must be a directory and must end in '/' (forward slash).
        So, the correct syntax is:
    COPY package.json README.md /app/
    - no need
    COPY package*.json README.md /app
    - no need


5. To copy everything in this directory:
    COPY . /app/
    - to copy everything, we use a '.' (period)

6. WORKDIR
    Used to set the working directory. Whatever instruction we type after
    this, will be executed in the directory mentioned in WORKDIR.

    WORKDIR /app
    COPY . .
    - copies everything from the current directory to the current working
        directory of the image - '/app'

7. ADD
    ADD has two additional features:
    a. You can add a URL. E.g.,
        ADD https://abc.com/file.json .
        - adds some file from the internet to the WORKDIR
    b. It uncompresses while adding it to the WORKDIR. E.g.,
        ADD file.zip .
        - adds a directory upzipped into the WORKDIR

    Best practice is to use COPY*

    Build Context - The Directory from where content is being taken. Also
        known as the Context Directory. 
        So docker client takes everything from here and sends it to 
        docker engine or docker daemon.

    

lesson34 - Excluding Files and Directories


Build Context - The Directory from where content is being taken. Also
        known as the Context Directory. 
        So docker client takes everything from here and sends it to 
        docker engine or docker daemon.
    Again:
        Docker client takes everything from 'build context' or 
        'context directory' and sends it to docker engine or docker 
        daemon.

1. There will be few files/ directories which we will not want the docker 
    client to copy from the 'context directory' to the image.
    In order to instruct docker engine to ignore files or directory, we
    have to create a file by the name:

    .dockerignore
    - create the file as it is (no extension etc.)
    - this is similar to '.gitignore' file
    So, suppose we have a directory we want docker engine to ignore. We
    open the '.dockerignore' file and simply type the name of the 
    directory followed by '/' forward slash. E.g.,

    node_modules/
    - this will ignore the above directory.

Here are few terms we should read. Taken from Google Gemini:
    Docker Engine (dockerd): The behind-the-scenes boss, a program that 
        builds, runs, and manages your containers. It's like a factory 
        for creating and controlling your containerized applications.
    Docker Client (docker): Your interface to the engine. It's the 
        command-line tool you use to give orders (build, run, stop) to 
        the Docker engine. Think of it as the remote control for the 
        container factory.
    Docker Daemon: Always on duty, this program listens for instructions 
        from the client and carries them out using the Docker engine. 
        It's the tireless worker that builds and manages your containers 
        based on the client's commands.


lesson35 - Running Commands

1. RUN Command
    With this command, we can execute any command we normally execute in
    a terminal session. E.g.,
    RUN npm install
    RUN apt install python


lesson36 - Setting Environment Variables

1. ENV
    Sometimes we need to set an environment variable. We can set it by:
    ENV API_URL=https://api.myapp.com/ 
    - sets an environmental variable

    Now rebuild the image and inspect the environment variable:
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


lesson37 - Exposing Ports

The EXPOSE command

1. EXPOSE is the instruction to tell on which port this container will
    listening on.
    The EXPOSE command doesn't automatically publish the port on the 
    host, it is just a form of documentation that tells us this container
    will eventually listen on the port mentioned. E.g.,
     EXPOSE 3000
     - conveys that this container will be listening of this port- 3000

     Later on when we run an application on a container, we have to map
     this port with our host to the container.

lesson38 - Setting the User

The RUN and USER commands

Here we will create a new 'system' user and put it in a group to work in 
the container

1. By default docker our application with the root user which has all
    the privileges but it makes it risky.
    So, to run any application on docker we should create a regular user
    with limited privileges.
      
2. We we type 'useradd' in the command line, we get to see all the options
    available. These are flags:
    -S 
    - creates a system user
    -G
    - creates/sets up the primary group of the user

3. Type the following command and understandd it:
    addgroup app
    - creates a group
    adduser -S -G app app
    - format: add user -S -G <group_name> <users_name>
    - adds a new user as a system user and put it in a group named 'app'

4. To check in which group the user is:
    groups app
    - checks the group of the user

5. Single command to perform the above:
    adduser mosh && adduser -S -G mosh mosh
    - 

6. In our Dockerfile we will use the above command as follows:
    RUN adduser mosh && adduser -S -G mosh mosh


7. USER command is used to set the user inside the container. Henceforth,
    all the commands will be executed using the user mentioned:
    USER app
    - switches the user to app


lesson39 - Defining Entrypoints

Ensure that the user that you have created is pushed to the top so that
    we don't get any permission errors.

RUN, CMD and ENTRYPOINT

1. We use the following command to start the starting point to start
    using our container:
    docker run react-app npm start
    - runs the container and starts npm start
    - now we do not have to write 'npm start' to start the container so,
        we include this in the Dockerfile.


1. CMD is used to use the default command to be executed:
    CMD npm start

2. Because the command instruction is for supplying the default
    command, it doesn't make sense to type multiple CMD commmand. If you
    have multiple of them in a Dockerfile, only the last of it will take
    take effect.

3. RUN vs CMD
    With both of these commands we can run commands but here is the 
    difference:
    RUN instruction is a build time instruction.

    Google Gemini:
    RUN: This is for building the image. RUN instructions execute commands 
        during the build process, adding layers to the final image. 
        Imagine it as adding ingredients to a recipe (image).
    CMD: This sets the default command for the container. The CMD 
        instruction specifies what the container will run when you start 
        it. Think of it as the starting instruction for your cooked dish 
        (container).

4. CMD instruction has two forms:
    a. Shell form
    b. Exec form (Execute form)

    Shell form: 
        When we use this syntax, docker will execute the command in 
        separate shell. That is why it is so called.
        In linux it is '/bin/sh'
        In Windows it is 'cmd' or the command prompt
    Exec form:
        This takes an array of strings. E.g., 
        CMD ["npm", "start"]

    The common best practice is to use the Exec form. Because here we 
    can execute the command directly and don't have to spin up another 
    shell process. Also, it makes it easier and faster to clean up 
    resources when you stop a container.

5. ENTRYPOINT
    This is similar to CMD and this also has 2 forms:
    a. Shell form
    b. Exec form

    The difference is we cannot easily override ENTRYPOINT. To override
    we have to use a flag: --entrypoint
    A lot of people forget to override so it is slightly harder to override
    but you have easily over ride CMD


lesson40: Speeding Up Builds

1. Layers: An image in docker is collection layers. Each layer is like 
    a small filesystem that only includes modified files.
    Each command is layer and that layer only modifies the image based on 
    this instruction.
    
    We can read the info from bottom to top.

2. Optimisation in docker is that it sees the instruction and build the 
    layer if there is any modification. If there are no modification in
    the instruction, it is not going to re-build the layer it is going 
    to reuse it its cache.
    If there is any change in the layer then docker has to rebuild the 
    layer and then entire layers following it.
    So, to optimise our builds, we have to separte the installation of 
    third party dependencies of our application files.

    COPY . .
    - instead of copying the entire files in one go. We can separte what
        is require in the subsequent command so that this particular 
        layer can be reuse and we can save time while creating the image.

3. Takeaway: While writing a Dockerfile. We should keep the instruction 
    that do not change frequently on the top so that the layer can be 
    reused from the cache.

lesson41 - Removing Images

1. Dangling Images with no name and no tag are known as Dangling Images.
    To remove these images, we use the prune command:
    docker image prune
    - removes the dangling images

2. To remove all stopped container:
    docker container prune
    - removes all the stopped containers

3. Use the following command to get all the options related to conatiners:
    docker images
    - lists all the option we can use with 'docker images'

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
        docker image tag <old_image_name:version> <new_image_name>
        docker image tag react-app:latest react-app:1

3. Instead of image name we can also use image ID

4. The 'latest' tag doesn't necessarily mean the latest image. We should
    fix it.


lesson43 - Sharing Images

hub.docker.com

Create a Repository

1. docker login
    - asks username and password to login

2. docker image tag <image_id> <image_name:tag>
    - tags the image. Since we can have multiple tags of an image we
        are tagging it in this format 'zamanmd/react-app:1'

2. docker push
    docker push zamanmd/react-app:1
    - pushes the image to docker hub
    - docker pushes each layer at a time. So the first timee it pushes it 
        takes some time then later it becomes quick assuming we have not 
        changed our application dependencies.

3. After pushing it on docker we can pull it in in machine using docker.


lesson44 - Saving and Loading Images








