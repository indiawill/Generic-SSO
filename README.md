**************************************************************
* Author: Kunal S. Bhardwaj (Indiawill)                      *
* Role:   Freelance Cyber Security Consultant & C# Developer *
**************************************************************

GenericSSO :: Enterprise Single Sign-On Module

* Parameters will be always starting from Application Name configured in data.ini file
* Commands passed through data.ini file is case-sensitive

* Supported Commands :: 
1. keys 
2. link
3. partial-link
4. button (id/name/xpath/classname/tagname)
5. field1/2/3/4/5/... (id/name/xpath/classname/tagname/send) 
6. msgbox
7. sleep
8. blockinput
9. bringtofront (no parameters)
10. checkfname
11. checkfcname
12. checkfaid
13. while (checkfname/checkfcname/checkfaid)

* Implementation examples for Supported Commands :: 
1. keys
==> This command will implement Microsoft sendkeys calls. Please refer below webportal for more info:
https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.sendkeys.send?view=netcore-3.1
eg: keys:{TAB};keys:{ENTER}

2. link
==> This command will help bypass links like "Continue to this Website" when you invoke any unencrypted webportal
eg: link:Continue to this Website

3. partial-link
==> This command will help bypass links same as above, but in this function you can just provide part of entire string
eg: partial-link:Continue

4. button
==> This command will help automate any button or focusing on any element. Extended parameters are id/name/xpath/classname/tagname.
eg: button:id:userName;button:name:Password

5. field
==> This command will help to automate parameters passed to the program after very first parameter of Application Name. It'll start reading from second parameter passed as field1 and respectively field2,field3,.... and so on. Any "field1 / 2 / 3 / ..." selected in data.ini file with extended command as "send" will jus send that particular placeholder directly to the assigned attribute. 
eg: field1:xpath://*[@id="email"];field2:send

6. msgbox
==> This command will show a message box with the data written in the data.ini file
eg: msgbox:This is a test message;msgbox:Kindly wait till the process completes

7. sleep
==> This command will help to sleep the program for a particular time frame and then executes the next command 
eg: sleep:1000

8. blockinput
==> This command will help to block user input till the process starts for automation. You may define this per time taken by any application to invoke and come to the sign in page or form.
eg: blockinput:5000

9. bringtofront
==> This command doesn't require any extended parameter as it'll directly read from data.ini file "PROCESSNAME" parameter and will bring that mentioned process in front for automation to work like sendkeys using "keys"
eg: bringtofront

10. checkfname
==> This command will help to check whether focused element name is the same as mentioned in data.ini file or not. Mostly to use when sending password on screen
eg: checkfname:username;checkfname:password

11. checkfcname
==> This command will help to check whether focused element classname is the same as mentioned in data.ini file or not. Mostly to use when sending password on screen
eg: checkfcname:username;checkfcname:password

12. checkfaid
==> This command will help to check whether focused element automation ID is the same as mentioned in data.ini file or not
eg: checkfaid:10001;checkfaid:10002

13. while
==> This command have supported extended command i.e. checkfname/checkfcname/checkfaid. This will help to wait for the mentioned attribute to come in focus or in selected mode to do further automation
eg: while:checkfname:username;while:checkfcname:Password
