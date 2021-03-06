# jlog
<div>
<a href="https://github.com/MichelML/jlog2"><img src="https://travis-ci.org/MichelML/jlog.svg?branch=master"  alt='Build Status'></img></a>
</div>

<p>Save Jira worklogs from the terminal. Stop switching context. Stop relying on your memory.</p>   
<p>The goal is to save your worklog <strong>as you do the actual work</strong>.

## Installation  
  
Clone the repository locally.  
  
```
git clone https://github.com/MichelML/jlog.git  
```

Use an alias to point to the _jlog_ standalone jar in your `.bash_profile` file. 
  
```
alias jlog="java -jar <path to the jlog cloned repo>/target/jlog-0.1.0-SNAPSHOT-standalone.jar"
```

## Usage  

Valid commands for _jlog_ are:

``` 
jlog -h                                            -     Prints the help menu to the console.
jlog -l                                            -     Prints your registered worklogs (contained in a file named jlog.txt) to the console.
jlog -o                                            -     Opens your jlog.txt file.
jlog -b <timelog> <message in quotes>              -     Writes a worklog to the jlog.txt file, retrieving the Jira issue key from your branch (see examples).
jlog <timelog> <issue key> <message in quotes>     -     Writes a worklog to the jlog.txt file using the provided information.
```  

## Examples  

Log a full day for a specific Jira issue  
```  
jlog 1d TEST-12 "write your comment message here"
```
  
Log a full day OR hours and minutes  
```bash
# valid commands
jlog 1d TEST-12 "write your comment message here"
jlog 2h30m TEST-12 "write your comment message here"
jlog 30m TEST-12 "write your comment message here"
jlog 2h TEST-12 "write your comment message here"

# invalid commands
jlog 1d1h TEST-12 "write your comment message here"
jlog 1d30m TEST-12 "write your comment message here"
```   
  
Log for a specific Jira issue retrieved from a repository branch's name. Currently works for Mercurial (hg) repositories only.
```bash
# while in your repository, on a branch having a name containing a Jira issue key (ex: fix-TEST-123-specifics)
jlog -b 1h45m "write your comment message here"
```  
  
Open your `jlog.txt` file at the end of the day and simply use the saved information to enter your worklogs in Jira.  

```bash
# Opens your jlog.txt file  
jlog -o
```

You can also print saved information in your terminal with the following command.

```bash
# Prints your jlog.txt content to the terminal 
jlog -l
```
