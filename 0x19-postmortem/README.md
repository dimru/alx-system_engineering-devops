Summary

duration of the outage

 start :10/10/2022, 3:AM
end : 12/10/2022, 5:PM


impact 

What service was down/slow?

    The whole application running on php 7 crashed during this time lapse.

 What were users experiencing? 

    Users were unable to connect into their accounts , those who were already connected were unable to send any requests (messages)

How many % of the users were affected?

Almost 100% of the users have been affected by this downtime error.    

what was the root cause

The root cause of the error is an update made into production environment while 
some methods were still dependent to previous development stack (php 7, apache 5)

Timeline

when was the issue detected

    The issue has been detected the 10/02/2022 at 5:PM

how was the issue detected

    The issue was detected via the application deployment log which was displaying 
        dependencies alert.

actions taken 

    In order to solve the issue, we proceeded to a rollback of the application 
           development state.

misleading investigation/debugging paths that were taken

    We first tried to convert methods and variables concerned to the new version what      
has led to complications. 

which team/individuals was the incident escalated to

    Incident was escalated to developers team.

how the incident was resolved

    Incident resolved via rollback on the server to the previous application state.
    It made new users lose their accounts but it was the best solution.


Root cause and resolution:

what was causing the issue

    Someone tried to upgrade his local development stack onto the next version but unfortunately he turned up to be upgrading the overall production environnement .
His error passed without devops noticing it then the clients started facing errors to connect or send requests using the methods concerned by the upgrade.
how the issue was fixed

    As explained earlier , the issue has been fixed via a complete rollback of the application including datas to the previous state.
    To be more accurate , we have automated a backup for the application each day at 23:59 PM.
So from 02/02 to 08/02 we made the application work for clients on the 01/02 state but tried to hard fix the issue. It was impossible so we definitely reset the app state to 01/02 erasing the upgrade.

Corrective and preventative measures:

what are the things that can be improved/fixed 

    Set developers' local environment with docker containers so they can do whatever they want without affecting the global system.
a list of tasks to address the issue 

Read log files
Fix logs where error has been shown
Locate concerned files
Identify the current error (“deprecated and unused methods”) message
Tried to update the methods whereas users were deferred on the backup server from the app file of 01:02
reset the whole app state to 01/02
