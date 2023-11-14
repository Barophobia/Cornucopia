+++
title = "Force a remote group policy update"
chapter = true
+++

### Steps to force a remote group policy update 

- Open GPMC
- Right-Click the OU that you want to update
- Click 'Group Policy Update'
  
 
The remote Group Policy refresh updates all Group Policy settings, including security settings that are set on a group of remote computers, by using the functionality that is added to the context menu for an OU in the Group Policy Management Console (GPMC). When you select an OU to remotely refresh the Group Policy settings on all the computers in that OU, the following operations happen:
 
An Active Directory query returns a list of all computers that belong to that OU.
 
For each computer that belongs to the selected OU, a WMI call retrieves the list of signed in users.
 
A remote scheduled task is created to run GPUpdate.exe /force for each signed in user and once for the computer Group Policy refresh. The task is scheduled to run with a random delay of up to 10 minutes to decrease the load on the network traffic.
