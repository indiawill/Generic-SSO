GenericSSO :: Enterprise Single Sign-On Module

*IMPORTANT: Minimum .NET Framework 4.8 is required
*Parameters will be always starting from Application Name configured in data.ini file as [SECTION]
*Commands passed through data.ini file is case-sensitive
*SPECIAL CHARACTERS NOT SUPPORTED: BACKSLASH (\) & DOUBLE QUOTES(")

*SUPPORTED COMMANDS :: 
1. keys
2. keyswait
3. staticpassword (id/name/xpath/classname/tagname/send/sendwait)
4. link
5. partial-link
6. button (id/name/xpath/classname/tagname)
7. field1/2/3/4/5/... (id/name/xpath/classname/tagname/send/sendwait/password)
8. msgbox
9. sleep
10. blockinput
11. bringtofront (no parameter/s)
12. checkfname
13. checkfcname
14. checkfaid
15. while (checkfname/checkfcname/checkfaid)
16. invokefile

*Implementation examples for Supported Commands :: 
1. keys
==> This command will implement Microsoft SendKeys 'Send' calls. Please refer below webportal for more info:
https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.sendkeys.send?view=netcore-3.1
eg: keys:{TAB};keys:{ENTER}

2. keyswait
==> This command will implement Microsoft SendKeys 'SendWait' calls. Please refer below webportal for more info:
https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.sendkeys.send?view=netcore-3.1
eg: keyswait:{TAB};keyswait:{ENTER}

3. staticpassword
==> This command will support encrypted password string from a filename
eg: staticpassword:filename:id/name/xpath/tagname/classname/send/sendwait

4. link
==> This command will help bypass links like "Continue to this Website" when you invoke any unencrypted webportal
eg: link:Continue to this Website

5. partial-link
==> This command will help bypass links same as above, but in this function you can just provide part of entire string
eg: partial-link:Continue

6. button
==> This command will help automate any button or focusing on any element. Extended parameters are id/name/xpath/classname/tagname.
eg: button:id:userName;button:name:Password

7. field
==> This command will help to automate parameters passed to the program after very first parameter of Application Name. It'll start reading from second parameter passed as field1 and respectively field2,field3,.... and so on. Any "field1 / 2 / 3 / ..." selected in data.ini file with extended command as "send" will jus send that particular placeholder directly to the assigned attribute. 
eg: field1:xpath://*[@id="email"];field2:send

8. msgbox
==> This command will show a message box with the data written in the data.ini file
eg: msgbox:This is a test message;msgbox:Kindly wait till the process completes

9. sleep
==> This command will help to sleep the program for a particular time frame and then executes the next command 
eg: sleep:1000

10. blockinput
==> This command will help to block user input till the process starts for automation. You may enable at the start of the SSO and disable at the end. 
eg: blockinput:true/false

11. bringtofront
==> This command doesn't require any extended parameter as it'll directly read from data.ini file "PROCESSNAME" parameter and will bring that mentioned process in front for automation to work like sendkeys using "keys"
eg: bringtofront

12. checkfname
==> This command will help to check whether focused element name is the same as mentioned in data.ini file or not. Mostly to use when sending password on screen
eg: checkfname:username;checkfname:password

13. checkfcname
==> This command will help to check whether focused element classname is the same as mentioned in data.ini file or not. Mostly to use when sending password on screen
eg: checkfcname:username;checkfcname:password

14. checkfaid
==> This command will help to check whether focused element automation ID is the same as mentioned in data.ini file or not
eg: checkfaid:10001;checkfaid:10002

15. checkffid
==> This command will help to check whether focused element automation ID is the same as mentioned in data.ini file or not
eg: checkffid:10001;checkffid:10002

16. while
==> This command have support for extended command i.e. checkfname/checkfcname/checkfaid/checkffid. This will help to wait for the mentioned attribute to come in focus or in selected mode to do further automation
eg: while:checkfname:username;while:checkfcname:Password

17. invokefile
==> This command can be used to invoke any file in between or after automation with the confirmation dialog to the user.
eg: invokefile:OKCancel:Do you want the some file to be invoked?:filepath:filearguments;invokefile:YesNo:Some Message:filepath:filearguments
