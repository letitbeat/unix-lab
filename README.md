# Introduction to Unix & Shell Scripting Laboratory

In this laboratory you will practice some of the commands studied at class and gain experience writing shell scripts.

Prepared by: *Jorge López* <jorge.lopez [at] telecom-sudparis.eu> and *José Reyes* <jose.reyes [at] telecom-sudparis.eu>

## Part 1 - Unix Commands

1. Create a directory named Lab1, all exercises will be done in this directory

2. Create a file with the file names in the directory `/usr/lib64` and append to that file the number of files in that directory, name the file 1.txt

3. Create a file containing the command used to recursively display all the files inside the `/usr/` directory that are directories, name the file `2.cmd`

4. Create a file named `3.cmd` containing the command used to recursively display only the name and the modification dates (and times) of the files inside the `/usr/` directory that have the word "power" in the name and that are directories
  
5. Create a file named `1.cmd` and write the command to create a file called `allusrlib64laandsh.txt` with the content of all the files in the directory `/usr/lib64` with the extensions `.la` and `.sh`
  
6. Give only execute rights to the user, none to the group nor to others on the file `1.cmd`; execute the command `1.cmd`, and capture its output on `1.out`, append the command used to execute the file and the output of `ls -l` (to `1.out`)

7. Create a file named `4.cmd` with the command for listing all environment variables that in their content have a colon (:), just the variable names (hint: you can replace for the empty string to delete certain part)

8. Download the file http://www.tcpdump.org/release/tcpdump-4.9.2.tar.gz, decompress it and display all the lines inside all the files of tcpdump that match "0x20"; create a file with the command used to do this, name it `5.cmd` (hint: `find`)
 
9. Create a file named `6.cmd` with the command used display the current temperature in Paris (hint: [wttr.in](https://github.com/chubin/wttr.in))


## Part 2 - shell scripts

### Task 1

Let's warm up our shell scripting skills!

For the first task we will be implementing a basic arithmetic calculator, our calculator should accept 2 arguments from the standard input and compute the addition, difference, multiplication and division of the provided arguments.

Example of the expected output:

```bash
$ ./calculator.sh 20 3
sum 20 + 3 =  23
diff 20 - 3 =  17
mult 20 * 3 =  60
div 20 / 3 =  6
```

In case the user executes the script without any arguments, it should prompt the user a message to enter them.

Example:

```bash
$ ./calculator.sh
Please enter operand a:
3
Please enter operand b:
10

sum 3 + 10 =  13
diff 3 - 10 =  -7
mult 3 * 10 =  30
div 3 / 10 =  0
```

> If you notice something interesting in the results for `div` is the fact that `bash` expression only uses integers, if you like to extend the functionality to allow other than integers, then an external tool like `bc` is necessary

> Hints: variables, arithmetic, `if` statements, `read`

### Task 2

How much free RAM memory do I have in my system? Is there enough to install and run applications?

In Linux systems you can use `free` to get a report on system's memory usage.

The output without using any option, should be something similar to this:

```bash
$ free
            total     used    free     shared   buffers  cached
Mem:          595      482     112         0       63     324

-/+ buffers/cache:      93     501
swap:                   0        0       0
```

Our goal on this task is to implement a light version of `free`! Which when executed will show information of total, used and free RAM in MB.

Example:

```bash
$ ./free.sh
total	free	used
3947 MB	1809 MB	2137 MB
```

> In Unix-like systems *proc* filesystem is a pseudo-filesystem which provides an interface to kernel data structures and system information, you can see information about memory utilization by executing `cat /proc/meminfo`

> Hint: cat, grep, awk

> Bonus: extend your script to accept an argument `n` and based on that the script should print the information `n` number of times every second

Example:

```bash
$ ./free.sh 3
total	free	used
3947 MB	1809 MB	2137 MB
total	free	used
3940 MB	1802 MB	2145 MB
total	free	used
3937 MB	1899 MB	2147 MB
```

### Task 3

For the last task of this laboratory, we will fetching and manipulating data! Fetching/accessing data from the web is a very common task nowdays and Unix-like systems provide us with very handy tools to do so.

The first step to complete this task is to fetch the data in CSV format from the following url:
[https://bit.ly/2ATet9V](https://bit.ly/2ATet9V) and store it in the current directory.

Once we have the file which contains information of users in the following structure:
*id, fist_name, last_name, email* our task is to list the data in the following format *fist_name* *last_name*, *email* but obfuscating the *email* so we don't show sensitive information of the users in the console!

Example of execution:

```bash
$ ./data-processor.sh

Leo Scoles, lscolesg@****.***
Emmanuel Staff, estaffa@****.***
Suzann Terne, sternen@****.***
...
...
```

> Hints: `curl -L`, `sed`

Enjoy!

## Final task

Create a file containing all the files created inside `Lab1` including the scripts, append your name; zip it and email it to us: jorge.lopez [at] telecom-sudparis.eu, jose.reyes [at] telecom-sudparis.eu

