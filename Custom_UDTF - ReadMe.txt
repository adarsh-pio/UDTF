Since catalog view QSYS2.MESSAGE_FILE_DATA is not available for ibm i versions lower than v7.3 tr6, 
you can use this custom function for the same purpose,  or modify as per convenience and requirement..

Step1 : upload the program CRTMSGDTA as a member into machine. The type will be SQLRPGLE.
Step2 : upload the function source as a member into machine. The type will be SQLFTN. 
Step3 : edit the source in SQLRPGLE for the message file name and library in DSPMSGD command.
Step4 : edit the function source for the library you want to create or remove library name from CALL command to CRTMSGDTA if that is already present in library list
Step5 : compile the sqlrpgle by taking option 14 against it.
Step6 : use command below command to compile the sql function..RUNSQLSTM SRCFILE(PIOLIB/QRPGLESRC) SRCMBR(MSGFFUNC) COMMIT(*NONE) NAMING(*SQL)             

you can access the data of msgf using sql now:  select * from table(msg_file_data())  
or,
use queries in sqlrpgle programs to fetch message file data